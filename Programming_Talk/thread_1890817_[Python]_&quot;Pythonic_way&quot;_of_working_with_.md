---
title: "[Python] &quot;Pythonic way&quot; of working with non-existing dictionary-keys"
date: 2011-12-04
forum: Programming Talk
---

### Post by kramer65 on 2011-12-04
Hello,


Since I come from php I was previously fighting with the lack of isset() in python ([see thread here]("http://ubuntuforums.org/showthread.php?t=1888458")). I solved that issue, but I now face another challenge in which I do if statements on dictionary-items of which I'm not sure they even exist. 
I've got two dictionaries in which I've got a price for almost every day. Almost, because not all days are in there. I now want to do the following if-statement on the two dictionaries (*first_stop_low* and *first_stop_high*):

```
if (first_stop_high[datum][:8] > buy_time and first_stop_high[datum][:8] < sell_time) or (first_stop_low[datum][:8] > buy_time and first_stop_low[datum][:8] < sell_time):
    if first_stop_low[datum][:8] <= first_stop_high[datum][:8]:
        sell_price = first_stop_low[datum][8:]
    else:
        sell_price = first_stop_high[datum][:8]
else:
    sell_price = tijd_dict.get(sell_time,0)

```
When I run this I obviously get a KeyError since I check for dates that are often not even in the dictionary. I can of course check in both the dictionaries whether the key exists. I then however, must do all sorts of combinations of if-statements. It could be for example that the datum exists in both dictionaries. In that case I also need to compare them. If it is in only the first dictionary though, I must only compare the first dictionary to the buy_time and sell_time. If it only appears in the second dictionary I obviously have to do the same, but then for the second one. And then there's the possibility that the datum doesn't exist in either of them, in which case I must resort to the last else statement.

I guess I am able to write all the different possible combinations into code. I just don't think that that is the "Pythonic" way to do this. There must be a shorter and simpler way of doing this.


Does anybody have any idea how I could solve this? All tips are welcome!

---

### Post by StephenF on 2011-12-04
It seems to me you are withholding the working ugly code and expecting us to do something with a broken code fragment.

---

### Post by cgroza on 2011-12-04
Simple as:
```

if "key" in { "Not_that_Key" : 6, "That_Key" : 1, "key" : 1232}:
       ...

```
This condition is valid since there is a key "key" in that dictionary.

---

### Post by ofnuts on 2011-12-04
There are several ways to tackle the problem:

Make sure the keys always exist: fill the dictionary with dummy value before loading the real ones orfill the holes once the values have been loaded (the latter method may let you fill missing values using those loaded).

Or cope with empty keys: code explicit tests or use try/catch blocks and define appropriate behavior for undefined values.

---

### Post by MadCow108 on 2011-12-04
> **ofnuts said:**
> Make sure the keys always exist: fill the dictionary with dummy value before loading the real ones orfill the holes once the values have been loaded (the latter method may let you fill missing values using those loaded).

in the collections module there is a defaultdict for this purpose
you can also use the .get function of dictionaries to get default values without needing to fill it first.

---

### Post by kramer65 on 2011-12-04
> **cgroza said:**
> Simple as:
```

if "key" in { "Not_that_Key" : 6, "That_Key" : 1, "key" : 1232}:
       ...

```
This condition is valid since there is a key "key" in that dictionary.
I know. The thing is that it is not one key in one dictionary, but one key in two dictionaries. So if I would want to use that, the total if-construction would be this:
```
if (datum in first_stop_high) and (datum in first_stop_low):
    if (first_stop_high[datum][:8] > buy_time and first_stop_high[datum][:8] < sell_time):
        first_stop_high_from_dict = first_stop_high[datum]
    else first_stop_high_from_dict = 0
    if (first_stop_low[datum][:8] > buy_time and first_stop_low[datum][:8] < sell_time):
        first_stop_low_from_dict = first_stop_low[datum]
    else first_stop_low_from_dict = 0

    if first_stop_high_from_dict != 0 and first_stop_low_from_dict != 0:
        if first_stop_low_from_dict[:8] <= first_stop_high_from_dict[:8]:
            sell_price = first_stop_low[datum][8:]
        else:
            sell_price = first_stop_high[datum][:8]
    elif first_stop_high_from_dict != 0 and first_stop_low_from_dict == 0:
        sell_price = first_stop_high[datum][:8]
    elif first_stop_high_from_dict == 0 and first_stop_low_from_dict != 0:

elif (datum in first_stop_high) and (datum not in first_stop_low):
    if first_stop_high[datum][:8] > buy_time and first_stop_high[datum][:8] < sell_time:
        sell_price = first_stop_high[datum][8:]
    else:
        sell_price = tijd_dict.get(sell_time,0)
elif (datum not in first_stop_high) and (datum in first_stop_low):
    if first_stop_low[datum][:8] > buy_time and first_stop_low[datum][:8] < sell_time:
        sell_price = first_stop_low[datum][8:]
    else:
        sell_price = tijd_dict.get(sell_time,0)   
else:
    sell_price = tijd_dict.get(sell_time,0)
```

