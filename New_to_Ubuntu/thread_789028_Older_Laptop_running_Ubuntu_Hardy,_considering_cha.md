---
title: "Older Laptop running Ubuntu Hardy, considering change to Xubuntu Hardy"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by swarup on 2008-05-10
I'm running a 1999 Gateway 9300 with celeron 433 mhz chip, RAM 288 MB [at 100 mhz], 20 GB HD. Been using it for a year with Feisty and now Hardy Ubuntu. It basically runs fine, just a little slow. Things like opening OOo, and using OO Base, are a bit slow. I've been reading about Xubuntu now, that: 
> 
Xubuntu uses the Xfce desktop environment, meaning that it will run fast while still delivering a user-friendly interface. Older computers feel lively again, while newer ones will run faster than ever before! 

So I'm considering a possible move to Xubuntu for reasons of speed. 

But there are certain features that I require:

1. Will my Netgear wg111v2 wireless adapter install the same way as it does in Ubuntu, using ndiswrapper with the Win98 driver.

2. Database. I need a database utility, and it doesn't seem that Xubuntu uses OOo. Is there a DB utility? Actually, I like Kexi (The KDE DB utility) very much. If that will install in Xubuntu, then I'll be all set here.

3. SCIM. I use SCIM for typing in Hindi. Specifically, I use the m17n protocol inside SCIM for my particular Hindi phonetic keyboard configuration. Will this work in Xubuntu.

4. What is the email application. Does it use the same Evolution?

---

### Post by ugm6hr on 2008-05-10
1. Xubuntu uses Network Manager (just like Ubuntu) - so should be the same.
2. You can install OO Base or Kexi in Xubuntu.
3. Don't know I'm afraid.
4. Thunderbird - I prefer it to Evolution - but you can install Evolution if you want.

---

### Post by fluteflute on 2008-05-10
If you install the 'xubuntu-desktop' package (through synaptic or apt-get or aptitude) then you will have Xubuntu effectively added to the current install so you can easily switch back.

Then before you log in, look for a 'Session' option under 'Settings' and change it to 'XFCE'. If you want to change back choose 'Gnome'.

---

### Post by barbedsaber on 2008-05-10
> **fluteflute said:**
> If you install the 'xubuntu-desktop' package (through synaptic or apt-get or aptitude) then you will have Xubuntu effectively added to the current install so you can easily switch back.

Then before you log in, look for a 'Session' option under 'Settings' and change it to 'XFCE'. If you want to change back choose 'Gnome'.

beat me to it, by 7 minutes, damn.

---

### Post by kwacka on 2008-05-10
installing Xubuntu on top of Ubuntu doesn't change what's already there.

So, as has been said, use synaptic and search for xubuntu-desktop or just "sudo apt-get install xubuntu-desktop".

OpenOffice will still be there, as will all the other applications you are currently using.

---

### Post by swarup on 2008-05-10
That's great news, that one can install Xubuntu on top of Ubuntu. :)

Two questions about this:

If I do this install of Xubuntu on top of a preexisting Ubuntu, then by so doing will I get to see what the true speed of Xubuntu is like? Or will Xubuntu be slowed down by the fact that it is installed on top of Ubuntu?

