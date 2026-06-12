---
title: "So I changed all &quot;warty&quot; references to &quot;hoary&quot; in sources.list"
date: 2005-02-09
forum: Repositories &amp; Backports
---

### Post by frijolito on 2005-02-09
And then upgraded and dist-upgraded. Of course, hilarity ensued.

Now, before you get all "YOU'RE NOT SUPPOSED TO TO THAT!!" on me, I know I'm not supposed to. But hey, I wanted the new software versions, and I figured that if everything breaks completely down, I'd just reinstall. See, I was curious, just wanted to see what happened.

Now, this is the interesting part: after upgrading (and dist-upgrading!), and seeing that everything was AFAICT still working, I rebooted. The machine rebooted fine, everything seemed to be OK, I got an X login screen and all. I logged in, Gnome fired up, but no toolbars!

Luckily I had a bash (gnome-terminal) window running automatically every time I log into Gnome, and that's how I was able to start firefox, email client, everything ('cause alt+f1 or alt+f2 don't seem to work). As far as I can tell, everything's ok, except no gnome toolbars.

OK, now I figure that in order for my life to be complete again, I don't really have to reinstall: I can just fix this gnome toolbar issue. Any suggestions?


*P.S.* hmm, it seems that this question may belong more in the Desktop forum than this one... but I'm still not sure, because the problem was caused by the alteration of repository sources. Should I (or a mod) move it over to that forum?

---

### Post by Kokosnuss on 2005-02-09
Toolbar? I think you mean the panel, don't you?
I had a similar problem lately. I had uninstalled the evolution-data-server with synaptic package manager. This uninstalled the gnome-panel as well and I was in the same situation you are experiencing. After reinstalling the gnome-panel in synaptic package manager (you can start it with "sudo synaptic package manager"), I could start it again by typing "gnome-panel" in the terminal...

Hopefully this can help you...
good luck!

---

### Post by frijolito on 2005-02-09
You are so right! My gnome-panel package is *gone*!

But it's not installable! Check out this output:

```

root@papalina:~ # apt-get install gnome-panel
(snip snip...)
The following packages have unmet dependencies:
  gnome-panel: Depends: libecal1.2-1 (>= 1.1.4.2) but it is not installable
               Depends: libedataserver1.2-0 (>= 1.1.4.2) but it is not installable
E: Broken packages


```
What do you think? Could this be irreversibly broken? (I, for one, prefer to think that there's no such thing as "irreversibly broken"  ;-) )

---

### Post by Klunk on 2005-02-09
I had a similar problem with kerberos on Warty. There were 2 dependent packages that had a later Ubuntu version which meant I could not install a number of kerberos packages. I forced the installed version of thos packages to the old, non-warty, one and everything worked fine from then on. Just be carfull when you then do an upgrade because it might screw everything up.

---

### Post by frijolito on 2005-02-09
[QUOTE=Klunk]I had a similar problem with kerberos on Warty. There were 2 dependent packages that had a later Ubuntu version which meant I could not install a number of kerberos packages. I forced the installed version of thos packages to the old, non-warty, one and everything worked fine from then on. Just be carfull when you then do an upgrade because it might screw everything up.[/QUOTE]
 *UPDATE*

OK, I ran 'apt-get update', and *then* 'apt-get install gnome-panel'. It worked! I now have a panel again... only for some reason, not all of the applets are there (e.g. mail notification, weather, sticky notes... and installing the gnome-applets package didn't help). But never mind that: I gots my panel back!

Thank you Kokosnuss for your invaluable help, and if you ever visit Guatemala and need someone to show you around, let me know! ;)

---

### Post by Kokosnuss on 2005-02-09
OK, I'll keep that in mind, buddy! ;-)

By the way...
What is new in "hoary"? Is it already the final version that you installed or just a beta or rc?

greetz

---

### Post by frijolito on 2005-02-09
[QUOTE=Kokosnuss]
What is new in "hoary"? Is it already the final version that you installed or just a beta or rc?
[/QUOTE]
 Actually, I'm not even quite sure! Seeing as how they point to archive.ubuntu.com, I'd guess that they're official sources... but I'm not really sure if it's beta, stable, unstable or whatever. It just originated by me wanting the latest *gaim* (and not wanting to install from source!).

Lemme show you the contents of my sources.list file:
```

# deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted

deb http://archive.ubuntu.com/ubuntu/ hoary main restricted
deb http://archive.ubuntu.com/ubuntu/ hoary universe
deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted

# saul (de ubuntuguide.org)
deb http://archive.ubuntu.com/ubuntu/ warty multiverse
deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main


```
What I did was replace all ocurrences of the string "warty" to "hoary". Wouldn't recommend it, though! ;)

---

### Post by paul cooke on 2005-02-09
[QUOTE=frijolito]And then upgraded and dist-upgraded. Of course, hilarity ensued.

Now, before you get all "YOU'RE NOT SUPPOSED TO TO THAT!!" on me, I know I'm not supposed to. But hey, I wanted the new software versions, and I figured that if everything breaks completely down, I'd just reinstall. See, I was curious, just wanted to see what happened.

Now, this is the interesting part: after upgrading (and dist-upgrading!), and seeing that everything was AFAICT still working, I rebooted. The machine rebooted fine, everything seemed to be OK, I got an X login screen and all. I logged in, Gnome fired up, but no toolbars!

Luckily I had a bash (gnome-terminal) window running automatically every time I log into Gnome, and that's how I was able to start firefox, email client, everything ('cause alt+f1 or alt+f2 don't seem to work). As far as I can tell, everything's ok, except no gnome toolbars.

OK, now I figure that in order for my life to be complete again, I don't really have to reinstall: I can just fix this gnome toolbar issue. Any suggestions?


*P.S.* hmm, it seems that this question may belong more in the Desktop forum than this one... but I'm still not sure, because the problem was caused by the alteration of repository sources. Should I (or a mod) move it over to that forum?[/QUOTE]

If you'd troubled to look in the Hoary Hedgehog Development Release forum, you'd have seen me have the exact same problem yesterday and the solution I was given to it... it appears that the Hoary repositories are currently in a state of flux and should not be attempted for a couple of days...

By the way, this forum is NOT the place to discuss Hoary issues until after the official release of Hoary... just thought I'd let you know that... ;)

---

### Post by dude2425 on 2005-02-10
I don't really have much time to read the few post's here, but just reading the main topic, I think I know a way to fix it. I actually had this problem before. All I did was delete all the hidden folders that reference gnome in my home directory, ie: ~/.gnome2 or ~/.gnome
Then log out and back on.

My problem that just started like yesterday or so, is that X won't start at all. I'm gonna keep trying, but I know it has something to do with the nvidia drivers, as when I comment out the nvidia stuff stuff and return to the generic nv drivers  in my /etc/X11/xorg.conf everything seems to work just fine.

---

### Post by cowlip on 2005-06-24
Huh?  I thought this IS how you upgrade Ubuntu to hoary?  What is the recommended procedure?

I also have the problem of no gnome-panel

---

### Post by dewey on 2005-06-25
Try not to bump 4 month old posts please.

And as for upgrading, yes, you're supposed to replace all the "warty" references with "hoary", but this thread was around before Hoary was officially released.

---

### Post by cowlip on 2005-06-25
[QUOTE=dewey]Try not to bump 4 month old posts please.

And as for upgrading, yes, you're supposed to replace all the "warty" references with "hoary", but this thread was around before Hoary was officially released.[/QUOTE]

Thanks for answering my question but you're not a moderator, so don't act like one.  I posted to it because I am searching for a reason why Hoary didn't upgrade correctly for me.

---

