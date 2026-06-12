---
title: "starting applications"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by davebo1123 on 2008-05-04
I am totally new to Linux, having used only windows since 3.1. I just downloaded Thunderbird to Ubuntu and expanded it. I now have a folder called Thunderbird do not know how to start an executable, IE Thunderbird.

I am sure it is very easy but I am a total novice

thanx in advance 
David

---

### Post by PeterJS on 2008-05-04
Generally installing things directly from the authors are a pain in the backside. A much better way to install thunderbird would be to go to Applications > Add/Remove Programs, and search for and install Thunderbird from there. Thunder bird should show up in the applications menu at Applications > Internet >Thunderbird.

And A good guide to installing other stuff:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Monicker on 2008-05-04
It would be less trouble to just use the Synaptic package manager to install it.

System -> Administration -> Synaptic Package Manager


I would get more familiar with Ubuntu before trying to install any external source packages.

---

### Post by mlentink on 2008-05-04
Even in Windows, the best way to explore a system is to have a look at what's in the menus. 
So have a look at the Applications menu (usually in the top-left corner of your screen). Click it. At the bottom, you will see an option called 'Add/Remove Programs'. Click it. Have fun.

P.S.: You will undoubtedly find Thunderbird in the 'Internet' section.

---

### Post by Eisenwinter on 2008-05-04
> **davebo1123 said:**
> I am totally new to Linux, having used only windows since 3.1. I just downloaded Thunderbird to Ubuntu and expanded it. I now have a folder called Thunderbird do not know how to start an executable, IE Thunderbird.

I am sure it is very easy but I am a total novice

thanx in advance 
David
To start Thunderbird, open Applications -> Internet -> Thunderbird.

It should be listed there.
If it's not, you have two other options.

**The first** (and faster, but possibly less comfortable one) is to open up terminal and launch it from there.

Go to Applications -> Accessories -> Terminal.
A small DOS-like window opens up.

In there simply type thunderbird.

**The second** (slower, but possibly more comfortable way) is to dig through your /usr/bin folder.

Go to Places -> Home Folder.

On the left Menu in your Home Folder window, click on File system.

In File system, go to the directory saying "usr", and in usr, go to "bin".

Once you are in the /usr/bin directory, start typing "thunderbird", until an application is found and selected.

If it's not there, try other folders, such as /bin, /usr/sbin, /usr/share, and /usr/local/share.

---

### Post by SunnyRabbiera on 2008-05-04
In ubuntu installing most stuff is a little different then it is in windows, we use tools like apt, add/remove and synaptic.
It takes some getting used to but learning how to install applications in ubuntu is very easy.

---

### Post by ace007 on 2008-05-04
That is correct.  Things are a little different in Linux.  In my opinion things are a little nicer.  Reasons behind certain things are usually understood by the user.  In my opinion, Windows sometimes hides the function of certain things and it leaves the user confused.

Anyways.  The synaptic package manager is by far one of the best utilities that Ubuntu has over Windows.  There are repositories that contain the latest stable builds of countless applications.  The repositories are maintained (most of the time) by responsible people who are not looking to flood the world with spyware/virus infested applications.  You can feel safe when you download an application from one of these repositories.  Also, the dependencies of each application, like a certain linked library, is kept track of so it tells you it must install an additional package to make the application you want work.  It likewise will uninstall the package if it is no longer needed.  Synaptic will give you a graphical tool for accessing these repos.  If you know the exact name of the package you can avoid launching the package manager by installing the package via the command line using the "apt-get" or "aptitude" functions.  Very helpful.

Welcome Aboard!

---

