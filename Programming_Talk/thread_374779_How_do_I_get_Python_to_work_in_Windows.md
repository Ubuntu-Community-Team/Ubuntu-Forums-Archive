---
title: "How do I get Python to work in Windows?"
date: 2007-03-02
forum: Programming Talk
---

### Post by billdotson on 2007-03-02
I am on a computer running Windows XP and it has those user accounts setup.  As it is not my computer I do not have administrative access I cannot edit system files. The odd thing though is I clicked on the Python installer and it installed, although I cannot get it to run any program I create.  Here is one of my sample programs.  

```
 p = input( "What is your initial investment (input a number)?" , )
r = input( "What is your rate of interest?" , )
t = input( "How many years will your money be invested?" , )
n = input( "How many interest payments do you receive a year (how many compounding periods)?" , )
money = p + (1+((r/100)/n)**(n*t))
print money 
```

when I open the DOS shell I do the following:

dir C:\py*

c:\Python25\python

then type exit() in the Python interpreter because Ctrl + Z + Enter does not work.

Then if I type python interest.py (my interest application) it just drops down a line and doesn't aska question and just has a blank line to enter the input.  It does this until the inputs are done and then it just goes back to the C:\> and doesn't return the answer.  
If I just double click on the .py file it oepns it ina terminal and shows the input questions but then after the final one is answered the terminal just closes.

I was thinking I needed to add Python to my autoexec.bat to make it work correctly but I am not sure.

---

### Post by Darkness3477 on 2007-03-02
EDIT: I was wrong. Sorry for wasting your tine.

EDIT: You have a space infront of p = ,,,, That gives a syntax error. Perhaps that is causing it.

---

### Post by billdotson on 2007-03-02
I looked and there isn't a space before p =

---

