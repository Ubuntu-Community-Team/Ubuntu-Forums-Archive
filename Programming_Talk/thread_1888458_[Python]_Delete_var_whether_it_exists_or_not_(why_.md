---
title: "[Python] Delete var whether it exists or not (why is there no isset()??)"
date: 2011-11-29
forum: Programming Talk
---

### Post by kramer65 on 2011-11-29
Hello,

Since a couple days I am messing around with Python. I now wrote a script in which I loop through a lot of data with which I do some stuff. I often set two variables and substract them from each other. If either one of them does not exist, I obviously can't substract them from each other and I simply move on with the loop.
In php, I would use an if-statement with an isset() to check whether both variables exist in the first place, but that doesn't seem to exist in python. Around the internet I saw some workarounds like this:
```
try:
    var3[x] = var1 - var2
except NameError:
    pass
```

This would work fine for one loop. However, if the next loop var1 cannot be set, it would still exist from the previous loop. So I have to make sure the vars don't get to the next loop. I would normally do a "del var1" for this. But this also results in a NameError if the var is not defined at all. So here I could do another one of these:

```
try:
    del var1
except NameError:
    pass
```

Since I often need to delete variables, this gets quite annoying though. So I though of making a class for it:
```
def delete_var(var):
    try:
        del var
    except NameError:
        pass
```

The problem is now that when I call this function with a "delete_var(var1)" while var1 doesn't exist, I still get a NameError.

All in all I'm trying all these quite dirty workarounds because there is simply no isset() function in Python. 

Does anybody have any idea how I could solve this in a lean and mean way? All tips are welcome!

---

### Post by Bachstelze on 2011-11-29
isset() is a very dirty feature of PHP and should only be used on superglobals like $_POST and suchlike. Initializing a variable is always the first thing you do with it, and if there is a possibility that a variable has not been initialized yet, then you should not attempt to do anything else with it. Instead of something like

```
if condition:
    var = value
if isset(var):
    do something
```

Just do


```
var = None
if condition:
    var = value
if var is not None:
    do something
```

---

### Post by kramer65 on 2011-11-29
Ok, but the thing is that I don't know whether a specific value exists in a dictionary. I've got a large (two dimensional) dictionary from which I always take two values in a loop and subtract them from each other. More or less as follows:
```
for datum, tijd_dict in open.iteritems():
    # Calculate differences
    verschil = tijd_dict[verkoop_tijdstip] - tijd_dict[koop_tijdstip]
```

So within the loop I am never sure whether the values tijd_dict[koop_tijdstip] and tijd_dict[verkoop_tijdstip] actually exist. There could be missing many of them. So if one of them is missing I don't want to do the calculation at all. 

How would you suggest I would do this?

---

### Post by javierrivera on 2011-11-29
```
for datum, tijd_dict in open.iteritems():
    if (verkoop_tijdstip in tijd_dict) and (koop_tijdstip in tijd_dict):
        # Calculate differences
        verschil = tijd_dict[verkoop_tijdstip] - tijd_dict[koop_tijdstip]
```

You can use *in* to check if a key exist in a dictionary.

```
>>> dictionary = {'1':1}
>>> '1' in dictionary
True
>>> 1 in dictionary
False
```

Dictionaries has also a .has_key method, but it's deprecated.

Anyway this looks very unpythonic to me. If you tell us what you are trying to achieve we can probably find a better solution.

---

### Post by kramer65 on 2011-11-29
"Unpythonic". In a couple days I've already seen (variations of) this word quite a lot. Love it!

On topic. What I am trying to achieve might seem a little confusing, but I'll try to explain it.

I'm trying to analyse financial data which contains the prices per minute for a certain [future]("http://en.wikipedia.org/wiki/Futures_contract") on the stock exchange. What I want to know is for example the average profit you would have made if you had bought the same future every single day at 09:00:00 and sold it the same day at 09:01:00 (i.e. one minute later). I want to know the same for buying at 09:01:00 and selling at 09:02:00. And for 09:02:00 and 09:03:00, and for 09:03:00 and 09:04:00 etc. etc.
So this computes the average price-difference for every minute time-difference over the full history of the future being traded on the stock exchange. I want to do the same thing for every two minutes difference, and every three minutes, and four, and five, etc. etc.
In this way I more or less get a matrix with the X-axis being the time you bought the future, and the Y-axis being the amount of minutes you kept it before selling it.

So in order to achieve this I loop over the days of the future and subtract the sell-price from the buy-price for every single day and put this difference in a list. I then calculate a couple things from that: the average, median, standard deviation, and some other statistics.

I had a look at numpy and the n-dimensional array it provides. For now this is simply a little bit confusing though, and since I just started learning python a couple days ago (coming from php) I thought I'd try it first with the knowledge I have.

But with the code I have being "unpythonic", how would you suggest I could achieve what I want doing it in a pythonic way?

---

### Post by Sworddragon on 2011-11-29
> **kramer65 said:**
> All in all I'm trying all these quite dirty workarounds because there is simply no isset() function in Python.

There is a similar way in python to check if a variable in a script is initialized:

```
print('varname' in vars())
```

This will print True if varname is initalized and False if not.

---

### Post by javierrivera on 2011-11-29
I'm not sure that I understand it correctly, but here is my take:

```
import datetime

data = {datetime.datetime(2000, 1, 1, 9, 0): 10,
        datetime.datetime(2000, 1, 1, 9, 1): 12,
        datetime.datetime(2000, 1, 1, 9, 2): 14,
        datetime.datetime(2000, 1, 1, 9, 5): 15,
        datetime.datetime(2000, 1, 1, 9, 6): 12,
        datetime.datetime(2000, 1, 1, 9, 7): 10,
        datetime.datetime(2000, 1, 1, 9, 10): 9,
        datetime.datetime(2000, 1, 2, 9, 0): 10,
        }

results = {}
time_list = data.keys()

for buy_time in sorted(data.keys()):
    results[buy_time] = {}
    time_list.remove(buy_time)
    for sell_time in time_list:
        results[buy_time][sell_time - buy_time] = \
                    data[sell_time] - data[buy_time]
```

I have build a dictionary with the data, using a datetime to keep the date and time of the value.

The result will be a dictionary, with a datetime with the buy moment as a key. Inside each key you will have another dictionary with a timedelta (you can convert it to minutes, or whatever unit you need) as keys, representing the time that this stock is going to be kept. The value of that dictionary is the result of the operation.

Note that dict.keys() returns a list with a ***copy*** of the dictionary keys.

---

### Post by kramer65 on 2011-11-29
Pfooo, that is a whole other take on the problem. It is quite late over here, so I will look at it tomorrow when my eyes and braincells are fresh again.. :-)

