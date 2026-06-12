---
title: "Any have anyone made a Lunux distro?"
date: 2008-12-04
forum: Other OS Talk
---

### Post by gjoellee on 2008-12-04
You see that I am doing the stunt of making a Linux distribution, but there are some things I have trouble with. Theming, is the issue, I have tried many different ways to get the set the theming layout over to the live CD, but I cant figure out how.

Now I am asking for help, does anyone know how to make a "new" desktop, and then make it be like that as default in live cd you make?

---

### Post by basenvironment on 2008-12-04
any files/folder in /etc/skel are transferred to any newly created users home...

Create your 'new' desktop, then transfer all the configuration settings to /etc/skel then any newly created user will inherit those settings.

---

### Post by gjoellee on 2008-12-04
> **basenvironment said:**
> any files/folder in /etc/skel are transferred to any newly created users home...

Create your 'new' desktop, then transfer all the configuration settings to /etc/skel then any newly created user will inherit those settings.

thanks, I will try and see how it becomes...

---

### Post by chris4585 on 2008-12-04
what I do is:

1. Get the base LiveCD done

2. Start the livecd

3. Make the changes you want

4. copy all the file settings within /home/$user/ that you need for your theme and create a zip of those settings, use sshfs or something to transfer the zip from LiveCD to the system you're using to create the LiveCD

5. Unpack the zip within the LiveCD's /etc/skel

6. Create the new LiveCD

7. Run the LiveCD and you should have the same settings on the new LiveCD as you tweaked from the LiveCD before

the easiest way you can do it

---

### Post by cardinals_fan on 2008-12-04
Making an Ubuntu remix can be very fun, but I sure wouldn't call it making a new distro.  Call me when it has its own repositories.

---

