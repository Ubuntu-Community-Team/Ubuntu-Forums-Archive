---
title: "Thinking in Python"
date: 2007-12-27
forum: Programming Talk
---

### Post by Auria on 2007-12-27
Hello all,

I'm a C/C++/Java/D programmer (all C-like languages) and I'm now trying to write some python code. I jave no problem grasping the syntax or stuff like that, what causes be trouble is how to *think* in python. I often seem to come up with solutions that are made for C-like languages.

Let's say I have the following C code and I would like to write a python equivalent? Note that I already know a few ways of getting it to work, but I would like to know how a python person would do it as I don't want to do ugly stuff :D

```


enum FoodType
{
potatoe,
pizza,
hot_dog,
pasta,
chicken
}

FoodType myFavoriteFood;

void askForVaroriteFood()
{
    // more code would go there
    myFavoriteFood = pizza;
}

void cookFavoriteFood()
{
  if(myFavoriteFood == pizza) printf("cooking pizza!\n");
  if(myFavoriteFood == ... ) etc.
}

int main()
{
  askForVaroriteFood();
  cookFavoriteFood();
}


```

My current idea is to create a dictionnary for food types + a global variable. Then I would say "global myFavoriteFood" at the beginning of every function. Is that correct? Is there a better way to do it?

thanks

---

### Post by Martin Witte on 2007-12-27
i would go for something where you avoid globals as much as possible, wheter it is in c++ or python, eg.
[PHP]#!/usr/bin/env python
food_type = ('potatoe', 'pizza')

class NotSupportedFood(Exception):
    def __init__(self, msg = ''):
        self.msg = msg
    def __str__(self):
        return str(self.msg)

def ask_favorite_food():
    fav_food = raw_input('enter your favorite food')
    if fav_food not in food_type:
        raise NotSupportedFood('food %s not valid' % fav_food)
    return fav_food

def cook_favorite_food(food):
    if food == 'potatoe':
        print 'cooking potatoe'
    elif food == 'pizza':
        print 'cooking pizza'
    else:
        raise NotSupportedFood('can not cook %s' % food)

if __name__ == '__main__':
    try:
        food = ask_favorite_food()
        cook_favorite_food(food)
    except NotSupportedFood, e:
        print str(e)[/PHP]

---

### Post by Majorix on 2007-12-27
I have 2 things to add.

When thinking in Python, you have to know that these languages maybe won't process complex loops, decisions etc as fast as you are used to in C. Therefore, the lines
[php]if something //do something
if something_else //do something else[/php]
may cause you problems when working in Python. As shown in the above example, you have to use if-elif-else statements so that only one choice is executed depending on a condition and others are fallen through. The poster above did it right, although (s)he didn't explain it, so I thought I might add it.

And a note about the exceptions, as shown in the above example. You will want your "try" statement to include only the necessary parts, and not anything else.
Consider this:
[php]try:
   something that could cause an exception
   something else that could "maybe" cause an exception, but overseen by the programmer
   another such situation
except (and cover only one exception)[/php]
The above example won't work as expected. A better approach is to either cover all the possible exceptions at the end (confusing, not recommended) or include each possible exception in its own "try" statement.

I have also come from a C/C++ and C# background, and only recently started working with Python;  so I can understand what you mean :)

Best of luck thinking in Python.

---

### Post by Auria on 2007-12-27
Martin Witte: Yes I know globals are to be avoided, however I am not writing Photoshop CS4 but only a very small utility so it would just have been more straight-forward to use them. But I'm starting to realise that python doesn't seem to support globals much, so I will probably need to take another approach even if it means writing more code to get the same result.

Majorix: Yes, I know python will not be as fast, thanks anyway. The pseudo-C-code I gave was not real code, it was only meant to show the general idea. I am not sure what your point about exceptions is though, do you mean to do try-catch on each individual command and not on blocks?

thanks I'll give it another go

---

### Post by Klipt on 2007-12-27
One of the main points of OOP with inheritance is to avoid switch statements or prolonged if tests:

```
#!/usr/bin/env python

class food:
	def __init__(self, name):
		self.name = name
	def cook(self):
		print 'Searching web for %s recipes...' % self.name
	def serve(self):
		print 'Searching web for %s serving suggestions...' % self.name

nameToFood = {}

class potatoe(food):
	def cook(self): print 'Microwave potatoe. Fill with grated cheddar and microwave another minute.'
	def serve(self): print 'Serve with pickles.'

nameToFood['potatoe'] = potatoe

class pizza(food):
	def cook(self): print 'Prepare credit card. Phone Pizza King.'
	def serve(self): print 'Rent a b-grade movie and invite friends over to share pizza.'

nameToFood['pizza'] = pizza

#...

def readFood():
	print "What is your favourite food?"
	fav = raw_input()
	return nameToFood.get(fav, food)(fav)

if __name__ == '__main__':
	meal = readFood()
	meal.cook()
	meal.serve()
```

---

### Post by Martin Witte on 2007-12-27
> **Auria said:**
> Martin Witte: Yes I know globals are to be avoided, however I am not writing Photoshop CS4 but only a very small utility so it would just have been more straight-forward to use them. But I'm starting to realise that python doesn't seem to support globals much, so I will probably need to take another approach even if it means writing more code to get the same result.

Majorix: Yes, I know python will not be as fast, thanks anyway. The pseudo-C-code I gave was not real code, it was only meant to show the general idea. I am not sure what your point about exceptions is though, do you mean to do try-catch on each individual command and not on blocks?

