# Real time Scenarios
- Scenario 01
- Scenario 02
- Scenario 03
- Scenario 04

## Scenario 01: Execute 'COPY ACTIVITY' when the file becomes available using Control-Flow Activity in ADF
In order to achieve this scenario, we have to use the 'Validation' activity under the 'General' catagory.
Steps:
- Add the 'Validation' activity in the pipeline workpace.
- Configure it.
  - Provide the name of the Validation activity
  - Point to the Data Set which the Validation is watch it.
  - Set the Time in the form of [ days.hours.minute.second ]
  - Set the Interval of the time which the validation activity will look for the file at a frequency. say 10sec, 100 seco, etc.
- Post Configuration.
  - Connect to the pipeline 'On completion' or 'On success'
  - Connect to the other activity 'On fail'
 
## Scenario 02: Execute 'Copy Activity' only if the file contents are as expected

## Scenario 03: Delete the File once the pipeline is completed
Here we use Delete activity inside the If activity


# Triggers
In the production level scenario, this pipeline has to run automaton. In order to make the automation, we can configure the Trigger points. The pipeline can  be triggered from 3 different ways:
- Schedule trigger
- Tumbling window trigger
- Event Trigger

| IMPORTAND
Difference between the Schedule trigger and Tumbling trigger
Schedule trigger:
Schedule triggers run pipelines on fixed recurring schedules like cron jobs, while tumbling window triggers process data in non-overlapping time slices with advanced dependency and backfill support.

## When to Use:
### Schedule Trigger: 
  Simple periodic jobs without data slicing or dependencies. "Use for daily reports or non-time-partitioned ETL where backfill isn't needed—e.g., nightly full backup."
### Tumbling Window: 
  Streaming-like batch processing with time windows, dependencies, or re-runs. "Ideal for hourly data lake ingestion where downstream pipelines depend on prior window success, or backfilling missed runs."
​
