---
title: "Help in Scripting"
date: 2012-10-22
forum: Programming Talk
---

### Post by Mohan1289 on 2012-10-22
How can we check weather the directory is created or not in shell script???

i mean if i write 

mkdir dirname

and if i have to run the script continuously 

is there a way to check weather the directory exists or not???

can we do that?

---

### Post by steeldriver on 2012-10-22
You can either check the exit status of the mkdir command directly

```
mkdir "$dir" || do something
```or by using the built-in **exit status** variable $?

```
mkdir "$dir"
if [ $? -ne 0 ]; then ...
```or test the directory existence with the -d **file test**

```
if [ -d "$dir" ]; then ...
```Just some ideas

---

### Post by Mohan1289 on 2012-10-22
> **steeldriver said:**
> You can either check the exit status of the mkdir command directly

```
mkdir "$dir" || do something
```or by using the built-in **exit status** variable $?

```
mkdir "$dir"
if [ $? -ne 0 ]; then ...
```or test the directory existence with the -d **file test**

```
if [ -d "$dir" ]; then ...
```Just some ideas

Thank you

---

