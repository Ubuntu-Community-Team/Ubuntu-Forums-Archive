---
title: "A question of lists and definitions in python"
date: 2011-12-07
forum: Programming Talk
---

### Post by borchst on 2011-12-07
Im an absolute beginner with python. Im trying to solve what seems to be a very simple problem, but i just dont know where to start. There might be a lot of resources on these things, but im not quite sure what im looking for. Sorry for my crude explanation. 

I have a list of things, which have a definition appended:

Cheddar: Cheese
orange: fruit
Brie: Cheese
banana: fruit
Camembert: Cheese
apple: fruit


Now, i want to output a list in the order of definition:

Cheese:
cheddar
brie
camembert

fruit:
orange
banana
apple

How do i append these definitions?

I have tried to make two lists and then, somehow, associate them through order of appearance:

```
objects ['cheddar', 'orange', 'brie', 'banana', 'camembert', 'apple']
dif ['cheese', 'fruit', 'cheese', 'fruit', 'cheese', 'fruit']
```But i dont know if i moving in the right direction.. 

I want to print the 'objects' while 'dif' equals cheese, or something like that. What would be the best practice in python for that?

---

### Post by Barrucadu on 2011-12-07
You could use something like a dictionary of lists:
```
stuff = {"cheese" : ["cheddar", ...], "fruit" : ["orange", ...]}
```

---

### Post by Bachstelze on 2011-12-07
You could do that, then the algorithm to print all cheeses would be

```
for s in list(set(dif)):
    print(s)
    for i in range(len(objects)):
        if dif[i] == s:
            print(objects[i])
```

However, your data structure is not very robust, you must be careful to not do anything that would cause the lists to go "out of sync". Probably better to use a dictionary, like that:

```
objects = {'cheddar': 'cheese', 'orange': 'fruit', 'brie': 'cheese' }
```

---

### Post by Bodsda on 2011-12-07
[LEFT]As Barrucadu mentioned, a dict of lists is a good way to go

```

mydict = {'cheese': ['cheddar', 'brie', 'camembert'], 'fruit': ['orange', 'banana', 'apple']}

for key in mydict:
    print "\n%s:" % key
    for item in mydict[key]:
        print item

```
```

cheese:
cheddar
brie
camembert

fruit:
orange
banana
apple

```

Bodsda
[/LEFT]

---

### Post by dodle on 2011-12-07
You can do it with lists and tuples as well:

[php]
objects = [('Cheese', ('cheddar', 'brie', 'camembert')), ('Fruit', ('orange', 'banana', 'apple'))]

for o in objects:
  print '%s:' % o[0]
  for i in o[1]:
    print i
  print[/php]

```
Cheese:
cheddar
brie
camembert

Fruit:
orange
banana
apple
```

---

