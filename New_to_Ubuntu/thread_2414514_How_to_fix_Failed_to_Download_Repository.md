---
title: "How to fix Failed to Download Repository?"
date: 2019-03-11
forum: New to Ubuntu
---

### Post by dec56 on 2019-03-11
I am also getting a " failed to download repository information"  when I do a update software what is this and what do I need to do? Thanks again..

---

### Post by CatKiller on 2019-03-11
> **dec56 said:**
> I am also getting a " failed to download repository information"  when I do a update software what is this and what do I need to do? Thanks again..

It's exactly what it says: the package manager can't download the information about the software repository. It could be a temporary Internet connection thing, or whichever repository server you've selected could be down, or it could be that your software sources aren't configured properly in some fashion.

More information about the message and which software sources you're using would help.

---

### Post by dec56 on 2019-03-11
It does say to check internet connection, when I do it is connected. I am using Opera as my browser. Not sure what I am doing wrong or what software you are asking about?

---

### Post by dec56 on 2019-03-11
[IMG]https://ubuntuforums.org/asset.php?fid=277147&uid=2120304&d=1552336589[/IMG]

---

### Post by oldrocker99 on 2019-03-11
That message is saying that the selected repository is offline. Select "Software and Updates." Then, on the first tab, look for "Download from:" then open the drop-down menu. Select "Other," and then "Select Best Server." It will ping all the Ubuntu servers (and there are a **LOT**) of them), and select the one that has the lowest ping (time it takes for a server to respond), and then, set that server.

Sorry you have hit this snag early on, but there is NO STUPID QUESTION. Everybody here is trying to help the best they can. The Linux community is Yet Another Great Thing about Linux.

Everybody here was a total n00b when they started, so don't be shy with questions. However, search for the topic here, because the solution may have been found by somebody else, so you don't always need to open a new thread.

You made an excellent decision when you installed Ubuntu, and you're embarking on a great adventure.

---

### Post by DuckHook on 2019-03-11
> **dec56 said:**
> I am also getting a " failed to download repository information"  when I do a update software what is this and what do I need to do? Thanks again..
Please ask new questions by starting new threads. Conflating two questions on one thread confuses those trying to help and those visiting the forums for solutions. I have split your question and the posts that were generated into a new thread with a separate title.

---

### Post by dec56 on 2019-03-11
Thank you all, and sorry about the double thread. I did what oldrocker99 said and now I get this message.

---

### Post by mtodorov69 on 2019-03-12
> **dec56 said:**
> Thank you all, and sorry about the double thread. I did what oldrocker99 said and now I get this message.

Can you open a text terminal and post the contents of your > cat /etc/apt/sources.list ?

---

### Post by oldrocker99 on 2019-03-12
The picture shows that the PPA is simply the Launchpad main URL, not a specific PPA. You'll need to delete it or use # to nullify the address. 

If you use this, if you're being careful, you can try this:```
sudo nano /etc/apt/sources.list
``` Put # before this line: (url]http://ppa.launchpad.net[/url].

TheL commands in nano are on the border of the window, and they're not standard; saving is not CTRL-S, but CTRL-W (for Write Out).

---

### Post by dec56 on 2019-03-12
I hope this helps, starting to get discouraged.

---

### Post by bsautner on 2019-03-12
can you try the following commands: 

```

sudo dpkg --configure -a
sudo apt-get update && sudo apt-get upgrade -y
sudo apt-get install -f

```

post any errors you get from running those commands

---

### Post by dec56 on 2019-03-12
Looks like a few.

---

### Post by oldos2er on 2019-03-12
dec56, please copy and paste the terminal text output into your posts rather than posting an image. It is much easier for others to read, and you can include all the output rather than just a portion of it.
Thanks.

---

### Post by deadflowr on 2019-03-12
You need to at least (based on the output form the last image) remove the muravjov-il ppa
```
sudo add-apt-repository --remove ppa:muravjov-il/ppa
sudo apt-get update
```
That ppa has not been updated in over 200 weeks, well longer than 18.04 has existed.
(Meaning there is no way any version is available for 18.04)

---

### Post by mtodorov69 on 2019-03-12
You haven't posted entire sources.list, but only the visible top lines :-(
As your sources.list outgrows the screenshot, it may be better if you COPY+PASTE the [B]file's text.
From the posted lines I don't see what is causing your problem, but you have posted a screenful of file only, not the entire sources.list .[/B]

Here's the content of my /etc/apt/sources.list :

Note that **hr** stands for the **Republic of Croatia (or Hrvatska)** and you may need to replace this with your country's TLD code:

```
root@efk:~# cat /etc/apt/sources.list
#

# deb cdrom:[Ubuntu-Server 18.04.1 LTS _Bionic Beaver_ - Release amd64 (20180725)]/ bionic main restricted

# deb cdrom:[Ubuntu-Server 18.04.1 LTS _Bionic Beaver_ - Release amd64 (20180725)]/ bionic main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://hr.archive.ubuntu.com/ubuntu/ bionic main restricted
# deb-src http://hr.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://hr.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
# deb-src http://hr.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://hr.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://hr.archive.ubuntu.com/ubuntu/ bionic universe
deb http://hr.archive.ubuntu.com/ubuntu/ bionic-updates universe
# deb-src http://hr.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://hr.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://hr.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://hr.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
# deb-src http://hr.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://hr.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src http://hr.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner

deb http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
root@efk:~#

```

---

### Post by dec56 on 2019-03-12
Well I solved the problem!! I took the easy way out, I uninstalled Ubuntu and then reinstalled it. Working fine now. I do want to Thank you all for all the help, us newbees need a lot of it sometimes. I like the fact that this forum exists and everyone is so helpful you don't see this in windows. Well again Thanks and if or when I need more help I know where to come!!             :p:p

---

### Post by mtodorov69 on 2019-03-13
Glad to hear your solution worked for you. I hope you did not lose any important data.

---

### Post by bsautner on 2019-03-13
great, when all else fails rebuild :)

It looks like you were close to being fixed, so if someone else has this problem and finds this thread, it looks like you just needed to run 

```

sudo apt-get autoremove
sudo apt-get dist-upgrade
sudo apt-get clean

```

---

### Post by mtodorov69 on 2019-03-14
> **bsautner said:**
> great, when all else fails rebuild :)

It looks like you were close to being fixed, so if someone else has this problem and finds this thread, it looks like you just needed to run 

```

sudo apt-get autoremove
sudo apt-get dist-upgrade
sudo apt-get clean

```

There was also a stale reference to a ppa repository which is no longer used, AFAIK.

---

### Post by oldrocker99 on 2019-03-14
@dec56, the good thing is that your problem is no more.

It's good manners to add [SOLVED] in the header of this thread, to help others with your problem.

---

