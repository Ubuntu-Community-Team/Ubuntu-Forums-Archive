---
title: "printing nested lists python"
date: 2011-03-02
forum: Programming Talk
---

### Post by Bigmon on 2011-03-02
I wonder if someone can help:

I am trying to print the following nested list in order but not nested. I only need print the values and not the names of the metals. I am only allowed to use a "for loop":

```


alkaline_earth_metals = [["Beryllium",4,9.012],["magnesium",12,24.305],
["calcium",20,40.078],["strontium",38,87.62],["barium",56,137.327],["radium",88,226]]


```

Any ideas

---

### Post by MadCow108 on 2011-03-02
where exactly is the problem? one solution is obvious from the wording of your question alone *cough**for loop**cough*

another possible solution involves this:
itertools.chain.from_iterable
in what way is for you to find out, as this looks like homework.

---

### Post by Bigmon on 2011-03-02
I have come up with the following, but it prints the elements nested on different lines. 

```

for i in alkaline_earth_metals:
    q = i[1:3]
    print(q)

```



I have also tried appending to another list but it still appears nested:

```

new_list =[]
for i in alkaline_earth_metals:
    q = str(i[1:3])
    new_list.append(q)
print(new_list)

```

---

### Post by onandcorei on 2011-03-02
What will the format of the output be? 
Values in order not in a list,in a list or etc.

e.g. 

```
[[4, 9.012], [12, 24.305], [20, 40.078], [38, 87.62], [56, 137.327], [88, 226]]
```

or 

```
[4, 9.012] [12, 24.305] [20, 40.078] [38, 87.62] [56, 137.327] [88, 226]
```

or different from these ones
SHARE THE EXPECTED OUTPUT FORMAT :D

---

### Post by Bigmon on 2011-03-02
In order, on the same line, but not in list form.

---

### Post by onandcorei on 2011-03-02
```

alkaline_earth_metals = [["Beryllium",4,9.012],["magnesium",12,24.305],
["calcium",20,40.078],["strontium",38,87.62],["barium",56,137.327],["radium",88,226]]

for eleman in alkaline_earth_metals:
	print eleman[1],eleman[2],


```

---

### Post by Bigmon on 2011-03-02
Yes, many thanks - I see. This is what I finished with, which produces the desired results. Long winded way of doing it I am sure:  

```

new_list = []
for i in alkaline_earth_metals:
    new_list.append(i[1])
    new_list.append(i[2])
print(new_list)

```

---

