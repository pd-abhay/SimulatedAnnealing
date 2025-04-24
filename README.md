# SimulatedAnnealing
* Simulated Annealing (SA) is an optimization technique inspired by the physical process of annealing in metallurgy, where materials are heated and then gradually cooled to remove defects and minimize the energy state of the system. SA is often used to find an approximate solution to a problem when dealing with large search spaces, especially when traditional methods like gradient descent might get stuck in local minima.

**Key Concepts of Simulated Annealing:**
* Energy Function (Objective Function): This represents the "cost" or "energy" of the current solution. The goal is to minimize this energy (or maximize if it’s a maximization problem).

* Temperature: Just like in physical annealing, SA uses a temperature parameter. At the start, the temperature is high, and as the algorithm progresses, the temperature gradually decreases. The temperature controls the probability of accepting worse solutions as the algorithm explores the search space.

* Transition/Move: The algorithm explores the solution space by making random changes (moves) to the current solution. Each move results in a new solution with an associated energy.

* Acceptance Probability: If the new solution has lower energy (better solution), it is always accepted. If the new solution has higher energy, it is accepted with a probability given by the formula:

* 𝑃(accept) = 𝑒xp(−Δ𝐸/𝑇)
where:
ΔE is the change in energy (new energy - old energy).
T is the current temperature.
This probability allows the algorithm to escape local minima, as worse solutions might be accepted at higher temperatures. As the temperature decreases, the likelihood of accepting worse solutions reduces, and the algorithm increasingly focuses on fine-tuning the current best solution.

Cooling Schedule: The temperature is decreased gradually following a cooling schedule, which is typically an exponential decay:

𝑇_new = 𝛼𝑇_old
 
where 
α is a constant between 0 and 1, and it controls the rate of cooling. The cooling schedule influences how quickly the algorithm converges to a solution.

**Optimal Hyperparameters**
* Initial temperature (T₀): Too high leads to excessive random moves (slow progress); too low leads to early freezing.
* Cooling factor (α): Closer to 1 (e.g. 0.99) yields slow cooling—better exploration but more iterations; lower α (e.g. 0.8) speeds convergence but risks trapping.
* Critical: Cooling schedule (combination of T₀ and α) dictates the algorithm’s ability to escape local minima and ultimately find the global optimum.

SA is sequential—better when memory is tight but slower overall.

**Convergence Speed**
Requires hundreds of steps to cool sufficiently—~200–300 iterations to approach within 1–2 % of its best.

**Premature Convergence**
Acceptance rate of uphill moves falls to zero and the “energy” plateaus early when cooling is too aggressive.SA depends critically on initial temperature and cooling schedule—poor choices lead to either excessive randomness or premature freezing. If α is set low (e.g. 0.80), temperature plummets rapidly and the algorithm “freezes” early: no uphill moves are accepted, so SA becomes a pure hill‑climber stuck in the first basin it finds.

**Mitigation Strategies**
* Slower cooling (α closer to 0.99) keeps the acceptance window open longer, but costs more iterations.
* Adaptive cooling: reduce α only when the recent acceptance rate stays above a threshold, pausing cooling when improvements stagnate.
* Reheating: occasionally raise T back up to a fraction of its initial value to escape deep local minima.
