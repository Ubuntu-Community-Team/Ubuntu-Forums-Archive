---
title: "[SOLVED] start over?"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by thekidxp on 2008-07-24
I am starting to like linux although all of the learning has made my brain hurt for the day.
I don't know if i should or could reinstall like i want to. i want to basically restore things to default without losing my data i have everything installed and partitioned like i want, and some pictures and songs and other things i would like to not lose but i think i did so much and i'm not sure what all i actually did i think it may be best to start over is there anyway to do what i want?

---

### Post by sdennie on 2008-07-24
The safest way to do this would be to make a backup of your home directory. Then, when you re-install, create a separate partition for / and /home.  If you are learning Ubuntu and your method for learning is tinkering in potentially damaging ways, this will separate your data from the OS and you can re-install as many times as you like while keeping the same /home partition.  

Though, it might be a lot less time consuming to setup a VM with Ubuntu in it and try things in that before trying them on your real machine.  I have several Ubuntu VMs for this very purpose.  I would recommend [www.virtualbox.org](www.virtualbox.org) to get you started.

---

### Post by thekidxp on 2008-07-24
the VM seems like a great idea although I'm not trying to mess things up and i could probably be ok but i just did things i didnt understand and so i'm just not sure what i have installed and what didnt get deleted right because i did something i prolly shouldnt have, and thats try a solution without understanding what im doing just commands copied and i have no clue how to interpret whats going on.

and could you explain a good way to back my things up i have 3 partitions and one has vista one is for data and one is for ubuntu thank you very much for helping me out

---

### Post by thekidxp on 2008-07-24
can someone please help me out or somethings i should check to see if i have the things i need please i want to keep figuing things out

---

### Post by sdennie on 2008-07-24
> **thekidxp said:**
> the VM seems like a great idea although I'm not trying to mess things up and i could probably be ok but i just did things i didnt understand and so i'm just not sure what i have installed and what didnt get deleted right because i did something i prolly shouldnt have, and thats try a solution without understanding what im doing just commands copied and i have no clue how to interpret whats going on.


In the future, I wouldn't use any "tips and tricks" you find online unless a) You understand them b) The author is willing to help you understand them or c) Someone on these forums can help you understand them.

> 
and could you explain a good way to back my things up i have 3 partitions and one has vista one is for data and one is for ubuntu thank you very much for helping me out

You could use something like Simple Backup:

```

sudo apt-get install sbackup

```

Then it will be in System->Administration->Simple Backup Config.  Of course, depending on the nature of your data, you could also just take all your important files and burn them to CD/DVD and then later just copy them back (this may even be easier for a quick, one time backup solution).

---

### Post by thekidxp on 2008-07-24
Thanks I'll try it out and I'm really new. I know what the code was supposed to do but even the code you gave me I still only half understand  like I know that sudo is super user and it will install that program but I really have no clue how it works or whats happening after I use it.

---

### Post by sdennie on 2008-07-24
For the vast majority of commands you use in the terminal there is extensive documentation on exactly what they do in the manpages.  For example:

To learn more about sudo:

```

man sudo

```

To learn more about apt-get:

```

man apt-get

```

Etc...

---

### Post by thekidxp on 2008-07-24
like the problems were small at first like I tried to use synaptic to install some things and I dont think most of them worked but then I tried to find a way to watch clips online and mostly so I could watch comercial DVD's and that did a lot of things that may have messed things up. like totem wont play it but MPlayer will without menus and some sites online will give weird pop-ups that look like video clips that won't play and shut down my broweser.

---

### Post by thekidxp on 2008-07-24
alright I think I'll take things slower this time I got a little too excited too quickly I should be able to reinstall safely and I'll watch what I type and see what happens.

this is going to be hard I really wish I could start using this I'm not against learing but starting like I know absolutly nothing is hard but with everybodys help I think I'll figure it out

---

### Post by watsbe on 2008-07-24
I love the first line ... I am starting to like linux although all of the learning has made my brain hurt for the day...
Remember that you have been learning MS Windows for about [your age -10] years, so expect it to take at least a couple of more days to master "Linux"!
And most of all, continue to enjoy it.  It is fun trying new things.

---

