---
title: "Python Advice"
date: 2010-05-23
forum: Programming Talk
---

### Post by xsinsx on 2010-05-23
Hello, I am new to programming with python i have a very general programming knowledge and I am looking to expand my knowledge, One way I learn is seeing what others would have done in the same position I am in. 

i have a unit converter I was working on and got it functional now. I was curious what others might have done [PHP]
#!/usr/bin/env python
#This program is designed to convert hour minutes seconds and days.

nums = (1.0, 60.0, 24.0)
units = ("hr", "min", "sec", "day")

def hr_to_min(convertee, unit, converter):
    if converter == units[1] and unit == units[0]:
        converted = convertee * nums[1]
        print converted, "=", convertee, unit, "*", nums[1], 

def hr_to_sec(convertee, unit, converter):
    if converter == units[2] and unit == units[0]:
        converted = (convertee * nums[1]) * nums[1]
        print converted, "=", convertee, unit, "*", nums[1], "*", nums[1]

def hr_to_day(convertee, unit, converter):
    if converter == units[3] and unit == units[0]:
        converted = convertee / nums[2]
        print converted, "=", convertee, unit, "/", nums[2] 

def min_to_hr(convertee, unit, converter):
    if converter == units[0] and unit == units[1]:
       converted = convertee / nums[1]
       print converted, "=", convertee, unit, "*", nums[1]

def min_to_sec(convertee, unit, converter):
    if converter == units[2] and unit == units[1]:
        converted = convertee * nums[1]
        print converted, "=", convertee, unit, "*", nums[1]

def min_to_day(convertee, unit, converter):
    if converter == units[3] and unit == units[1]:
        converted = (convertee / nums[1]) / nums[2]
        print converted, "=", "(", convertee, unit, "/", nums[1], ")", "/", nums[2]
        
def sec_to_hr(convertee, unit, converter):
    if converter == units[0] and unit == units[2]:
        converted = (convertee / nums[1]) / nums[1]
        print converted, "=", "(", convertee, unit, "/", nums[1], ")", "/", nums[1]
        
def sec_to_min(convertee, unit, converter):
    if converter == units[1] and unit == units[2]:
        converted = convertee / nums[1] 
        print converted, "=", convertee, unit, "*", nums[1]

def sec_to_day(convertee, unit, converter):
    if converter == units[3] and unit == units[2]:
        converted = ((convertee / nums[1]) / nums[1]) / nums[2]
        print converted, "=", "(", "(", convertee, unit, "/", nums[1], ")", "/", nums[1], ")", "/", nums[2]  

def day_to_hr(convertee, unit, converter):
    if converter == units[0] and unit == units[3]:
        converted = convertee * nums[2]
        print converted, "=", convertee, unit, "*", nums[2]

def day_to_min(convertee, unit, converter):
    if converter == units[1] and unit == units[3]:
        converted = (convertee * nums[2]) * nums[1]
        print converted, "=", "(", convertee, unit, "*", nums[1], ")", "*", nums[1]
        
def day_to_sec(convertee, unit, converter):
    if converter == units[2] and unit == units[3]:
        converted = ((convertee * nums[2]) * nums[1]) * nums[1]
        print converted, "=", "(", "(", convertee, unit, "*", nums[2], ")", "*", nums[1], ")", "*", nums[1]    
        
               
def main():
    convertee = int(raw_input("Imput how many seconds, Minutes, Hours you would like to convert "))
    unit = raw_input("imput what unit that number is in, (use min, hr, sec, day): ")
    converter = raw_input("imput what unit you would like to switch it to (use min, hr, sec, day): ")
   
    hr_to_min(convertee, unit, converter)
    hr_to_sec(convertee, unit, converter)
    hr_to_day(convertee, unit, converter)
    min_to_hr(convertee, unit, converter)
    min_to_sec(convertee, unit, converter)
    min_to_day(convertee, unit, converter)
    sec_to_hr(convertee, unit, converter)
    sec_to_min(convertee, unit, converter)
    sec_to_day(convertee, unit, converter)
    day_to_hr(convertee, unit, converter)
    day_to_min(convertee, unit, converter)
    day_to_sec(convertee, unit, converter)

if __name__ == "__main__":
    main()        
[/PHP]

This is the code. I will listen to any and all advice just tell me what you think what I can do to improve and what you would have done. I am not looking for you to type out a new set of code(that would be awesome though) I am looking for just some general advice to help me get better at programming in general.

---

### Post by KdotJ on 2010-05-23
One thing I would do is error trapping. I know this is a simple program, but for programming in general, you can't assume what the user will do. You have to account for the user being stupid...

in your example...

What is the user doesn't type in an integer for the convertee? What if they type in the word "twelve", your program is not equipped to deal with such a problem.

What happens if someone types in "lightyears" for the converter? Nothing will happen, because your code for each method is inside an **if** block, which will only execute if the input matches the expected input. But the user might not know why it didn't work.


In my opinion, a good program will handle 'bad situations' gracefully (eg. display an error/help message in such case)

nice work though!

---

### Post by Barrucadu on 2010-05-23
Not the best of code, but here's a much more concise implementation:

