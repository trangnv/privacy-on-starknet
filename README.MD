# Privacy on StarkNet

By default, Starknet transactions and their payloads are visible to the network in the same way that they are visible on Ethereum. It would be more appropriate to call StarkNet a validity rollup rather than zk-rollup.

However, it is possible to deploy various privacy protocols on StarkNet, which will offer full privacy from all network participants.

The project Linear regression machine learning competition on StarkNet, [link](https://github.com/trangnv/linear-regression-starknet) tries to prototype hosting data science competitions with simple linear regression models.
Some functions of the contracts:
- Before competition begins
  - **Organizer**:
    - Commit the merkle root of the test data
- During the competition:
  - **Competitors**
    - Commit the hash of the model
- Evaluation phase:
  - **Competitors**
    - Reveal the real model
  - **Organizer**
    - Reveal the test data
    - Run the models with test data onchain and publish the evaluation metric for each competitor

The commit-reveal scheme serves well that
- Competitors commit the model without anyone seeing it
- The test data is commited without being seen
  - If competitors see the test data, they could just overfit it, or even have a rule-based model
  - But it need to be commited, otherwise organizer can alter the test data

But there is major drawback: *Everything is onchain*, test data, model, evaluation which might be ok for small model but definitely won't work for compute heavy applications

What if we can have (*STARK*) proof can then be verified on-chain for a much smaller computational cost?