I simply cannot imagine that this is the best way. This is why I find Pythons behaviour of not accepting non existing keys so enormously annoying. I know, it is bad programming to call for keys that are not there, but giving straight errors.. :confused:


> **ofnuts said:**
>  Make sure the keys always exist: fill the dictionary with dummy value before loading
But it may well be that more than half of the values is missing, so I would have to insert more dummy values than there are real values. Which sounds kind of awkward..

> **ofnuts said:**
>  or fill the holes once the values have been loaded (the latter method may let you fill missing values using those loaded).
How would you suggest I would do this? Sorry to ask, but I'm kinda lost in how I would go over something like that..


> **MadCow108 said:**
> in the collections module there is a defaultdict for this purpose
But do I need to insert all the keys that are missing with the default value then, or does a defaultdict simply serve a default value (eg. 9999) if a key is asked for which is not in the dictionary?

> **MadCow108 said:**
>  you can also use the .get function of dictionaries to get default values without needing to fill it first.
But when I use the get method, can I already get a slice of the value in case the key does exist? So something like this:

```
if (first_stop_high.get(datum[:8], 0) > buy_time and first_stop_high.get(datum[:8], 9999) < sell_time):
```

---

### Post by MadCow108 on 2011-12-04
> **kramer65 said:**
> 
But do I need to insert all the keys that are missing with the default value then, or does a defaultdict simply serve a default value (eg. 9999) if a key is asked for which is not in the dictionary?
a default value is insert on request of a missing key, very useful for dictionary containing lists or counting dictionaries (see also collections.Counter in python 3.2)
```

d = defaultdict(list)
d[1].append(1)
d[1].append(1)
d[1] == [1,1]

```
but its probably not appropriate in your case as you do not appear to want to insert missing keys
you probably want to use .get if you choose to take the default value route

> **kramer65 said:**
> 
But when I use the get method, can I already get a slice of the value in case the key does exist? So something like this:

```
if (first_stop_high.get(datum[:8], 0) > buy_time and first_stop_high.get(datum[:8], 9999) < sell_time):
```
are you here comparing strings to numbers? thats not good, convert the values to appropriate types.
you can do some slicing by just adjusting the default value appropriatly so that it slices the same way a real entry would:
```
dict().get("key", "123456789")[:4] == "1234"
```

---

### Post by Tony Flury on 2011-12-05
A very pythonic way of doing this - if you want a certain specific behaviour if your key is missing from a pair of dictionaries is to subclass your dictionary into a new type which behaves like a dictionary but crucially does something special if your key is missing.

Without understanding exactly what your code is trying to do I can't give you a code sample, but this method would at least stop you having to repeat ugly code multiple times.

Could it also be that your data model is wrong if you are having to check in two separate dictionaries ? This suggests to me that actually they are very similar or related things and it might be better to merge them into one dictionary (maybe a dictionary of tuples, or a dictionary of class instances).

---

