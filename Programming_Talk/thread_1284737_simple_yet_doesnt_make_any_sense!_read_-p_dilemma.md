---
title: "simple yet doesnt make any sense! read -p dilemma"
date: 2009-10-06
forum: Programming Talk
---

### Post by alesserfate on 2009-10-06
hey guys/girls

i've completed a script that works with writing addresses and full names into a file

however, when i use

       read -p "Enter your address here: " address

and issue example "48 Owned St"

it only saves "48"

I've tried using the 
     
              read -p "Enter your address here: " -r address

and that -r command works when in a separate small script but not in my script

just some background info: the line that contains this command is a really long command that consists of many arguments linked together with && and a || midway

if anyone could help soon would be great, thanks!

---

### Post by slavik on 2009-10-07
you might be doing something wrong:

```
slavik@slavik-desktop:~$ read -p "Enter your address here: " address && echo $address
Enter your address here: 48 Owned St
48 Owned St

```

---

