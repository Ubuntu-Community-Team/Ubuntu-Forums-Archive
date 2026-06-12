---
title: "gnome 3.4 didn't work with me :("
date: 2012-09-02
forum: New to Ubuntu
---

### Post by amrosama77 on 2012-09-02
Hello, 
I am on new installation for ubuntu 12, I try a lot to have gnome 3.4 but nothing work with me ,can any one help me but please forget about default solution such as the below links as I try all of it but no use

[http://www.filiwiese.com/installing-gnome-on-ubuntu-12-04-precise-pangolin/](http://www.filiwiese.com/installing-gnome-on-ubuntu-12-04-precise-pangolin/)
[http://www.noobslab.com/2012/04/install-gnome-shell-34-and-extensions.html](http://www.noobslab.com/2012/04/install-gnome-shell-34-and-extensions.html)
[http://www.gnome.org/getting-gnome/](http://www.gnome.org/getting-gnome/)

---

### Post by anewguy on 2012-09-02
What doesn't work?  Which piece/pieces?  Detail on what you are trying that isn't working is needed.

---

### Post by Frogs Hair on 2012-09-02
Why use a PPA ? Gnome 3.4 is the default in the software center on 12.04 . What do you mean by forget about the default solution ?

---

### Post by amrosama77 on 2012-09-02
All what I want is to have this gnome >> [http://www.gnome.org/gnome-3/](http://www.gnome.org/gnome-3/)

beside my default unity desktop

I used PPA as I didn't know in the beginning that it is there in the software center and maybe this is the problem ,not sure

details, after my try to have gnome 3.4 on my ubuntu I only have the login screen with gnome options but not the real desktop (check the attached screen shot) 

this is what I get when I login to gnome option !!!!

Please advice,

---

### Post by ZoiaGuyver on 2012-09-02
That looks like gnomes fallback session (does that when Shell can't load). I would hazard a guess that something is wrong with the graphics driver being used. 

If you have shell it should have 3 options on the login screen when you click the little "ubuntu" logo on the top right of where you sign in. 

> Gnome
Gnome Classic
Gnome Classic (no effects)

Do you get a black screen with a little unhappy computer face up when you log in on the normal "Gnome" session?

---

### Post by amrosama77 on 2012-09-02
for my login menu I have,

gnome (with ubuntu icon)
gnome classic (gnome icon)
gnome no effect (gnome icon)
recovery console
unity 
unity 2D
user defined session

and for the drivers please check the attached file,

---

### Post by amrosama77 on 2012-09-02
>>Do you get a black screen with a little unhappy computer face up when you log in on the normal "Gnome" session?

NO

---

### Post by Frogs Hair on 2012-09-02
Here is a PPA purge if you did install with the Linked PPA.```
sudo apt-get install ppa-purge
``````
sudo ppa-purge ppa:ricotz/testing 
``````
sudo ppa-purge ppa:gnome3-team/gnome3
```

---

### Post by amrosama77 on 2012-09-02
Hello Frogs Hair,
I did all what you said, then installed the gnome from the software center 

but nothing ,same situation :(

---

### Post by amrosama77 on 2012-09-03
Please, any one help me :mad:

---

### Post by nyamina on 2012-09-03
> **amrosama77 said:**
> Please, any one help me :mad:
Try pasting ```
gnome-shell --replace
``` into a terminal and then open another terminal (ctrl+alt+t) and paste ```
mutter --replace
``` and see what happens.

---

### Post by amrosama77 on 2012-09-03
Thank you,

SO I think you mean to do this after login to gnome ...?

after 1st order ,the gnome just come !!! but with all this errors (check 1.png file)

after 2nd order ,unity back :( with the this (check 2.png)

what about installing ubuntu gnome remix ?

any way 
check the attached screen shots
and tell me what do you think

---

### Post by nyamina on 2012-09-03
> **amrosama77 said:**
> Thank you,
I'm sorry it didn't work, if it had worked as planned it would have started Gnome 3.4 working perfectly. It has for me in the past, and I don't know why it hasn't for you. The error message on the terminal is certainly on I haven't seen before. I do notice, however, that you're running it in Virtualbox, which may be the culprit. That could be the reason why it won't running Gnome, Virtualbox sometimes has a problem with 3D graphics.

(on a side note, you can make Chrome fit in with Ubuntu a lot better by going to settings, appearance, and ticking "use system titlebar and borders," :) )

---

### Post by anewguy on 2012-09-03
Actually, given your bad-gnome.jpg image, I think you DO have gnome-3 working at the point.  It looks like the gnome desktop (the "System" option didn't show on the top bar when I tried this either).

Perhaps you could explain more what you are expecting to see.

If what you expect is in the one link you pointed to, I would suggest you try the gnome-shell package from the repositories (it is in synaptic package manager, and I would think in the software center).  What shows in that link looks more like gnome-shell to me (don't confuse this with the gnome shell - gnome-shell is a desktop manager package you have to install).

---

### Post by 73ckn797 on 2012-09-03
Did you try Gnome Classic (with no effects), or, Unity 2D?

---

### Post by PhilGil on 2012-09-04
Something here isn't computing. Your screenshot in post #6 shows the graphics drivers installed on your host Ubuntu system. The screenshots in post #12 show Ubuntu running in Virtualbox.

If you are trying to run Gnome Shell in Virtualbox, you'll need to do the following:

1) Be sure that you have 3D acceleration enabled for the Ubuntu virtual machine (Display-->Video--Enable 3D Acceleration). Also, set the video memory to the largest amount available (in my version of Virtualbox it's 128MB)

2) Install guest additions in the Ubuntu virtual machine.

---

### Post by amrosama77 on 2012-09-04
OkAY,

I will try post #11 in my real system, so should I run those orders after I log to gnome? or gnome classic ? or unity ?

no I didn't test in gnome classic.

Thank you for the chrome advice :)

no one advice me about ubuntu gnome remix ?

---

### Post by newb85 on 2012-09-04
> **amrosama77 said:**
> for my login menu I have,
gnome (with ubuntu icon)


That's odd.

Please give the output of 

```
ls /usr/share/xsessions
```

---

### Post by amrosama77 on 2012-09-04
amr@amr-HP-Pavilion-g6-Notebook-PC:~$ ls /usr/share/xsessions
gnome-classic.desktop   gnome-shell.desktop  xsession.desktop
gnome.desktop           ubuntu-2d.desktop    xterm.desktop
gnome-fallback.desktop  ubuntu.desktop
amr@amr-HP-Pavilion-g6-Notebook-PC:~$

---

### Post by amrosama77 on 2012-09-04
I tested the following order in my real system 
 >>> gnome-shell --replace

and here is the result (please check attached file)

---

### Post by amrosama77 on 2012-09-04
Is it good to follow the following instructions:
>>Instructions for adding the PPA and installation of the package:
$ sudo apt-get install python-software-properties # for apt-add-repository
$ sudo apt-add-repository ppa:jan-hoffmann/gnome-shell
$ sudo apt-get update
$ sudo apt-get install gnomeshell-desktop
After you have verified your new desktop interface is working (reboot)

and if it a good idea then where to write them ,while I am in my ubuntu unity or gnome or what ??

---

### Post by newb85 on 2012-09-04
> **amrosama77 said:**
> Is it good to follow the following instructions:
>>Instructions for adding the PPA and installation of the package:
$ sudo apt-get install python-software-properties # for apt-add-repository
$ sudo apt-add-repository ppa:jan-hoffmann/gnome-shell
$ sudo apt-get update
$ sudo apt-get install gnomeshell-desktop
After you have verified your new desktop interface is working (reboot)

and if it a good idea then where to write them ,while I am in my ubuntu unity or gnome or what ??

I have no idea where you found those instructions, but regardless, they're not good instructions.

The first line says it's to allow you to use add-apt-repository.  In Ubuntu 12.04, you already have that ability by default, so that first line is pointless.
The second line adds Jan Hoffmann's PPA for "Metapackages for Installing Gnome Shell".  Once again, in 12.04, equivalent metapackages are already available in the repositories, so this step is also pointless.
Consequently, the third step is unnecessary.
In the 12.04 repos, the metapackage is not titled gnomeshell-desktop, but rather gnome.

You've now listed four sets of outdated instructions for installing the Gnome DE, but you haven't told us which one(s) you followed.  To get this to work, you're going to need to reverse what you've done and then do a very clean and simple install from the repos.  I would be happy to provide you with verbatim commands to achieve this, but I need to know what you've done so far.

Which PPA(s) have you added?
What metapackage(s) have you added?

---

### Post by newb85 on 2012-09-04
> **newb85 said:**
> Which PPA(s) have you added?
What metapackage(s) have you added?

If you don't know the answers, you can easily find them through the software center.  
At the top, click on "Installed."  Click on the arrow to the right of "Installed", and after the first four entries will be the PPA's you've added.  By clicking on them, you can see what you've installed from them.

---

### Post by amrosama77 on 2012-09-04
Okay,

1. GNOME 3 WebUpd8 PPA 
nothing in this one

2. Gnome 3 - Noobslab
GNOME SHELL IM MESSAGE NOTIFIER

---

### Post by anewguy on 2012-09-04
Reverse what what ever you did to install the gnome-shell package, then use the package manager to install it straight from the ubuntu repositories.  I never had to do any of the things in that old, old set of instructions you posted.  Simply go to the package manager and install it.  It may be in the software center, but personally I prefer using Synaptic Package Manager.  It (Synaptic) is not installed by default in the last couple of releases, but you can install it from the software center.  Then use it to install the gnome-shell package.  It may come up with a list of requisites it wants to install as well - let it do so.

I've done some work with gnome-shell and always installed it via the package manager.  Instead of the --replace you did at the command line to "start" gnome-shell, just select it at the logon screen.  It will look like the image in the link you posted.  Always remember, it's "gnome-shell", not "gnome shell".  If you put the wrong thing in the search box in the package manager you won't install gnome-shell.  It's the desktop manager that looks like that in your link.

---

### Post by newb85 on 2012-09-05
> **amrosama77 said:**
> Okay,

1. GNOME 3 WebUpd8 PPA 
nothing in this one

2. Gnome 3 - Noobslab
GNOME SHELL IM MESSAGE NOTIFIER

I'm surprised those were the only ones, but okay, if there weren't any others...

Some of these might not be installed, but go ahead and run the remove command for them, anyways.

```
$ sudo apt-get remove -y gnome-shell-extensions shell-extensions3.4 gnome-shell-system-monitor gnome-shell-message-notifier gnome-shell-extensions-weather
$ sudo apt-get autoremove
$ sudo add-apt-repository -ry ppa:noobslab/gnome
```

This should undo what you've done.
Now,

```
$ sudo apt-get install gnome
```

During the install, it will probably ask you which login manager you want to use.  Choose LightDM.

Once installation is finished, log out and log back in, selecting Gnome as the DE.

---

### Post by amrosama77 on 2012-09-05
I did all the orders (please check the attached file)

then log-out -> log-in in gnome

but nothing changed :(

---

### Post by amrosama77 on 2012-09-05
My installed drop down list have more than what I provide ,but I provide only what is related to gnome >> here is the full list after first 4 

Boot-repair
GNOME 3 WebUpd8 PPA
Jupiter
skype-wrapper
unknown

---

### Post by newb85 on 2012-09-05
> **amrosama77 said:**
> I did all the orders (please check the attached file)

then log-out -> log-in in gnome

but nothing changed :(

Please open the Software Center, search for "gnome", and confirm that "The GNOME Desktop Environment, with extra components" is installed.

---

### Post by amrosama77 on 2012-09-06
Please check the attached file

---

### Post by newb85 on 2012-09-06
I know that you've done it before, but again, please give the output of

```
$ ls /usr/share/xsessions
```

---

### Post by Epodx64 on 2012-09-07
Just a thought but maybe give KDE a try I've been using it for years and KDE SC 4.9 is great

sudo apt-get install kubuntu-desktop

p.s.
just a suggestion I personally don't care for Gnome 3.x but then again I didn't really use Gnome 2.x either oh yeah and another Desktop environment that is excellent that uses Gnome 3.x is Cinnamon maybe give that one a try.

---

### Post by amrosama77 on 2012-09-07
amr@amr-HP-Pavilion-g6-Notebook-PC:~$ ls /usr/share/xsessions
gnome-classic.desktop   gnome-shell.desktop  xsession.desktop
gnome.desktop           ubuntu-2d.desktop    xterm.desktop
gnome-fallback.desktop  ubuntu.desktop
amr@amr-HP-Pavilion-g6-Notebook-PC:~$ 

Thank you EPOD
but I so kde before and didn't like it ,I really see gnome 3.4 as the only think which may let me drop win7 and go for it

---

### Post by amrosama77 on 2012-09-07
OOooops, I think I discovered where is the problem

it's my ATI graphics card :(

here is what happends today, I install a new free copy of ubuntu 12 then from the software I installed the gnome-shell,

so it works very well, but when I installed my ATI driver I went back to the original screen shoot :( bad gnome

I think this is the END

---

