---
title: "[Python] Partitioning a String to Extract Values"
date: 2010-02-16
forum: Programming Talk
---

### Post by covertcj on 2010-02-16
Hi,

I'm attempting to partition a string that contains values along the lines of
```
"1c,2b,3w,4g,5r,6u"
```The string does not have to have all six of these terms and they are in no particular order. What I want to do is extract the value one and put it in a variable c, extract the 2 and put it in b, etc. As of now, I have been trying to do something along the lines of:

```
string         = string.lower()
costs          = string.split(',')

for cost in costs:
    cost                    = cost.strip()
    value, sep, garbage     = cost.partition(('u', 'r', 'w', 'g', 'b', 'c'))
```and yet I have found that you can't use a tuple of strings to partition by. I tried using google to find a way, but was unsuccessful. Is there a way to do this that I am unaware of? If not, does anyone have any suggestions on how to do this sort of string parsing?

Thanks,
Chris

---

### Post by sharpdust on 2010-02-16
> **covertcj said:**
> Hi,

I'm attempting to partition a string that contains values along the lines of
```
"1c,2b,3w,4g,5r,6u"
```The string does not have to have all six of these terms and they are in no particular order. What I want to do is extract the value one and put it in a variable c, extract the 2 and put it in b, etc. As of now, I have been trying to do something along the lines of:

```
string         = string.lower()
costs          = string.split(',')

for cost in costs:
    cost                    = cost.strip()
    value, sep, garbage     = cost.partition(('u', 'r', 'w', 'g', 'b', 'c'))
```and yet I have found that you can't use a tuple of strings to partition by. I tried using google to find a way, but was unsuccessful. Is there a way to do this that I am unaware of? If not, does anyone have any suggestions on how to do this sort of string parsing?

Thanks,
Chris

Before I attempt to help you out, I want to point out a red flag: don't call a variable 'string'. It may not appear to have any side affects now, but it may later on.

Anyways, consider this code:

```
#!/usr/bin/env python

def main():
    aString = "1c,2b,3w,4g,5r,6u".lower()

    costs = aString.split(',')
    print costs

    theDictionary = {}
    for cost in costs:
      theDictionary[cost[0]] = cost[1]

    print theDictionary



if __name__ == "__main__":
    main()
```

The first print has a list of all your char/letter combinations. The second print splits the combinations into a dictionary of key value pairs.

---

### Post by covertcj on 2010-02-16
> **sharpdust said:**
> Before I attempt to help you out, I want to point out a red flag: don't call a variable 'string'. It may not appear to have any side affects now, but it may later on.
Yeah, that's probably true. Wasn't planning on it though, I just typed up some code really quick to get the point across. :)

Yeah that method should work nicely, my string should never have a 2 digit value, but for the sake of learning, is there a good way of doing this if I could have values of ten or above (ex: "12u,1b,2r")?

Thanks!
Chris

---

### Post by sharpdust on 2010-02-16
> **covertcj said:**
> ... my string should never have a 2 digit value, but for the sake of learning, is there a good way of doing this if I could have values of ten or above (ex: "12u,1b,2r")?

Thanks!
Chris

Try adjusting the slice values

```
theDictionary[cost[0]] = cost[1]

```

The first slice cost[0] says give me the first character. The second says cost[1] give me the second character.

To always get the last character, try figuring out a solution that uses the len built-in function.

To get everything but the last character, you will have to use the len function and tweak the slice by using the colon ":" character.

Consider the following:

```

aword = "someword"
print aword[:2]

```

This slice notation says starting from the left side of the string, give me 2 characters.

From there you should be able to apply this to your program.

---

