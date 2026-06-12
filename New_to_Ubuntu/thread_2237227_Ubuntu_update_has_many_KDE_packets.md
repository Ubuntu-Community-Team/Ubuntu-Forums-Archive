---
title: "Ubuntu update has many KDE packets"
date: 2014-07-31
forum: New to Ubuntu
---

### Post by Gnusboy on 2014-07-31
Hello

I update Ubuntu and Firefox whenever I get notifications. Today the update package shows 33 security updates and 7 recommended updates to install.
Most of these files are for KDE and I only use Ubuntu. My best that Ubuntu shares KDE files, but why would I need so many updates at once?
It's kind of weird.
Does anyone have an explanation?

Thanks

---

### Post by Bashing-om on 2014-07-31
Gnusboy; Well, Like this;

KDE (Kubuntu) is built with different engines than that of ubuntu. When you installed a KDE application it pulls in the required libraries to support that application. Those libraries ( and files) require maintenance and updates too.

[INDENT][INDENT]to the best of my thoughts
[/INDENT][/INDENT]

---

### Post by Gnusboy on 2014-08-01
But, that's my problem - I never installed KDE. Ubuntu is the ONLY OS I ever installed.

Ubuntu is the ONLY OS I have ever used
.

---

### Post by mcduck on 2014-08-01
it's not a question of if you use KDE or not, it's a question of if you have* any installed application* that uses any of those components. Pretty much any Qt-based application, for example, might also use some KDE library.

Also keep in mind that not everything with "KDE" in it's name is actually an integral part of KDE desktop and not useful for anything else, just like many Gnome packages are used by other GTK-based applications and desktop environments.

...and finally, you will never get an update for something you don't actually have installed, so if you get an update for KDE package, that means you must already have older version of the same package on your system.

---

### Post by Gnusboy on 2014-08-01
I cut my previous message too soon. Sorry


Is there a problem if my machine has some small pieces of KDE, 
and the complete version of Ubuntu installed? Will that create any conflict?

Can I install a newer version of Ubuntu and get rid of all the KDE stuff, or do I have to wipe the drive?

How about if I go through all of the updates listed and do not install anything not labeled for Ubuntu?

Sorry I'm asking so many questions, but I need to know this stuff to make me better understand and learn.

Thank you.

---

### Post by Bashing-om on 2014-08-01
Gnusboy; Hi !

I will try, I am sure mcduck can do better, but, here is mine.
> 

Is there a problem if my machine has some small pieces of KDE, 
and the complete version of Ubuntu installed? Will that create any conflict?

No ! No conflict as that is the function of the package manager.

> 
Can I install a newer version of Ubuntu and get rid of all the KDE stuff, or do I have to wipe the drive?

Either option will do; If in the install process you choose " erase disk and install ubuntu"; it will, it will !

> 
How about if I go through all of the updates listed and do not install anything not labeled for Ubuntu?

Nope, not a good thing to go behind what the package manager is managing // Remove the application // While that ability does exist, do not without a good reason and knowing why and what the consequences will be //.

> 
Sorry I'm asking so many questions, but I need to know this stuff to make me better understand and learn.


Hey, responding to a valid question(s) is what we do ! .. We have a mandate to "teach" -> here, there is no such thing as a dumb question. But the onus is on you to think, search the forum for the background info and - Google, duckduckgo are your friends; ask !

