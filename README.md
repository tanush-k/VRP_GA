# Vehicle Routing Problem with Genetic Algorithms

## Introduction

This project implements a Genetic Algorithm (GA) to solve the Vehicle Routing Problem (VRP). The VRP is a complex optimization problem in logistics where the objective is to find the optimal set of routes for a fleet of vehicles to deliver goods to a set of locations. The goal is to minimize the total distance traveled and balance the workload among the vehicles.

## Project Structure

### Required Libraries

The project uses the following libraries:
- `random`
- `numpy`
- `matplotlib`
- `deap` (Distributed Evolutionary Algorithms in Python)

### Files and Functions

1. **Initialization**
   - **Number of Locations and Vehicles:**
     - `num_locations`: Defines the number of locations (excluding the depot) that the vehicles need to visit.
     - `locations`: Generates random `(x, y)` coordinates for each location.
     - `depot`: Defines the central depot location.
     - `num_vehicles`: Defines the number of vehicles available to visit the locations.
   
2. **Genetic Algorithm Setup**
   - **Fitness Function and Individual Structure:**
     - `creator.create("FitnessMin", base.Fitness, weights=(-1.0, -1.0))`: Defines a fitness function to minimize total distance and balance penalty.
     - `creator.create("Individual", list, fitness=creator.FitnessMin)`: Defines the individual structure as a list with a fitness attribute.
   
3. **Toolbox Registration**
   - **Individual and Population Initialization:**
     - `toolbox.register("indices", random.sample, range(num_locations), num_locations)`: Generates a list of unique, randomly ordered location indices.
     - `toolbox.register("individual", tools.initIterate, creator.Individual, toolbox.indices)`: Creates an individual as a shuffled list of location indices.
     - `toolbox.register("population", tools.initRepeat, list, toolbox.individual)`: Creates a population of individuals.
   
4. **Fitness Function**
   - `evalVRP(individual)`: Evaluates an individual by calculating the total distance traveled and balance penalty among vehicles.

5. **Genetic Operators**
   - **Crossover, Mutation, and Selection:**
     - `toolbox.register("mate", tools.cxPartialyMatched)`: Partial match crossover function.
     - `toolbox.register("mutate", tools.mutShuffleIndexes, indpb=0.05)`: Mutation function to shuffle indices with a 5% chance per index.
     - `toolbox.register("select", tools.selTournament, tournsize=3)`: Tournament selection function.

6. **Plotting Function**
   - `plot_routes(individual, title="Routes")`: Visualizes the routes taken by the vehicles using `matplotlib`.

7. **Main Execution**
   - `main()`: Runs the genetic algorithm, generates the initial population, tracks statistics, and plots the best route found.

## Usage

### Running the Project in Google Colab

To run the project in Google Colab, follow these steps:

1. **Open the Colab Notebook**
   - [Vehicle Routing Problem with Genetic Algorithms](https://colab.research.google.com/github/tanush-k/VRP-GA/blob/master/vrp_ga.ipynb)

2. **Run the Cells**
   - Execute each cell in the notebook sequentially. The notebook is structured to guide you through the initialization, setup, and execution of the genetic algorithm.