Is there any difference (in Xubuntu's general functionality) between doing a fresh install of Xubuntu alone, versus installing Xubuntu on top of Ubuntu?

---

### Post by ugm6hr on 2008-05-10
Xubuntu actually uses a lot of Gnome dependencies, but not all.

You could get to a "pure" Xubuntu with this: [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

Not sure how much difference that will make though.

---

### Post by swarup on 2008-05-10
So in your view is the basic sense then, that I would get a pretty realistic taste of how speedily Xubuntu can work on my computer if I install it on top of Ubuntu?

---

### Post by ugm6hr on 2008-05-10
> **swarup said:**
> So in your view is the basic sense then, that I would get a pretty realistic taste of how speedily Xubuntu can work on my computer if I install it on top of Ubuntu?

In essence yes.

It might be worth seeing what the running tasks are when you boot into XFCE though - just to make sure you don't have multiple gnome processes running in the background.

And then you *could* turn it into a genuine Xubuntu (by removing all trace of gnome) with the advice on psychocats to see how much more difference it makes.

---

### Post by swarup on 2008-05-10
Many thanks to you for all the useful info. And thanks to the others also who have written on this thread. ...All incredibly useful. I'll try installing Xubuntu on top of Ubuntu for starters, and see how it goes. :)

---

### Post by Cifra on 2008-05-10
Yeah, liek teh other people said, try installing XFce on top of your current setup, less hassle.

You can also take a look at another desktop enviroment, such as Enlightenment 17 or just a WM, like Fluxbox :)

Type in 'sudo synaptic' and you'll have all of the apps you ever need. It's not just XFCE yo usee, but also teh apps which are a bit lighter, so search for alternatives which consume less resources such as Abiword instead of Ooo Writer, Gnumeric instead of Spreadsheet, XMMS instead of Rhythmbox, VLC for videos, etc.

Good luck ;)

---

### Post by swarup on 2008-05-10
> **Cifra said:**
> Yeah, liek teh other people said, try installing XFce on top of your current setup, less hassle.

You can also take a look at another desktop enviroment, such as Enlightenment 17 or just a WM, like Fluxbox :)

Type in 'sudo synaptic' and you'll have all of the apps you ever need. It's not just XFCE yo usee, but also teh apps which are a bit lighter, so search for alternatives which consume less resources such as Abiword instead of Ooo Writer, Gnumeric instead of Spreadsheet, XMMS instead of Rhythmbox, VLC for videos, etc.

I see, yes thank you. I'll certainly try Abiword for my word processing. Now, do you happen to know whether Abiword works together with SCIM, the input method for inputting non-English characters like Serbian, Croatian, and Armenian? That will be one critical point for me. I need to be able to work in SCIM, which is what I use to type Hindi in.

Is it the case that all the applications I have installed in Gnome Ubuntu, will automatically appear on the SFCE desktop of Xubuntu when I install it on top? Or do I select which ones I want to bring over from Gnome? Or do I have to reinstall everything afresh? (As I understood from previous posters, this last would not be the case.)

---

### Post by swarup on 2008-05-10
> **fluteflute said:**
> If you install the 'xubuntu-desktop' package (through synaptic or apt-get or aptitude) then you will have Xubuntu effectively added to the current install so you can easily switch back.

Then before you log in, look for a 'Session' option under 'Settings' and change it to 'XFCE'. If you want to change back choose 'Gnome'.

Three questions:

1. I just want to confirm that I correctly understand the above. It means that every time I boot up the computer, at the login screen there will be a 'Session' option under 'Settings', via which I can opt at any given bootup, to go into XFCE or Gnome. So both desktops will exist in parallel, giving me full option to go into either one.

2. If I install Xubuntu on top of Ubuntu using Synaptic Package Manager, and if I decide later that I want to uninstall Xubuntu, then is it as simple as booting up into Gnome (Ubuntu), opening Synaptic, and marking the "Xubuntu-desktop" package for uninstall.

3. If after installing Xubuntu-desktop on top of Ubuntu Hardy I then decide that I prefer Xubuntu (XFCE) over Gnome (Ubuntu), I have been given the following link [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce), for a way to remove Gnome and be left with pure XFCE. But after looking at the link, I am a bit confused. It looks to me like the link is designed for someone who started out with XFCE, then added Gnome on top of it, and then wants to remove Gnome and be left with their pure XFCE. But does this link also work for someone who started with Gnome, later added XFCE, and then ultimately decides to remove Gnome and be left with XFCE?

---

### Post by ugm6hr on 2008-05-10
In response:

1. Yes.