Thanks a lot for the effort. I will let you know tomorrow how that works out!

---

### Post by kramer65 on 2011-11-30
@ javierrivera

After looking over your code with a new fresh perspective I think it doesn't what I would like it to do. Because you take the date and the time together in one datetime element, I think you are only comparing a specific date and time (for example 2001-07-27 09:01:00) with another specific date and time (for example 2001-07-27 09:02:00).

What I am trying to do however, is compare the price of 09:01:00 with the one of 09:02:00 for every day in the dataset. I then make a list of these differences and from that I take the average difference, and some other statistics.

So what i have now is this:

```
fut_open_origineel = {'1997-05-28': {'09:02:00': 74.54, '09:01:00': 77.22},
'1997-05-29': {'09:02:00': 76.98, '09:01:00': 77.34, '09:03:00':79.23},
'1997-05-30': {'09:03:00': 80.12, '09:01:00': 78.27, '09:02:00': 79.94}}
buy_time = '09:01:00'
sell_time = '09:02:00'
difference = []
for date, time_dict in fut_open_origineel.iteritems():
    buy_price = sell_price = 0
    if (buy_time in time_dict) and (sell_time in time_dict):
        buy_price = time_dict[buy_time]
        sell_price = time_dict[sell_time]
    
    # Calculate differences
    if (buy_price != 0) and (sell_price != 0):
        difference.append(buy_price - sell_price)

def average(somelist):
    average = float(sum(somelist)) / len(somelist)
    return average

avg_difference = average(difference)
```

