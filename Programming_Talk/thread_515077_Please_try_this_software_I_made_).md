---
title: "Please try this software I made :)"
date: 2007-08-01
forum: Programming Talk
---

### Post by xavier_r on 2007-08-01
Basically it all started with this [http://ubuntuforums.org/showthread.php?t=491119](http://ubuntuforums.org/showthread.php?t=491119)
I had planned and arranged some ncurses based apps, so that common tasks, can be started from command line...
Besides system tasks like Volume Control, Process Manager, Software Manager, Network Monitoring etc... could also be done...
Also one could run many apps, in a single terminal window, which I find great for my own use...
Its a total environment of its own...

After about 1 month of small small developing it turned out to be really quite something... 
At this moment, **I think some feedback would be great**... :)

The lastest stable version can be found here:
[http://screenface.66ghz.com/](http://screenface.66ghz.com/)

And I am including the current latest version(unstable) as an attachment here

To install it just, extract,... and then there's a file called install.sh
From the terminal do:
$ chmod +x install.sh
$ ./install.sh

and after installation is done add these lines in the bottom of your /etc/screenrc file
> 
#Displays tab name and date at the bottom of screen
shell -${SHELL}
caption always "%n(%t) : %C"


and that should do it...
It will install varous softwares, and make the CLI environment for you according to your choice...
Run ScreenFace, and then for knowing any commands(there are very few)  just press H for Help...

Please try it and tell me how you felt using it...

---

### Post by xavier_r on 2007-08-02
Did anyone try it?
Did you like using CLI apps?

---

### Post by Wybiral on 2007-08-02
Your install script should automatically fill in the default response if they enter a blank response (it's kind of unclear the way it is).

Other then that, it's nice, but why the use of PHP for a command line app?

EDIT:

Nevermind... It apparently does, but it's just not executing the programs for some reason.

I take that back... It's just not installing everything correctly (sorry, I'm tired and in the middle of a couple other projects, I'll look more into it in a little)

---

### Post by rolando2424 on 2007-08-02
I installed it, but when I type ScreenFace, nothing happens (when I'm inside screen, when I'm outside, it just runs my normal screen session, and I get no cool menu :D )).

Perhaps it's because I haven't add the text to my .screenrc (because I already have something similar).

EDIT: Nevermind, I installed the 1.3 version and it worked :D

It's nice, but since I already have my .screenrc to start all my apps, I might not have a lot of use for it (except remember some programs from time to time :D)

By the way, does the 1.3 write over the original ScreenFace, or do I have to manually erase that one?

---

### Post by thomasaaron on 2007-08-02
I didn't install it, but I did look at the Youtube video.

So, correct me if I'm wrong, here. But it seems like it is essentially an... applications manager. Which is fine. A while back I wrote a similar manager, albeit not as nicely done as yours. So good job.

I've always thought it would be cool to create an ncurses office suite with original applications, etc...

It would be nostalgic, lightning fast and probably not very popular. But it would be fun and maybe some old Linux goats would enjoy it.

---

### Post by xavier_r on 2007-08-02
Guys thanks for your comments... :)

> 
Other then that, it's nice, but why the use of PHP for a command line app?

Well PHP/Ncurses, is very new...
So I thought better give it a try...

> 
I take that back... It's just not installing everything correctly (sorry, I'm tired and in the middle of a couple other projects, I'll look more into it in a little)

Hey check out the stable version (1.3) then... :)

> 
By the way, does the 1.3 write over the original ScreenFace, or do I have to manually erase that one?

It overwrites the original one...

> 
I've always thought it would be cool to create an ncurses office suite with original applications, etc...
It would be nostalgic, lightning fast and probably not very popular. But it would be fun and maybe some old Linux goats would enjoy it.


Dude are you thinking what I am thinking? :D
Basically mostly Linux buffs would enjoy it... and yup, very low memory consumption so lightning fast...

Anyways, thanks for the comments :)

---

### Post by xavier_r on 2007-08-02
> **rolando2424 said:**
> I installed it, but when I type ScreenFace, nothing happens (when I'm inside screen, when I'm outside, it just runs my normal screen session, and I get no cool menu :D )).

Perhaps it's because I haven't add the text to my .screenrc (because I already have something similar).


Hey dude, I'm glad ver1.3 is working on your machine...
The latest version includes un-debugged code...
Maybe to check, why it didnt run
Do this

$ cd ~/.ScreenFace
$ php ScreenFace.php

Is it showing any errors? Then that might be the problem...
Otherwise it might be the problem with screen...

---

### Post by rolando2424 on 2007-08-02
> **xavier_r said:**
> Hey dude, I'm glad ver1.3 is working on your machine...
The latest version includes un-debugged code...
Maybe to check, why it didnt run
Do this

$ cd ~/.ScreenFace
$ php ScreenFace.php

Is it showing any errors? Then that might be the problem...
Otherwise it might be the problem with screen...

> Warning: touch(): Utime failed: Operation not permitted in /home/rolando/.ScreenFace/ScreenFace.php on line 32

Warning: touch(): Utime failed: Operation not permitted in /home/rolando/.ScreenFace/ScreenFace.php on line 33

But ScreenFace seems to be working fine.

Too bad I don't know PHP, or I could see what was the problem.

---

### Post by xavier_r on 2007-08-03
> **rolando2424 said:**
> 

Warning: touch(): Utime failed: Operation not permitted in /home/rolando/.ScreenFace/ScreenFace.php on line 32

Warning: touch(): Utime failed: Operation not permitted in /home/rolando/.ScreenFace/ScreenFace.php on line 33


Dude I know what the problem is... :)
Dammit... I overlooked this...!!! Even though its just a warning...

I've attached the changed version here...(its unstable, not 1.3)
I think the warning will be removed
You can install it or 
You can just copy the "ScreenFace.php" file to your "$HOME/.ScreenFace" directory
and copy the "ScreenFace" file to "/usr/bin/ScreenFace"

---

### Post by rolando2424 on 2007-08-03
> **xavier_r said:**
> Dude I know what the problem is... :)
Dammit... I overlooked this...!!! Even though its just a warning...

I've attached the changed version here...(its unstable, not 1.3)
I think the warning will be removed
You can install it or 
You can just copy the "ScreenFace.php" file to your "$HOME/.ScreenFace" directory
and copy the "ScreenFace" file to "/usr/bin/ScreenFace"

Well, it seems to be working fine now :D

---

### Post by xavier_r on 2007-08-04
> **rolando2424 said:**
> Well, it seems to be working fine now :D

Thanks :)

I was wondering that do many people use CLI as an alternative environement?
I think its very rare nowadays... even thought of the fact that CLI is AWESOME...
It consumes less memory and is superfast...

---

