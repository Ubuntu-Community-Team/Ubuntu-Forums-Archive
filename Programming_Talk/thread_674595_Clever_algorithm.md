---
title: "Clever algorithm?"
date: 2008-01-21
forum: Programming Talk
---

### Post by Xavieran on 2008-01-21
I am almost finished writing my little python banking program and am wondering...is it more clever to use a fancy algorithm that I made (which is really quite limited) to let the user select their choices ,or a simple if choice == 1:doThat()
structure?...
P.S.This question was brought upon by reading the end of Mark Pilgrims book,where it says "Don't try to be too clever,sometimes the most obvious is obvious for a reason":)

Fancy Algorithm...
```
        print "Welcome to pybank\n"
        values=[]
        cnt=1
        for key in self.MainMenuOps.keys():
            print "%d)"%cnt+key
            cnt+=1
        for value in self.MainMenuOps.values():
            values.append(value)
        prompt=int(raw_input("Select an option:"))-1
        eval("self.%s()"%values[prompt])      
```

Unfancy thing...

```
print "Welcome to pybank\n"
print "1)Login\n2)Logout"
choice = raw_input("Select an option")
if choice == 1:Login()
elif choice == 2:Logout()
else:print "Invalid option" 
```

---

### Post by gimfred on 2008-01-21
The non fancy program was easier to read.... but then I just started teaching myself programming....

---

### Post by Xavieran on 2008-01-21
Yeah, I think it is easier to read...and it wouldn't waste any time appending and formatting stuff,not only that but I would consider it more staightforward and *pythonic*...

Also,a developer coming into my project wouldn't have to familiarise himself with the rationale for using that kind of code...

---

### Post by Wybiral on 2008-01-21
I would stick with the conditions since their intention is clearer (the other way will get confusing really quick if you're not careful).

PS:
Using "eval" is EVIL :)
Imagine if this were a real bank program and the user could execute any code just by entering it!

---

### Post by Xavieran on 2008-01-21
Yup,looks like we will stick to the normal way of doing things...

Wish me luck as I change all the instances of fancy algorithm xD

P.S...
The eval statement would only have executed the users choice...the user could only choose using a number or an error would ensue...but I see your point ;)

---

### Post by pmasiar on 2008-01-21
In Pythonland "clever" has negative association. Positive is "strightforward" "obvious" and "simple".

For a zen wisdom of Python, in shell, type "import this".

---

### Post by Wybiral on 2008-01-21
> **Xavieran said:**
> 
The eval statement would only have executed the users choice...the user could only choose using a number or an error would ensue...but I see your point ;)

True, but the "eval" function should really be avoided if you can. In fact, the next time you're in a situation like that, assign the actual methods in the list like this:
```

values = [self.login, self.logout]

```

Then you can call them using:
```

value[0]()

```

For this case, the conditions would look much better, but if you ever have a situation like that, remember that Python has function pointers.

---

### Post by Quikee on 2008-01-22
You can do it to get good things from both worlds:

[PHP]
availableChoices = {
    "1" : Login
    "2" : Logout
}

print "Welcome to pybank\n"
print "1)Login\n2)Logout"
choice = raw_input("Select an option")
if choice not in availableChoices:
    print "Invalid option"
else:
    availableChoices[choice]()[/PHP]

Now all you have to do is fill the dictionary ;)

---

### Post by Paul Miller on 2008-01-22
> **Quikee said:**
> You can do it to get good things from both worlds:
.. (code and stuff deleted) ....


IMO, this is the best way of all.  I was going to post this exact code, but you beat me to it. :-)  It's explicit, clear, efficient, and maintainable all at the same time.  To me, that combination of things is the very definition of the word "pythonic."

---

### Post by pmasiar on 2008-01-22
Pythonic code uses dictionaries :-)

---

### Post by popch on 2008-01-22
> **Quikee said:**
> 
[php]
availableChoices = {
    "1" : Login
    "2" : Logout
}

...
print "1)Login\n2)Logout"
...
[/php]Now all you have to do is fill the dictionary ;)

In that case, I would rather print the contents of ***availableChoices***. 

Why: The proposed code contains the same decision twice, once in the dictionary and once in the printed text constant. That's a good recipe for inviting problems at a later time.

---

### Post by Quikee on 2008-01-22
> **popch said:**
> In that case, I would rather print the contents of ***availableChoices***. 

Why: The proposed code contains the same decision twice, once in the dictionary and once in the printed text constant. That's a good recipe for inviting problems at a later time.

