---
title: "HOWTO: Change GTK themes for root application &amp; Standard greeter"
date: 2005-04-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Perfect Storm on 2005-04-04
Are you tired of that your root applications doesn't match your desktop theme?

Here's the answer, this show with the D3a GTK2 theme. Just change D3a with your favorite GTK theme:

```

cd /home/orion/.themes
sudo cp -r  d3a /usr/share/themes
sudo gedit /etc/gdm/gdm.conf

```

Now I changed under [gui]

GtkTheme=d3a
GtkThemesToAllow=d3a


Check the attached snapshot of Package Manager, it's now with D3a theme instead of human theme.
This will also change the Standard greeter GTK theme.

---

### Post by PinGzor on 2005-04-04
Thanks! Needed this fix

---

### Post by j_baer on 2005-04-04
Artificial Intelligence,

Thanks for the tip, worked great.

j baer

---

### Post by Perfect Storm on 2005-04-07
Glad to be a help ^_^

---

### Post by Buffalo Soldier on 2005-04-10
Something I've been looking for quite some time. Thanks :)

---

### Post by Yukonjack on 2005-04-10
Thanks a bunch Artificial Intelligence! 
Good stuff

---

### Post by Quest-Master on 2005-04-10
I've been looking for this one too. Nice job. :D

---

### Post by donar73 on 2005-04-21
:)  :)  :) 

I've been looking for this for weeks! Thx alot!

---

### Post by Perfect Storm on 2005-04-23
No problem. :)


If I'm not mistaken (I havn't tried it yet) if you add in 'GtkThemesToAllow=d3a' with other themes like this: 'GtkThemesToAllow=d3a, human, etc., etc.' then you can choose which themes to use in the Standard Greeter or replace d3a with 'all' then you can choose all the gtk themes. Though you have to install them as shown in the first post. These themes can only be changed when you're Standard greeter log in screen, there's a tab called 'themes'.



.:=The AI Dude=:.

---

### Post by Chayyiel on 2005-04-25
Awesome! I'll give this a shot.

---

### Post by globalspace on 2005-04-25
wonderfull !
now my Desktop is really beatyfull  :razz:

---

### Post by Chayyiel on 2005-04-25
Works wonderful! Thank you!

---

### Post by XplOzIOn on 2005-04-25
Hey thats cool!

---

### Post by Perfect Storm on 2005-05-10
Thanks for the kind words, guys ^_^

---

### Post by abbot on 2005-05-20
Actually, you dont even have to change the first line from "GtkTheme=Human"

and like you said before, just change the other line to read "GtkThemesToAllow=all"
Then copy whatever theme you are using from ~/.themes to /usr/share/themes
you could really just copy them all over there if you wanted, then whenever you switch around themes the root will switch too, at the same time even.  You dont have to switch it in the standard greeter screen.

---

### Post by Poul on 2005-05-21
Hmm i don't know why but it doesn't work for me. I made my own theme by connecting  icons and window borders from GnoMetal theme and cdntrols from GlossyP theme (both downloaded from art.gnome.org) Aftherwards some aplications (synaptic , my custom nautilus-root-here script, sudo gedit) strarted looking really ugly. I hoped that it will fix it but it didn't .
Any ideas?

Edit: I worked it out. Since my custom theme has been using 2 themes i just copied them as well.
And copied icons (gnometal) to /usr/share/icons

Btw Sweet  O:)

---

### Post by angrykeyboarder on 2005-05-25
As far as root applications sharing my themes go, I simply symlink my ~/.themes and ~/.icons directories to /root/.themes and /root/.icons, respectively.

---

### Post by m87 on 2005-06-02
good, but if you break into X when "root"... I remember I changed a theme once, and since then, synaptic and every other suid app follows the theming [i don't know if with that solution works, mine is more brutal hahaha]

---

### Post by abbot on 2005-06-17
[QUOTE=angrykeyboarder]As far as root applications sharing my themes go, I simply symlink my ~/.themes and ~/.icons directories to /root/.themes and /root/.icons, respectively.[/QUOTE]
haha.  well then.  thats so simple and it works perfectly.  you dont even have to edit any .conf files.  just make the links in the /root directory and you're good.

---

### Post by tabasko on 2005-06-27
Thanks!

---

### Post by -DarkMind- on 2005-07-10
hello

i use kubuntu (i have kde only) and i use synaptic (kynaptic sucks)

i installed gtk2-engines-gtk-qt with this gtk2 applications looks good (like the kde theme actually used)

all applications look godd, but if execute "kdesu synaptic" , synaptic looks horrible  :???: 

but if i execute synactic from the console with "sudo synaptic" looks good  :???: 

how i fix this?



thanks and sorry for my english, i speak spanish only  :)

---

### Post by -DarkMind- on 2005-07-10
[QUOTE=-DarkMind-]hello

i use kubuntu (i have kde only) and i use synaptic (kynaptic sucks)

i installed gtk2-engines-gtk-qt with this gtk2 applications looks good (like the kde theme actually used)

