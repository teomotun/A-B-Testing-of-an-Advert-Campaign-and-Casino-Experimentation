## Advert Data A/B Testing and Casino Simulation Experiment

#### Part 1: Probability

Q1: Craps
The casino game of craps is played as follows:

1. The player rolls a pair of standard 6-sided dice and takes their sum
a. If the sum is 7 or 11, then the player wins and the game is over
b. If the sum is 2, 3, or 12, then the player loses (this is called “crapping out”) and the game is over
c. If the sum is anything else, then we record the sum (lets call it “X”) and continue to the next step

2. The player then rerolls the dice and takes their sum
a. If the sum is X, the player wins and the game is over
b. If the sum is 7, the player loses and the game is over
c. If the sum is anything else, repeat step 2.

Now suppose that you notice something odd - one of the two dice isn’t balanced that well, and always comes up in the range 2-5 (with equal probability) but never 1 or 6.
1. For each number between 2 and 12, what is the probability of rolling the dice so that they sum to that number?

2.  a. What’s the probability of winning on the very first roll?
    b. What’s the probability of losing (“crapping out”) on the very first roll?

3. Suppose that on the first roll, you do not win or lose, but rather, you get the sum X, which has roll probability p. Given that you have already made it to this point, what’s your chance of winning going forward?

4. If you bet a dollar on a game of craps with these two dice, what is the expected return? (If you win, you will get your original dollar back plus a second dollar; if you lose, then you do not get your dollar back)

a. What is the expected return on that dollar?


#### Part 2: Experiment Analysis

Context
An advert company  provides a platform where businesses can create advertising campaigns to increase awareness of their brands or to increase adoption of their products or services. For this bexercise, imagine we have a single ad product where advertisers pay us each time a user clicks on their ad. Each campaign has a budget (how much money the advertiser is willing to spend during a period of time). An advertiser never has to pay more than their budget, so if we were to spend more than the campaign’s budget, we would not be able to bill the advertiser for the additional spend. This is called overspending . In practice it’s difficult to avoid overspending because there is a delay between when we send ads to users and when they actually click on those ads. Since the company only charges advertisers for actual clicks on their ads, the charges can enter into the system after some (random) delay. For example, suppose a campaign has $10 of budget remaining and the ad serving systems serves out 1000 ads, expecting 10 of them to generate a click resulting in $1 of revenue each. If, however, 20 ads end up generating clicks, we would
receive $20 worth of events and not be able to bill the advertiser for $10 of that. Ultimately, this implies the company has “wasted” $10 worth of ad placements (say 500 in this example) and therefore has incurred a cost.

Suppose that lately, we have been noticing an increase in overspend on the platform. In an attempt to reduce the amount of overspend, we decided to create a new product where advertisers pay each time their ad appears in a user’s viewport rather than each time it is clicked on -- presumably these engagements would be received at a lower latency. In order to test the
new product, we ran an A/B test. We randomly split the advertisers on the platform. Half of the advertisers remained on the old product and half received the new product. A week later we have some data and want to determine whether or not the experiment was a success.


**Data Schema**

Use the data in the attached CSV to answer the questions in the next section.

Column Type Meaning
* treatment => bool If true, the campaign is using the new product. If false, it is using the old product.
* company_size => categorical A small company is typically a local business, a medium company is a smaller national brand (e.g. Dell Computers), and a large company is a global brand (e.g. McDonalds). This is included because businesses of different sizes
use the company's ads in very different ways and may react differently to the new product.
* campaign_spend => decimal Campaign spend during the experiment
* campaign_budget => decimal Campaign budget during the experiment


**Questions Answered**

1. How many campaigns have overspend of greater than 1% of their budget in the control group? In the treatment group?

2. Was the new product effective at reducing overspend, and was it more or less effective depending on the company size? Put together an analysis describing how the treatment affected overspend.

3. A product manager on the team is concerned that certain advertisers in the treatment group are entering lower budgets because they are wary of the new product. Provide some evidence to support their suspicions, or show that any differences in budgets are likely due to random fluctuations.

