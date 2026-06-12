---
title: "Travelling salesperson problem"
date: 2007-05-06
forum: Programming Talk
---

### Post by laxmanb on 2007-05-06
Does anybody have any good resources on solving the [Travelling salesperson problem]("http://en.wikipedia.org/wiki/Traveling_salesman_problem")/ Eulerian & Hamiltonian paths (in any language)? I'm having trouble understanding the implementation provided to us at college...

---

### Post by dwblas on 2007-05-06
To start with, you have to do it first using brute force-->flame on (some people __Hate__ brute force).  Brute force is necessary to define what "correct" is, and is just trying every possible combination so that you know when you have the correct answer or answers, i.e. could be more than one route.  Then you would try filters, say traveling to the closest city from the one you are in as you go from city to city.   Think of the cities as a solid with x number of sides, one for each city and that should help get you started.

---

### Post by Wybiral on 2007-05-06
Use a genetic algorithm... They sound more complex then they are. It can probably be implemented in just about any language.

I've seen examples of GA's solving this problem before. Google it.

---

### Post by d80tb7 on 2007-05-07
I once solved this as part of my physics undergrad.  This was a long time ago though so don't stake your life on this solution :) 

The method is called simulated annealing and is a type of Monte Carlo Simulation.

1. Choose a 'temperature', T.  This is just a number and should be higher than your highest 'cost' of moving between cities)
2.  Put all your cities into an array.  In any order.
3. Calculate the cost of the journey assuming that the salesman moves along the array.
4. Randomly pick two cities and calculate the new cost of travelling along the array.
5.  If the cost is lower than before then accept the swap.  If the cost is not lower than before then accept the swap with a probability of exp(-cost_difference/T)
6. Repeat steps 3 - 5 a large number of times (you should eventually find that you get stuck in a local minima).  Record the value of the cost (this should be the lowest cost for the value of T you have chosen). 
7. Choose a new value of T and repeat steps 2 - 6.  Hopefully the new cost should be lower than the last one.  Keep performing the simulation, reducing T each time, until the new cost no longer decreases.  At this point you have found the route with the least cost.


Chris

---

### Post by THaugland on 2007-05-07
> **laxmanb said:**
> Does anybody have any good resources on solving the [Travelling salesperson problem]("http://en.wikipedia.org/wiki/Traveling_salesman_problem")/ Eulerian & Hamiltonian paths (in any language)? I'm having trouble understanding the implementation provided to us at college...

dwblas: Huh? Brute force requires much too many computations in many cases, and it is by all means not necessary. It can be used as a spot test for the correctness of the algorithm, but I do not recommend using brute force for every single problem.

Wybiral: Genetic algorithms are (normally) not guaranteed to give you an optimal solution, but rather a local optima. This could be good enough though.