[INDENT][INDENT]this is open source
[INDENT][INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mcduck on 2014-08-01
> **Gnusboy said:**
> I cut my previous message too soon. Sorry


Is there a problem if my machine has some small pieces of KDE, 
and the complete version of Ubuntu installed? Will that create any conflict?

Not a problem at all, mixing applications from different desktop environments is just fine. And keep in mind that all the Ubuntu variants are, in the end, one and the same operating system, no matter what came installed by default with the install disc you used. You can freely mix and match any applications, desktop environments and other things that are available in Ubuntu's repositories. You can install Ubuntu with the default desktop, add KDE, remove both Gnome and KDE and replace them desktops with XFCE, and mix programs from all of them if you want without any conflicts.

> **Gnusboy said:**
> 
Can I install a newer version of Ubuntu and get rid of all the KDE stuff, or do I have to wipe the drive?

If you really want to get rid of them, the correct way would be just finding out what program you have installed that came with those packages. Uninstalling the program in question would allow you to remove the KDE packages it uses as well. Simply upgrading to new Ubuntu version would behave just like updates, upgrading all the packages you have on your computer, including the KDE ones.
> **Gnusboy said:**
> 
How about if I go through all of the updates listed and do not install anything not labeled for Ubuntu?

If you have them installed, you should definitely update them. Especially if the updates are security updates. Or find out what application is using those packages and uninstall it.

> **Gnusboy said:**
> 
Sorry I'm asking so many questions, but I need to know this stuff to make me better understand and learn.

Thank you.
No worries, it's better to ask questions than to break something or feel unsure about what's going on with your computer....


------
Edit: If you want to check what application might have brought the KDE packages with it, you can use Synaptic Package Manager, or if you prefer the "apt-cache showpkg *packagename*" command in a terminal.

For example, I just checked the info abut one of the packages that I currently have in updates. The "Reverse Depends"-section tells you what other packages depend on this one:
```

mcduck@Hyperion:~$ apt-cache showpkg libnautilus-extension1a 
Package: libnautilus-extension1a
Versions: 
1:3.10.1-0ubuntu9.3 (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_main_binary-amd64_Packages
                  MD5: 24d74241fbd9274f58339c68e65e6d46
 Description Language: en
                 File: /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en
                  MD5: 24d74241fbd9274f58339c68e65e6d46

1:3.10.1-0ubuntu9.2 (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_main_binary-amd64_Packages
                  MD5: 24d74241fbd9274f58339c68e65e6d46
 Description Language: en
                 File: /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en
                  MD5: 24d74241fbd9274f58339c68e65e6d46

1:3.10.1-0ubuntu8 (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_main_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_main_binary-amd64_Packages
                  MD5: 24d74241fbd9274f58339c68e65e6d46
 Description Language: en
                 File: /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en
                  MD5: 24d74241fbd9274f58339c68e65e6d46


Reverse Depends: 
  nautilus,libnautilus-extension1a 1:2.91
  nautilus-columns,libnautilus-extension1a
  libnautilus-extension1a:i386,libnautilus-extension1a
  tracker-gui,libnautilus-extension1a 1:2.91
  nautilus,libnautilus-extension1a 1:2.91
  libnautilus-extension-dev,libnautilus-extension1a 1:3.10.1-0ubuntu9.3
  gir1.2-nautilus-3.0,libnautilus-extension1a 1:2.91
  file-roller,libnautilus-extension1a 1:2.91
  evince,libnautilus-extension1a 1:2.91
  libnautilus-extension1a:i386,libnautilus-extension1a
  nautilus-dropbox,libnautilus-extension1a 1:2.91
  tracker-gui,libnautilus-extension1a 1:2.91
  seahorse-nautilus,libnautilus-extension1a 1:2.91
  python-nautilus,libnautilus-extension1a 1:2.91
  nautilus-wipe,libnautilus-extension1a 1:2.91
  nautilus-open-terminal,libnautilus-extension1a 1:2.91
  nautilus-image-converter,libnautilus-extension1a 1:2.91
  nautilus-ideviceinfo,libnautilus-extension1a 1:2.91
  nautilus-gtkhash,libnautilus-extension1a 1:2.91
  nautilus-filename-repairer,libnautilus-extension1a 1:2.91
  nautilus-actions,libnautilus-extension1a 1:2.91
  gnome-mplayer,libnautilus-extension1a 1:2.91
  gnome-hwp-support,libnautilus-extension1a 1:2.91
  eiciel,libnautilus-extension1a 1:2.91
  totem,libnautilus-extension1a 1:2.91
  nautilus-share,libnautilus-extension1a 1:2.91
  nautilus,libnautilus-extension1a 1:2.91
  libnautilus-extension-dev,libnautilus-extension1a 1:3.10.1-0ubuntu8
  gir1.2-nautilus-3.0,libnautilus-extension1a 1:2.91
  file-roller,libnautilus-extension1a 1:2.91
  evince,libnautilus-extension1a 1:2.91
  deja-dup,libnautilus-extension1a 1:2.91
  brasero,libnautilus-extension1a 1:2.91
Dependencies: 
1:3.10.1-0ubuntu9.3 - libc6 (2 2.2.5) libglib2.0-0 (2 2.37.3) libgtk-3-0 (2 3.0.0) nautilus (3 1:3.0) nautilus:i386 (3 1:3.0) libnautilus-extension1 (0 (null)) libnautilus-extension1:i386 (0 (null)) libnautilus-extension1a:i386 (0 (null)) 
1:3.10.1-0ubuntu9.2 - libc6 (2 2.2.5) libglib2.0-0 (2 2.37.3) libgtk-3-0 (2 3.0.0) nautilus (3 1:3.0) nautilus:i386 (3 1:3.0) libnautilus-extension1 (0 (null)) libnautilus-extension1:i386 (0 (null)) libnautilus-extension1a:i386 (0 (null)) 
1:3.10.1-0ubuntu8 - libc6 (2 2.2.5) libglib2.0-0 (2 2.37.3) libgtk-3-0 (2 3.0.0) nautilus (3 1:3.0) nautilus:i386 (3 1:3.0) libnautilus-extension1 (0 (null)) libnautilus-extension1:i386 (0 (null)) libnautilus-extension1a:i386 (0 (null)) 
Provides: 
1:3.10.1-0ubuntu9.3 - 
1:3.10.1-0ubuntu9.2 - 
1:3.10.1-0ubuntu8 - 
Reverse Provides: 

```

---

### Post by Rob Sayer on 2014-08-02
I really wouldn't worry too much about having a bunch of KDE stuff on there.  I actually don't like the idea of having multiple DE's installed (though I have done it) but I don't believe that having KDE programs on a GTK based DE version like the other 3 official ubuntu DEs is a problem.  They use different libraries (Qt v. GTK) so there's not so much of a chance of conflicts.

My xubuntu 14.04 running laptop has Dolphin installed because I just don't want to use any other file manager.  It's great.  And it also loaded a lot of KDE dependencies in the process.  This is not surprising because KDE is a highly integrated DE.  But it doesn't run anything it doesn't need to run Dolphin.

I've done this for some time now and have never had any problem with it.  I'm mostly a Kubuntu user but not on my netbook because of its limited RAM.  But I'm a big fan of KDE apps.

---

### Post by The Cog on 2014-08-02
I agree with Rob Sayer. It's probably not worth worrying about. So an application you have installed requires a lot of KDE libraries: that doesn't make it a bad app. In a number of cases, a KDE app is the best of all the Linux equivalents, although people can always argue about which app is best. 

If it really bothers you for some reason, you can install synaptic which is a detailed package manager, ask it to uninstall a lot of those KDE packages, and then see what else it says you have to uninstall because they depend on the packages you said to remove. Then you can choose whether to remove them all, or cancel.

---

### Post by Gnusboy on 2014-08-05
Wow! Y'all are great and this gnumb gnut begins to understand. Thank you all.

---

