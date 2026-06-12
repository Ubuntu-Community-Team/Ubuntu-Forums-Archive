---
title: "Where is Suspend?"
date: 2014-06-05
forum: New to Ubuntu
---

### Post by gary38 on 2014-06-05
Hi, I'm quite new to Linux and very new to Ubuntu.  I started off with Pinguy and I liked it but it kept doing odd things and it had way more stuff on there than I would ever use so I decided to make the plunge into Ubuntu after reading that it is basic to begin with and you customize it to the way you want it from the start blah blah blah right?

Anyway, to my question - I installed Ubuntu 14.04 LTS over Pinguy and one thing that I find missing that I liked on Pinguy is the option to Suspend.  When I go up to the top right corner I only get the option to  Power Off.

Can anyone please advise?

Thanks.

p.s. I'm sure this will be the first of many questions, but you never know, I'll see how I get on :P

---

### Post by TheFu on 2014-06-05
Does running **sudo pm-suspend** work?

**The GUI is NOT the OS** with Linux. You can modify the GUI settings/locations/styles - I find it easier if any other GUI besides the default Unity is used. There are 20-50 alternates.  I use LXDE and **suspend** is on the normal logout menu options.  However, I usually just run **sudo pm-suspend** from a terminal.

Oh - and I've never seen/tried pinguy - don't know anything about it.

---

### Post by gary38 on 2014-06-05
Sorry, what's a GUI? something something Interface is it?

---

### Post by slickymaster on 2014-06-05
> **gary38 said:**
> Sorry, what's a GUI? something something Interface is it?

