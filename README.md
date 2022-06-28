# :baseball: MLB Hard Hits to Player Value

For this project, my objective is to see if an MLB player hitting the ball hard makes them statistically more valuable. I will be comparing the correlation between Hard Hit Rate and Average Exit Velocity with Wins Above Replacement(WAR). 

I will also measure the correlation of more traditional baseball stats to WAR, compare them to the hard hit stats, and use the highest correlated one to run a simple Linear Regression model to determine if it is a good predictor of WAR. 

To help complete this project I will be using the Python package Pandas as well as numpy, matplotlib, seaborn, and SKlearn

## Background

I was watching the New York Mets broadcast when they played a clip from an interview with 2B/OF Jeff McNeil where they discussed his strong start to the 2022 season. [Here is the clip](https://youtu.be/bdelnn9rQT8?t=52) In this interview Jeff credited a change in his approach at the plate to his early success. He states that over the last two seasons he was only trying to hit the ball hard, while this year he is simply "hitting it where they're not". This made me question: Is hitting the ball hard statistcally more valuable? What is the measureable relationship between hitting the ball hard and total player value? How does hitting the ball hard stack up when compared to more traditional baseball stats?

## The Categories

<div align="center">

| Statistic                  | Description                                                                                   |
|:---------------------------|:----------------------------------------------------------------------------------------------|
| At Bats(AB)                |  Total At Bats a player recorded in the given season. At Bats are outcome dependent   |
| Runs(R)                    |  Total Runs scored in the given season                   |
| Home Runs(HR)              |  Total Home Runs a player hit in the given season                                     |
| Runs Batted In(RBI)        |  Total Runs a player drove in while at the plate |
| Batting Average(BA)        |  The number of hits a player records divided by his total at-bats|
| On Base Percentage(OBP)    |  The frequency that a batter reaches base per plate appearance|
| On Base Plus Slugging(OPS) |  Displays how well a hitter can reach base, hit for average, and power|
| Plate Appearances(PA)      |  Total turns a batter takes at the plate regardless of outcome |
| Exit Velocity(EV)          |  The average speed of the ball off the players bat|
| Hard Hit Rate(HardH%)      |  The frequency that a player bats a ball of 95mph or greater |
| Wins Above Replacement(WAR)|  Total player value when measured against a replacement level player |
</div>

To help further understand WAR here is the breakdown from Baseball Reference:
    
    WAR for position players has six components:

        ⋅⋅*Batting Runs
        ⋅⋅*Baserunning Runs
        ⋅⋅*Runs added or lost due to Grounding into Double Plays in DP situations
        ⋅⋅*Fielding Runs
        ⋅⋅*Positional Adjustment Runs
        ⋅⋅*Replacement level Runs (based on playing time)

    The first five measurements are all compared against league average, so a value of zero will equate to a league average player. Less than zero means worse than average, and greater than zero means better than average. These five correspond to the first half of our equation above (Player_runs - AvgPlayer_runs). The sixth factor is the second half of the equation (AvgPlayer_runs - ReplPlayer_runs).

If you would like a more complete explanation on how WAR is calculated you can check the source page [here](https://www.baseball-reference.com/about/war_explained_position.shtml)

## The Data

The data I will be using will be from the 2021 MLB season which I downloaded in CSV format from baseball-reference [here](https://www.baseball-reference.com/leagues/majors/2021-standard-batting.shtml). 

