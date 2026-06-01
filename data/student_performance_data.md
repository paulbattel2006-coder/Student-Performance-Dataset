# Student Performance Dataset - Portuguese Language

## Introduction and problem statement
This dataset approaches student achievement in secondary education at two Portuguese schools: Gabriel Pereira (GP) and Mousinho da Silveira (MS). The data evaluates student performance specifically in the **Portuguese language (por)** subject. It was collected through a combination of official school reports and student questionnaires to capture demographic, social, and school-related features.

As established in the foundational study by *Cortez and Silva (2008)*, the primary machine learning problem is predicting academic outcomes based on these multifaceted background features. This can be approached as a classification task (e.g., binary pass/fail or five-level grading eras) or a regression task to pinpoint exact scores.

An essential nuance of this problem statement lies in the predictive timeline: the final year grade (**G3**) is strongly correlated with the first-period (**G1**) and second-period (**G2**) grades. While predicting **G3** using **G1** and **G2** yields higher accuracy, modeling **G3** *without* using previous period grades serves as a much more difficult—yet significantly more useful—predictive tool for early intervention systems.

---

## Contained attributes
The underlying data is stored in the file `student-por.csv`. It contains 649 student records across 33 attributes, detailing demographics, family background, academic habits, and lifestyle factors:

### School & Demographic Features
*   `school`: Student's school (binary: 'GP' - Gabriel Pereira or 'MS' - Mousinho da Silveira)
*   `sex`: Student's sex (binary: 'F' - female or 'M' - male)
*   `age`: Student's age (numeric: from 15 to 22)
*   `address`: Student's home address type (binary: 'U' - urban or 'R' - rural)
*   `famsize`: Family size (binary: 'LE3' - less than or equal to 3 or 'GT3' - greater than 3)
*   `Pstatus`: Parent's cohabitation status (binary: 'T' - living together or 'A' - apart)

### Family & Socioeconomic Features
*   `Medu`: Mother's education (numeric: 0 - none, 1 - primary education (4th grade), 2 - 5th to 9th grade, 3 - secondary education, or 4 - higher education)
*   `Fedu`: Father's education (numeric: 0 - none, 1 - primary education (4th grade), 2 - 5th to 9th grade, 3 - secondary education, or 4 - higher education)
*   `Mjob`: Mother's job (nominal: 'teacher', 'health' care related, civil 'services', 'at_home', or 'other')
*   `Fjob`: Father's job (nominal: 'teacher', 'health' care related, civil 'services', 'at_home', or 'other')
*   `reason`: Reason to choose this school (nominal: close to 'home', school 'reputation', 'course' preference, or 'other')
*   `guardian`: Student's guardian (nominal: 'mother', 'father', or 'other')

### Academic Context & Habits
*   `traveltime`: Home to school travel time (numeric: 1 - <15 min., 2 - 15 to 30 min., 3 - 30 min. to 1 hour, or 4 - >1 hour)
*   `studytime`: Weekly study time (numeric: 1 - <2 hours, 2 - 2 to 5 hours, 3 - 5 to 10 hours, or 4 - >10 hours)
*   `failures`: Number of past class failures (numeric: $n$ if $1 \le n < 3$, else 4)
*   `schoolsup`: Extra educational support (binary: yes or no)
*   `famsup`: Family educational support (binary: yes or no)
*   `paid`: Extra paid classes within the course subject (binary: yes or no)
*   `activities`: Extra-curricular activities (binary: yes or no)
*   `nursery`: Attended nursery school (binary: yes or no)
*   `higher`: Wants to take higher education (binary: yes or no)
*   `internet`: Internet access at home (binary: yes or no)

### Social, Lifestyle & Health Features
*   `romantic`: With a romantic relationship (binary: yes or no)
*   `famrel`: Quality of family relationships (numeric: from 1 - very bad to 5 - excellent)
*   `freetime`: Free time after school (numeric: from 1 - very low to 5 - very high)
*   `goout`: Going out with friends (numeric: from 1 - very low to 5 - very high)
*   `Dalc`: Workday alcohol consumption (numeric: from 1 - very low to 5 - very high)
*   `Walc`: Weekend alcohol consumption (numeric: from 1 - very low to 5 - very high)
*   `health`: Current health status (numeric: from 1 - very bad to 5 - very good)
*   `absences`: Number of school absences (numeric: from 0 to 93)

### Periodic Grades
*   `G1`: First period grade (numeric: from 0 to 20)
*   `G2`: Second period grade (numeric: from 0 to 20)

---

## Potential targets

The primary target variables represent student academic performance evaluating the subject. Depending on the machine learning setup, you can target multiple goals using the numeric grade variables or the final outcome:

*   **`G3` (Final Grade):** The core target attribute. It represents the final year grade issued during the 3rd period (numeric: from 0 to 20).
*   **Regression Targets:** Predicting the exact numerical value of `G3` directly using feature sets (with or without `G1` and `G2`).
*   **Binary Classification Target:** Transforming `G3` into a pass/fail output (e.g., $\text{Grade} \ge 10$ as Pass, $\text{Grade} < 10$ as Fail).
*   **Five-Level Classification Target:** Mapping `G3` into the traditional five-level European grading system based on specific score brackets (e.g., Excellent, Good, Satisfactory, Sufficient, Fail).