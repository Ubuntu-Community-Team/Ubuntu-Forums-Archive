---
title: "Panel Icons"
date: 2011-05-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by cecilpierce on 2011-05-06
I took out LireOffice icons and put the ones I wanted in the side panel and every time I reboot mine go and LibreOffice is back !
Any body know why or how to fix it ?

---

### Post by MacUntu on 2011-05-06
How did you change the icons?

---

### Post by cecilpierce on 2011-05-06
drag and drop from the applications icon at the bottom of the panel.

---

### Post by cariboo on 2011-05-06
> **cecilpierce said:**
> drag and drop from the applications icon at the bottom of the panel.

It looks like you may have to change the icon in the Launcher in /usr/share/applications, in order to make the change stick through a reboot.

---

### Post by VinDSL on 2011-05-06
> **cecilpierce said:**
> I took out LireOffice icons and put the ones I wanted in the side panel and every time I reboot mine go and LibreOffice is back !

Any body know why or how to fix it ?
I submitted a bug report on this earlier.

[INDENT][https://bugs.launchpad.net/ubuntu/+source/ca-certificates-java/+bug/778759](https://bugs.launchpad.net/ubuntu/+source/ca-certificates-java/+bug/778759)[/INDENT]


Does this sound familiar?

---

### Post by VinDSL on 2011-05-06
> **cariboo907 said:**
> It looks like you may have to change the icon in the Launcher in /usr/share/applications, in order to make the change stick through a reboot.
We might be talking about two separate issues, but in my case...

I have a *feeling* this ca-certificates-java error is a regression.  ;)

---

### Post by cecilpierce on 2011-05-06
> **VinDSL said:**
> I submitted a bug report on this earlier.

