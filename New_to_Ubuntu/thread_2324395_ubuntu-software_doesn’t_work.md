---
title: "ubuntu-software doesn’t work"
date: 2016-05-13
forum: New to Ubuntu
---

### Post by cristiano4 on 2016-05-13
Hello everybody!

I installed from zero the last LTS version 16 from Ubuntu.
For some reason when I try to open the ubuntu-software, nothing happen! just don't open.

When I try to open via terminal, please see the error:

```
cbarros@cbarros-pc:~$ sudo ubuntu-software
[sudo] password for cbarros: 

(ubuntu-software:6884):  Gs-WARNING **: failed to open plugin  /usr/lib/gs-plugins-9/libgs_plugin_xdg_app_reviews.so:  /usr/lib/gs-plugins-9/libgs_plugin_xdg_app_reviews.so: cannot open  shared object file: No such file or directory
```



Can you please help me to sort out this bug.

---

### Post by DuckHook on 2016-05-13
Ubuntu software no longer ships. It has been replaced with gnome-software (I believe). Do *not* invoke it with *sudo*. Don't invoke *anything* with *sudo* unless you know exactly what you are trying to do with it.

---

### Post by mc4man on 2016-05-13
ubuntu-software is Ubuntu's 'frontend' to gnome-software so the command _Without_ sudo should work. 
Or just open the Dash > search software.

What you posted from the terminal is not an error,  just a Warning that anyone opening ubuntu-software from a terminal would see, it's basically meaningless to the user.
If it continues to fail to open then check for home folder & it's contents for root owned files/folders, should either return nothing or if files/folders have root in their name you should be the owner for all
```
ls -lA -R |grep root
```

---

### Post by cristiano4 on 2016-05-13
I've tried to open with my regular user (_Without_ sudo) and the problem persist.

---

### Post by grahammechanical on 2016-05-13
The error message is irrelevant. I can open Ubuntu Software both by clicking its icon and by typing that command (without sudo) in the terminal. I get the same error message.

> (ubuntu-software:6182): Gs-WARNING **: failed to open plugin /usr/lib/gs-plugins-9/libgs_plugin_xdg_app_reviews.so: /usr/lib/gs-plugins-9/libgs_plugin_xdg_app_reviews.so: cannot open shared object file: No such file or directory

And there is nothing wrong with Ubuntu Software on my installation. Apart from remove/purge of Ubuntu Software and then install again, I can think of nothing else 
to add.

Regards

---

### Post by DuckHook on 2016-05-13
Since this is a new install, and you presumably have no data on it yet, perhaps the best course at this point is to just reinstall. However, this time, make sure that the DVD image is not corrupted. If you downloaded by torrent, error checking should already be done. If by repository, then follow [this]("https://help.ubuntu.com/community/HowToMD5SUM") guide for md5sum instructions.

---

### Post by mc4man on 2016-05-14
> **cristiano4 said:**
> I've tried to open with my regular user (_Without_ sudo) and the problem persist.

And what about the state of your $HOME directory?

---

### Post by cristiano4 on 2016-05-15
Hey guys,
I can't believe the best course at this point is to just reinstall... I can't imagine if happen something like this with Linux we should reinstall all the system.

Please if someone has some idea... to fix it, share with us. I'm also using the old version of ubuntu software center while the official is out.

---

### Post by DuckHook on 2016-05-15
Part of the difficulty is that, so far, you've given us no real information or feedback. Did you look after the items that mc4man asked you to? If so, what were the results? We cannot reproduce your problem and it is impossible for us to physically look into your system. Therefore, you must diagnose the problem and provide us with data. For example, what do your logs say?

Last, but not least, a re-install is not that big a deal and is often the best solution, especially on a virgin install. On my system, it takes about 30 minutes. You've probably already spent far more than that amount of time trying to chase down this problem. It also gives you the chance this time to check the integrity of your ISO image. I gave you the instructions to check md5sum. Did you do so the first time? What was the result?

We are happy to continue working with you on this problem if that is what you want. Sometimes, tracking a problem down is a good learning exercise. But if you want us to help you effectively, please read the link in my signature about how to ask for help.

---

### Post by RobGoss on 2016-05-15
> [COLOR=#000000]I can't believe the best course at this point is to just reinstall... I can't imagine if happen something like this with Linux we should reinstall all the system.[/COLOR]

I think** DuckHook** has a good point when he advised you to **reinstall Ubuntu** if you just setup your installation then you really don't have much to worry about loosing any data

Sometimes trying to figure a problem with your system can linger for days there have been moments were I keep a USB stick with each ISO file just in case I have to reinstall any of my operating systems. You will find that doing a reinstall from time to time can save you a lot of time and headaches and in most cases will surprise you and  fix major problems

It's also a good thing to always keep your important data backup for safe keeping

---

### Post by RobGoss on 2016-05-15
Hello and welcome to the forum, It's always good to share what the specs are for the machine is question this is the only way anyone can pin point your problems

How did you install Ubuntu USB or DVD?

Sometimes it makes a world of difference what method was used to install a Ubuntu distribution

---

### Post by tbl0605 on 2016-05-29
In my case this helped:
```
mv "$HOME/.config" "$HOME/.config.old"
mv "$HOME/.local" "$HOME/.local.old"
```

ubuntu-software and gnome-software store some data in your profile, in my case /home was on another partition than / and /home was not wiped when installing the newest version of Ubuntu.

---

### Post by The Cog on 2016-05-31
I'm not sure, but this may be linked to an issue last week with a hang when doing apt-get update. Something called appstreamcli was getting stuck in a loop at the end of the update and I gather this was the process that updates the software centre database. In which case, I guess they've fixed it and another update through the Software Updater might cure it.

Just guessing.

---

