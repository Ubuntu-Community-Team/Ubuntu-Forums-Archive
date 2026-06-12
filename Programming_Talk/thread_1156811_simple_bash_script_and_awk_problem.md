---
title: "simple bash script and awk problem"
date: 2009-05-12
forum: Programming Talk
---

### Post by meborc on 2009-05-12
Hi all... need help with awk


i'm working on a bash script that has to check the time and then execute the commands specified in the script only if the minutes are 10, 20, 30 etc, else sleep for certain amount of seconds until the minutes are correct

now i can get the minutes easily with > $(date +%M) but i need only the last digit... so is there a way to display only the second character in first field with awk?

i have searched the web, and there are a lot of information about printing the first, second, whatever field, but never the character...

i guess it is simple, but i just can't find the solution :)

any help appreciated

---

### Post by meborc on 2009-05-12
well... found a fix

> $(date +%M | tail -c 2)

seems to do it... why didn't i think of tail before :D

---

### Post by Dill on 2009-05-12
If you'd still like to use awk, you can also try this:

```
date +%M | awk '{split($0,a,""); print a[2]}'
```

Basically, we're splitting the output with a null delimiter, which just splits it into an array character-by-character. Printing the second element of the array gives us the final character:

```
satherdy@lamp:~/test$ date +%M
17
satherdy@lamp:~/test$ date +%M | awk '{split($0,a,""); print a[2]}'
7

```

---

### Post by meborc on 2009-05-12
> **Dill said:**
> If you'd still like to use awk, you can also try this:

```
date +%M | awk '{split($0,a,""); print a[2]}'
```

Basically, we're splitting the output with a null delimiter, which just splits it into an array character-by-character. Printing the second element of the array gives us the final character:

```
satherdy@lamp:~/test$ date +%M
17
satherdy@lamp:~/test$ date +%M | awk '{split($0,a,""); print a[2]}'
7

```

thank you :) awk rocks

---

### Post by ghostdog74 on 2009-05-12
don't have to do split
```

date +%M |awk  'BEGIN{FS=""}{print $NF}'

```

---

### Post by meborc on 2009-05-14
> **ghostdog74 said:**
> don't have to do split
```

date +%M |awk  'BEGIN{FS=""}{print $NF}'

```

Thank you! can you also explaine, what different parts of this code mean? I would like to modify it later... 

I will digg into awk tutorials as soon as i'm finished with work :D

---

### Post by ghostdog74 on 2009-05-14
> **meborc said:**
> Thank you! can you also explaine, what different parts of this code mean? I would like to modify it later... 

I will digg into awk tutorials as soon as i'm finished with work :D

when you put FS="", it means field separator with nul value. essentially it means each character is its individual column.

---

### Post by meborc on 2009-05-14
> **ghostdog74 said:**
> when you put FS="", it means field separator with nul value. essentially it means each character is its individual column.

thanks... very cool!

---

