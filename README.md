# predicting-amount-of-gold-extracted

## Project Description
Prepare a prototype machine learning model for Zyfra. The company is engaged in developing efficient solutions for heavy industry.

Your model should be able to predict the amount of gold extracted or recovered from gold ore. There are data related to the extraction and refining process of gold ore that you can use.

Eventually, the model is expected to help create a more efficient production process and eliminate parameters that are not profitable.

You need to:

Prepare the available data
Run data analysis
Develop and train the model
To complete this project, you may need to use documentation from the Pandas, Matplotlib, and Sklearn libraries.

## Process Technology
How to extract gold from gold ore? Let's take a look at the stages of this extraction process.
The mined ore undergoes primary processing to obtain a coarser ore mixture or feed. The results of that process are used as feedstock for flotation (aka the process to produce a coarser concentrate). After flotation, the resulting particles go through a two-stage refining process.

![image](https://github.com/sultanazhari/predicting-amount-of-gold-extracted/assets/89324682/8508de7a-e284-4172-b7f6-14a5add2e44b)


Let's break down the process:

1. Flotation

The gold ore mixture is fed into a float tank to obtain Au concentrate and coarser tails (product residue with low concentration levels of precious metals).

The stability of this process is affected by the volatility and non-optimal physicochemical state of the flotation pulp (a mixture of solid particles and liquid).

2. Refining

The coarser Au concentrate undergoes two stages of refining. After the refining process, we will also have a final metal concentration grade and a new tail.

## Data description
#### Process technology

- Rougher feed - raw material for the flotation process
- Rougher additions (or reagent additions) - reagents for flotation: Xanthate, Sulphate, Depressant
- Xanthate - flotation activator or activators
- Sulphate - sodium sulphide, specific to this process
- Depressant - sodium silicate
- Rougher process - flotation
- Rougher tails - product residue
- Float banks - flotation unit
- Cleaner process - purification
- Rougher Au - coarser gold concentrate
- Final Au - final gold concentrate
- Parameters of each stage are available

- air amount - air volume
- fluid levels
- feed size - feed particle size
- feed rate


#### Feature naming

Here is how to name the features:

[stage].[parameter_type].[parameter_name]

Example: rougher.input.feed_ag

Possible values for [stage]:

- rougher - flotation
- primary_cleaner - first purification
- secondary_cleaner - second purification
- final - final characteristics

Possible values for [parameter_type]:

- input - raw material parameters
- output - product parameters
- state - a parameter indicating the characteristics of the current stage
- calculation - characteristic calculation

![image](https://github.com/sultanazhari/predicting-amount-of-gold-extracted/assets/89324682/8b727096-8dc6-4ebe-a7e5-cd01977fd699)


#### Calculation for recovery
You need to simulate the process of gold recovery from gold ore.

Use the following formula to simulate the recovery process:
![image](https://github.com/sultanazhari/predicting-amount-of-gold-extracted/assets/89324682/bfaeb8f5-2950-4fbb-ba27-76170774942f)


With:
<br>
C - percentage of gold in the concentrate right after the flotation process (to find the recovery of the coarser concentrate)/ after refining (to find the recovery of the final concentrate)<br>
F - percentage of gold in the feed before the flotation process (to find the coarser concentrate recovery)/ in the concentrate right after the flotation process (to find the final concentrate recovery)<br>
T - percentage of gold in the coarser tail, right after the flotation process (to find the coarser concentrate recovery)/ after refining (to find the final concentrate recovery)<br><br>
To predict the coefficient, you need to find the percentage of gold in the concentrate and the tails. Remember that both the final concentrate and the coarser concentrate are equally important.

#### Evaluation metrics
To solve the problem at hand, we will need a new metric. It is called sMAPE (symmetric Mean Absolute Percentage Error). 

sMAPE is similar to MAE, except that sMAPE is expressed in relative values instead of absolute values. So, why is this metric called symmetrical? Well, that's because sMAPE takes into account the scale of both the target and the prediction.

Here is how to calculate sMAPE:
![image](https://github.com/sultanazhari/predicting-amount-of-gold-extracted/assets/89324682/d4cb35b0-fab1-433b-866f-61890b8f4913)


We need to predict two values:

Rougher concentrate rougher.output.recovery
Final concentrate recovery final.output.recovery
The last metric includes two values:
![image](https://github.com/sultanazhari/predicting-amount-of-gold-extracted/assets/89324682/b6227203-aa9d-40ca-a65a-5449cc5b3197)
