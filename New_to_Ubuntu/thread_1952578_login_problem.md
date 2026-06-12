---
title: "login problem"
date: 2012-04-04
forum: New to Ubuntu
---

### Post by dreyyy07 on 2012-04-04
after i put in my login password and press enter, the laptop freezes. I am using ubuntu 11.04

---

### Post by 23dornot23d on 2012-04-04
What login manager is it that you are using .....

Can you see Sessions ..... if so what other choices do you have ....

Is it Unity you are trying to boot into or something else ......


does Ctrl + Alt + F1  take you to a console ok ..... and can you login there ......

and do 

**df**
[B]
sudo apt-get clean
sudo apt-get autoclean[/B]


Just making sure you have not run out of space ..... is it a hard drive boot up
or from a USB stick ......

---

### Post by dreyyy07 on 2012-04-04
> **GCLumpkin said:**
> Click on your name, then look at the bottom of the login screen. Change the session to Ubuntu Classic. Type in your password and log in. Are you able to get to the desktop then?
it showed my wallpaper and froze

---

### Post by mörgæs on 2012-04-04
Please don't post the same question multiple times. 
Merged.

---

### Post by dreyyy07 on 2012-04-06
--my choices are:recovery console, ubuntu, ubuntu classic, ubuntu classic(no effects),ubuntu(safe mode), user defined session.
--the safe mode is the only option that works but is limited
--the whole thing about the ctrl+alt+f1 worked
--i am trying to boot into ubuntu
--it is a hard drive boot up

---

### Post by dreyyy07 on 2012-04-06
it played the login sound and hanged

---

### Post by dreyyy07 on 2012-04-10
help pls??!!  really urgent

---

### Post by 23dornot23d on 2012-04-10
If it was my machine the first thing I would do is make sure that everything is uptodate

get to the console like you did before .... if you have a internet connection make sure it is on ......

then

[B]sudo apt-get update

sudo apt-get install aptitude

sudo aptitude update

sudo aptitude safe-upgrade[/B]

once its upto date ....... try it again ....... if it still does not go in it may be a config
problem .....

if that is the case ( try to login as guest ) see if it goes in ok

If its not that then the desktop may not be loading in properly

**sudo aptitude reinstall unity **

may sort it ..... * ( Unity --reset ) is also a option if compiz settings were altered ...... 
and caused a problem with the config ...

best I can do for now ...... show screen shots or take photos and post back if there is
anything you think we should see ,,,,,,,

---

### Post by dreyyy07 on 2012-04-13
my laptop cant even boot into  ubuntu anymore

---

### Post by raja.genupula on 2012-04-13
choose Grub recovery mode and from there failsafeX mode and from there try to reinstall your graphics drivers .

---

### Post by 23dornot23d on 2012-04-13
> 
After i put in my login password and press enter, the laptop freezes. I am using ubuntu 11.04 	



> 
it played the login sound and hanged 	



> 
my laptop cant even boot into  ubuntu anymore 	


You can continue to try to fix it ...... but information is needed .....

What have you done to the computer that may have caused it to stop working
in the first place ..... the information you have told us so far is not making it easy to 
tell what the cause was - or what a solution could be ......

So from the original commands I asked you to use ..... df returned some figures ...
you responded with

> 
--my choices are:recovery console, ubuntu, ubuntu classic, ubuntu classic(no effects),ubuntu(safe mode), user defined session.
--the safe mode is the only option that works but is limited
--the whole thing about the ctrl+alt+f1 worked
--i am trying to boot into ubuntu
--it is a hard drive boot up 	


What make and version of laptop is it ?

How much Data is on it and is it all backed up .... is it Dual Boot ......

How much hard drive space do you have free ?

What graphics card is in the machine ?

My feelings on this one are that after all the information you have  given - 
( for a solution to fix this problem it would be as easy to install alongside the version you have a fresh Ubuntu ..... if you have the room on the hard disk for it ...... )

It would possibly be better for you or someone else to  reinstall a fresh version of Ubuntu 
 in a clean partition ..... use that to then get to your files .... it  takes 30 mins to do a fresh install .... do this alongside your original  .... if you have enough space on your
hard drive to do it ...... 

* ( only 2 weeks time the new 12.04 comes out .... it may be worth installing this when it does )

Meanwhile you can try to fix it or do as I say and add a fresh install alongside your original version  .....  try to give as much information as possible about your machine its graphics card and the drive space you have free and available to use on it .....

or as I say a fresh install alongside the existing takes 30 mins ... usually ....

---

### Post by dreyyy07 on 2012-04-23
i gave up and installed 11.10

---