Yes you are right - I didn't think about printing of choices at all. This is even better - but maybe then I would make a tuple with function and description as the dictionary value. The only problem is that dictionary doesn't define an order, but this can be solved with sorting (I don't think printing choices in a random order as a good thing ;) ).

[PHP]
availableChoices = {
    "1" : (Login,  "Log me in")
    "2" : (Logout, "Log me out")
    "3" : (Exit, "Exit the application")
}

print "Welcome to pybank\n"

sortedKeys = availableChoices.keys()
sortedKeys.sort()
for key in sortedKeys:
     function, description = availableChoices[key]
     print "%d: %s" % (key, description)

choice = raw_input("Select an option")
if choice not in availableChoices:
    print "Invalid option"
else:
    function, description = availableChoices[choice]
    function()
[/PHP]

---

### Post by popch on 2008-01-22
> **Quikee said:**
> ... but maybe then I would make a tuple with function and description as the dictionary value. The only problem is that dictionary doesn't define an order, but this can be solved with sorting 

Since the domain of the keys are (small) natural numbers anyway, why not dispense with the dictionary and use a list? Well, yes, the dictionary looks more python-ish but does not really offer an advantage I can see.

---

### Post by Quikee on 2008-01-22
> **popch said:**
> Since the domain of the keys are (small) natural numbers anyway, why not dispense with the dictionary and use a list? Well, yes, the dictionary looks more python-ish but does not really offer an advantage I can see.

Is also OK for me, but with a dictionary you are more flexible.. this is why I choose to use it.

[PHP]availableChoices = [
    (Login,  "Log me in"),
    (Logout, "Log me out"),
    (Exit, "Exit the application")
]

print "Welcome to pybank\n"

for index, choice in enumerate(availableChoices):
     function, description = choice
     print "%d: %s" % (index + 1, description)

choice = raw_input("Select an option")
choiceIndex = int(choice) - 1 # should handle the conversion string to int properly
if choiceIndex not in range(len(availableChoices)):
    print "Invalid option"
else:
    function, description = availableChoices[choiceIndex]
    function()
[/PHP]

---

### Post by Nekiruhs on 2008-01-22
> **Quikee said:**
> Yes you are right - I didn't think about printing of choices at all. This is even better - but maybe then I would make a tuple with function and description as the dictionary value. The only problem is that dictionary doesn't define an order, but this can be solved with sorting (I don't think printing choices in a random order as a good thing ;) ).

[PHP]
availableChoices = {
    "1" : (Login,  "Log me in")
    "2" : (Logout, "Log me out")
    "3" : (Exit, "Exit the application")
}

print "Welcome to pybank\n"

sortedKeys = availableChoices.keys()
sortedKeys.sort()
for key in sortedKeys:
     function, description = availableChoices[key]
     print "%d: %s" % (key, description)

choice = raw_input("Select an option")
if choice not in availableChoices:
    print "Invalid option"
else:
    function, description = availableChoices[choice]
    function()
[/PHP]
I believe
[PHP]
sortedKeys = availableChoices.keys()
sortedKeys.sort()
for key in sortedKeys:[/PHP]
Could be shortened to
[PHP]for key in availableChoices.keys().sort():[/PHP]
Not sure though. It looks more clear like that I think. No need to make unnecessary variables.

---

### Post by Wybiral on 2008-01-22
Not "availableChoices.keys().sort()" but if you meant "sorted(availableChoices.keys())" then that would work. The "sort" method doesn't return anything.

---

### Post by Quikee on 2008-01-22
> **Wybiral said:**
> Not "availableChoices.keys().sort()" but if you meant "sorted(availableChoices.keys())" then that would work. The "sort" method doesn't return anything.

Cool.. I didn't knew about "sorted" trick. ;)

---

### Post by Wybiral on 2008-01-22
> **Quikee said:**
> Cool.. I didn't knew about "sorted" trick. ;)

There's also "reversed". They're definitely handy for when you need to iterate something, but you don't want to alter the original container. Of course, with "reversed", you could also use "container[::-1]" but that doesn't seem quite as obvious. IMO, it's more pythonic to avoid symbols whenever you can.

---

### Post by ssam on 2008-01-22
> **popch said:**
> Since the domain of the keys are (small) natural numbers anyway, why not dispense with the dictionary and use a list? Well, yes, the dictionary looks more python-ish but does not really offer an advantage I can see.

for apps driven by menus with number options, it can be handy for 9 or 0 to always mean 'cancel' or 'back' or 'quit'. that means that you other have something like

1: apple
2: pear
3: banana
9: back

for a list you would need some sort of dummy value for 4, 5 etc.

---

