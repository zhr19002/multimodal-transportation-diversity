## Portfolio Risk Assessment — InsurAIR Flood Loss Modeling

### Overview
Computes flood-induced losses for an insurance portfolio, including:
- Building loss
- Time element loss
- Total portfolio loss
- Exceedance Probability (EP) curve and Average Annual Loss (AAL)

### Inputs
- `FloodIntensityFile_AIRton_2021.dat` — EventID, GridID, flood intensity  
- `InsurAIR_BuildingDamageFunction.xlsx` — mapping + depth-damage curves
- `InsurAIR_TimeElementDamageFunction.xlsx` — damage ratio → downtime
- `InsurAIR_ExposurePortfolio_2021.csv` — exposure data

### Core functions
- **IntensityFunction**: Maps location → flood depth via grid averaging
- **BuildingDamageFunction**: Maps building attributes → damage ratio
- **TimeElementDamageFunction**: Converts damage ratio → downtime

### Workflow
1. Load and preprocess data
2. For each location and event:
   - Compute flood depth
   - Compute damage ratio
   - Calculate building and time element losses
3. Aggregate to portfolio level
4. Generate EP curve and AAL

### Outputs
- `InsurAIR_LocationEventLossTable.dat` — event-level losses
- `InsurAIR_EPCurve.dat` — EP curve + AAL
