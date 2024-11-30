# Create an LLM app with deep understanding of a GitHub repo

## Overview  

This repository contains scripts designed to extract and summarize data from various sources, including GitHub repositories, local folders, and custom data formats. Additionally, it provides tools to generate summaries and Q&A pairs from CSV files for knowledge-based applications.  

Follow the steps outlined below to use the scripts effectively.  

---  

## Prerequisites  

Before running the scripts, ensure the following tools and libraries are installed:  

1. **Python**: Version 3.10 or above  
2. Required Python libraries: Install them using the `requirements.txt` file:
   ```bash
   pip install -r requirements.txt
   ```  
---  

## Script Descriptions  

### **Data Parsing Scripts**  

1. **GitHub Parser** (`github_parser.py`)  
   Extracts data from a GitHub repository and creates a CSV file.  
   - **How to Run**:
     ```bash
      python github_parser.py <repo_path> <output_path> --exclude folder1 folder2
     ```

2. **Local Folder Parser** (`local_parser.py`)  
   Extracts data from a local folder and creates a CSV file.  
   - **How to Run**:
     ```bash
     python local_parser.py /path/to/local/repo output.csv --exclude folder1 folder2
     ```

3. **Repopack Parser** (`repopack_parser.py`)  
   Processes a `.txt` file generated by the Repopack tool and creates a CSV file.  
   - **How to Run**:
     ```bash
     python repopack_parser.py <input_text_file> <output_csv_file>
     ```

### **Summarizer and Q&A Generator Scripts**  

1. **Summarizer and Q&A Generator** (`summarizer.py`)  
   Processes a CSV file containing textual data to generate summaries and Q&A pairs.  
   - **How to Run**:
     ```bash
     python summarizer.py <input_csv> <output_csv>
     ```
   - **Output**:  
     - A CSV file with the original content, generated summaries, and Q&A pairs.  

2. **Individual Operation Scripts**:  
   - Separate scripts are available for running **only one operation** at a time:  
     - **Summary Only**: Use `summary_only.py`  
     - **Q&A Only**: Use `qna_only.py`  
   - **How to Run**:
     ```bash
     python summary_only.py <input_csv> <output_csv>
     python qna_only.py <input_csv> <output_csv>
     ```  

---  

## Workflow  

### **Step 1: Parse Data**  
Choose the appropriate parser script based on your data source. Run the script to generate a CSV file with raw content.  

### **Step 2: Summarize and Generate Q&A Pairs**  
Use the `summarizer.py` script to process the CSV file and generate summaries and Q&A pairs.  

### **Step 3: Individual Operations (Optional)**  
If you need only summaries or Q&A pairs, use the corresponding individual operation script.  

---  

## Automate the Workflow  

To keep the process automated, you can set up a cron job for periodic execution of the summarizer or parser scripts.  

### **Example Cron Job for Daily Updates**  
1. Open the crontab editor:
   ```bash
   crontab -e
   ```
2. Add the following line to run the summarizer at midnight:
   ```bash
   0 0 * * * python /path/to/summarizer.py /path/to/input.csv /path/to/output.csv >> /path/to/logfile.log 2>&1
   ```
3. Save and exit.  

---  

## Notes  

- Ensure input CSV files are well-formed and contain valid textual data.  
- For large datasets, the processing time may vary depending on system resources.  
- Modify the `summarizer.py` script to adjust the prompt or model settings as needed.  
- The repository is structured to support additional scripts for parsing or summarizing different formats.  
- Once the database is created using these scripts, it can be utilized to generate a knowledge base that helps address issues related to a specific repository. For more information, refer to [this resource](https://github.com/staru09/Gradio_bot).
- Knowledge bases for certain repositories, along with the final CSV files containing summaries and Q&A pairs, can be accessed [here](https://docs.google.com/spreadsheets/d/1_hRiQkVr9Dl2BLyjY87XjfReXUow0c9vKNA4nw_s34g/edit?usp=sharing).
- An example of creating a knowledge base for Gradio can be found [here](https://github.com/staru09/Gradio_bot)
---  

## Additional Resources  

- [Python Official Documentation](https://docs.python.org/)  
- [Gaianet Tools](https://docs.gaianet.ai/)  

