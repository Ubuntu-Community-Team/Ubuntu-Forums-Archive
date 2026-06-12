---
title: "Easy Python Question regarding Dictionaries"
date: 2009-05-02
forum: Programming Talk
---

### Post by M4rotku on 2009-05-02
Hello all,

I am currently trying to write a phone book program just for the sake of gaining some experience.  I would like to use a dictionary to keep track of the names and numbers before outputting them to a file.  I have a loop set up that prompts the user for a name and its number over and over again.  Is there any way in which I can use a function similar to what append() does for lists to add new definitions to my dictionary?  The dictionary idea is as follows:

> book = {name : number, name : number, etc}

If anyone can tell me of an append() equivalent function for dictionaries, it would be much appreciated.

Much thanks,
M4rotku

---

### Post by Flimm on 2009-05-02
[php]
dict = {}
dict["new name"] = 123456
[/php]
Yup, you can assign values to new keys directly. Every key is unique, so assigning a value to an already existing key:value pair will overwrite the old value.

---

### Post by M4rotku on 2009-05-02
Thanks, I was a bit worried that I wouldn't be able to use a dictionary and thus wouldn't be able to sort the names and number.

Thanks for your quick response.

---

### Post by M4rotku on 2009-05-03
Okay, I ran into another problem with my dictionary.  I need to be able to separate the keys from the values.  This can be done with the .keys(), but I need to be able to do it one at a time.

For example, if my phonebook dictionary is defined as:

> phonebook = {'home' : 123-456-7890, 'work' = 908-65-4321}

then I need a command that will allow me to extract 'home' so that i can print it to a file and then another command that will extract 123-456-7890 so that i can put that in a file.  I'm guessing that the function would probably work so that I can specify the number of the key or value that I am extracting.

Ex)
phonebook.function(0) would return 'home'
phonebook.function(1) would return 'work'

Is there anything that does this?  I would imagine that such a function has to exist.

Much thanks,
M4rotku

---

### Post by sujoy on 2009-05-03
```
phonebook = {'home' : "123-456-7890", 'work' : "908-65-4321"}
for key in phonebook.keys():
    print "key is %s : value is %s" % (key,phonebook[key])
```

---

### Post by M4rotku on 2009-05-03
wow, can you explain what all of those % are doing?  I've seen them in code before, but I have no idea what they are there for.  I guess that works, but I was just looking for something a bit less confusing.

Can you put that in layman's terms?

---

### Post by .Maleficus. on 2009-05-03
%s is a string, so what you're doing is replacing every instance of "%s" in the preceding line with the respective value in the tuple following the % sign.  SOOO...

The first instance of "%s" is replaced by the first value in (key,phonebook[key]).  That is the value of the 'key' variable.  The second instance is replaced by 'phonebook[key]'.  This can go on an indefinite amount of times, ie, "%s %s %s" % (key, bookmark[key], var_x) would print the values of key, then bookmark[key], then var_x, if that makes sense.

---

### Post by wmcbrine on 2009-05-04
> **M4rotku said:**
> phonebook.function(0) would return 'home'
phonebook.function(1) would return 'work'

Is there anything that does this?  I would imagine that such a function has to exist.No. A Python dictionary is unordered, by definition; it makes no sense to look for the Nth entry. Instead you must use .keys(), and parse the list it returns.

phonekeys = phonebook.keys()
phonekeys[0] # 'home'
phonekeys[1] # 'work'

Since there is no guaranteed order (and the order *will* change as you add items), you may also want to sort the list of keys.

---

### Post by benj1 on 2009-05-04
why don't you use a nested dictionary or a list of dictionaries eg
```

mum = { home : '012345',mobile: '123456'}
dad = { home : '712345',mobile: '234567'}
```

then either:
```
phonebook = { entry1 : mum, entry2 : dad}
```

or

```
phonebook = [mum, dad]
```

then you can easily access all the details of one person or all home phone numbers etc

---

### Post by Can+~ on 2009-05-04
> **benj1 said:**
> why don't you use a nested dictionary or a list of dictionaries eg
```

mum = { home : '012345',mobile: '123456'}
dad = { home : '712345',mobile: '234567'}
```

then either:
```
phonebook = { entry1 : mum, entry2 : dad}
```

or

```
phonebook = [mum, dad]
```

then you can easily access all the details of one person or all home phone numbers etc

Or better, mum and dad are instances of a single class called Person, that has a home phone number, mobile phone number, ID, etc.

---

