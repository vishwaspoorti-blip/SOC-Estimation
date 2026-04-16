# SOC-Estimation
State of Charge (SOC) is the "fuel gauge" for batteries, representing the energy level relative to capacity. Since charge can't be measured directly, it's estimated using voltage, current, and temperature data. Methods range from Coulomb Counting to Kalman Filters. Accurate SOC is vital for range prediction, safety, and battery longevity in EVs.
below shown should be added in the command window
%% --- 1. BATTERY PARAMETERS (Lead-Pb / ECM) ---
Cn = 10;            % Nominal Capacity (Ah)
Q = Cn * 3600;      % Capacity in Coulombs (As)
SOC_init = 0.8;     % Starting at 80% charge
r = 0.012;          % Internal Resistance (Ohms)
R0 = 0.012;         % Ohmic Resistance
R1 = 0.005;         % Polarization Resistance 1
C1 = 2000;          % Polarization Capacitance 1
Cx = 1000;          % Diffusion Capacitance
Rx = 0.01;          % Diffusion Resistance
C0 = 500;           % Main Capacitance
m = 0.1;            % OCV-SOC Slope
E0 = 12.6;          % Full Charge Voltage

%% --- 2. VEHICLE DYNAMICS (For 'dynamique du véhicule' block) ---
g = 9.81;           % Gravity (m/s^2)
G = 9.81;           % Duplicate for alternative block names
M = 1200;           % Vehicle Mass (kg)
rho = 1.225;        % Air Density (kg/m^3)
Cd = 0.3;           % Aerodynamic Drag Coefficient
A = 2.2;            % Frontal Area (m^2)
Rw = 0.3;           % Wheel Radius (m)
f = 0.015;          % Rolling Resistance Coefficient

%% --- 3. OBSERVER GAINS (Luenberger, SMC, Super Twisting) ---
S = 1;              % Sliding Surface Slope
L = 0.5;            % Luenberger Gain
lambda = 0.1;       % Sliding Mode Constant
gamma = 0.05;       % Switching Gain
k = 1;              % General Gain constant
k1 = 10;            % Super Twisting Gain 1
k2 = 5;             % Super Twisting Gain 2
sigma = 0.05;       % Chattering Reduction Constant

fprintf('All parameters loaded. You can now press RUN in Simulink.\n');
All parameters loaded. You can now press RUN in Simulink.
>> 