[http://en.wikipedia.org/wiki/Graphical_user_interface](http://en.wikipedia.org/wiki/Graphical_user_interface)
[http://www.webopedia.com/TERM/G/Graphical_User_Interface_GUI.html](http://www.webopedia.com/TERM/G/Graphical_User_Interface_GUI.html)

---

### Post by grahammechanical on 2014-06-05
In my 14.04 suspend is in the power/cog menu. It is the line above shutdown. Do you have ACPI disabled in the BIOS? 

> [COLOR=#333333][FONT=Ubuntu Beta]Modern power management is handled via ACPI, a spec designed by various companies (Microsoft, Intel, Phoenix, HP, etc). It contains information about the given system's hardware, including details on how to suspend/resume (and hibernate).[/FONT][/COLOR]

[https://wiki.ubuntu.com/UnderstandingSuspend](https://wiki.ubuntu.com/UnderstandingSuspend)

I would not call Ubuntu "basic." It far from basic. Easy to use it is.

Regards.

---

### Post by gary38 on 2014-06-05
> **grahammechanical said:**
> In my 14.04 suspend is in the power/cog menu. It is the line above shutdown. Do you have ACPI disabled in the BIOS? 



[https://wiki.ubuntu.com/UnderstandingSuspend](https://wiki.ubuntu.com/UnderstandingSuspend)

I would not call Ubuntu "basic." It far from basic. Easy to use it is.

Regards.

'Basic' was a bad choice of word, I meant you start with a basic (as in preliminary) platform that has many possibilities to be customized, for want of a better description if you get my meaning.

---

### Post by gary38 on 2014-06-05
So is Gnome the GUI?  If so, how do I get Suspend to appear on Gnome?  Thanks.

---

### Post by gary38 on 2014-06-07
> **grahammechanical said:**
> In my 14.04 suspend is in the power/cog menu. It is the line above shutdown. Do you have ACPI disabled in the BIOS? 



[https://wiki.ubuntu.com/UnderstandingSuspend](https://wiki.ubuntu.com/UnderstandingSuspend)

I would not call Ubuntu "basic." It far from basic. Easy to use it is.

Regards.

I don't seem to have a power/cog menu either.
ACPI disabled in the BIOS  -  No idea sorry.

Any further help would be much appreciated :)

---

### Post by TheFu on 2014-06-08
Does suspend work on non-ACPI systems?  
Enable that in the BIOS and install the **acpid** package.
If the system runs Windows too, do not change the BIOS without more research. I think Microsoft installs different stuff based on ACPI or non-ACPI.  I don't know any of this, just thinking out loud.

Also - thanks for this link [https://wiki.ubuntu.com/UnderstandingSuspend](https://wiki.ubuntu.com/UnderstandingSuspend) - I have an XBMC machine that doesn't like to recover from suspend. That machine doesn't run any normal GUI - just XBMC.

---

### Post by kurt18947 on 2014-06-08
> **gary38 said:**
> So is Gnome the GUI?  If so, how do I get Suspend to appear on Gnome?  Thanks.

If you are using Ubuntu Gnome, the suspend function is found by clicking the 'power' button in the upper right corner.  A new window will open with a couple buttons on the bottom.  The right button should be another power button.  Hold the <alt> key and that button should turn into a 'pause' button.  Click that to suspend.  There are a couple extensions that add a 'suspend' button without needing the <alt> key.

---

### Post by gary38 on 2014-06-09
> **kurt18947 said:**
> If you are using Ubuntu Gnome, the suspend function is found by clicking the 'power' button in the upper right corner.  A new window will open with a couple buttons on the bottom.  The right button should be another power button.  Hold the <alt> key and that button should turn into a 'pause' button.  Click that to suspend.  There are a couple extensions that add a 'suspend' button without needing the <alt> key.

Thats great, thanks for the reply, how do you get one of these extensions then if you don't mind?

---

### Post by kurt18947 on 2014-06-09
> **gary38 said:**
> Thats great, thanks for the reply, how do you get one of these extensions then if you don't mind?

Go to this web site:  extensions.gnome.org.  You install the extensions directly from the web site.  There used to be the case that some extensions, after being installed needed to be enabled using gnome-tweak-tool.  i haven't run into that recently.  There is one - Weather by Neroth - that I haven't been able to install from the web site.  I needed to follow the link to github and get the data to install it manually.

The downside to relying on extensions is one is relying on the kindness of strangers to an extent.  Gnome seems to support certain extensions - those are available in the repositories.  Several of my favorites are not in that package so the extension's developer may need to tweak to work with newer versions of gnome-shell.

---

### Post by gary38 on 2014-07-25
> **kurt18947 said:**
> If you are using Ubuntu Gnome, the suspend function is found by clicking the 'power' button in the upper right corner.  A new window will open with a couple buttons on the bottom.  The right button should be another power button.  Hold the <alt> key and that button should turn into a 'pause' button.  Click that to suspend.  There are a couple extensions that add a 'suspend' button without needing the <alt> key.

Apologies for dragging this up again, I have used the Alt Key while clicking the power button to suspend, however I cannot get the PC to re-awake.  Have you any suggestions for this problem?

Thank you.

---

### Post by bapoumba on 2014-07-25
What did you try to wake it up ? Please try the space bar.

---

### Post by gary38 on 2014-07-25
Hi Sorry, I need to elaborate, I awake the PC with the space bar but then nothing responds to clicks of the mouse, nothing at all, I can't even shut down or anything, I have to power off the PC using the switch on the front.

---

### Post by TheFu on 2014-07-25
can you ssh in and run **sudo shutdown -h now**?

---

### Post by bapoumba on 2014-07-25
Just for a test, please <ctrl><alt><f1> and then <ctrl><alt><f7>. Does that bring you back to the graphical login screen where you can enter your password and unlock your session ?

---

### Post by buzzingrobot on 2014-07-25
When you installed Ubuntu "over" Pinguy, did you burn an ISO image, boot it, and completely replace Pinguy with Ubuntu?

To clear up possible confusion, Ubuntu's standard interface is Unity, has a panel across top, with that little gear icon on the far right, and a single vertical colimn of icons to the left.

Gnome Shell is an alternative interface to Ubuntu.  It has a black panel across the top on which the word "Activities" appears on the far left. Pushing the cursor into the top left corner tiggers a display of a dock on the left, thumbnails of virtual workspaces on the right, and a large pageable display of icons representing available applications in between.

---

### Post by gary38 on 2014-07-25
> **buzzingrobot said:**
> When you installed Ubuntu "over" Pinguy, did you burn an ISO image, boot it, and completely replace Pinguy with Ubuntu?

To clear up possible confusion, Ubuntu's standard interface is Unity, has a panel across top, with that little gear icon on the far right, and a single vertical colimn of icons to the left.

Gnome Shell is an alternative interface to Ubuntu.  It has a black panel across the top on which the word "Activities" appears on the far left. Pushing the cursor into the top left corner tiggers a display of a dock on the left, thumbnails of virtual workspaces on the right, and a large pageable display of icons representing available applications in between.

Hi, Thanks for the reply,
I installed via a pendrive over Pinguy.  I do still have the words Pinguy OS when I open up the Internet as my home-screen though.....

As for the layout, I have "Activities" in the left top corner, I have to click on it for icons to appear, they don't open when I hover (if that matters?) Along the top in the centre is the clock and at the right top I have "en1" then the speaker symbol and then the power symbol with and inverted arrow next to it.  I don't have thumbnails of virtual workspaces on the right and I don't have a large pageable display of icons representing applications in between.

:-)

Edit - I do have thumbnails at the right - never noticed before!  Sorry. Nothing in between though, unless you just mean a blank desktop where icons can sit if you want them to???

---

### Post by gary38 on 2014-07-25
Hi, Thanks for the reply,
When I press <ctrl><alt><f1> I get a black screen with text in the top left and then when I press <ctrl><alt><f7> it returns me to this screen.

:-)

---

### Post by gary38 on 2014-07-25
> **TheFu said:**
> can you ssh in and run **sudo shutdown -h now**?

Hi Thanks for the reply,
Sorry I don't know what you mean by ssh in and run sudo shutdown -h now :redface:

---

### Post by buzzingrobot on 2014-07-25
> **gary38 said:**
> 
I installed via a pendrive over Pinguy. 

Did you boot from the pen drive, see the Ubuntu installer that offered two options:  "Try Ubuntu" and "Install Ubuntu", opt to install, and select the option to replace Pinguy with Ubuntu? 

> As for the layout, I have "Activities" in the left top corner, I have to click on it for icons to appear, they don't open when I hover (if that matters?) Along the top in the centre is the clock and at the right top I have "en1" then the speaker symbol and then the power symbol with and inverted arrow next to it.  I don't have thumbnails of virtual workspaces on the right and I don't have a large pageable display of icons representing applications in between.

:-)

I've never used Pinguy. Except for the "Activities" label, that isn't default Gnome you are describing and it isn't anything like Unity.  

I'd suggest the best course is to reinstall.  If you want Ubuntu Unity, it's here: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) (other good info on that page).  If you want Ubuntu Gnome, it's here: [http://ubuntugnome.org/](http://ubuntugnome.org/)

---

### Post by whitesmith on 2014-07-26
Gnome is a desktop environment (DE). In Windows there is only one DE, a program called explore.exe (not to be confused with Windows Explorer, a file manager, or Internet Explorer). Linux has dozens of DEs. Some of the more popular DEs are listed here: [http://www.linuxlinks.com/article/2008112315231841/Desktop.html](http://www.linuxlinks.com/article/2008112315231841/Desktop.html)

---

### Post by TheFu on 2014-07-27
> **gary38 said:**
> Hi Thanks for the reply,
Sorry I don't know what you mean by ssh in and run sudo shutdown -h now :redface:

What is ssh? [https://en.wikipedia.org/wiki/Secure_Shell](https://en.wikipedia.org/wiki/Secure_Shell)

It is a way to connect between computers on a network, securely. It is extremely handy and can be used from the same machine to connect as a network user might or from across the world to connect.  In the list of achievements of mankind, ssh is just after UNIX.  Pretty much every webserver on the internet is managed and maintained through ssh.  There are clients for almost every platform (if it has networking, there is probably an ssh client).

Might that be something worth learning?  Even if only to ssh into your other PC and tell it to shutdown?

---

