---
title: "Newbie needing codes for compiz and etc."
date: 2008-08-01
forum: New to Ubuntu
---

### Post by jooking on 2008-08-01
im a newbie, so i dont know anything about the codes that are needed to use linux. can anyone tell me some of the standard codes that are needed to use linux well and also to get all the cool effects that ubuntu has. any help with codes would be helpful. thanks. also, how do u access the thing to type all the codes in?

---

### Post by overdrank on 2008-08-01
> **jooking said:**
> im a newbie, so i dont know anything about the codes that are needed to use linux. can anyone tell me some of the standard codes that are needed to use linux well and also to get all the cool effects that ubuntu has. any help with codes would be helpful. thanks. also, how do u access the thing to type all the codes in?

Hi and welcome, these links may help
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
For the desktop effects (compiz)  look at the FAQ's link in my signature.

---

### Post by Paqman on 2008-08-01
> **jooking said:**
> can anyone tell me some of the standard codes that are needed to use linux well and also to get all the cool effects that ubuntu has.

You shouldn't need to use the terminal to get desktop effects. Go to System > Admin > Hardware Drivers and make sure your graphics card has it's drivers installed. Then you can go to System > Preferences > Appearance > Visual Effects and pick the level of effects you want. If you want to really go to town install compizconfig settings manager and you'll be able to tweak every little effect.

---

### Post by daberger on 2008-08-01
elaborating on paqman you can install the compizconfig manager with sudo apt-get install compizconfig  in the terminal. or some code like that i forget the whole thing just try that one or maybe sudo apt-get install compizconf. you get the picture

if you cant figure it out check out one of oooooooold posts about desktop effects when i was having teh same questions

---

### Post by bryncoles on 2008-08-01
if you want help using the terminal, heres a barrage of information that should somewhere contain something useful:

[http://www.scottklarr.com/topic/115/linux-unix-cheat-sheets---the-ultimate-collection/](http://www.scottklarr.com/topic/115/linux-unix-cheat-sheets---the-ultimate-collection/)
[http://ubuntuforums.org/showthread.php?p=990636](http://ubuntuforums.org/showthread.php?p=990636)
[http://linuxcommand.org/index.php](http://linuxcommand.org/index.php)
[http://www.futuredesktop.com/getting-help.html](http://www.futuredesktop.com/getting-help.html)
[http://cb.vu/unixtoolbox.xhtml](http://cb.vu/unixtoolbox.xhtml)

you can also type a few letters into the terminal and press tab twice, then it'll show you all possible completions for that letter combo - all the possible things you could type...

remember, some command line things can be very dangerous to your system (but most arent). make sure you know what you're typing into the terminal before typing it. you can always type 'man COMMAND' to get an unintelligible geek-speak computer-syntax account of what a command does. or google it. or post it in the forum with a 'whats this gonna do?' question. 

if you want to set up compiz, then try this for size:

[http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074)

there we are: something for everyone!;-)

---

### Post by Paqman on 2008-08-01
> **daberger said:**
> elaborating on paqman you can install the compizconfig manager with sudo apt-get install compizconfig  in the terminal. or some code like that i forget the whole thing just try that one or maybe sudo apt-get install compizconf. you get the picture


Or just hit Applications > Add/Remove and search for "compiz". It'll be in there called Advanced Desktop Effects Settings.

There's also a good [Compiz FAQ](http://ubuntuforums.org/showthread.php?t=809695) in the Desktop Effects section of this forum.

---

### Post by jooking on 2008-08-01
hey thanks for the help guys, but i need to install it first lol, im trying to install it with wubi and the ubuntu iso offline, but its not working, i downloaded the desktop iso, but there are all these things in the folder. i put the stuff and the wubi in a folder together and i turned off the internet to install, but it wont work. i might have dled the wrong things. any help?

---

### Post by Paqman on 2008-08-01
> **jooking said:**
> hey thanks for the help guys, but i need to install it first lol, im trying to install it with wubi and the ubuntu iso offline, but its not working, i downloaded the desktop iso, but there are all these things in the folder. i put the stuff and the wubi in a folder together and i turned off the internet to install, but it wont work. i might have dled the wrong things. any help?

Sounds like you've unzipped the .ISO, which you don't want to do. Just put it in with wubi as a .iso file.

The other way to do it would be burn the .ISO to a disk (as an image, not data) and pop it in the drive while in Windows. It'll autorun a menu from which you can kick off the Wubi process.

---

### Post by daberger on 2008-08-01
did u get the alternate ISO?

---

### Post by jooking on 2008-08-01
when i dled it, it came as a winzip and its not an iso file, im dont want to burn into a cd and do i need the alternate file? thanks for the help.

---

### Post by Paqman on 2008-08-01
> **jooking said:**
> when i dled it, it came as a winzip and its not an iso file, im dont want to burn into a cd and do i need the alternate file? thanks for the help.

That's weird, where did you download it from? 

Try downloading it from the [Ubuntu download page](http://www.ubuntu.com/getubuntu/download), you'll definitely get the right image. It comes as a .ISO

---

### Post by jooking on 2008-08-01
thanks guys everything has worked now so far, and now i have to customize it and stuff. thanks for all the help

---

### Post by daberger on 2008-08-02
enjoy ubuntu

---