As far as I understand this does not do the same as the code you wrote right (please correct me if I'm wrong here)?

Now is my code here still "Unpythonic"? Would there be any faster/better methods of doing this?

---

### Post by javierrivera on 2011-11-30
This is clearly different to my code. It will wield different results (BTW, mine is a matrix, yours a vector).

I don't understand why are you using so many intermediate variables, i.e.:

```
for date, time_dict in fut_open_origineel.iteritems():
    if (buy_time in time_dict) and (sell_time in time_dict):
        # Calculate differences
        difference.append(time_dict[buy_time] - time_dict[sell_time])
```

This will be the same, but (IMHO, this things are always relative) is more legible.

Even if you like to keep the intermediate variable, this:

```

buy_price = sell_price = 0
if (buy_time in time_dict) and (sell_time in time_dict):
    buy_price = time_dict[buy_time]
    sell_price = time_dict[sell_time]
```

is the same than this
```

buy_price = time_dict.get(buy_time,0)
sell_price  = time.dict.get(sell_time,0)
```

The second option is clearly more pythonic (easier to read, faster to execute, more concise).

You can also change the loop for a map() (a list constructor), it will likely execute faster (the loop will be done in the map C code, not in python), but much more difficult to read (again IMHO).

---

### Post by kramer65 on 2011-11-30
You are right that so many intermediate variables are not needed. The thing is that I later on want to calculate the sell_price in a different way (I need to add a stop-loss strategy to it). This is why I already use the intermediate variables. About the other thing you suggest:

```
buy_price = time_dict.get(buy_time,0)
sell_price  = time.dict.get(sell_time,0)
```

I didn't know the option of get() (I am only starting with python.. :-) ). So I will definitely use that one. Thanks for that!

I also thought of map() instead of a for loop. The thing is that I've got a lot of loops within loops within loops (kinda Inception-like). So I first want to have my code ready and working, and then I will think about substituting for-loops with map().

Thanks for your ideas though. Next to the fact that I will definitely use some of the things you suggest, it also gives me a more critical view of my code. At least I achieved what I started this thread for. I will go on building my script now, and once I've got it working I will go over it again to make it as fast and "pythonic" as possible.. :-)

Thanks again!

---

### Post by StephenF on 2011-12-01
> **javierrivera said:**
> ```

buy_price = sell_price = 0
if (buy_time in time_dict) and (sell_time in time_dict):
    buy_price = time_dict[buy_time]
    sell_price = time_dict[sell_time]
```

is the same than this
```

buy_price = time_dict.get(buy_time,0)
sell_price  = time.dict.get(sell_time,0)
```

The former forces both values to be 0 if either is missing. The second code example doesn't.

Here is my solution.
```

from collections import defaultdict as ddict

time_dict = ddict(lambda: float("nan"))

# [ collect some data here ] 

buy_price = time_dict[buy_time]
sell_price = time_dict[sell_time]
```

Any missing data points will be float("nan") and will pollute any calculations done with them so that the end computed value will be float("nan"). See also the math.isnan() function.

---

### Post by kramer65 on 2011-12-01
> **StephenF said:**
> 
Here is my solution.
```

from collections import defaultdict as ddict

time_dict = ddict(lambda: float("nan"))

# [ collect some data here ] 

buy_price = time_dict[buy_time]
sell_price = time_dict[sell_time]
```

Any missing data points will be float("nan") and will pollute any calculations done with them so that the end computed value will be float("nan"). See also the math.isnan() function.

Thanks for your suggestion. May I ask what the advantages of this method would be? Would it be any faster or otherwise better than the other options you already quoted?

---

### Post by StephenF on 2011-12-01
> **kramer65 said:**
> May I ask what the advantages of this method would be? Would it be any faster or otherwise better than the other options you already quoted?
It will help you concentrate on your calculation code.

In this order.[LIST=1]
[*]Make something that works
[*]Look for solutions with a lower time complexity
[*]Optimise the code (this includes resorting to numpy or C)
[/LIST]
Optimisations reduce your ability to see cleaner solutions or refactor the code in a manner that would run faster.

I'm not even clear on where you are up to yet.

---

### Post by kramer65 on 2011-12-01
> **StephenF said:**
> It will help you concentrate on your calculation code. You can optimise it later.
Ah, like that. In that case, thanks a lot!

> **StephenF said:**
> If you cared that much about execution speed you wouldn't be using Python.
To be honest, I *am* indeed actually using python because it is a lot faster than the code I used to do it in before, which was plain old php. This is the first "non web-based language" which I learn. Mainly because it is supposed to be faster than php, and it has map() which is supposed to be a lot faster, and last but not least.. because it's easy*! \\:D/

[SIZE="1"]* In comparison with C/C#/C++/Java/Perl/etc.[/SIZE]

---

### Post by javierrivera on 2011-12-01
> **StephenF said:**
> The former forces both values to be 0 if either is missing. The second code example doesn't.


Well spotted :)

Anyway, as the calculation is only done when both values are different from 0 it doesn't matter in this particular case.

---