2. No. If you use aptitude to install xubuntu-desktop, then you can use a single command to remove it.  If you use apt-get or Synaptic, you will have to remove all the Xubuntu components individually (psychocats has a link for Pure Gnome).

3. > But does this link also work for someone who started with Gnome, later added XFCE, and then ultimately decides to remove Gnome and be left with XFCE?
Yes.

---

### Post by inportb on 2008-05-10
> **Cifra said:**
> You can also take a look at another desktop enviroment, such as Enlightenment 17 or just a WM, like Fluxbox :)

Indeed, E17 and Fluxbox are awesome. btw, E17 is a WM, not a DE.

---

### Post by swarup on 2008-05-10
> **ugm6hr said:**
> In response:

1. Yes.

2. No. If you use aptitude to install xubuntu-desktop, then you can use a single command to remove it.  If you use apt-get or Synaptic, you will have to remove all the Xubuntu components individually (psychocats has a link for Pure Gnome).

3. 
Yes.

Great. Perfect. Thank you. Now I'm all tooled up to do this thing properly. I'll give it a go and see how it works. Will use the aptitude command for the install, as per the reference you gave in psychocats.

---

### Post by swarup on 2008-05-10
> **inportb said:**
> Indeed, E17 and Fluxbox are awesome. btw, E17 is a WM, not a DE.

How is that people can do so much playing around with various distros? Isn't it a big hassle to go on installing and uninstalling one distro after another on the computer. After all, setting up anything more than a dual boot is somewhat complex.  --or--are you talking about just running light distros like these from their livecd's?

---

### Post by gn2 on 2008-05-10
> **swarup said:**
> How is that people can do so much playing around with various distros? Isn't it a big hassle to go on installing and uninstalling one distro after another on the computer. 

Not if you have a separate /home partition.

Or are prepared to swap hard drives, which is quite easy on many laptops.

Or boot from an external drive.

There are many options.

---

### Post by swarup on 2008-05-10
> **gn2 said:**
> Not if you have a separate /home partition.

Or are prepared to swap hard drives, which is quite easy on many laptops.

Or boot from an external drive.

There are many options.

I see. Very cool. So I guess in my case the easiest, if I wanted to experiment, would be to boot from an external drive. I could just set the boot sequence so that the computer looks for an external drive first, before the internal one? But will the PCMCIA port (that's where my external HD plugs in) be able to be recognized before the computer boots?

---

### Post by gn2 on 2008-05-11
> **swarup said:**
> But will the PCMCIA port (that's where my external HD plugs in) be able to be recognized before the computer boots?

That depends on your BIOS.

Not all options work on all hardware, I was just answering your question of how others are able to do it easily.

---

### Post by Cifra on 2008-05-11
> **inportb said:**
> Indeed, E17 and Fluxbox are awesome. btw, E17 is a WM, not a DE.

You're 50% right:
```
Enlightenment is a window manager. Enlightenment is a desktop shell. Enlightenment is the building blocks to create beautiful applications. Enlightenment, or simply e, is a group of people trying to make a new generation of software. 
```:)

---

### Post by Cifra on 2008-05-11
> **swarup said:**
> How is that people can do so much playing around with various distros? Isn't it a big hassle to go on installing and uninstalling one distro after another on the computer. After all, setting up anything more than a dual boot is somewhat complex.  --or--are you talking about just running light distros like these from their livecd's?

There is a beauty to the challenege of running a modern OS on say, a 300 Mhz Thinkpad :D

Now that psychocats link is for the advanced user, I believe - you build the system from the ground up with apt. First, you install teh base, then the X graphical server and then your graphical environment of choice.

I don't recommend it, it's really time consuming and you can get into trouble if you're not an advanced user.

---

### Post by fluteflute on 2008-05-11
> **swarup said:**
> How is that people can do so much playing around with various distros? Isn't it a big hassle to go on installing and uninstalling one distro after another on the computer. After all, setting up anything more than a dual boot is somewhat complex.  --or--are you talking about just running light distros like these from their livecd's?
In the same way you can install Xubuntu over a Ubuntu install,you can do the same thing with fluxbox and e17.

Whole distros is more time consuming though. :)

