---
title: "logging in as root"
date: 2011-08-14
forum: Recurring Discussions
---

### Post by p3aul on 2011-08-14
Why can't I login as root? I googled and found the command su When I type su - in the terminal, like it said, I am prompted for the password which I then supply, expecting the command prompt to change to a #. instead I get this:
```
p3aul@p3aul-Aspire-X3910:~$ su -
Password: 
su: Authentication failure
p3aul@p3aul-Aspire-X3910:~$
```Now this is the password I supplied when I installed Ubuntu and works when I need to type sudo. I thought my root username was p3aul and my password was the one I was asked to supply when I installed U. I was only asked once, so I've no idea what the systems wants. Should I just reinstall U? Please tell me the steps I need to take to be sure what my root username and password are.

Thanks,
Paul

---

### Post by haqking on 2011-08-14
> **p3aul said:**
> Why can't I login as root? I googled and found the command su When I type su - in the terminal, like it said, I am prompted for the password which I then supply, expecting the command prompt to change to a #. instead I get this:
```
p3aul@p3aul-Aspire-X3910:~$ su -
Password: 
su: Authentication failure
p3aul@p3aul-Aspire-X3910:~$
```Now this is the password I supplied when I installed Ubuntu and works when I need to type sudo. I thought my root username was p3aul and my password was the one I was asked to supply when I installed U. I was only asked once, so I've no idea what the systems wants. Should I just reinstall U? Please tell me the steps I need to take to be sure what my root username and password are.

Thanks,
Paul


read this thread.

[http://ubuntuforums.org/showthread.php?t=1824766](http://ubuntuforums.org/showthread.php?t=1824766)

In ubuntu we use Sudo for elevated priveleges

also make sure you read this [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Root is disabled by default and should stay that way for most purposes.

also read here [http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by p3aul on 2011-08-14
Well! I have read all your links and I mus tsay I have never heard of a forum dedicated to keeping people in the dark about an OS. Ubuntu and Linux are supposed to be free and open-sourced. What gives you the gall to restrict how a person uses it?! I see you have gone to the point in one thread to delete a user's post  who wrote how to login as root. I only found out that's what you did by reading another post in the same thread. By your keeping this information from everyone you violate even the spirit of the internet. What's so free and open source about ubuntu?

Paul

---

### Post by aysiu on 2011-08-14
> **p3aul said:**
> Well! I have read all your links and I mus tsay I have never heard of a forum dedicated to keeping people in the dark about an OS. Ubuntu and Linux are supposed to be free and open-sourced. What gives you the gall to restrict how a person uses it?!
You misunderstand. There's no restriction.

The root account is disabled for direct login in Ubuntu by default, but there is also no need to log into the root account directly.

You can get a persistent root prompt with the command ```
sudo -i
``` (authenticate with your user password).

If you need a root file browser, use the command ```
gksudo nautilus
``` > I see you have gone to the point in one thread to delete a user's post  who wrote how to login as root. The reason why is explained in [this link you claim to have read](http://ubuntuforums.org/showthread.php?t=1486138). > I only found out that's what you did by reading another post in the same thread. By your keeping this information from everyone you violate even the spirit of the internet. Well, actually, no. Read the link. "Read" doesn't mean click on it and pass your eyes over it. It means actually understanding what is written. > What's so free and open source about ubuntu? Well, it doesn't cost you any money, and you are free to modify the source code as you see fit. That's how it free and open source. You can actually even create a root login if you want. We just aren't going to tell you *on the forums* how to do it. It is also, as I mentioned before, *wholly unnecessary*, since you can get a root login without enabling the root account.

---

### Post by WyleECoyote on 2011-08-14
[http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html](http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html)

there is very little difference between the 2 and I definitely advise against running gnome with root access it causes way too many problems that you may not see right away which is also the reason for having gksudo and whatever the kde version of graphical sudo is.

Personally I NEVER use su because it is no more powerful or convenient than sudo or gksudo

---

### Post by p3aul on 2011-08-14
Well personaly I don't want to start a flame war but I reject all you accusations as unfounded and a deliberate attempt to sidestep the issue. It's your forum, you can do what you want but if there is a way to contact somebody other than webmaster on the Ubuntu site I'll find out if they approve of your withholding this information. Failing that I will find out how other distros of linux feel about the issue of revealing how to loggin as root and swithch to that distro.

---

### Post by haqking on 2011-08-14
> **p3aul said:**
> Well! I have read all your links and I mus tsay I have never heard of a forum dedicated to keeping people in the dark about an OS. Ubuntu and Linux are supposed to be free and open-sourced. What gives you the gall to restrict how a person uses it?! I see you have gone to the point in one thread to delete a user's post  who wrote how to login as root. I only found out that's what you did by reading another post in the same thread. By your keeping this information from everyone you violate even the spirit of the internet. What's so free and open source about ubuntu?

Paul

I did not restricct anything or remove anyones post, i am not a moderator.

In my post to you i was merely pointing out how it is with root.

It is disabled by default in the security model.

You can enable it if you wish, however under the forum guidelines we do not supply that information.  So i provided you with links which answer your questions.

and open source means the source code is available for modification and distribution under the GNU GPL

---

### Post by haqking on 2011-08-14
> **p3aul said:**
> Well personaly I don't want to start a flame war but I reject all you accusations as unfounded and a deliberate attempt to sidestep the issue. It's your forum, you can do what you want but if there is a way to contact somebody other than webmaster on the Ubuntu site I'll find out if they approve of your withholding this information. Failing that I will find out how other distros of linux feel about the issue of revealing how to loggin as root and swithch to that distro.

what accusations.

I think you are misunderstanding.

The Root account is disabled by default in Ubuntu as a security measure.

You can enable it if you wish, however due to forum guidelines (which by the way are nothin to do with me, i am merely  a member here offering you help) we are not to show how to enable root account as you have seen when done so the threads get closed or modified.
 Read all the links supplied especially the ROOTSUDO documentaion and you will be able to do everything  you need.

---

### Post by Sef on 2011-08-14
Locked to avoid inflammatory responses.

Also question has been answered.

---

