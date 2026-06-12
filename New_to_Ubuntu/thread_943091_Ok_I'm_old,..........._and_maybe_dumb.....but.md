---
title: "Ok I'm old,........... and maybe dumb.....but"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by Ron G on 2008-10-09
I have the latest version of Ubuntu, and I love it. I messed with linux a few years ago, and wasn't too successful with running it ( on much older pc's) so I sort of gave up. I'm not much of a geek, so I found some of the directions hard to follow. I do however remember that I could log in as "root", and make changes to folders, ect., ect.
Now my Ubuntu problem: I have been trying to add some skins to my aMSN, just to change it up once in a while, but the directions on their page tells me what commands to enter, and where, but Ubuntu wont except the commands. I assume it's because I am not logged in as "root", and the reason I am not, is because I cant figure out how to do that particular exercise. Now before you guys with so much knowledge jump in here and give me direction in the error of my ways, please remember, I am about to be 62 years old, and my understanding of the computer world is somewhat limited.
OK, that being said, fire at will, and thanks in advance for any and all assistance.

---

### Post by SunnyRabbiera on 2008-10-09
yes the root account is disabled by default in Ubuntu, as a substitute we use sudo.
I am not exactly sure on how to fix your issue as I dont use amsn but yeh instead of using a root account here in Ubuntu we use sudo.

---

### Post by jerome1232 on 2008-10-09
A link to the instructions you are following would help us to give the adjustments you would need to make.

---

### Post by crazyness003 on 2008-10-09
Basically, when you get a command to enter, tack a sudo in front of is. Like this
```
sudo <random command>
``` So its gonna look like this:
```
user@xxx:~$ sudo <random command>
```then you get greeted with a 
```
[sudo] password for user:
``` here you enter your root password (the one you set up when you installed)
Its not gonna show your input, but its still registering your password, so when you hit enter, it will execute.
If not you get 
```
Sorry, try again.
[sudo] password for user:
```
If that dosnt work, then like the guy before me said, a link to the instructions would be helpful

---

### Post by SuperSonic4 on 2008-10-09
Normally you'd use gksudo nautilus and navigate there.

However with aMSN you can install the skins by copying to /home/<user>/.amsn/skins which can be done as user

---

### Post by Jim! on 2008-10-09
Just type "sudo" before the command, after that it might ask for your password.

---

### Post by lisati on 2008-10-09
> **SuperSonic4 said:**
> Normally you'd use gksudo nautilus and navigate there.

However with aMSN you can install the skins by copying to /home/<user>/.amsn/skins which can be done as user

sudo, "Super User DO", is good for command-line stuff, gksudo is used for GUI stuff.

---

### Post by Ron G on 2008-10-10
> **SuperSonic4 said:**
> Normally you'd use gksudo nautilus and navigate there.

However with aMSN you can install the skins by copying to /home/<user>/.amsn/skins which can be done as user
Thanks for all the good replies. I got it done last night while at home (where I could relax, and cuss), when I figured it out. When it asked for me to extract the files, I entered the .amsn/skins in the window and the skins went where the would be seen in the program for me to load as I was supposed to. I wasnt realizing that the first part of the command was already loaded in the window where it shows the folders. In this case, it would have been good to know this, but like I said, I'm old and dumb when it comes to the working of linux, and pc's. Thanks again for all the help.

---

### Post by crazyness003 on 2008-10-12
well, im glad your problems is solved...speaking of which, you might wanna click the "thread tools" link in this thread and mark this thread [SOLVED], I dunno why, but the guys here like that.

---

### Post by hyper_ch on 2008-10-12
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

Just imagine what these forums would look like if everybody would just post "Help" or "Noob here". What do you think how many people will still look at such threads?

Furthermore, for unrelated questions it's also adviced to open a seperate thread for each one, so that each problem can be addressed (and eventually marked as solved) individually.

---

