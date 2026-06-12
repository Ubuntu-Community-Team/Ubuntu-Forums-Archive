---
title: "Java warning message"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by selkie1964 on 2008-07-07
I'm a new user of Linux (Ubuntu, 7.10), so please bear with me.  I was having trouble getting Java installed and running under Firefox, but a little research led me to the restricted extras and so on, so I finally got Java up and going.  However, every time I go to a new page which has a Java applet, a warning window opens first which says some stuff about security and Java applets (sorry, I'm at my work computer right now, which is Windows-platform, so I can't tell you the exact text of the message) and instructs me to add the page to the list of allowed URLs if I don't want to see the message again.

The thing is, where this happens mostly is in an online game I play in which the URL changes every time a page is accessed because the new URL includes the last play made (so adding the page to the "white list" is completely useless).  Is there any way to stop this happening?  It's so annoying I finally disabled the Java option for that site, but that is really cramping my style.

Any help would be appreciated.  Thanks.

---

### Post by neurostu on 2008-07-07
do you have the same problem when you visit the site on a windows machine?

Java has some weird security issues, but for good reasons as it allow remote execution of code and it needs to protect your machine.

I guess what i'm trying to stay is I'm not sure the message is exactly ubuntu related... it could be but I'm not sure it is...

---

### Post by selkie1964 on 2008-07-08
No, this has never happened on a Windows machine.  I'm at my home computer now, so here is the actual text of the message:

[INDENT][http://www.genericurl.com](http://www.genericurl.com) wants to load an applet.
GNU Classpath's security implementation is not complete.
HOSTILE APPLETS WILL STEAL AND/OR DESTROY YOUR DATA!

Click "Cancel" if you do not trust the source of this applet.
Click "Trust Applet" to load and run this applet now.
Click "Trust Applet and Add To Whitelist" to always load and run this applet from now on, without asking.
The whitelist is a list of the URLs from which you trust applets.
Your whitelist file is " /home/vera/.gcjwebplugin/whitelist.txt ".[/INDENT]

Then there are three buttons: "Cancel" "Trust Applet" and "Trust Applet and Add To Whitelist"

Like I said before, the URL is dynamic, so adding it to the whitelist doesn't really help because the next time I access the same page, I get the same warning.  I know in general this level of protection is a good thing, but I'd like to disable it at least for this website if possible.

Thanks for your help.

---

### Post by kpkeerthi on 2008-07-08
Looks like you are using GCJ as your default Java Runtime. You may want to switch to Sun's which is much better in my opinion.

1. Open a Terminal window
2. Run ```
sudo update-alternatives --config java
```
3. Follow the onscreen prompt

[... more info ...]("https://help.ubuntu.com/community/Java")

---

### Post by selkie1964 on 2008-08-17
First, sorry it's taken me so long to try this and get back to you -- been kinda busy.

Anyway, I tried what you suggested above and it hasn't worked.  I didn't have Sun Java in the list of alternatives, so I had to download and install the Sun Java 6 package, which I did using Add/Remove applications (as it suggested on the page to which you provided the link).  Then I restarted Ubuntu, tried the site again, and got the exact same message as before (see my second post above).  This is getting very frustrating.  :mad:

One thing I noticed was that if I select either of the other two Java options which appear when I use the command line above, the indication that they are selected is just an asterisk (*), but when I select the Sun Java version, it shows an asterisk and a plus sign (*+).  I'm sure this means something, but I have no idea what, and I also have no idea if it has anything to do with the problem I'm (still) having.  :confused:

Any further help/suggestions would be appreciated.  Thanks.

---

### Post by selkie1964 on 2008-09-19
I upgraded to Ubuntu 8.04 and that seems to have made this problem magically go away.  Seems to be specific to 7.10 -- weird.

Edit:

After upgrading to 8.04, I suddenly had no sound.  Nothing I did could get it going. So I upgraded again to 8.10 (alpha) -- Java worked under that too, but I still had no sound, and my touchpad page-scroll thingy stopped working.  I was fed up and decided to just go back to 7.10 figuring I could live without the dumb java applet since having both sound and page-scrolling not working was driving me nucking futz!  So I did a reinstall to return the laptop to its original factory settings, ran all the updates again, installed restricted extras (just like before), and all of a sudden, Java is working perfectly under 7.10.  double-weird!  must be gremlins.

---

