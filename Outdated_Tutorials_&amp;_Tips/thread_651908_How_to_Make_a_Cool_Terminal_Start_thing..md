---
title: "How to: Make a Cool Terminal Start thing."
date: 2007-12-28
forum: Outdated Tutorials &amp; Tips
---

### Post by fedex1993 on 2007-12-28
Okay many people have seen that when some people start up there is like a "Ubuntu" logo well i will tell you how you can do that.


1. The first thing you will need is to install a program called figlet. To do that Open up a terminal (Usually if your using gnome you would go to Applications>Accessories>Terminal) And than type "Sudo apt-get install figlet" it will most likely ask you yes or no do you want to install and you will half to type your password.


2. The second thing your going to do is while yo are still inside of the terminal(Applications>Accessories>Terminal) your going to type sudo gedit /home/username/.bashrc (where it says username put your login name) and at the very bottom of your .bashrc press enter than copy and paste in ```
figlet "ubuntu";echo -n 'Hello '; whoami; echo ''
``` just like that. Save the file.


3. Close the terminal window that you where in. Open up a brand new terminal(Applications>Accessories>Terminal) and you should see something like this at the top of your terminal [link]("http://img02.picoodle.com/img/img02/5/12/28/f_screeniem_3021efb.png") Something like that but i am still working on getting other stuff Like this.

Credits Go to Dr.Small from ubuntu forums he is the one that showed me how do actually do this from start.

Hope you try it.
Fedex

---

