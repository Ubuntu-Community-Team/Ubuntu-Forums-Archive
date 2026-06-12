---
title: "Converting myself from OpenSuse to Ubuntu"
date: 2017-08-21
forum: New to Ubuntu
---

### Post by johngw on 2017-08-21
I've been using using OpenSuse for the last ten years or so, so I'm pretty familiar with Linux, but now I've got a machine running Ubuntu.

What should I read in order to convert myself on how to use Ubuntu most effectively?

---

### Post by yancek on 2017-08-21
You could start with the Ubuntu Manual at the link below.

[https://ubuntu-manual.org/](https://ubuntu-manual.org/)

---

### Post by vocx on 2017-08-21
> **johngw said:**
> I've been using using OpenSuse for the last ten years or so, so I'm pretty familiar with Linux, but now I've got a machine running Ubuntu.

What should I read in order to convert myself on how to use Ubuntu most effectively?
If you really know Linux, then I don't think you should have a big problem adapting. You just have to be smart and use common sense to realize that not everything will be the same.

I think this question can only be answered well by people who have plenty of experience in both Ubuntu and Suse, so they can mention the major differences. Some people have used Ubuntu a lot, but not Suse, so we actually don't know if our experience is radically different from Suse or not.

If I were to guess, I'd say, learn about the package management. Ubuntu uses repositories, and installs things with "apt". Of course, you can use a graphical interface like "Software center" and "Synaptic", but if you are experienced, you should be using the command line anyway.

Another thing is about the release schedule. Ubuntu releases a new version every 6 months, and releases a long term support (LTS) version every 2 years. So this has an impact on the version of the software, kernel, and drivers that you will find in a particular version. That is, you won't get the newest version of a particular piece of software, but only the version in the repository of that Ubuntu release. This may be a bit disconcerting for those that are used to "rolling distributions" and getting the newest versions of everything.

And finally, I'd inform myself about the personal package archives (PPA). Some people don't want to wait for a new Ubuntu version, and updated packages, so they can set up PPAs in their "/etc/apt/sources.list" so they download the latest version for a particular program.

---

### Post by oldfred on 2017-08-21
I thought one of the big differences was the use of sudo for temporary admin rights rather than having an admin/root user.

 Forum rules on root vs. sudo
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
[http://xkcd.com/149/](http://xkcd.com/149/)
[https://help.ubuntu.com/community/WikiGuide](https://help.ubuntu.com/community/WikiGuide)
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)
sudo is not to be used for GUI applications. current recommended method is
sudo -H # which keeps /home as location of files.

---

### Post by johngw on 2017-08-21
Thanks vocx for the fast reply. From what you say I think I need to get to grips with apt, so I've found the documentation page. Hopefully, since Ubuntu has the reputation of being the easiest distro to learn, pointers like this are all I'll need. :p

---

### Post by johngw on 2017-08-21
And thanks for the links, oldfred. I've seen the xkcd cartoon before. It's one of my favourites (we also have sudo in OpenSuse). I'll have a read through the other ones as well.

---

### Post by vocx on 2017-08-21
> **johngw said:**
> Thanks vocx for the fast reply. From what you say I think I need to get to grips with apt, so I've found the documentation page. Hopefully, since Ubuntu has the reputation of being the easiest distro to learn, pointers like this are all I'll need. :p
Yeah, there is not much to learn really, just a few tasks, "update", "upgrade", "install", "reinstall", "remove", "purge".
```

sudo apt update
sudo apt upgrade
sudo apt install [package]
sudo apt install --reinstall [package]
sudo apt remove [package]
sudo apt purge [package]

```

> **johngw said:**
> And thanks for the links, oldfred. I've seen the xkcd cartoon before. It's one of my favourites (we also have sudo in OpenSuse). I'll have a read through the other ones as well.
Yeah, "sudo" may be important to mention as well. When I tried Suse back in 2007 or so, I think it was normal to have and use a "root" account. I don't know if Ubuntu's use of "sudo" eventually spread to other distributions but I would imagine nowadays many people are familiar with it.

Basically, whenever a guide tells you to use the "root" account, you use "sudo" instead.
```

root@PC:~# apt purge [package]

user@PC:~$ sudo apt purge [package]

```

---

### Post by vasa1 on 2017-08-21
> **vocx said:**
> ...
Basically, whenever a guide tells you to use the "root" account, you use "sudo" instead.
...
+1 several times over.

I've never had to use "root". All a normal user needs is *sudo* or *sudo -H*.

---

### Post by johngw on 2017-08-21
Thanks vox. As I said, sudo is used in OpenSuse as well as root (you have the choice and you don't have to be consistent). I seldom log on as root and then only when I have a real emergency. And then I never use GUIs.

But I do have another problem, in that the PC that I have received will only let me log on as Guest and I do not have a root password. so how would I create an actual user? I've sent an email to supplier, but I thought it might be worth asking here as well.

---

### Post by vocx on 2017-08-21
> **johngw said:**
> Thanks vox. As I said, sudo is used in OpenSuse as well as root (you have the choice and you don't have to be consistent). I seldom log on as root and then only when I have a real emergency. And then I never use GUIs.

That's strange. Having both "root" and "sudo" to do the same seems unnecessary and inconsistent. Well, I hope the Suse guys know what they are doing.

> 
But I do have another problem, in that the PC that I have received will only let me log on as Guest and I do not have a root password. so how would I create an actual user? I've sent an email to supplier, but I thought it might be worth asking here as well.
This is puzzling. Normally when you install Ubuntu, you create only one initial user. This is a regular user who can temporarily gain "root" privileges with "sudo". The password used in "sudo" is the regular user's password. So that initial user is both a regular user, and when is needed, also "root".

When an Ubuntu machine starts, it does give you the option of a guest account, but I think this is only a temporary user that won't be able to change the system in any way. What you mean to say is, currently, with that guest account you cannot use "sudo" for any changes, nor you have a password? This is strange indeed. Definitely contact the vendor of your system. They probably installed the system in a non-standard way. Or maybe they created a user account but did not give you the password that you can use with "sudo".

---

### Post by johngw on 2017-08-21
> **vocx said:**
> That's strange. Having both "root" and "sudo" to do the same seems unnecessary and inconsistent. Well, I hope the Suse guys know what they are doing.

It just gives the user a choice. I recall one bit od sysadmin I had to do (due to an nvidia ****-up) where it would have been hell to do everything prefixed by "sudo". Using "su" would have been more dangerous than using "root". But mostly I use "sudo" (and I think most OpenSuse users do too) because it's more convenient. It's never a problem if there's more than one way to skin a cat, in my experience.

> **vocx said:**
> This is puzzling. Normally when you install Ubuntu, you create only one initial user. This is a regular user who can temporarily gain "root" privileges with "sudo". The password used in "sudo" is the regular user's password. So that initial user is both a regular user, and when is needed, also "root".

When an Ubuntu machine starts, it does give you the option of a guest account, but I think this is only a temporary user that won't be able to change the system in any way. What you mean to say is, currently, with that guest account you cannot use "sudo" for any changes, nor you have a password? This is strange indeed. Definitely contact the vendor of your system. They probably installed the system in a non-standard way. Or maybe they created a user account but did not give you the password that you can use with "sudo".

Thanks for this information. That's what I suspected.

The other solution that occurred to me would be to download the latest version of Ubuntu and try to install that.

---

### Post by Andreyshel on 2017-08-21
> [COLOR=#000000]sudo is used in OpenSuse as well as root (you have the choice and you don't have to be consistent). I[/COLOR]
You can unlock root in ubuntu too if you wish.
just use 
```

sudo passwd root
(system asks you to set password)
sudo passwd -u root 

```
but it is not recommended.> [COLOR=#000000][INDENT]But I do have another problem, in that the PC that I have received will only let me log on as Guest and I do not have a root password. so how would I create an actual user? I've sent an email to supplier, but I thought it might be worth asking here as well.[/INDENT]
[/COLOR][COLOR=#000000]

[/COLOR]



Also you are able to change user account password with r[COLOR=#000000][I]ecovery mode. So if it is your computer follow [this steps]("https://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password")



Apt and Synaptic was already mentioned. Some configuration files can be on other places perhaps. Modern ubuntu versions use systemd. So if you need to restart some daemon try systemctl restart [/I][/COLOR]*<name> *[COLOR=#000000][I] .
It will be no really big changes.
Hope it helps. [/I][/COLOR]

---

### Post by sudodus on 2017-08-21
> **johngw said:**
> The other solution that occurred to me would be to download the latest version of Ubuntu and try to install that.

I think this is a good solution. Often it is easier to install a fresh system than to repair a faulty system.

Maybe you can try the version with the longest time until end of life, 16.04.1 LTS, according to this link,

[How to select the version and flavour of Ubuntu](https://ubuntuforums.org/showthread.php?t=2230389&p=13540865#post13540865)

---

### Post by 1clue on 2017-08-21
Really the main things are what has already been mentioned: Package management and sudo. Both are commercially supported distros with a real help desk, and fit for enterprise use. Suse is aiming more for the desktop in the enterprise, Canonical (the organization controlling Ubuntu) uses Ubuntu as a stable platform for commercial server products they sell, and also for enterprise desktops of course.

If I remember correctly Suse uses KDE desktop? If so then you might choose Kubuntu, which is the fully-supported KDE flavor of Ubuntu.

[I]**PS: **My favorite feature of Ubuntu is what they did with sudo. The changes they made make it so you never need to be root while booted normally. IMO this is a huge benefit to security, as many budding admins tend to leave a terminal opened as root "just in case they need it."

[/I]

---

