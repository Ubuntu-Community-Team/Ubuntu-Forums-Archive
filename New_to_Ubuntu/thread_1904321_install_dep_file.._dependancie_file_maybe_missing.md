---
title: "install dep file?.. dependancie file maybe missing?"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by bilblueyes@hotmail.com on 2012-01-04
Please help.

.deb file wont install

used x-terminal and followed instructions which work but as far as Im aware I need to have a dependance file aswell to install it.

my question is- is there away to install it with out this file or how do i get the file? 

Would really help me out if there is anyone that can! :)

---

### Post by KdotJ on 2012-01-04
What file are you trying to install?

---

### Post by audiomick on 2012-01-04
As far as I know, a right click on a .deb file should offer you the option of installing. For it to pull in it's dependancies, you need to have an active internet connection. I don't think you can install something without the dependancies, and there would not be much point, because it probably wouldn't work.

What might trip you up is if the .deb you want to install is dependant on an older version of some package that is installed on your system, but newer than the one the .deb is looking for. I believe I actually saw something recently that described a way around that, but I have no idea where it was.

To find out if this might be the case, observe which package the error message is complaining about, then go into the software centre, search for the package and look at "further information" to see which version is installed.

---

### Post by bilblueyes@hotmail.com on 2012-01-04
thank you for replying so quick.

right... I should have mentioned its on a nokia n900 so I dont have a right click button.

Im trying to install games that i have found on btjunkie.

is there a place to download apps, like angry bird and the other popular ones... Im not just looking for games tho.

thanks guys... you know your stuff!!

---

### Post by KdotJ on 2012-01-04
Ok I'm a little confused, you have installed Ubuntu on your Nokia n900? Ubuntu (and mostly linux in general) is not a case of downloading apps from the internet and installing them. As far as I am aware games like Angry Birds and such do not exist on Ubuntu...

---

### Post by audiomick on 2012-01-04
> **bilblueyes@hotmail.com said:**
>  its on a nokia n900 so I dont have a right click button.
So what is the operating system that is on it? I didn't know that Ubuntu would run on one of them.

Which OS it is will make a difference to how you get programs. Ubuntu has the software centre (or synaptic). Other Linux variants have other things.

---

### Post by Seq on 2012-01-04
> **audiomick said:**
> So what is the operating system that is on it? I didn't know that Ubuntu would run on one of them.

Which OS it is will make a difference to how you get programs. Ubuntu has the software centre (or synaptic). Other Linux variants have other things.

The n900 is essentially debian-based (at least my n810 was, and I don't think maemo/meego changed that part of the stack in between).

The easiest thing to do to solve your .deb issue is to get your package via a repository. If I recall (I've been out of this world for a while. I switched to palm. I can pick platforms, can't I?) Most software listed repositories that could be added, then installed via a package browser or apt.

If the only distribution method for it is via .deb download, then dpkg should list the package dependancies. You'll have to either use apt-get to install them if they are in a repository you do already have, or manually track them down and add them in the proper order.

---