```
#!/usr/bin/env python

def timeconv(unto, unfrom, val):
    convfactor = {'s'   : 1,
                  'min' : 60,
                  'hr'  : 60*60,
                  'day' : 60*60*24}
    
    inseconds = val * float(convfactor[unfrom])

    return inseconds / convfactor[unto]

def getfloat(prompt):
    value = None
    
    while value is None:
        inp = raw_input(prompt)
    
        try:
            value = float(inp)
        except ValueError:
            value = None

    return value

def getunit(prompt):
    value = None
    units = ['s', 'min', 'hr', 'day']
    
    while value is None:
        inp = raw_input(prompt)
        value = inp if (inp in units) else None

    return value

duration  = getfloat("Enter a duration of time (in seconds, minutes, hours, or days): ")
startunit = getunit("Enter a unit to convert from (s, min, hr, or day):              ")
endunit   = getunit("Enter a unit to convert to (s, min, hr, or day):                ")

print str(duration) + startunit, '=', str(timeconv(endunit, startunit, duration)) + endunit

```

---

### Post by xsinsx on 2010-05-23
I appreciate the advice from both of you. I did realize that there was no error handling and i should always consider for error handling even if its for my own use. Since it is always good practice. i did know that my code was a bit out there and not the best implementation but im just starting to get to a point where I am starting on my own projects. Its my summer goal to get much better at python and just programming in general so if anyone has any further advice I would love some. :D.

---

### Post by KdotJ on 2010-05-23
> **xsinsx said:**
> I appreciate the advice from both of you. I did realize that there was no error handling and i should always consider for error handling even if its for my own use. Since it is always good practice. i did know that my code was a bit out there and not the best implementation but im just starting to get to a point where I am starting on my own projects. Its my summer goal to get much better at python and just programming in general so if anyone has any further advice I would love some. :D.

Sometimes I might leave the error handling till later on, just to get the program together (although this is sometimes a bad idea). 
But remember, with programming there is not necessarily one correct way to do it. Sure there are "preferred" ways and "optimized" ways... but you will learn as you go on. Getting something to work, regardless of how you implemented it, is a real great way to boost learning confidence. Keep it up

---

### Post by xsinsx on 2010-05-23
> **KdotJ said:**
> Getting something to work, regardless of how you implemented it, is a real great way to boost learning confidence. Keep it up

Thank you for the words of confidence and inspiration. I will do just that.

---

### Post by Barrucadu on 2010-05-23
Have you looked at Project Euler? Whilst highly mathematical, I find the problems helpful for learning new languages. In fact, implementing any algorithm is good practice &#8212; try writing a bubble sort function, a prime number generator, or a Towers of Hanoi solver.

---

### Post by xsinsx on 2010-05-23
I will look into the mentioned Project later tonight and i think the three projects would be very interesting to attempt. Specially the last one. Thank you for the advice.

---

### Post by KdotJ on 2010-05-23
I remember writing bubble sorts back in college, along with recursive factorial methods and such like

---

### Post by lisati on 2010-05-23
One possible exercise is taking a relatively easy to understand algorithm such as bubble sort, and trying to make it more efficient. A couple of ways of doing that are mentioned [here]("http://en.wikipedia.org/wiki/Bubble_sort").

---

### Post by km0r3 on 2010-05-23
I warmly recommend you to look into the [Defensive Programming]("http://en.wikipedia.org/wiki/Defensive_programming") concepts if you want "normal users" to use it.

---

### Post by xsinsx on 2010-05-23
Thank you all so much all of this is helping me alot i looked into Project Euler and that is the most amazing thing I have seen in a long time. I checked out project python it was neat but it just wasnt what i was looking for. the bubble sort talk got me thinking about it and I am going to try and take simple ones and optimize them as someone mentioned thank you all so very much. :D

---

### Post by Can+~ on 2010-05-23
> **xsinsx said:**
> I am going to try and take simple ones and optimize them as someone mentioned thank you all so very much. :D

Premature optimization is the root of all evil.

I suggest you to get a working Bubble-sort (it's really not that hard), then understand it, see what you can improve, and then read about Mergesort and Quicksort.

This is much about python, but mostly about algorithms in general.

---

### Post by xsinsx on 2010-05-24
> **Can+~ said:**
> Premature optimization is the root of all evil.

Thank you for the advice. I have a tendency to be a quick start and such so thank you for giving me a reality check again i appreciate that. If anyone has any good algorithm reads or materials they might recommend i would not mind I shall search now i think.

---

### Post by Can+~ on 2010-05-24
> **xsinsx said:**
> Thank you for the advice. I have a tendency to be a quick start and such so thank you for giving me a reality check again i appreciate that. If anyone has any good algorithm reads or materials they might recommend i would not mind I shall search now i think.

Algorithm Design by Eva Tardos and John Kleinberg.
Introduction to Algorithms by Thomas H. Cormen.

Only if you want to go hardcore on algorithms.

---

### Post by simeon87 on 2010-05-24
> **Can+~ said:**
> Algorithm Design by Eva Tardos and John Kleinberg.
Introduction to Algorithms by Thomas H. Cormen.

Only if you want to go hardcore on algorithms.

More knowledge never hurts though.

---

### Post by xsinsx on 2010-05-26
I appreciate all the advice and more knowledge is better. I have a thing about just liking to have resources for when something comes up.

---

