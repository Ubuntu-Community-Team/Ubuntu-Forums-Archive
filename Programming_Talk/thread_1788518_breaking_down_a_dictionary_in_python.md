---
title: "breaking down a dictionary in python"
date: 2011-06-22
forum: Programming Talk
---

### Post by Pilen on 2011-06-22
I'm creating a simple text adventure in python. It takes commands from the user input and checks it in a dictionary, and the values are references to functions. But as I'm creating more functions(more stuff to do in the world) the dictionary is getting bigger. And it looks really bad to just let it grow on one line. Something must be done if it's going to get bigger.

Is there a proper way to break down a dictionary? Or should I just cut it down with the \ knife where it pleases me?

The dictionary:
```
userDict = {'e': goEast, 'exit': endGame, 'help': helpFunc, 'l': look, 'n': goNorth, 's': goSouth, 'storage': lookStorage, 'take': takeItem, 'w': goWest}
```

And can I make two keywords for the same value? For example 'e' and 'east' for value goEast, without repeating myself?

---

### Post by schauerlich on 2011-06-22
Just put them on separate lines.

```
def main():
    some_dict = {
        "a" : 1,
        "b" : 2,
        "c" : 3,
    }

    for pair in some_dict.items():
        print pair

if __name__ == "__main__":
    main()

```

---

### Post by Pilen on 2011-06-22
Thanks man.

---

### Post by cgroza on 2011-06-22
> **Pilen said:**
> 
The dictionary:
```
keywords for the same value? For example 'e' and 'east' for value goEast, without repeating myself?
I don't think so, the closest i could get was:
[CODE]
a[1], a[2] = "Hello", "Hello"

```

---

### Post by ziekfiguur on 2011-06-23
> **Pilen said:**
> And can I make two keywords for the same value? For example 'e' and 'east' for value goEast, without repeating myself?

sure you can: ```
userDict = {'e' : goEast, 'east': goEast}
```
or ```
userDict['e'] = goEast
userDict['east'] = goEast
```

---

### Post by TwoEars on 2011-06-23
There's several ways of doing it.
```

>>> keyword_list = ['a','b','c']
>>> d = dict(zip(keyword_list, [1 for x in keyword_list]))
>>> d
{'a': 1, 'c': 1, 'b': 1}

```
How about something like that?

---

