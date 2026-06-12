---
title: "nvidia ubuntu"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by djallalnamri on 2008-08-21
*hello all
*i am absolute beginner to ubuntu
*installation made no problem
*my main problem after was the screen resolution as it would not go more than 640*480:my graphic card i an nvdia gfx 5200
*anybody can help ... as my main hobby is computer graphics
*thanks in advance

---

### Post by neurostu on 2008-08-21
How did you install your nvidia driver?

Did you use the Hardware Drivers Manager? Envy? The Nvidia Binary?

---

### Post by bobnutfield on 2008-08-21
The easiest thing to do to get your resolution correct is to install the nVidia drivers with a program called EnvyNG/  This program will install the correct drivers for ATI and nVidia cards.  Open a terminal and type:

> sudo apt-get install envyng

This is a GUI program and will be in the System menu list.  Just run the program, choose the nVidia driver.  Close down X and restart it, and your resolution should be fine.

---

### Post by djallalnamri on 2008-08-21
*thanks really for such quick replies and feedback
*will quickly try them all and let you know
*again big thanks

---

### Post by neurostu on 2008-08-21
First try the ubuntu driver... 
envy does things a little different and while it improves the experience for most people I would recommend against it unless you absolutely cannot get the ubuntu packaged driver to work

---

### Post by djallalnamri on 2008-08-21
*sorry again
*as an absolute beginner to ubuntu i don't know how it installs new application :it seems to have installed envyng but i cannot tell exactly
*sorry and thanks again

---

### Post by neurostu on 2008-08-21
did you run the command that he listed above?

Here is what you should try:
click System-->Administration-->Hardware Drivers
type in your password 
then click the driver for the Nvidia card and set it to enabled...
Ubuntu will then install the driver
then restart!

---

### Post by djallalnamri on 2008-08-21
*well 
 system...administration...hardware drivers...don't take to a password and a list of drivers on this ubuntu 8.04 it simply says that a drivers is already running the one of nvidia as i have tried to use the cd which is delivered with the graphic but it is full of windows files simply

---

### Post by neurostu on 2008-08-21
Then try this:
open a terminal and type the following commands:
```

sudo apt-get install nvidia-settings

```
then run:
```

gksudo nvidia-settings

```
then try to resize your screen resolution... click apply and click Save X Configuration File

---

### Post by djallalnamri on 2008-08-22
*hello again
*finally the problem was solved when i did what you said:
 -installing envyng first
 -then it asked for nvidia-glx-legacy-envy
 and all i did was to let the application do the job while being scared reading error messages....but it works!!!!
*now as experienced ubuntu users have you any golden rules to teach an ubuntu asbolute beginner!!!!
*once again:thank you * 4

---

### Post by neurostu on 2008-08-22
There is only one RULE use for FORUM!!!
-Search the Forums before you Post your question.
-Post when you have questions
-Give help when you can.

---