all applications look good, but if execute "kdesu synaptic" , synaptic looks horrible  :???: 

but if i execute synactic from the console with "sudo synaptic" looks good  :???: 

how i fix this?



thanks and sorry for my english, i speak spanish only  :)[/QUOTE]

jajajajja, a friend help me... for another with the same problem...

copy the files:

/home/youruser/.qt/qt_plugins_3.3rc
/home/youruser/.qt/qtrc

to /root/.qt/


:D

---

### Post by AndyAWS on 2005-07-31
For some reason this doesn't work at all for me. Not only are all apps run as root theme-less...I also have no icons if I run Nautilus as root.

---

### Post by Perfect Storm on 2005-08-01
You sure you typed in the right theme you want to use?

---

### Post by AndyAWS on 2005-08-01
Yes...Human.

I just want root to use the default Ubuntu theme. Instead everything is gray and plain, always has been.

The icons were working until I changed the icons that I use for my normal user, then all of the icons for root changed to the blank paper looking icon. I remember fixing that once before but I don't remember how i did it.

Also, if I actually log-in as root everything looks fine.

---

### Post by AndyAWS on 2005-08-01
Do I have to be using the Standard Greeter for this to work? I currently use a graphical greeter I downloaded from gnome-look.org.

---

### Post by LaSSarD on 2005-08-01
[QUOTE=Artificial Intelligence]Are you tired of that your root applications doesn't match your desktop theme?

Here's the answer, this show with the D3a GTK2 theme. Just change D3a with your favorite GTK theme:

```

cd /home/orion/.themes
sudo cp -r  d3a /usr/share/themes
sudo gedit /etc/gdm/gdm.conf

```

Now I changed under [gui]

GtkTheme=d3a
GtkThemesToAllow=d3a


Check the attached snapshot of Package Manager, it's now with D3a theme instead of human theme.
This will also change the Standard greeter GTK theme.[/QUOTE]
 I was wondering how to do this since I noticed that running apps as root makes them use a old GTK theme... Then you came up with this great tut! Thx a lot man ;D

---

### Post by AndyAWS on 2005-08-01
Ok, I got my icons back by symlinking my ~/.icons to /root/.icons.

I also had the root apps themed by symlinking .themes but that made root apps the same as normal apps which isn't what I wanted, so I'll settle for root apps being unthemed.

I've tried everything I can think of to give the root apps a different theme from my normal theme.

---

### Post by bjesus on 2005-08-02
I´m having the exact same problem as **AndyAWS** - The root theme won´t change until I create a symlink and then it´s just the same as my user´s.

AndyAWS: Are you using Hoary or Breezy? I´m using Breezy and have thought that maybe that the source to our problems.

---

### Post by Perfect Storm on 2005-08-03
Hmmm...I'm not sure why it won't for you two. Are you superuser(sudo) or split ubuntu into root and user(su)?

---

### Post by AndyAWS on 2005-08-03
[QUOTE=bjesus]AndyAWS: Are you using Hoary or Breezy? I´m using Breezy and have thought that maybe that the source to our problems.[/QUOTE]

I'm running Hoary.


@AI: I'm not sure what you mean. I use sudo for all root tasks, but the root user does exist, I have logged in as root once and the root user was using the default Human theme.

---

### Post by lynng on 2005-08-04
Thanks for the tip.  I orginally tried to make the symlinks from inside my home dir like so:
```
~$ sudo ln -s .themes /root/.themes
~$ sudo ln -s .icons /root/.icons
``` but the links were broken.  I had to do:
```
~$ cd /root
/root$ sudo ln -s /home/*username*/.themes .themes
/root$ sudo ln -s /home/*username*/.icons .icons
``` to make it work.  This is probably something about symlinking that I haven't picked up on yet, but thought I'd post in case anyone else thought it didn't work perhaps for the same reason.

---

### Post by Perfect Storm on 2005-08-04
I'm just trying to figure out if there was something similar with you two ubuntu that might explain the problem.

Can I get both of you to try to download the d3a theme and follow the howto strictly and see if it works? It might be a problem with the human theme because there's already a human theme configuration in /usr/share/themes folder which could mess up your stuff.

---

### Post by AndyAWS on 2005-08-04
Thanks AI I should have thought of that ](*,) ....I'll give it a try tonight and let you know.

---

### Post by AndyAWS on 2005-08-04
Didn't work...I tried switching to the Standard Greeter instaed of the graphical one, and the greeter was in the d3a theme. Also d3a was listed in the greeter theme menu.
But sudo apps are still not themed...is there a conf file somewhere for sudo?

---

### Post by Penguin Guy on 2009-04-07
Where can I find the d3a theme and icons? I looked all over the internet and found nothing.

---

### Post by Perfect Storm on 2009-04-07
It does not exist anymore, nor do I have them anymore.

---

### Post by Penguin Guy on 2009-04-07
Awww, it looked so cool as well! And sorry for accidently breaking the necromancy rule.

---