---

### Post by swarup on 2008-05-11
> **fluteflute said:**
> In the same way you can install Xubuntu over a Ubuntu install,you can do the same thing with fluxbox and e17.

Whole distros is more time consuming though. :)

Very, very interesting. 

A couple of questions:

1. It is not told on the psychocats site, how to install fluxbox or e17 on top of Ubuntu. If I download these respective distros from their websites, will their software want to be installed as a completely seperate, whole distro? Or during their install will a window come where it offers to install on top of Ubuntu and be present as an option at the session window at the login screen?

-- Or perhaps I have misunderstood. I see that both these softwares label themselves as "window managers" and a "desktop shell". Does that mean they are not actual linux distributions, but just desktops like Gnome or KDE, which are only made to work as the "front end" or desktop "GUI" for a distribution? Can fluxbox and e17 work independently as distros, or not?

2. If fluxbox and e17 DO work independently as distros, then will I get a real sense of their true speed by installing them on top of Ubuntu?

3. Is interest in fluxbox and e17 mostly or greatest among those with old computers? That is, the inspiration for systems/distros/window managers like fluxbox and e17 is to maxamize speed of a modern OS on an old computer? 

Or are there other attractions to them as well, that make people with modern fast computers also interested in them?

---

### Post by Cifra on 2008-05-11
Let me explain how a distro works:
Take Ubuntu, for instance.
First, there's the Linux Kernel
Then you have your graphical X server (that's X.org)
Then you gave a login manager (GDM, the gnome display manager, that's where you login)
And your desktop environment.

Now, if I were to go to synaptic and install say XFCE, I'd get the same thin gas if I took a completely different distro like Slackware - it's the same software, much like Notepad on Windows and Vista (although on a larger scale).

Each desktop environment has a specialty, be it for old or new computers, let me name some of them
GNOME - simple, customizable
XFCE - very similar GNOME, only much cuter, with its own compositor
KDE 3 - Windows like, VERY customizable, nice
KDE 4 - very cool, sleek, customizable (Plasmoids), wiidgets, Compositing
Enlightenment - sleek desktop, fast, has a Dock (OS X! Take a look at gOS)

... etc

Now what may confuse you is that some of these, such as teh KDEs and XFCE are complete desktop environments - a difference between that is that with KDE for instance you will download additional software from the KDE DE project, such as the Kate text editor, because KDE is giving you an environment, while Enlightenment for instance gives you just a window manager, with which you open/manage windows, launch apps. SO Desktop environments are Window managers + productivity and system management apps and WMs are just window managers.

Whew.

Hope this made things a bit clearer for you.

---

### Post by swarup on 2008-05-12
Thank you, yes. That is helpful information. And I went and read further on the differences between WM's and DE's, and now the distinction is much clearer. So for example, whereas Fluxbox is a WM, in contrast Fluxbuntu is a DE. And I suppose then that although Fluxbuntu is propagated as being very slim and fast, but even then, since it IS a DE and therefore gives some "productivity and system management apps" in addition to its WM, it will therefore take more energy to use than Fluxbox which is the stripped down WM. Right?

---

### Post by Cifra on 2008-05-12
Well, yes and no :D

See, Fluxbuntu is a distribution - Fluxbox would be called a desktop environment if the developers **that developed fluxbox ** made applications like a text editor to work specifically with fluxbox, like gedit for GNOMe, Kwrite for KDE, or Mousepad for XFCE. What the Fluxbuntu project did is they bundled software from other projects to form a "desktop enviroment" which uses Fluxbuntu as a WM.

For instance, GNOME is a desktop environment, but Metacity is the name of the window manager. So in teh default Ubuntu, you use Metacity in the GNOME desktop environment.

So now you use FLuxbox in the Fluxbuntu environment.

That's why my reply is yes and no :)

---

