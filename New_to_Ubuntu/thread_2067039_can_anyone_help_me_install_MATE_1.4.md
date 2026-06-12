---
title: "can anyone help me install MATE 1.4"
date: 2012-10-06
forum: New to Ubuntu
---

### Post by agnisflugen on 2012-10-06
i clung onto 10.10 Maverick for as long as i could, but eventually my  sound went out, flash was all jacked up, and the touchpad on my netbook stopped working, so i had to give into the new 12.4 release, but the thing is i really don't like it,  so i figured out how to change it with the help of this article:

[http://scottlinux.com/2011/03/05/ubuntu-11-04-change-from-unity-to-classic-gnome/](http://scottlinux.com/2011/03/05/ubuntu-11-04-change-from-unity-to-classic-gnome/)

it  gave pretty simple instructions on how to change from Unity to classic  gnome which made me happier, but i still miss the way 10.10 looked.  i did some  more research and heard about MATE 1.4  from here:
 
[http://mate-desktop.org/install/](http://mate-desktop.org/install/)

which explained how to install it here:

[http://wiki.mate-desktop.org/download](http://wiki.mate-desktop.org/download)

but their instructions are  confusing to me. is there anyone by any chance that could put the  installation instructions in layman's terms for me? i apologize in advance for not being very Linux savvy and thank you for your time and consideration in helping me!

---

### Post by critin on 2012-10-06
Get to the terminal by holding Ctrl + Alt + T

Add the repository by copy and pasting this into the terminal.  Your password is needed but will not show.

> sudo add-apt-repository "deb [http://packages.mate-desktop.org/repo/ubuntu](http://packages.mate-desktop.org/repo/ubuntu) precise main"
   Then copy & paste  the following commands to update your repositories and install MATE: 

 > sudo apt-get update sudo apt-get install mate-archive-keyring 
sudo apt-get update 
 sudo apt-get install mate-core 
 sudo apt-get install mate-desktop-environment

---

### Post by agnisflugen on 2012-10-06
oh never mind...i think i found a super easy tutorial here:

[http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-install-the-mate-desktop](http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-install-the-mate-desktop)

i'm gonna try it out so keep your fingers crossed for me! hopefully i don't hit any snags along the way...

---

### Post by agnisflugen on 2012-10-06
thank you so much critin! that sounds like something i could figure out!!!:p

---

### Post by critin on 2012-10-06
I didn't say to press 'enter' after each paste, but you know you have to do that--right?

---

### Post by agnisflugen on 2012-10-06
yeah, i hit paste :) now i'm just waiting on terminal to do it's thing....i hope this works!

---

### Post by agnisflugen on 2012-10-06
okay, just updating to say it worked! i got one weird message along the way about, "the hddtemp program can be run as a daemon, listening on port 7634 for in coming connections......blah blah blah...." i had no idea what they were talking about. the message went onto say, "If in doubt, it is suggested to not start it automatically on boot" so that's what i did, and so far so good :) i like this interface soooo much better. life is good :)

---

### Post by critin on 2012-10-06
Great!  I've not tried Mate yet, maybe I will.

---

