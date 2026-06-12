---
title: "entirely new to linux and having a problem"
date: 2013-06-13
forum: New to Ubuntu
---

### Post by CardinalEntropy on 2013-06-13
I installed Ubuntu 13.04 this evening. The install went smooth but after I log in the screen I get looks like this[IMG]http://ubuntuforums.org/images/attach/jpg.gif[/IMG] IMG_1093.JPG (115.4 KB)
 I tried running from the DVD and it worked perfectly for a while then did the same thing. I have searched for an answer but haven't found anything yet. I should say I am using a fairly old and pretty crappy computer. Hopefully someone can help me out.

---

### Post by 1clue on 2013-06-13
Are you using an old CRT monitor?

It seems like you've got an invalid resolution on your monitor, but it should by default set something that works for you.

---

### Post by CardinalEntropy on 2013-06-13
I am actually using my 32 inch LCD TV. Could that be part of the problem?

---

### Post by 1clue on 2013-06-13
Almost certainly not.  What type of connector are you using?  Are you using the old-school analog monitor cable?

See if you can get a purely digital signal path between your TV and your computer.  I don't believe a digital card and digital monitor combo will show a screen like that.

What's going on is your monitor doesn't work with the resolution your video card is putting out.  You can sort of see how the desktop is severely slanted in your pic.

A modern flat-panel monitor using DVI or HDMI will tell the source device what resolutions it supports.

One thing you could try is go grab the TV's remote and change zoom modes.  I don't really think that will make much difference, but it might.

Do you have another Linux/UN*X box handy?  We could try some things that way too.

---

### Post by CardinalEntropy on 2013-06-13
I'm using the VGA connection, which was working and displaying just fine when I was running Windows Vista, and worked fine on my older Windows XP system. My computer doesn't have DVI or HDMI inputs. Sadly I don't have anything else running Linux. When I ran from the DVD it worked fine for about 5 minutes before it did it, which seems weird to me since without the DVD I get that screen as soon as I hit enter to log in.

---

### Post by 1clue on 2013-06-13
You ran from the DVD and it worked for five minutes, and then it did what?  Went crazy zebra desktop?  That seems to me to be a poorly connected cable.  I assume you jiggled everything?

OK we're going to go into a command-line mode.

Type <ctrl>-<alt>-<f1>.  You should get a text screen with a login prompt.

Log in as your main user.

type what's in bold.

**ls -al /etc/X11**

If you see an xorg.conf in there, then type:

**sudo rm -f /etc/X11/xorg.conf**

and then reboot.

---

### Post by 1clue on 2013-06-13
Oh yeah.  To reboot, type:

**sudo reboot**

---

### Post by Impavidus on 2013-06-14
What kind of video card do you have? It could be a driver issue.

---

### Post by CardinalEntropy on 2013-06-14
I don't have a xorg.conf when I type that in. I have XvMCConfig and Xwrapper.config but not xorg.conf. If I tried a different distro (maybe 12.04LTS)would I maybe have better luck?

---

### Post by cincinnatus13 on 2013-06-14
Hit CTR ALT F1 at the login. This will bring you to the command line. Log in using your username and password.
Type in
```
sh /etc/X11/Xreset
```
Go back and resume normal boot.

On a side note, do you have an Nvidia card, ATI card, integrated graphics?

---

### Post by CardinalEntropy on 2013-06-14
Ok so I realized that since I didn't have an xorg.conf I could create one and I did and moved it to the /etc/X11. Now I get past the login screen and can run the OS but it is extremely slow. So I guess my newest question is, is there any way I can fix that?

---

### Post by linuxtechguy on 2013-06-14
> **1clue said:**
> Oh yeah.  To reboot, type:

**sudo reboot**

You should not use reboot but shutdown -r now

---

### Post by 1clue on 2013-06-14
OK I'm rapidly running out of expertise with which to help.

I've been around since the early days of XFree86, but ever since I switched to xorg everything just worked for the most part.  So I don't really have a lot of debug expertise on that.

The sort of issue you're having, probably it's the same every distro.  This is well-marked territory I think.

It seems to be a config issue or maybe a driver issue.

---

### Post by 1clue on 2013-06-14
@linuxtechguy,

Why?

---

### Post by 1clue on 2013-06-14
[http://linux.about.com/od/commands/l/blcmdl8_reboot.htm](http://linux.about.com/od/commands/l/blcmdl8_reboot.htm)

> 
If halt or reboot is called when the system is not in runlevel 0 or 6, in other words when it's running normally, shutdown will be invoked instead (with the -h or -r flag). For more info see the shutdown(8) manpage.


It's the same thing.  It has been the same thing for a very long time.

---

