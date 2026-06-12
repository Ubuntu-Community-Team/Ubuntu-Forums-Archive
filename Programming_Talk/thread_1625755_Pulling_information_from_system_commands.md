---
title: "Pulling information from system commands"
date: 2010-11-19
forum: Programming Talk
---

### Post by msjones on 2010-11-19
Hi,

Is there any way to grep information from the output of system commands. For example I want to pull the amount of free system memory from the free command:
> 
             total       used       free     shared    buffers     cached
Mem:          3017        848       2169          0         97        363
-/+ buffers/cache:        386       2631
Swap:         7628          0       7628


I want to be able to pull the top columns and first row from the table.

Can this be done?

---

### Post by Arndt on 2010-11-19
> **msjones said:**
> Hi,

Is there any way to grep information from the output of system commands. For example I want to pull the amount of free system memory from the free command:

I want to be able to pull the top columns and first row from the table.

Can this be done?

Is this what you want?

```
$ free | head -2
             total       used       free     shared    buffers     cached
Mem:       3026500    2639152     387348          0     346092    1090280
$ 
```

---

### Post by msjones on 2010-11-20
Exactly what I was looking for thank you very much.

Is there anyway to select just the free column?

---

### Post by spjackson on 2010-11-20
> **msjones said:**
> Exactly what I was looking for thank you very much.

Is there anyway to select just the free column?
Here's one way.
```

free | head -2 | sed 's/Mem://' | awk '{print $3}'

```

---

### Post by msjones on 2010-11-20
> **spjackson said:**
> Here's one way.
```

free | head -2 | sed 's/Mem://' | awk '{print $3}'

```

Thank you very much. Can you explain how this works, I'd like to get a grasp on it so I can apply it to other things.

---

### Post by spjackson on 2010-11-20
> **msjones said:**
> Thank you very much. Can you explain how this works, I'd like to get a grasp on it so I can apply it to other things.
awk '{print $3}' outputs only the third column, where each column is separated by one or more spaces. However, by this definition, we want the 3rd column from the 1st line and the 4th column from the second line. Therefore the sed command throws away the first column consisting of "Mem:" so that from what we feed into awk, we now want the 3rd column from each line.

---

### Post by msjones on 2010-11-20
> **spjackson said:**
> awk '{print $3}' outputs only the third column, where each column is separated by one or more spaces. However, by this definition, we want the 3rd column from the 1st line and the 4th column from the second line. Therefore the sed command throws away the first column consisting of "Mem:" so that from what we feed into awk, we now want the 3rd column from each line.

Thats brilliant, thanks dude. Your help is much appreciated!

---

### Post by Arndt on 2010-11-20
> **msjones said:**
> Thank you very much. Can you explain how this works, I'd like to get a grasp on it so I can apply it to other things.

For the commands mentioned, look at their manual pages: do "man sed", "man awk", "man head".

---