[INDENT][https://bugs.launchpad.net/ubuntu/+source/ca-certificates-java/+bug/778759](https://bugs.launchpad.net/ubuntu/+source/ca-certificates-java/+bug/778759)[/INDENT]


Does this sound familiar?

I read the bug report and can't say that's it.
All I can say is I change the icons in the launcher and when I reboot they go back to this set. (screen shot)

---

### Post by VinDSL on 2011-05-06
Yep!  Identical to the way mine looks (at boot).  Same apps -- same order.

The only difference is, I'm using a custom icon set, e.g. the icons look slightly different.

---

### Post by cecilpierce on 2011-05-07
I've got a lot of held-back packages for awhile now, I wonder if that is it ?

---

### Post by macroshaft on 2011-05-07
If you right click on your chosen icons is 'keep in launcher' ticked?

---

### Post by VinDSL on 2011-05-07
> **macroshaft said:**
> If you right click on your chosen icons is 'keep in launcher' ticked?
Yep!

And, any changes that I make are gone, on the next boot.

If I drag n' drop custom launchers into the Launcher Panel, they are gone too, after a restart.

It's almost like the boot process is invoking:

```

unity --reset-icons

```

It's quite a mystery...  :)

Are YOUR changes sticking?!?!?

---

### Post by VinDSL on 2011-05-07
> **VinDSL said:**
> I submitted a bug report on this earlier.

[INDENT][https://bugs.launchpad.net/ubuntu/+source/ca-certificates-java/+bug/778759](https://bugs.launchpad.net/ubuntu/+source/ca-certificates-java/+bug/778759)[/INDENT]


Does this sound familiar?
I slew one dragon -- removing the ca-certificates-java package (along with icedtea) got rid of the persistent error messages while performing updates.

But, it didn't do anything to cure the Unity Panel icon reset at boot.

Thus, two separate issues...  ;)

---

### Post by arpanaut on 2011-05-08
> Are YOUR changes sticking?!?!?

Nope!

First time I just thought maybe I hadn't changed to my liking, second time I doubted my sanity, now I know I'm okay...
Well Sorta.

Hey, maybe this is an extension of Mark's "Zero Configuration" mantra, and it's not a bug after all.  
Heaven help us all!

---

### Post by terry_gardener on 2011-05-08
i also have the same problem.

---

### Post by VinDSL on 2011-05-08
The funny thing is...

I can see my Unity -> Launcher -> Favorites in dconf.

They're just being ignored by Oneiric...  :P


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-8-may-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-8-may-2011.png")[/INDENT]

---

### Post by williejones on 2011-05-08
Same here.  I get rid of all the Libre icons and Ubuntu One.  Then I add
a terminal and Synaptic Package Manager.  The changes are undone on
the next reboot.

---

### Post by yaxomoxay on 2011-05-08
same here...

---

### Post by CreativeReach on 2011-05-08
I'm having no such problems on my three computers.

---

### Post by williejones on 2011-05-08
> **VinDSL said:**
> The funny thing is...

I can see my Unity -> Launcher -> Favorites in dconf.

They're just being ignored by Oneiric...  :P

[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-8-may-2011%28600x480%29.png[/IMG]]("http://vindsl.com/images/vindsl-desktop-8-may-2011.png")[/INDENT]

In looking at the bottom of your screenshot, the default is what seems to be coming back each reboot.

---

### Post by cecilpierce on 2011-05-08
@VinDSL

I can't find unity>launcher in gconf-editor, where did you get that ?

---

### Post by williejones on 2011-05-08
> **cecilpierce said:**
> @VinDSL

I can't find unity>launcher in gconf-editor, where did you get that ?

You have to install it.  I played with it and it seemed buggy on my system
so I uninstalled it.

---

### Post by cecilpierce on 2011-05-09
> **williejones said:**
> You have to install it.  I played with it and it seemed buggy on my system
so I uninstalled it.

I have it installed but no unity or launcher it it, the only thing found with the word 'launcher' in it was firefox, guess we have to wait for a fix.

---

### Post by mc4man on 2011-05-09
> **yanfeng said:**
> I also want to know how to solve this problem, thank you.

If you wish to explore this a bit and maybe workaround the current little problem, (if any), then try what [I suggested here]("http://ubuntuforums.org/showthread.php?t=1753224")

If no new line is written when adding/removing icons then  try running a gsettings set command. 
If that doesn't work, (withstand a log out/in),  then add the command  to your startup.
 
use this this format
```
gsettings set com.canonical.Unity.Launcher favorites "[insert your .desktops here]"
```
Ex. my natty current set

```
gsettings set com.canonical.Unity.Launcher favorites "['firefox.desktop', '/home/doug/.local/share/applications/utility.desktop', 'nautilus-home.desktop', '/home/doug/.local/share/applications/multimedia.desktop', 'gnome-terminal.desktop', '/home/doug/.local/share/applications/ImgBurn.desktop']"


```

---

### Post by cecilpierce on 2011-05-09
I disabled 'GSettings Data Conversion' in Startup Applications and now my icons are back the way I had them

---

### Post by VinDSL on 2011-05-09
> **cecilpierce said:**
> I disabled 'GSettings Data Conversion' in Startup Applications and now my icons are back the way I had them
Sweet!

I'll try that, when I get home.

---

### Post by cecilpierce on 2011-05-09
Strange, I have 3 oneiric's and only 1 kept the old icon list and the other 2 went right back to the libre-ubuntu junk, see if it works for you.
:oops:

---

### Post by Bowmore on 2011-05-09
You need to install the package dconf-gsettings-backend

More info here:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/778950](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/778950)

---

### Post by cecilpierce on 2011-05-09
> **Bowmore said:**
> You need to install the package dconf-gsettings-backend

More info here:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/778950](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/778950)

WOW! that did the trick, I've been going crazy with this and I guess a lot of other people to.

Thanks a million!      :D

---

### Post by VinDSL on 2011-05-10
> **Bowmore said:**
> You need to install the package dconf-gsettings-backend

More info here:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/778950](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/778950)
BINGO!!!

Thank you, so much!


SOURCE: (link above)
> 
Unity doesn't store the launcher icon preferences or doesn't read any dconf setting (e.g. the form factor of dash) unless the dconf-gsettings-backend is also installed along with libdconf0. Unity should depend on dconf-gsettings-backend package as well.

In the latest sync of d-conf from Debian, the libdconf0 binary was split into libdconf0 and dconf-gsettings-backend, both of which are needed in Unity.



Installing the dconf-gsettings-backend package worked wonders!  

All of my Favorites are back... ;)

---

### Post by Geeb on 2011-06-22
I'm having the same problem, but I am unable to install the needed package:
sudo apt-get install dconf-gsettings-backend
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package dconf-gsettings-backend


Am I doing something wrong?  This all happened after I installed Gnome 3 to try it out. It caused some video problems so I ran sudo ppa-purge ppa:gnome3-team/gnome3 which removed it but now I'm having these panel problems.

---

### Post by cariboo on 2011-06-23
@Geeb, try a different server, the  Main server is usually the best when running a testing version.

---