### Post by StephenF on 2011-12-05
After refactoring the core logic becomes more apparent.
```

class Wrapper(str):
    """This class allows for sane access methods to the data.

    For want of better names it uses l and r for the left and right values.
    """
    
    def __new__(cls, newval):
        if newval is None:
            return None
        return super(Wrapper, cls).__new__(cls, newval)

    @property
    def l(self):
        return self[:8]

    @property
    def r(self):
        return self[8:]


def within_time(d):
    return d.l > buy_time and d.l < sell_time


sell_price = tijd_dict.get(sell_time, 0)  # Use fallback value unless overwritten.

# Note: list comprehensions leak the dummy variable in Python 2.x (yes, really).
hd, ld = t = tuple(Wrapper(x.get(datum, None)) for x in (first_stop_high, first_stop_low))

if all(t):  # Strings are always boolean true in Python.
    hd, ld = t = tuple((within_time(x) and x or None) for x in (hd, ld))
    if all(t):
        if ld.l <= hd.l:
            sell_price = ld.r
        else:
            sell_price = hd.l
    elif hd is not None:
        sell_price = hd.l
    elif ld is not None:
        sell_price = ld.r  # This is a guess since the code was missing.

else:
    d = max(t)
    if d is not None and within_time(d):
        sell_price = d.r

```

---

### Post by kramer65 on 2011-12-06
Thank you for all your answers. Although pretty different in nature, all your answers made me have another critical look at my code. I tried so many things over the past two days. In the end I went back to where I create the two dictionaries and had a look at that. I finally decided that it was indeed easier to combine them into one dictionary. I now only have to check one dictionary for the existence of a  certain key. Next to being easier, it even made my code faster.. :)

So thank you for your critical remarks and suggestions! They made my mind sharper as well.. :)

I'll mark this thread as solved now. If anyone has time I do have one more question though.

Lets say that I have two numbers in each dictionary together as one string. I then want to check whether a part of the value of the dictionary element (ie, the first of the two numbers, which is always 8 figures) is above a certain value, but I obviously only want to check this if the key exists. Is the most simple way to do this the following:

```
if k in some_dictionary:
    if some_dictionary[k][:8] > other_number:
	variable_to_be_set = float(some_dictionary[k][8:])
    else:
        variable_to_be_set = 99
else:
    variable_to_be_set = 99
```

It somehow seems weird that I have to define the variable_to_be_set two times as 99 (in both else statements). What am I doing wrong here?

[SIZE="1"](or is it again totally wrong to have two numbers in a dictionary together as one string..? )[/SIZE]

---

### Post by ofnuts on 2011-12-06
> **kramer65 said:**
> Lets say that I have two numbers in each dictionary together as one string. I then want to check whether a part of the value of the dictionary element (ie, the first of the two numbers, which is always 8 figures) is above a certain value, but I obviously only want to check this if the key exists. Is the most simple way to do this the following:

```
if k in some_dictionary:
    if some_dictionary[k][:8] > other_number:
    variable_to_be_set = float(some_dictionary[k][8:])
    else:
        variable_to_be_set = 99
else:
    variable_to_be_set = 99
```It somehow seems weird that I have to define the variable_to_be_set two  times as 99 (in both else statements). What am I doing wrong here?

Because you are testing two conditions in sequence, that could be tested together:
```

if k in some_dictionary and some_dictionary[k][:8] > other_number:
     variable_to_be_set = float(some_dictionary[k][8:])
else:
     variable_to_be_set = 99
 
```When using a "logical and", if the first condition isn't met, the interpreter (or the code generated by a compiler) knows that the overall condition can't be met and so doesn't evaluate the rest of the expression, so you won't get an error when evaluating some_dictionary[k].

---

### Post by kramer65 on 2011-12-07
> **ofnuts said:**
> When using a "logical and", if the first condition isn't met, the interpreter (or the code generated by a compiler) knows that the overall condition can't be met and so doesn't evaluate the rest of the expression
Ah! I didn't know that. That is actually really handy since I often need to do a sequence of tests like
```
if k in a_dictionary:
    if a_dictionary[k] == some_value:
        if p in another_dictionary:
            if another_dictionary[p] == some_other_value:
                do stuff
```
So I can now write all of them in one if-statement.

Thanks a lot!

---

