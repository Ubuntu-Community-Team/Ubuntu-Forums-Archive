---
title: "python CNC code interpreter ....file read n parse"
date: 2009-05-12
forum: Programming Talk
---

### Post by lonewolfaka9 on 2009-05-12
[B]hey im trying to make an python code which will read some txt file having CNC programming code .
On the basis of those code it will run an CNC 3-axis drill machine :guitar:

Baiscally the machine is connnected to PC via rs232 port an printer cable whose code will also be in python or c 

.
i need a way to read those CNC code n on the basis of code i want to do some task that will make rs232 port pin get high or low depanding upon code feature 

[/B]> G00 x ,y, x << move drill machine to certain coordinate 

G01 x,y,z << linear interpolation to given axis co-ordinates 


G04 n << delays the machine n times 

M00 stop machine 
M01 option stop 

M02 end of program 
M03 start drill amchine spindle

,M04 stop drillmachine spindle[B]

now code will be the combination of these few CNC codes


here n example

[/B]```
G00 x1.5 , y2.3 , z6.7
G01 z1.2
M03 
G01 z 1.5
G01 z -1.5
M01

```[B]


what i gotta do is read the source file using python command line 

then parse the CNC code if these codes are their it,ll check for the co-ordinates or numeric values provided an call some function


pls give me any source to do such task 

thanx n regards in advance :confused:
[/B]

---

### Post by Zugzwang on 2009-05-12
Read a general python introduction on how to split strings, parse simple stuff, etc.

Then look out for modules for interfacing with the RS-232 ports. Do some tests on the interfacing and then program your application.

---

### Post by dandaman0061 on 2009-05-12
This sounds awful homework-y...  Make some attempts at some code and we can correct/guide you.

The way I would go about designing the parsing would be to create an 'Instruction' baseclass and have subclasses for each of the different G00, G01, etc...  All of these classes should have a 'run' method which knows how to work based on what kind of class it is.

Then in the execution of the file create a list and every line you parse create the proper class and append it to the list.  When you are done parsing  you could go through this list of instructions and call each Instruction's run method in order.

---

