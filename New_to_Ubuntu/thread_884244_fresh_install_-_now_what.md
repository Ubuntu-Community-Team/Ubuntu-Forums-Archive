---
title: "fresh install - now what"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by mgmoore on 2008-08-08
I'm a very basic linux user trying to develop some skills.
So I just installed ubuntu, I've made it to the console and I can log in. Now what right?
I have no idea how to open the gui or to get an ip. Help!

---

### Post by tinny on 2008-08-08
> **mgmoore said:**
> I'm a very basic linux user trying to develop some skills.
So I just installed ubuntu, I've made it to the console and I can log in. Now what right?
I have no idea how to open the gui or to get an ip. Help!

You have no GUI??? Did you install the desktop or server edition?

also here is a link the the official Ubuntu Desktop documentation.

[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by cdtech on 2008-08-08
What did you install? It should go right into the desktop. Try typing "startx" at the terminal and let us know what it says.

Thanks......

---

### Post by mgmoore on 2008-08-08
I'm pretty sure I installed the desktop edition. When I boot up it goes to console login screen. When I log in, I'm at command prompt.
When I type startx it says it's not installed, and i can install by typing
sudo apt-get install xinit
when I type that, I get an E: Couldn't find package xinit

---

### Post by mgmoore on 2008-08-08
Thanks for "https://help.ubuntu.com/" I have been looking at it, but most of what it says assumes I'm in the GUI, not the console.
:)

---

### Post by Witling on 2008-08-08
It would be helpful to know which version of Ubuntu you installed and whether, aside from your Firefox problem, Ubuntu is otherwise working correctly. When you install Ubuntu, Firefox should appear on the -- uh, I don't know the magic Ubuntu words for it but I'd call it a task bar -- at the top of the page. Simply clicking on it should take you somewhere. Assuming that it's working, you can configure it to your liking as you go.

A few questions.

Is there a bar across the top of your screen with entries like "Applications," "Places," "Tools," etc?

Does Firefox appear as an icon on that same bar? Hint: in every Ubuntu installation I've ever seen, the answer would be "Yes."

Assuming that there is a Firefox icon in a bar at the top or your screen, what happens if you do a single click on that Firefox icon?

---

### Post by Witling on 2008-08-08
I'm going to lay in the weeds a while. It looks like your getting plenty of help that's more relevant than I can provide. Just ignore my previous post. No need to answer those questions.

---

### Post by cdtech on 2008-08-08
Did you download from here?
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

First selection:
Ubuntu 8.04 LTS Desktop Edition - Supported to 2011

What type of computer do you have? Standard personal computer or 64bit?

---

### Post by mgmoore on 2008-08-08
Witling - I cant get to the GUI. There is no bar, I'm in the console.
The iso I've used is:
ubuntu-8.04.1-server-i386.iso

So I guess I installed the server. Real smart. Should I start over and reinstall with the desktop edition?

---

### Post by ad_267 on 2008-08-08
Sounds like you actually installed the server edition, not the desktop edition. You could either reinstall with the desktop edition or you can do "sudo apt-get install ubuntu-desktop".

The server edition also comes with other stuff you probably don't need like apache web server and MySQL so if it's not too much hassle it might be easiest to just install with the desktop edition, otherwise you can remove the stuff you don't need later.

---

### Post by rossjman1 on 2008-08-08
To find out what version you're using (and if it's desktop or server) login and post the output of this command.
```
uname -a
```

---

### Post by cdtech on 2008-08-08
> **mgmoore said:**
> Witling - I cant get to the GUI. There is no bar, I'm in the console.
The iso I've used is:
ubuntu-8.04.1-server-i386.iso

So I guess I installed the server. Real smart. Should I start over and reinstall with the desktop edition?

wrong one, just click the link I left above.......

---

### Post by mgmoore on 2008-08-08
I can't do the command: "sudo apt-get install ubuntu-desktop"
It says it can't find package. I'm assuming because it's not connected to internet, and or it's not able to find it on the cd, or hd.

---

### Post by mgmoore on 2008-08-08
Ok, yeah . Step one install the right package. So before I waste any more people's time I'll do that. :)
I'm sure I'll be right back here after that.
Thanks for the help party people.

---

### Post by ad_267 on 2008-08-08
> **mgmoore said:**
> I can't do the command: "sudo apt-get install ubuntu-desktop"
It says it can't find package. I'm assuming because it's not connected to internet, and or it's not able to find it on the cd, or hd.

Oh right, you probably have to edit the /etc/apt/sources.list file to add repositories for the Ubuntu desktop edition first. I say just install the desktop edition. You'll have to download another 700MB but it will be a lot simpler.

---

### Post by Vivaldi Gloria on 2008-08-08
I suggest you install the desktop cd rather than installing the ubuntu-desktop on the server cd. You don't need server programs and the server kernel on a desktop system.

---

