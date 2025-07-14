# HonoursResearchProject
This respository shows all the python code and data used for this project.

•	Load Profile Matching Algorithm: An algorithm, designed with the assistance of Google Gemini 2.5 Pro, was developed to match or approximate the measured power data (from CSV) with the farm's load specifications and estimated operating times. This automated the estimation of actual operating schedules for each load, which were then used to build the digital twin in Simulink. This script also performed power profile optimization using scipy.optimize.minimize (L-BFGS-B method) to best fit measured power while minimizing errors and penalizing daily usage constraint violations. Results were exported to CSV and MATLAB .mat formats .

•	kWh and Cost Calculation: A Python code was developed to calculate the daily and monthly electricity energy consumption (kWh) from the time-series power data using the trapezoidal integration method. It also calculated the cost based on a tiered City Power tariff, processing each calendar day and filling missing time intervals with zero power.

•	Data Point Reduction for Initial Simulations: To manage computational load during initial simulations, the data (originally 2324 rows with multiple power columns) was condensed. For some test runs, one day with the highest power consumption (7 May 2025, 11h05 to 8 May 2025, 11h00) and one day with the lowest (3 May 2025 to 4 May 2025) were selected. This resulted in 288 data points per day (5-minute intervals). This was further reduced to 24 points per day (hourly peaks) for certain rapid test simulations, though this introduced a Mean Absolute Percentage Error (MAPE) around 50.12%.

•	Irradiance Data Upsampling: The hourly irradiance data was upsampled from 24 points to 288 points per day using cubic interpolation in Python to match the 5-minute resolution of the load data for final simulations.
