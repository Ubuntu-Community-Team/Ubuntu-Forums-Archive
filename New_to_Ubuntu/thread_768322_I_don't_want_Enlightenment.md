---
title: "I don't want Enlightenment"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Kymeia on 2008-04-26
I just updated last night and rebooted this morning to finish it and its started with something called Enlightenment and I can't find anything and it's ugly and seems to have a manual the size of a bible to read to get to know it. Also, unlike in 7.10 it's not automatically detected my graphics card so I'm stuck in low graphics mode and I can't even find the legacy drivers applet to change to my graphics card (an old NVidia)- 7.10 did this flawlessly. How do I get back to my normal desktop?

---

### Post by Gulyan on 2008-04-26
you should try a clean install

---

### Post by Kymeia on 2008-04-26
How do I do that? I just installed using the updater and it's a mess now. I'd rather uninstall it and go back to 7.10 but how do I do that? Isn't there a way to turn off Enlightenment? It's annoying - menus slide out of my way when I click on something and I don't know where anything is. Terrible ergonomics - whoever designed it is crazy if they think it's in any way user friendly.

---

### Post by Kymeia on 2008-04-26
Plus it seems my internet is disabled too!! I can't seem to run Firestarter to unblock stuff.

---

### Post by Kymeia on 2008-04-26
The menu's don't even work half the time - I click on something and nothing happens. This is a really useless piece of junk.

---

### Post by marquee moon on 2008-04-26
click on the 'off' button, then chose 'log-out', this'll take you to the login screen. Then 'options' > 'select session' then click on 'run x-client'* or* 'gnome' then log back in. 

The safest way to do a clean install is to make some space on your hard disk using gnome partion manager on the live CD. Then install onto that free, unformated space  (I re-size or delete partitions to create the empty space, then use the 'guided: install onto the largest free space' option during the installation process) . Then you'll have your existing install and the new 8.04 clean installation. Then transfere over your personal files, then format your old installation.

---

### Post by _oOMOo_ on 2008-04-26
enlightenment is NOT installed by default. You can choose GNOME at login - before you enter your username and password choose session > GNOME

---

### Post by Kymeia on 2008-04-26
Thanks - the X option just took me into Enlightenment again but the Gnome one works - it's easier to use but still looks weird compared to how 7.10 looked and I still can't seem to run half the stuff I click on and can't get internet access or even check the firewall. Plus I can't find the restricted drivers applet so I can get out of 800x600

---

### Post by Kymeia on 2008-04-26
> **_oOMOo_ said:**
> enlightenment is NOT installed by default.

Well it was - I didn't select it on purpose.

---

### Post by marquee moon on 2008-04-26
it may be a remnant from some previous tweaking you've been doing- have you tried to install enlightenment (e-17) previously? 

If its still not right, go for a clean install like I described above.

---

### Post by _oOMOo_ on 2008-04-26
Were you using KDE (Kubuntu) before? Is there a KDE option as well as a GNOME and enlightenment one?

The upgrade process doesn't remove (m)any packages, it just upgrades them, so a clean install may be a safer option as marquee moon suggests.

Hardy has introduced a lot of changes and in my experience a clean install just works better than an upgrade.

---

### Post by Kymeia on 2008-04-26
How do I do that? Do I need to reformat?

---

### Post by nhandler on 2008-04-26
You can either do a clean install on a separate partition. That will leave you with your current Ubuntu installation, as well as a fresh installation. The other option is to install the new installation over your current one. This will delete all of your programs, data, and files. If your /home is on its own partition, you can keep all of your settings and documents (even after a fresh install). Just be sure that the installer is set NOT to format that partition. If you don't have a separate /home partition, you will have to back up your documents to an external hd/flash drive/cd/other computer if you want to preserve them.

---

### Post by _oOMOo_ on 2008-04-26
If you back up your entire home folder including the hidden files and folders (all those starting with a . - press Ctrl h to see them in the file manager Nautilus) then your settings will be saved - but it sounds like you're not terribly impressed with your default settings anyway, so you could just back up all your important files.

You will need to reformat at least one partition, but you get the choice to do that as you install with the cd. You need to choose "manual" when you get to the partition manager bit, and select the partition that contains your existing install to contain the new installation.

There are ways to make reinstalling considerably more painless, one of which is to create a separate "/home" partition, which may be something to consider. That way you don't need to fudge about backing up all your files before reinstalling.

---

### Post by Kymeia on 2008-04-26
When I first installed I made 2 partitions - one for downloads, media, files etc and one for the Ubuntu system - would that be a "home" partition?

---

### Post by _oOMOo_ on 2008-04-26
> **Kymeia said:**
> When I first installed I made 2 partitions - one for downloads, media, files etc and one for the Ubuntu system - would that be a "home" partition?

You could use it as your home partition, but I seem to remember it can't be a FAT32 partition. You can choose it as /home using the manual option in the installer, and (obviously) choose not to format it. It should then create a fresh home directory in that partition called your choice of username.

---

### Post by marquee moon on 2008-04-26
Your "downloads & media files" partition will not be your 'home' by default. This is just where you've decided to put stuff you want to keep. You need to do some cleaver stuff to create a 'home' on another partition (there's a 'how-to' in the tips & tricks forum)

Your 'home', by default, sits off the root dirrectory (ie, the full address for it is /home, where '/' is the root of the file system). In your file manager, there's a file icon with your name on- this is your personal space within the 'home' directory. Inside that file are the 'documents', 'pictures', and 'music' files that you may have saved data to. This is probably were a lot of your personal files are. Go through all these files and grab your personal documents.   Make sure these are backed up (onto your download & media partition, for example..) before doing anything.

---

### Post by steveneddy on 2008-04-26
> 
I don't want Enlightenment


I don't blame you.

---

### Post by rajeev1204 on 2008-04-26
> **steveneddy said:**
> I don't blame you.

:D

---

