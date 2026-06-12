---
title: "Install VLC media player theme?"
date: 2013-11-20
forum: New to Ubuntu
---

### Post by Niemil on 2013-11-20
I wanna install a nice VLC theme!
This one: [http://gnome-look.org/content/show.php/VLT+DeepDark?content=154884](http://gnome-look.org/content/show.php/VLT+DeepDark?content=154884)

I first had problem with extracting the .vlt file. When I googled and found out this thread that explains it: [https://forum.videolan.org/viewtopic.php?f=13&t=89582](https://forum.videolan.org/viewtopic.php?f=13&t=89582)

In short: I need to just drag this .vlt file to **usr/share/vlc/skins2**
Problem is, that when I drag the .vlt file from my download folder to this skins2 folder, it just wont stick! It wont transfer over this file to the skins2 folder, meaning I can't install this theme.

I guess I have to go root somehow? or do some magic via terminal which I don't even understand :/
Anybody got solution?

---

### Post by Niemil on 2013-11-20
This is so weird, I searched on google how to do this.
This is what I did:

[B]sudo cp -a /home/downloads/154884-vlt_deepdark.vlt . /usr/share/vlc/skins2/

[/B]So it said that the file "154884-vlt_deepdark.vlt" doesn't exist, when it does! Instead it copied the whole downloads folder there, and somehow I got intense lag after that.

[edit]
I changed so it looks like this, but still not working.
[B]user@UB:~$ sudo cp -a home/downloads/154884-vlt_deepdark.vlt . usr/share/vlc/skins2
[sudo] password for user: 
cp: target &#8216;usr/share/vlc/skins2&#8217; is not a directory[/B]

[edit #2]
Getting angry, just a tweak change, makes huge difference!?!?!?!?!?!?!?!?!?!
**user@UB:~$ sudo cp -a home/downloads/154884-vlt_deepdark.vlt . /usr/share/vlc/skins2/**
**[sudo] password for user: **
**cp: cannot stat &#8216;home/downloads/154884-vlt_deepdark.vlt&#8217;: No such file or directory**

---

### Post by Niemil on 2013-11-20
[edit]

[B]sudo cp -a /home/user/Downloads/154884-vlt_deepdark.vlt . /usr/share/vlc/skins2/

it just lagging still, why? isn't this correct!?!?[/B]

---

### Post by Niemil on 2013-11-20
Whatever, somehow it worked even though my computer were lagging of this failing attempts, I started VLC now and the skin seems to be there now. No idea how I did though. had to restart computer like 5 times because of terminal lagging

---

### Post by simbauad on 2013-11-21
Welcome to linux. As is evident from your posts you seem not to be accustomed to the command line(Don't get me wrong). Your commands are actually wrong.
The command should be:
[CODE]**sudo cp -a /home/user/Downloads/154884-vlt_deepdark.vlt /usr/share/vlc/skins2/[\CODE]**where user should be replaced by your username. Your username can be known by just opening the terminal. There should be something like niemil@home. Replace user with the text before @.Supposing your username is niemil.
The command would then be
[CODE][B][B]sudo cp -a /home/niemil/Downloads/154884-vlt_deepdark.vlt /usr/share/vlc/skins2/[\CODE]
[/B][/B]To avoid the command line here's another solution. Run
[CODE]sudo apt-get install gksu[\CODE]
Then type
[CODE]gksu nautilus[\CODE]
Type in your password and then you will be able to drag and drop in the directory.
The problem is that linux doesn't allow a normal user to modify any files other than those in home. This can be considered similar to the prompt you get when you try to install a program in windows. However linux ensures additional security by having you to type your password. Hope, I could be clear.

---

