# Missed Medical Appointments

An exploratory data analysis of over 100,000 medical appointment records from Espirito Santo state (Vitoria), Brazil, investigating why patients miss scheduled appointments. This project was completed as the introductory data analysis project for Udacity's Data Analyst Nanodegree.

## Data

The dataset is the "Medical Appointment No Shows" dataset from Kaggle: [https://www.kaggle.com/datasets/joniarroba/noshowappointments](https://www.kaggle.com/datasets/joniarroba/noshowappointments). It contains roughly 100,000 medical appointment records, including patient demographics (age, gender, neighborhood), health conditions (hypertension, diabetes, alcoholism, handicap), whether the patient held a scholarship, whether an SMS reminder was received, and whether the patient showed up for the appointment.

The CSV file is not included in this repository. To run the notebook, download the dataset from the Kaggle link above and save it in the project directory as `appointment_data.csv`.

## Method / What was done

The notebook cleans and explores the dataset, then investigates three research questions:

- Do patients with multiple scheduled appointments miss appointments more often than patients with only one appointment?
- Do no-show rates vary meaningfully by neighborhood?
- Are patients who receive an SMS reminder less likely to miss their appointment than patients who do not?

Data wrangling steps include: correcting misspelled column names ("Hipertension" to "Hypertension," "Handcap" to "Handicap"), renaming "Neighbourhood" to "Neighborhood" and "No-show" to "No_show," converting the "ScheduledDay" and "AppointmentDay" columns to datetime64, converting "PatientId" to a fixed-width integer, and filtering out records with an invalid age (a value of -1) and patients under 18. Missed-appointment rates were then compared across patient groups using pandas grouping and aggregation, and visualized with bar and pie charts (matplotlib and seaborn).

## Key findings

- Comparing patients with more than one appointment to patients with only one appointment showed no meaningful difference in no-show rate: both groups missed appointments about 20% of the time on average.
- No-show rates varied by neighborhood. The neighborhood "Santos Dumont" had a no-show rate of roughly 29% (n=967), compared to roughly 8.6% (n=35) for "Ilha do Boi." Given that the overall mean no-show rate across neighborhoods was about 20% with a standard deviation of about 1%, both of these neighborhoods fell outside two standard deviations of the mean.
- Patients who received an SMS reminder missed appointments more often (about 26%) than patients who did not receive one (about 16%), the opposite of the expected direction. Possible explanations discussed in the notebook include self-selection (patients who anticipate missing appointments may be more likely to sign up for reminders) or that patients without SMS reminders were reached through another, more effective channel (such as a phone call) not captured in the data.

These findings are exploratory and observational; the notebook does not run formal statistical significance tests, and the analysis is limited to about three months of data from the summer of 2016.

## Repository structure

- `Understanding+Missed+Medical+Appointments.ipynb`: the analysis notebook, covering data wrangling, exploratory data analysis, and conclusions.
- `README.md`: this file.
- `LICENSE`: MIT license.

## How to run

This notebook was written in 2018 against Python 2.7 with a Jupyter/IPython kernel; the library versions in use at the time are not pinned and are considered historical rather than reproducible as-is. To run it today, use a current Python 3 environment with Jupyter installed, along with:

- pandas
- numpy
- matplotlib
- seaborn

Download the dataset CSV from the Kaggle link above, save it as `appointment_data.csv` in the project directory, and run the notebook cells in order. Note that the notebook contains a small number of Python 2 print statements (for example, `print appointments_df.count()`) that will need to be updated to Python 3 syntax (`print(appointments_df.count())`) to run under a modern kernel.

## License

Released under the MIT License. See [LICENSE](LICENSE) for details.
