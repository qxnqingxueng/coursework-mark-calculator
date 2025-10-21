# 🧮 Coursework Mark Calculator (C++)

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1_OH_1dVZRkIuFCDdH8ZACEFxmWO9BvxO?usp=sharing)

---

## 1️⃣ Project Overview
The **Coursework Mark Calculator** is a specialized **C++ program** developed to assist the **CPT111 lecturer** in efficiently calculating and managing coursework marks.  

The program reads raw student data, validates lecturer-defined weightages, performs automatic weighted mark calculations, assigns grades, and outputs the final results into a structured report file.  

This system eliminates manual calculation errors and automates repetitive academic grading tasks.

---

## 2️⃣ Data Flow and Requirements

### 📥 Input Data
The program operates using **two input sources** — user-defined settings and an external data file.

| Input Type | Source | Data Points |
|-------------|--------|-------------|
| **User Input (Settings)** | Runtime (main function) | Total coursework percentage, total number of students (`NumStudent`), and individual weightages for Test 1, Test 2, Assignment 1, and Assignment 2 (`WeightageT1`, `WeightageT2`, `WeightageA1`, `WeightageA2`). |
| **File Input (Scores)** | `CPT111_CwMarks.txt` | Matric number, and raw scores for Test 1, Test 2, Assignment 1, and Assignment 2. |

---

### ✅ Core Validation
Before computation begins, the program enforces strict validation on weightage inputs:

- A `while` loop continuously checks that the **sum of all weightages** (`WeightageT1 + WeightageT2 + WeightageA1 + WeightageA2`) equals the **total coursework percentage**.  
- If incorrect, the program prompts the user to **re-enter** all weightages until the sum matches.  

This ensures consistent grading proportions and prevents calculation errors.

---

## 3️⃣ Calculation Logic and Output

### 🧮 Conversion & Weighted Mark Calculation
Each student’s marks are calculated using the following process:

1. Convert raw marks to weighted marks:  
   \[
   \text{WeightedMark} = \text{OriginalMark} \times \frac{\text{Weightage}}{100}
   \]
2. Sum all weighted marks using the `Calculate` function to get each student’s total coursework score (`total[i]`).

---

### 🏷️ Grading Logic
The `Grading` function assigns grades based on percentage thresholds of the total coursework mark:

| Grade | Criteria |
|:------:|-----------|
| **A** | 80.0 ≤ total ≤ 100.0 |
| **B** | 70.0 ≤ total < 80.0 |
| **C** | 60.0 ≤ total < 70.0 |
| **D** | 50.0 ≤ total < 60.0 |
| **F** | total < 50.0 |

This grading mechanism ensures standardized academic evaluation across all students.

---

### 🗂️ Output File Structure
All results are exported to a file named **`CPT111_CwMarks_Output.txt`**, containing detailed information per student:

| Field | Description |
|--------|-------------|
| 1 | Matric Number |
| 2 | Test 1 Score |
| 3 | Test 1 Weighted Mark |
| 4 | Test 2 Score |
| 5 | Test 2 Weighted Mark |
| 6 | Assignment 1 Score |
| 7 | Assignment 1 Weighted Mark |
| 8 | Assignment 2 Score |
| 9 | Assignment 2 Weighted Mark |
| 10 | Total Coursework Mark (based on Total Percentage) |
| 11 | Final Percentage Score (out of 100) |
| 12 | Grade |

---

## 4️⃣ Validation Rules Summary

| Validation | Description |
|-------------|-------------|
| **Weightage Validation** | Ensures total weightage sum matches overall coursework percentage. |
| **Input Range Validation** | Confirms entered marks and percentages are within valid numeric bounds. |
| **Data Integrity Check** | Verifies data format consistency in the input file. |

---

## 5️⃣ How to Compile and Run

### ⚙️ Required Files
- `main.cpp`  
- `CPT111_CwMarks.txt` (input file containing student scores)

### 💻 Compilation Command
```bash
g++ main.cpp -o CourseworkCalculator.exe
./CourseworkCalculator.exe
