---
title: "Best Remote Access Software?"
date: 2018-07-29
forum: New to Ubuntu
---

### Post by Taylz on 2018-07-29
Hi all,

I have two laptops that are both running Xubuntu 18.04.1 and ones my work horse, the other being my entertainment laptop. Is there some Linux/Ubuntu specific software that acts/does the same as VNC on Windows? What would you recommend for me to be able to control my entertainment laptop via my work horse laptop? 

Any help would be greatly appreciated (and if you can dumb it down a lot for me that'd be great as I'm just getting to grips with the basics on this distro haha).

Regards,

Tayl.

---

### Post by Autodave on 2018-07-29
Linux specific?  I am sure there are many, but I personally like Teamviewer. Very easy to install and run.

---

### Post by Taylz on 2018-07-29
> **Autodave said:**
> Linux specific?  I am sure there are many, but I personally like Teamviewer. Very easy to install and run.

Hi Autodave,

I take it this isn't something you can install via the software centre? As I can't seem to find it in there.

Regards,

Tayl.

---

### Post by monkeybrain20122 on 2018-07-29
I heard nomachine is good. [https://www.nomachine.com/](https://www.nomachine.com/)

We are planning to test it out at the work machines.

---

### Post by Taylz on 2018-07-29
> **monkeybrain20122 said:**
> I heard nomachine is good. [https://www.nomachine.com/](https://www.nomachine.com/)

We are planning to test it out at the work machines.

Hey monkeybrain,

How do you install software like that outside of the software center? Literally just click and install via the website links?

Regards,

Tayl.

---

### Post by Autodave on 2018-07-29
I use *gdebi *to install software like that. Gdebi is in the repos. As for Teamviewer, get it at [www.teamviewer.com](www.teamviewer.com). You want to get the .deb file: either 32 or 64 bit depending on what you are running.

.deb files are the easiest to install into Linux, and gdebi will install all of the dependencies automatically for you.

---

### Post by HermanAB on 2018-07-30
Hmm, ex-Windows users usually want to remote the whole kit and caboodle to another machine, while neckbeard UNIX users only remote execute the specific applications they want to run.  

It is mostly pointless to remote execute a desktop system, since the local machine presumably already has a working desktop, so it is not usually useful to overwrite the local desktop with a slower remote desktop, unless the point of the exercise is to debug/support a remote desktop system for a remote user.

Remoting single applications over SSH is more efficient and it allows you to easily run multiple programs on multiple remote machines at the same time, something that you cannot do with the whole kit and caboodle approach.

---

### Post by mastablasta on 2018-07-31
+1 on the SSH:

[https://help.ubuntu.com/lts/serverguide/openssh-server.html.en](https://help.ubuntu.com/lts/serverguide/openssh-server.html.en)

one of the many usefull Digital ocean guides:
[https://www.digitalocean.com/community/tutorials/how-to-use-ssh-to-connect-to-a-remote-server-in-ubuntu](https://www.digitalocean.com/community/tutorials/how-to-use-ssh-to-connect-to-a-remote-server-in-ubuntu)

desktop is a server and server can be a desktop (if you add graphic desktop components on it)

---

