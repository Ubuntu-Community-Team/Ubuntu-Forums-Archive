---
title: "Easiest HOW-TO for 3D Desktop Effects! W/out Compiz/Beryl"
date: 2007-10-06
forum: Outdated Tutorials &amp; Tips
---

### Post by kshane on 2007-10-06
If you're having trouble getting all the fancy 3D stuff working, i.e., Compiz, beryl, etc., try this: 3ddesktop.  I have an ATI Radeon x1650 and had nothing but problems after having tried EVERY how-to on the forums.  

I finally DID get Compiz working after a TON of private help from another forum user.  But, after all the work and literally hours of banging away on the keyboard making modifications and tweaks, my system was slowed to a crawl.  3ddesktop gave me the 3d desktop switcher I was imnpressed with the screenshots of, with no degradation of the system.  See the screen shot at the bottom!

So, if you're running Gnome, here's a short "how-to".  Users of KDE and others desktop environments should read the docs for keylaunch to find the differences (minimal).

First, download and install through Synaptic the following programs:  3ddesktop and keylaunch.  Just use the search in Synaptic if you have trouble finding either one.  After installing, follow these steps:

Set the number of desktops you want by using the default "Workspace Switcher" that comes with Gnome (right-click and choose "properties").  If you don't have it on your panel, put it on by right-clicking the panel and choosing "Add To Panel", find "Workspace Switcher" and click ADD.  Then, after setting your number of desktops, you can remove it.

Next, open terminal and cut & paste the following ("user" is your home directory):

```

cd /usr/share/doc/keylaunch
cp example_rc /home/"user"/.keylaunchrc

```

Now, open a text editor in the terminal (and enter your password) as follows:
```

cd /home/"user"
gksudo gedit .keylaunchrc

```

paste these lines to the bottom of the file and then save and close gedit
```

key=...F2:3ddesk --acquire
key=...F3:/usr/bin/3ddesk

```

Next, go to System>Preferences>Sessions.
Click on NEW.  Add the word "keylaunch" under Name and Command, then click OK and CLOSE.

Now, restart your session, either by <CTL>+<ALT>+<BACKSPACE>, or logging off and back on or by rebooting.

When you're back to your desktop press F2 to acquire the desktops you've set up.  **You only need to hit F2 when the desktop first comes up.**  You don't need to do it again, unless you restart your desktop. Wait 5 or 10 seconds, then hit F3.  You should then get a view like the one below.  By using your right or left mouse buttons, or the right and left arrow keys, you should be able to spin the desktops in either direction until you are at the desired one.  By hitting spacebar or enter or middle mouse button, you should bring the desktop back to the front.  Use F3 to change desktops again.

Good Luck!

Kevin

---

### Post by Armadillo Kilr on 2007-10-07
i tried the codes and nothing worked. but beryl works for me i just wanted to try this out just in case.

---

### Post by kshane on 2007-10-07
> **Armadillo Kilr said:**
> i tried the codes and nothing worked. but beryl works for me i just wanted to try this out just in case.

If you already have Beryl or Compiz installed, it probably won't....

Kevin

---

### Post by kshane on 2007-10-07
Anybody else had luck with this?

Kevin

---

### Post by JohnOhl on 2007-10-08
works well ;)...

Also running on an ATI Radeon X1650 :D

I do hate the 1-2 second delay after hitting F3 but who can complain when compiz / beryl is a bitch to setup for this card.

---

### Post by kshane on 2007-10-08
> **JohnOhl said:**
> works well ;)...

Also running on an ATI Radeon X1650 :D

I do hate the 1-2 second delay after hitting F3 but who can complain when compiz / beryl is a bitch to setup for this card.

Agreed.  Also, it will not run under Gutsy - which I just upgraded to...  :(

On the bright side, ATI is supposed to be releasing the new driver in a week or so.  Supposedly along with the final release of Gutsy.  Looking forward to it.  I got Compiz going with this card, but it was too much work and REALLY bogged down the system...

Kevin

---

### Post by magikx21 on 2007-10-17
Are we gonna see 3D Desktop for Gutsy or do I have to take another shot at Compiz?

---

### Post by kshane on 2007-10-17
> **magikx21 said:**
> Are we gonna see 3D Desktop for Gutsy or do I have to take another shot at Compiz?

Yeah...  Not supported in Gutsy...  But, for me, not too bad, cuz ATI's new driver should be out soon...  I hope...

Kevin

---

### Post by xtian88 on 2007-10-18
got this working.. im using an ati radeon 9600.. still a noob and im still learning.. this is a good start for me.. hope to get compiz working on this card because as far as i know it is supported.. thanks!

---

### Post by kshane on 2007-10-18
> **xtian88 said:**
> got this working.. im using an ati radeon 9600.. still a noob and im still learning.. this is a good start for me.. hope to get compiz working on this card because as far as i know it is supported.. thanks!

Good luck!  I have an ATI X1650 and I DID get Compiz going, but it brought my system to a CRAWL.  So, I found and installed 3Ddesktop.  It was pretty cool!  But, now I have no 3DDesktop effects of ANY kind, because I upgraded to Gutsy and 3DDesk isn't supported...  I am SOOOoooo hopeful that ATI releases their new driver soon!

Kevin

---