In the case of generic TSP (not euclidic distances) I recommend Branch and Bound! [http://en.wikipedia.org/wiki/Branch_and_bound](http://en.wikipedia.org/wiki/Branch_and_bound). Relatively easy to implement, and guarantees an optimal solution. I have solved TSP using Branch and Bound myself. 

Eulerian paths can be used to reduce the problem. In real life, there can be many different paths from A to B. If we are only interested in the shortest paths, we can reduce all possible paths to the shortest paths between any of the vertices (cities). The input to eg. Branch and Bound shoul be an eulerian graph and the output an eulerian path.

---

### Post by slash2314 on 2007-05-07
```

import random

class City(object):
	__cityNum = 0
	def __init__(self):
		City.__cityNum += 1
		self.__distances = {}
		self.__distances[City.__cityNum] = 0
		self.__number = City.__cityNum

	def get_distance_from(self, cityNumber):
		try:
			return self.__distances[cityNumber]
		except:
			return False

	def set_distance(self, cityNumber, distance):
		self.__distances[cityNumber] = distance
		
	@property
	def number(self):
		return self.__number
	

class Traveler(object):
	def __init__(self, numberOfCities, upperDistance, lowerDistance):
		self.__cityList = []
		self.__numberOfCities = numberOfCities
		self.__upperDistance = upperDistance
		self.__lowerDistance = lowerDistance
		self.__generate_distances()

	def __generate_distances(self):
		for x in range(1,self.__numberOfCities+1):
			self.__cityList.append(City())
		for city in self.__cityList:
			for number in range(1, self.__numberOfCities+1):
				if self.__cityList[number-1].get_distance_from(city.number) and number != city.number:
					city.set_distance(number, self.__cityList[number-1].get_distance_from(city.number))
				elif number != city.number:
					city.set_distance(number, random.randint(self.__lowerDistance, self.__upperDistance))
					
					
	def __factorial(self, number):
		if number <= 1:
			return 1
		else:
			return number * self.__factorial(number-1)
	
	def get_distances(self):
		distanceList = []
		for city in self.__cityList:
			for y in range(1,self.__numberOfCities+1):
				if city.number != y:
					distanceList.append("City: %d, distance from %d is %d" % (city.number, y, city.get_distance_from(y)))
		return distanceList
	
	def run_simulation(self):
		cityHistory = []
		distanceHistory = []
		minRoute = []
		curSum = 0
		minDistance = self.__upperDistance * (self.__numberOfCities + 1)
		count = 0
		while count != self.__factorial(len(self.__cityList)):
			city = random.choice(self.__cityList)
			if len(cityHistory) == 0:
				cityHistory.append(city.number)
			elif city.number not in cityHistory:
				distanceHistory.append(city.get_distance_from(cityHistory[-1]))
				cityHistory.append(city.number)
			if len(cityHistory) == self.__numberOfCities:
				distanceHistory.append(city.get_distance_from(cityHistory[0]))
				cityHistory.append(cityHistory[0])
				curSum = sum(distanceHistory)
				if curSum<minDistance:
					minDistance = curSum
					minRoute = cityHistory
				cityHistory = []
				distanceHistory = []
				count+=1
		return (minRoute,minDistance)
	

if __name__ == '__main__':
	salesman = Traveler(6,15,5)
	print salesman.run_simulation()
	print '\n'.join(salesman.get_distances())

```

Here is a python solution, but I came up with this algorithm.  I don't think it is very efficient, but it does work I think.

---

### Post by steveneddy on 2007-05-07
> **Wybiral said:**
>  Google it.

I think I shouldn't talk to you because of you signature.

My mom is looking, she saw me read it and now.....no more Windows time for me!!!!

... cool ...

---

### Post by Wybiral on 2007-05-07
> **steveneddy said:**
> I think I shouldn't talk to you because of you signature.

My mom is looking, she saw me read it and now.....no more Windows time for me!!!!

... cool ...

Was that sarcasm I heard, or are you serious?

EDIT:

BTW, GA's get pretty close if you use the right balance and they are relatively fast. I'm not saying it's the best solution for this problem, just that I've seen it solved many times using GA's so it might be worth a shot... I guess is depends what type of solution you are looking for. Especially considering that there may me multiple solutions to a given set (GA's shouldn't have a problem finding it after enough generations)

---

### Post by tgalati4 on 2007-05-07
There are some web-based/JAVA calculators available for small problems.  I'm not sure what method they use, but they can be used as a sanity check.  Nothing wrong with brute force, it's not like we're short of computer cycles.

---

### Post by steveneddy on 2007-05-26
> **Wybiral said:**
> Was that sarcasm I heard, or are you serious?



steveneddy: Hey Wybiral

Wyberal: Hey back, steveneddy

steveneddy: what's up?

Wyberal: nuttin'

steveneddy: hey Wybiral?

Wybiral: yeah

steveneddy: Wybiral, I love you

Wybiral: steveneddy.....are you serious?

Wyberal: steveneddy?

Wybiral: steveneddy - are you serious?

Wybural: hello?

Wybiral: steveneddy - are you serious?

Wybiral: are you serious, steveneddy?

....................... :| ..................  ...   . ..  ... . .. .. .. . .

---

### Post by nitro_n2o on 2007-05-26
I would go with GA... even better go with Neural Networks.. there are many implementations that solve the salesperson problem using neural nets here's one [http://www.vias.org/simulations/simusoft_travsalm.html](http://www.vias.org/simulations/simusoft_travsalm.html) with a nice GUI, you can find more if you google more

---

