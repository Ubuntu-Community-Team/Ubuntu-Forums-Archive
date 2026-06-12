---
title: "HOWTO: Making Your Ubuntu Support Traditional Chinese in 3 Steps"
date: 2005-04-10
forum: Outdated Tutorials &amp; Tips
---

### Post by tzutolin on 2005-04-10
[FONT=Arial Black][SIZE=3]**HOWTO: Making Your Ubuntu Support Traditional Chinese in 3 Steps**[/SIZE][/FONT]

[B]Step 1: In the root terimal:
[/B]
```

echo "deb ftp://ftp.hk.debian.org/unofficial/dlot-apt unstable main" 
>> /etc/apt/sources.list && apt-get update && apt-get install scim 
scim-chinese scim-chewing scim-config-socket scim-frontend-socket 
scim-gtk2-immodule scim-server-socket xfonts-intl-chinese 
ttf-arphic-gbsn00lp ttf-arphic-gkai00mp ttf-arphic-bkai00mp 
ttf-arphic-bsmi00lp
```

or if you want to install them manually, these packages are needed: 

(NOTE: Be sure to add the site first **"deb [ftp://ftp.hk.debian.org/unofficial/dlot-apt](ftp://ftp.hk.debian.org/unofficial/dlot-apt) unstable main"** in your /etc/apt/sources.list)

[INDENT]scim 
scim-chinese 
scim-chewing 
scim-config-socket 
scim-frontend-socket 
scim-gtk2-immodule 
scim-server-socket 
xfonts-intl-chinese 
ttf-arphic-gbsn00lp 
ttf-arphic-gkai00mp 
ttf-arphic-bkai00mp 
ttf-arphic-bsmi00lp[/INDENT]

[B]
Step 2: Go to "System" -> "Perferences", and select "Sessions". In "Startup Programs", add the command "scim -d".[/B]

[B]
Step 3: Restart X (Ctrl+Alt+BackSpace)[/B]

---

### Post by benkorkor on 2005-04-10
apt-get install scim-chewing reported the following:

Package scim-chewing is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

---

### Post by tzutolin on 2005-04-10
[QUOTE=benkorkor]apt-get install scim-chewing reported the following:

Package scim-chewing is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source[/QUOTE]

Thanks benkorkor! I just made a correction in the guide. Thanks for your help!!

---

### Post by Rinnan on 2005-04-10
Thank you for this guide.  I actually did it on a fresh install of Ubuntu.  It works, however a newbie might run into problems.  Some tips:

#1: Step one might not be clear to a newbie -- it cut-n-pastes as multiple lines, but is meant to be entered as a single line.  It might be better to break it up?

#2:  Typo : it's "apt-get install scim ..." not "apt-get scim ..." or at least, my version of apt-get required the keyword "install".

#3:  Will this work on a truly fresh install of Ubuntu 5.04, or does it require that you add universe and multiverse repositories first?

Ubuntu is the first system I ever got any Chinese input method to work on (after a long time of trying with multiple distros) and your guide was the first I've ever gotten to work.  Thanks again!

---

### Post by nanaban on 2005-04-10
missing **install** after apt-get in step one?

---

### Post by tzutolin on 2005-04-11
Thank you, Rinnan! Thank you, nanaban! 
I've corrected it.

---

### Post by kuleali on 2005-04-13
Woow! :)

---

### Post by djib on 2005-10-26
Hey,
This doesn't work on my pc.
Scim does appear near the clock but I still can't input chinese in any program...

---

### Post by ubuntutinger on 2005-11-10
I have using Synaptic to include SCIM package as you recommended. Now, I got input icon next to the speaker. But, I can't activate it. Could you tell me howto? I have used ctrl-space, atl-LShift, atl-RShift etc. all did not work.

---

### Post by djib on 2005-11-10
Hello,
This really depends on what you want to do.
If you only want to use SCIM with GTK applications like gaim, epiphany, gedit and so on (ie : not firefox or openoffice) the only thing you have to do is to right click in the area where you want to input text and select SCIM as the input method. Then doing ctrl+space will activate SCIM.
If you cant SCIM to work in every application you need to create a file called .xsession in your home with the following text :

export XMODIFIERS=@im=scim
export GTK_IM_MODULE=scim
gnome-session

(provided you use gnome)

---

### Post by ubuntutinger on 2005-11-13
[QUOTE=djib]Hello,
This really depends on what you want to do.
If you only want to use SCIM with GTK applications like gaim, epiphany, gedit and so on (ie : not firefox or openoffice) the only thing you have to do is to right click in the area where you want to input text and select SCIM as the input method. Then doing ctrl+space will activate SCIM.
If you cant SCIM to work in every application you need to create a file called .xsession in your home with the following text :

export XMODIFIERS=@im=scim
export GTK_IM_MODULE=scim
gnome-session

(provided you use gnome)[/QUOTE]

Thank you, djib,

I assume this is for single user. If I wanted to make this input option to entire system, how should I do? In addition, if I use Kubuntu (KDE), I assume I just change the third line to "kde-session". Am I right?

---

### Post by djib on 2005-11-13
I am pretty sure that for KDE you have to write 'startkde' instead of 'gnome-session'.

If you create a .xsession it will only work for the user who has the .xsession. I don't know if there is a way to make it available for any user. Maybe there is a file that is used as default .xsession when creating a new user...

---

### Post by ubuntutinger on 2005-11-13
[QUOTE=djib]I am pretty sure that for KDE you have to write 'startkde' instead of 'gnome-session'.

If you create a .xsession it will only work for the user who has the .xsession. I don't know if there is a way to make it available for any user. Maybe there is a file that is used as default .xsession when creating a new user...[/QUOTE]

Thank you, djib,

In other words, if another user needs this function, we need to put .xsession in each user's home direction.

---

### Post by djib on 2005-11-14
[QUOTE=ubuntutinger]Thank you, djib,

In other words, if another user needs this function, we need to put .xsession in each user's home direction.[/QUOTE]

That is correct.
There may be another way to do it but I don't know.

You are welcome.

---

