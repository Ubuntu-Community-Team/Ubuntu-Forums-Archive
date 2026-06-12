---
title: "Python CSV module error"
date: 2007-05-24
forum: Programming Talk
---

### Post by b1g4L on 2007-05-24
This is my first time using the CSV module in python. I am importing a pretty massive (4 columns with over 7000 rows) csv file. I do some parsing and save the variables which I build an object with. Then, I store the objects in a list. Essentially, the data on each row will equal one object. My code works fine with a relatively small sample of the data, but when I try to process the whole file I get the following error in terminal:

IOError: [Errno 24] Too many open files: 'file.csv'

Anyone recognize this error? I've searched and found very little. Thanks in advance.

---

### Post by ghostdog74 on 2007-05-24
show your code

---

### Post by b1g4L on 2007-05-25
The 'loadCSV' method is the part of the code that loads the data from the csv file, builds an object and inserts the object in a list. It's storing a small sample of food contents:

```
import csv

class Food():
    def __init__(self):        
        self.foodFile = csv.reader(open("FOOD_SHORT.csv", "rb"))
        self.foodList = []
        self.foodName = ''
        self.calories = 0
        self.fat = 0
        self.carbs = 0

    def loadCSV(self):
        for row in self.foodFile:
            foodObject = Food()
            foodObject.setFoodName(row[0])          # Store food name
            foodObject.setCalories(int(row[1]))     # Convert to int and store calories
            foodObject.setCarbs(float(row[3]))      # Convert to float and store carbs
            self.foodList.append(foodObject)        # Store foods in list
            
    def getFoodName(self):
        return self.foodName
    
    def getCalories(self):
        return self.calories

    def getFat(self):
        return self.fat

    def getCarbs(self):
        return self.carbs

    def setFoodName(self, food):
        self.foodName = food

    def setCalories(self, calories):
        self.calories = calories

    def setFat(self, fat):
        self.fat = fat

    def setCarbs(self, carbs):
        self.carbs = carbs

```

Here is code to run the class above:

```
from food import *

n = Food()
n.loadCSV()
for item in n.foodList:
    print item.getFoodName()
print "DONE"
```

I'll also include the CSV file (zipped).

---

### Post by b1g4L on 2007-05-25
I believe the error has nothing to do with reading the file, but actually putting the objects into a list. I can comment out the line:```
self.foodList.append(foodObject)
``` and it works. Anyway, that's the update.

---

### Post by b1g4L on 2007-05-25
I figured it out. I created separate classes for the Food object and the Food Database. I think some recursion was going on somewhere causing too many instances to occur.

---