### Post by WaeV on 2008-12-04
How do repositories work?  Like if I made a new website [http://www.myOS.com/](http://www.myOS.com/) how would I get custom repos to work?  Is it just a big folder with a bunch of .debs?

---

### Post by cardinals_fan on 2008-12-04
> **WaeV said:**
> How do repositories work?  Like if I made a new website [http://www.myOS.com/](http://www.myOS.com/) how would I get custom repos to work?  Is it just a big folder with a bunch of .debs?
I can't believe I actually clicked that link :D

Anyway, my point is that a distro must be able to stand alone.  If it just piggybacks of the Ubuntu repos, it is not independent.

Repositories are a storage location for files, usually packages to be fetched by the package manager.

---

### Post by gjoellee on 2008-12-05
> **cardinals_fan said:**
> Making an Ubuntu remix can be very fun, but I sure wouldn't call it making a new distro.  Call me when it has its own repositories.

Yes I will start off with an Ubuntu base, using it to learn. My goal is to make something independent, but I have about no experience yet, that is why I am making a Ubuntu base....How do I make repositories, I have a domain so it is just to tell....

---

### Post by Sorivenul on 2008-12-05
> **gjoellee said:**
> Yes I will start off with an Ubuntu base, using it to learn. My goal is to make something independent, but I have about no experience yet, that is why I am making a Ubuntu base....How do I make repositories, I have a domain so it is just to tell....

You could host on your domain, or you could setup through Launchpad via a PPA (Personal Package Archive).  IMO, Launchpad may be the best way as it sets things up automatically in the correct format.

---

### Post by WaeV on 2008-12-05
> Repositories are a storage location for files, usually packages to be fetched by the package manager.

I know that but what is the structure of the storage location, and how does APT know where to look, given a directory?  I there an index file?  Does it search manually?

---

### Post by gjoellee on 2008-12-05
> **Sorivenul said:**
> You could host on your domain, or you could setup through Launchpad via a PPA (Personal Package Archive).  IMO, Launchpad may be the best way as it sets things up automatically in the correct format.

I guess I would need something like 3gb space++ do you get that with launchpad?

---

### Post by Sorivenul on 2008-12-05
> **gjoellee said:**
> I guess I would need something like 3gb space++ do you get that with launchpad?

Why would you need 3+ GB just to host your own packages?  
If you are using the Ubuntu repositories, you don't need to duplicate them.  Just add whatever packages you want that aren't in the Ubuntu repositories and add your PPA to your distributions sources.list.  This is akin to what Linux Mint does.

---

### Post by gjoellee on 2008-12-05
> **Sorivenul said:**
> Why would you need 3+ GB just to host your own packages?  
If you are using the Ubuntu repositories, you don't need to duplicate them.  Just add whatever packages you want that aren't in the Ubuntu repositories and add your PPA to your distributions sources.list.  This is akin to what Linux Mint does.

oh, yes of  course!
oh....I tried to move some files I think was what I needed to set the new layout over to the live CD, but it was just adding the themes and stuff, not making them default, and both panels where still there.

Programs added to startup where no problem, PCMan started as well as gnome-do

Does anyone have a "little" howto on how to build a ubuntu base?

---

### Post by chris4585 on 2008-12-05
> **gjoellee said:**
> oh, yes of  course!
oh....I tried to move some files I think was what I needed to set the new layout over to the live CD, but it was just adding the themes and stuff, not making them default, and both panels where still there.

Programs added to startup where no problem, PCMan started as well as gnome-do

Does anyone have a "little" howto on how to build a ubuntu base?

yes and no, I'm working on a script to do this very thing

right now its not stable, but I plan on getting it fixed soon... 

[https://launchpad.net/ultra-livecd]("https://launchpad.net/ultra-livecd")

until then all I can offer is this thread: [http://ubuntuforums.org/showthread.php?t=688872]("http://ubuntuforums.org/showthread.php?t=688872")

---

### Post by LinuxGuy1234 on 2008-12-07
> **gjoellee said:**
> oh, yes of  course!
oh....I tried to move some files I think was what I needed to set the new layout over to the live CD, but it was just adding the themes and stuff, not making them default, and both panels where still there.

Programs added to startup where no problem, PCMan started as well as gnome-do

Does anyone have a "little" howto on how to build a ubuntu base?

debootstrap?

---

### Post by gjoellee on 2008-12-07
> **LinuxGuy1234 said:**
> debootstrap?
no, simple copy and paste actually

---

### Post by damis648 on 2008-12-07
I would highly recommend [this guide]("http://ubuntuforums.org/showthread.php?t=869659"). It got me started once I started remastering Ubuntu. :popcorn: It is pretty short, just throw in whatever you want between installing gnome and making a LiveCD and boom, there you have it. :popcorn: I would use /etc/skel for any user extra things, by the way, as another user suggested.

---

### Post by cardinals_fan on 2008-12-07
> **WaeV said:**
> I know that but what is the structure of the storage location, and how does APT know where to look, given a directory?  I there an index file?  Does it search manually?
I'm not familiar with APT (I try to stay as far away from Debian package management as I can).  Since I mostly use SliTaz now, I'll point you [here]("http://www.slitaz.org/en/devel/") for a pretty good overview.

@OP: Either of the guides posted should be very helpful.

---

### Post by gjoellee on 2008-12-07
> **damis648 said:**
> I would highly recommend [this guide]("http://ubuntuforums.org/showthread.php?t=869659"). It got me started once I started remastering Ubuntu. :popcorn: It is pretty short, just throw in whatever you want between installing gnome and making a LiveCD and boom, there you have it. :popcorn: I would use /etc/skel for any user extra things, by the way, as another user suggested.

does remastersys work fine with KDE? I have see that KDE 4.2 beta have received the required functionality for my upcoming system to work fine, as well the default look of KDE 4.2 is good.

---

### Post by Sorivenul on 2008-12-07
> **gjoellee said:**
> does remastersys work fine with KDE? I have see that KDE 4.2 beta have received the required functionality for my upcoming system to work fine, as well the default look of KDE 4.2 is good.

Remastered an older version of Kubuntu just fine when I used it.

---

### Post by gjoellee on 2008-12-09
> **Sorivenul said:**
> Remastered an older version of Kubuntu just fine when I used it.

that's nice, thank you for the feedback

---

### Post by Sorivenul on 2008-12-09
Remember, though, if you're remastering Kubuntu, Remastersys is a GTK application, so you'll have a little extra bloat from the required libraries, AFAIK.  Not a lot, but worth mentioning.

---

