---
title: "Why does he uses floating point on line 2 in this source code?"
date: 2011-06-15
forum: Programming Talk
---

### Post by 0101amt on 2011-06-15
Greetings, first of all thanks for all the useful sticky posts. I'm a beginner, and I decided to go for Python as my first programming language. I found a book called Learn Python the Hard way and I am currently reading from it but I am stuck at an exercise.

"Explain why the 4.0 is used instead of just 4."

```

cars = 100
space_in_a_car = 4.0  #Why does he uses 4.0 instead of 4?
drivers = 30
passengers = 90
cars_not_driven = cars - drivers
cars_driven = drivers
carpool_capacity = cars_driven * space_in_a_car
average_passengers_per_car = passengers / cars_driven


print "There are", cars, "cars available."
print "There are only", drivers, "drivers available."
print "There will be", cars_not_driven, "empty cars today."
print "We can transport", carpool_capacity, "people today."
print "We have", passengers, "to carpool today."
print "We need to put about", average_passengers_per_car, "in each car."



```

 I see no point of using a floating point at line 2 except  for the fact to serve as an  example  that if I have a floating point number it affects the rest of  the expression evaluation(cars_driven * space_in_a_car) resulting in 120.0.

So, am I loosing something? Is there another point why he uses a floating point at line 2?

---

### Post by BkkBonanza on 2011-06-15
Maybe he's allowing for children to be counted as half size people. 
So you could have 3.5 people in a car? 
(tongue in cheek)

---

### Post by simeon87 on 2011-06-15
I don't think there's a good reason for it.

The only thing I can think of is that it's the average number of people in a car. If you have 100 cars then probably not all the cars have the same capacity. Some cars are for 2 people, others for 4 or 6. So you could have, on average, a space for 3.7 people in the car.

However, if there was the case, I wouldn't design the code like that because it becomes a mess later on.

I wouldn't worry too much about it.

---

### Post by TwoEars on 2011-06-15
In truth, there's no reason he should have used it. You can't have less than a whole person. You either can have a person, or not. Still, the answer is meant to be something along the lines of "Because there might be extra space in the car".

---

### Post by prshah on 2011-06-15
> **0101amt said:**
> 
```

space_in_a_car = 4.0  #Why does he uses 4.0 instead of 4?

```


Giving a python variable an initial value of "x.xxx" will indicate how many decimal places the output is to show. So, if you have a formula x - 2, then

if x = 4 ; result = 2
if x = 4.0 ; result = 2.0
if x = 4.00 ; result = 2.00

However, I still cannot explain why [te]("http://ubuntuforums.org/showpost.php?p=10869035&postcount=24") feels the need to use 4.0 for "space_in_a_car"; assigning "90.0" to passengers makes more sense than this.

---

### Post by cgroza on 2011-06-15
Maybe he is worried that an operation will give a floating point number as a result and he does not want it to be rounded to int by default.? I am not sure, it is just I have seen similar use to avoid this type of automatic conversion.

---

### Post by simeon87 on 2011-06-15
> **prshah said:**
> Giving a python variable an initial value of "x.xxx" will indicate how many decimal places the output is to show. So, if you have a formula x - 2, then

if x = 4 ; result = 2
if x = 4.0 ; result = 2.0
if x = 4.00 ; result = 2.00

However, I still cannot explain why [te]("http://ubuntuforums.org/showpost.php?p=10869035&postcount=24") feels the need to use 4.0 for "space_in_a_car"; assigning "90.0" to passengers makes more sense than this.

That doesn't happen on my computer:

```
>>> 4.00 - 2
2.0
```

For Python, the values 2.0 and 2.00 are the same (both floating point). The way values are displayed is determined by a format specifier, in strings for example. But that's not the case in the computation itself where only the differene between integer and floating point matters.

---

### Post by TwoEars on 2011-06-15
> **prshah said:**
> Giving a python variable an initial value of "x.xxx" will indicate how many decimal places the output is to show. So, if you have a formula x - 2, then

if x = 4 ; result = 2
if x = 4.0 ; result = 2.0
if x = 4.00 ; result = 2.00

However, I still cannot explain why [te]("http://ubuntuforums.org/showpost.php?p=10869035&postcount=24") feels the need to use 4.0 for "space_in_a_car"; assigning "90.0" to passengers makes more sense than this.

Urm, no it doesn't. The number of places after the decimal point is dictated firstly on whether it's a floating point or an integer/long, and then secondly on the format when it comes to output. If it's a floating point, it defaults to one digit after the decimal point. If it's integer/long, there will be nothing after the decimal point.

Also, 90.0 passengers makes about as much sense as 4.0 spaces in a car - you can't have anything but a whole of a person. And as for counting children as "half people", that would be illegal, as it would warrant children riding in a car without a seatbelt.

---