thanks I'll give it another go
what Majorix means with the exceptions is (please correct me if i'm wrong) is to catch only one exception in an 'except' handler, so you have a good idea where things went wrong, i changed my example a little to demonstrate this:
[PHP]#!/usr/bin/env python
food_type = ('potatoe', 'pizza')

class FoodError(Exception):
    def __init__(self, msg = ''):
        self.msg = msg
    def __str__(self):
        return str(self.msg)

class AskFoodError(FoodError):
    pass

class CookFoodError(FoodError):
    pass

def ask_favorite_food():
    fav_food = raw_input('enter your favorite food')
    if fav_food not in food_type:
        raise AskFoodError('%s is an invalid food to ask' % fav_food)
    return fav_food

def cook_favorite_food(food):
    if food == 'potatoe':
        print 'cooking potatoe'
    elif food == 'pizza':
        print 'cooking pizza'
    else:
        raise CookFoodError('can not cook %s' % food)

if __name__ == '__main__':
    try:
        food = ask_favorite_food()
        cook_favorite_food(food)
    except AskFoodError, e:
        print 'AskFoodError: %s' % e
    except CookFoodError, e:
        print 'CookFoodError: %s' % e

[/PHP]

if you put every command in it's own try .. except block your program will run to the end, also if the first step goes wrong and no valid food is supplied, it will be cooked and raising here another error, that is not what you want.

---

### Post by pmasiar on 2007-12-27
To learn idiomatic Python, read "Learning Python", then [Thinking in Python](http://www.mindview.net/Books/TIPython)

As a rule of thumb, the more you use dictionaries, the better :-)
So ie to make fast code dispatcher, you can make dictionary with values - references to functions (to avoid long "if ...elif .. elif" chains). ut usually the obsession with inefective execution shows lack of experience: speed is not a problem until you can prove it is a problem. For nost application, Python is fast enough.

---

### Post by Majorix on 2007-12-28
> **Auria said:**
> Majorix: Yes, I know python will not be as fast, thanks anyway. The pseudo-C-code I gave was not real code, it was only meant to show the general idea. I am not sure what your point about exceptions is though, do you mean to do try-catch on each individual command and not on blocks?

Glad you know of the powers and weaknesses of the tools you work with. There are sadly still some people who would write nested for-loops with large limits or recursive functions with Python, and when they don't get the speed and memory usage results they did in C or similar languages, they blame Python of being for noobs and being useless.

And about the exceptions, I was referring to the example Martin wrote for you, where he confusingly handled the exception structure. But you got the correct idea, yes, you have to split your code into single commands if you are writing exceptions. And you should get the habit of doing so, because it can help with larger programs.

---

### Post by Auria on 2007-12-28
Ok good, thanks everyone, I got it to work :) I'm still unsure I will use python very much but at least I got started correctly

---

### Post by CptPicard on 2007-12-28
> **Majorix said:**
> There are sadly still some people who would write nested for-loops with large limits or recursive functions with Python

Regarding Python recursion, here's a thread I started a while ago on this topic, interesting results:

[http://ubuntuforums.org/showthread.php?t=649295](http://ubuntuforums.org/showthread.php?t=649295)

The good part was that C was so fast that it means we'll be able to analyze one particular game exhaustively. Stay tuned. ;)

> But you got the correct idea, yes, you have to split your code into single commands if you are writing exceptions.

It depends on what your code is like. Proper exceptions ought to be fatal or something like that, so if you have a lot of calls throwing exceptions in some method, it's one and the same really to catch them all at the end of the method, clean up in one place and potentially throw further. I would personally consider it really ugly code if you had exception handlers everywhere...

---

### Post by Majorix on 2007-12-28
> Regarding Python recursion, here's a thread I started a while ago on this topic, interesting results:

[http://ubuntuforums.org/showthread.php?t=649295](http://ubuntuforums.org/showthread.php?t=649295)

Interesting thread...

> The good part was that C was so fast that it means we'll be able to analyze one particular game exhaustively. Stay tuned. ;)

I believe Java is also nearly as fast as C, however it has much larger overhead.

> I would personally consider it really ugly code if you had exception handlers everywhere...

Obviously we have different views on beauty, but no two people share the same views on this matter ;)

---

### Post by CptPicard on 2007-12-28
> **Majorix said:**
> 
I believe Java is also nearly as fast as C, however it has much larger overhead.

As can be seen, Java is pretty much as fast as unoptimized C in this simple exercise which essentially consists of recursing over an array and calling "sum" at the end. Optimized C is still many times faster. And Java's overhead is glaring in this case, as you've got the entire JVM running for something this simple, while in C your memory consumption is of course really minimal -- essentially just the code, the array, and the stack. But when you just look at code speed, JIT compilation does a fair job.

Essentially, C allows us to add one more character at the end of the array and do it in the same time. But RAM is cheap, and Java less painful.

Now, things get more interesting when you introduce Java's standard library and more complex memory structures. I do believe that Java has the upper hand here in the vast majority of cases because of the easier coding of the increasingly complex system. Yet, it remains much faster than, say, Python.

> Obviously we have different views on beauty, but no two people share the same views on this matter ;)

The point is the general fatality of exceptions. When there is an exception, you essentially can no longer continue, so you just might give up and clean up in one place and then pass back whatever you can. Sprinkling exception handlers all over the place just adds explicit exit points when they are otherwise implicit and just as "bad" as far as the continued execution of your code is concerned.

---