### Post by fedex1993 on 2008-03-10
now one likes this :(

---

### Post by Takinu on 2008-03-10
Hm, never thought of doing something like that, 
actually, it's pretty cool!

Welcome on:
 _                           ____       _        
| |   _   _  ___ _   _      | __ )  ___| |_ __ _ 
| |  | | | |/ __| | | |_____|  _ \ / _ \ __/ _` |
| |__| |_| | (__| |_| |_____| |_) |  __/ || (_| |
|_____\__,_|\___|\__, |     |____/ \___|\__\__,_|
                 |___/                           
Remember, with great power comes great responsibility.
takinu@Lucy-Laptop:~$ 




Thanks dude :P

---

### Post by Chokkan on 2008-03-10
That is pretty cool. Any way to customize?

---

### Post by fedex1993 on 2008-03-11
yeah i think you can change like what it says, like where it says "ubuntu" put like "FedeX" or something like that.

---

### Post by bobbocanfly on 2008-03-11
Was bored so wrote another one, this time using your hostname. Surprisingly useful to have your headless servers print their hostname in massive letters. You have no idea how many times i have messed things up typing the wrong commands into the wrong servers.

```
hostname | figlet; echo -n 'Hello '; whoami; echo;
```

Edit: PS fedex, this is cool :)

---

### Post by fedex1993 on 2008-03-11
yeah there is a unlimted possibilites of what you can put on there  :)

---

### Post by Dr.Ninethousand on 2008-03-11
neat, thanks..  :)

---

### Post by svtfmook on 2008-03-11
cool, thanks!

---

### Post by PinkFloyd102489 on 2008-03-11
I adapted the figlet command into the print command.


Thanks for this guide, fun to play with. :-)

---

### Post by Lunks on 2008-03-11
Didn't like much the figlet stuff, but it enlightened me on the possibilities I can do when starting a terminal.
Going for a textfile reading random frases. :)

---

### Post by Dr.Ninethousand on 2008-03-11
is it possible to set colors in the greeting?   :)

---

### Post by Chokkan on 2008-03-12
Yeah, that is pretty cool :)

---

### Post by fedex1993 on 2008-03-12
i think you might be able to hold on i am going to see if i can get the colors setup and what not

---

### Post by markp1989 on 2008-03-14
very nice thanks

---

### Post by Darkagentx on 2008-03-14
Now this I like; thanks :D

---

### Post by ChaoticVengeance on 2008-03-16
Very nice.  I love doing little things like this; you get to customize your system and learn more about how it works at the same time.

---

### Post by zxscooby on 2008-03-16
thats pretty slick! thanks

---

### Post by fedex1993 on 2008-03-17
welcome

---

### Post by blacksm1th on 2008-03-17
Thanks for the tip. Here is my terminal:
[[IMG]http://img220.imageshack.us/img220/9122/screenshotterminalroothyb8.th.png[/IMG]](http://img220.imageshack.us/my.php?image=screenshotterminalroothyb8.png)

```
brown='\e[0;33m'
nc='\e[0m' 
echo -e ${brown}; figlet -f speed.flf ubuntu; echo -e  ${nc}
```
:guitar:

---

### Post by elianthony on 2008-03-17
I agree, this is pretty cool.

Thanks Fedex

---

### Post by fedex1993 on 2008-03-17
yeah i got it working with each diffrent letter is a different color :)

---

### Post by Dr.Ninethousand on 2008-03-17
> **blacksm1th said:**
> Thanks for the tip. Here is my terminal:
[[IMG]http://img220.imageshack.us/img220/9122/screenshotterminalroothyb8.th.png[/IMG]](http://img220.imageshack.us/my.php?image=screenshotterminalroothyb8.png)

```
brown='\e[0;33m'
nc='\e[0m' 
echo -e ${brown}; figlet -f speed.flf ubuntu; echo -e  ${nc}
```
:guitar:

nice..  too bad I don't really understand any of that code..  :p

---

### Post by blacksm1th on 2008-03-17
> **Dr.Ninethousand said:**
> nice..  too bad I don't really understand any of that code..  :p
The first two lines define "human" names of colors - here is the others:
```
BLACK='\e[0;30m'
BLUE='\e[0;34m'
GREEN='\e[0;32m'
CYAN='\e[0;36m'
RED='\e[0;31m'
PURPLE='\e[0;35m'
BROWN='\e[0;33m'
LIGHTGRAY='\e[0;37m'
DARKGRAY='\e[1;30m'
LIGHTBLUE='\e[1;34m'
LIGHTGREEN='\e[1;32m'
LIGHTCYAN='\e[1;36m'
LIGHTRED='\e[1;31m'
LIGHTPURPLE='\e[1;35m'
YELLOW='\e[1;33m'
WHITE='\e[1;37m'
NC='\e[0m'              # No Color
```

This "echo -e ${brown}" make all following text brown
This "figlet -f speed.flf ubuntu" define font "speed.flf" and text "ubuntu"
This "echo -e  ${nc}" reset color to terminal default (in my case green)

Fonts are here: [_FONTS_](http://www.figlet.org/fontdb.cgi) - copy *.flf in /usr/share/figlet

---

### Post by Dr.Ninethousand on 2008-03-18
thanks!  makes sense now..

---

### Post by fooman on 2008-03-18
haha ...another cool tip!  :)

thanks to fedex1993 for this post and to blacksm1th for the explanation of the code.

:guitar:

---

### Post by Marcial Contreras on 2008-08-10
I like this, I think

|_ _| |_ ___    ___ ___   ___ | |
 | || __/ __|  / __/ _ \ / _ \| |
 | || |_\__ \ | (_| (_) | (_) | |
|___|\__|___/  \___\___/ \___/|_|

---

### Post by blacksm1th on 2009-04-30
Just to share some information about figlet: if you want to format output of another command with figlet fonts:
```
$ whoami | figlet

```

My new terminal:
[[IMG]http://img237.imageshack.us/img237/7968/screenshotbrr.th.png[/IMG]](http://img237.imageshack.us/my.php?image=screenshotbrr.png)

```
brown='\e[0;33m'
nc='\e[0m'
echo -e ${brown}; cat /etc/lsb-release | grep CODENAME | cut -d"=" -f2 | figlet -t -c -d  /home/azot/.fonts -f isometric3.flf ; echo -e  ${nc}
```

---

