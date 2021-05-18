# First CI Pipeline

This rudimentary CI Pipeline follows the [First Green 
Build](https://circleci.com/docs/2.0/getting-started/) tutorial from 
*Circle CI*.

## Setup

After following the setup steps in the tutorial, the `Hello World` 
configuration example creates a `.circleci/config.yml` file at the root 
of a new branch called `circle-ci-setup`. This can be merged into your 
main branch or continue to be worked on.

## Digging In

### Spin Up Environment

Circle CI used an [orb](https://circleci.com/orbs) to help provide some 
defaults for this project. By using an orb, we get quick access to 
common configuration.

### View Step Results

Every job is made up of a series of steps. Some steps, like `checkout`, 
are special reserved commands in Circle CI. Other steps are specified by 
a user to achieve a specific purpose. For the beginning tutorial, a 
`welcome` orb is used, which doesn't contain custom steps.

You can view the source of the `welcome` orb 
[here](https://circleci.com/developer/orbs/orb/circleci/welcome-orb).


### Finishes

Here are the contents of the `config.yml` file that was added by this 
tutorial:

```yaml
# Use the latest 2.1 version of CircleCI pipeline process engine. See: 
https://circleci.com/docs/2.0/configuration-reference
version: 2.1
# Use a package of configuration called an orb.
orbs:
  # Declare a dependency on the welcome-orb
  welcome: circleci/welcome-orb@0.4.1
# Orchestrate or schedule a set of jobs
workflows:
  # Name the workflow "welcome"
  welcome:
    # Run the welcome/run job in its own container
    jobs:
      - welcome/run
```

Even though there was no actual source code and no actual tests 
configured in this `config.yml` file, CircleCI considers this build to 
have "succeeded" because all steps completed successfully (i.e. returned 
an exit code of `0`). Most projects are far more complicated, often 
with multiple Docker images and multiple steps, and include a large 
number of tests.

Learn more about all possible steps one may put in a `config.yml` 
[here](https://circleci.com/docs/2.0/configuration-reference).
