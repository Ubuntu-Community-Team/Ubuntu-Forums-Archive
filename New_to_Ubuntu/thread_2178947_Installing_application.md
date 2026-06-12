---
title: "Installing application"
date: 2013-10-05
forum: New to Ubuntu
---

### Post by adithya2 on 2013-10-05
I am new to Ubuntu.I want to install applications(default D: (Ubuntu)/) in other media devices(like E:/F: drive).Is there any possible method to do this.
Thanks and regards in advance.

---

### Post by heir4c on 2013-10-05
You have a Wubi install (Ubuntu IN Windows)?
And why you want to do that?

---

### Post by adithya2 on 2013-10-05
The reason is because I allocated only 4GB of space for the installation of Ubuntu.

---

### Post by heir4c on 2013-10-05
Ooh, that is to small. 20 or 25GB is better. You better install it again after change the size of the partition. Better do that because you have in the future more problems with that.
(Don't forget to make back-ups of your files)

---

### Post by adithya2 on 2013-10-05
Isn't there any other way to solve this problem other than reinstalling the OS.

---

### Post by heir4c on 2013-10-05
I don't know at the moment. I try something but it did not work.
So, I look further tomorrow. Or maybe somebody else will help you.

---

### Post by adithya2 on 2013-10-06
Anyway,thanks a lot.

---

### Post by DuckHook on 2013-10-06
Ubuntu and Linux in general use a different disk-naming convention than Windows. I recommend that you familiarize yourself with it so that future discussions won't lead to confusion and mistakes. In Linux, different physical drives are sda, sdb, sdc... Different partitions within drives are sda1, sda2, sda3...

If you have a WUBI install, the difficulty is that not many people on this forum are well-versed in it, so we are very limited in the sort of help we can provide. Almost all Linux experts install into a physically separate partition so we have no experience with WUBI. In my case, I am very concerned about giving you some instruction that will hose your system.

heir4c is correct: 4GB is very limiting and will quickly fill up. In a non-WUBI installation, it is possible to modify your settings so that apps install somewhere other than the default directories, but this is only recommended for experts who can properly allow for such customizations during upgrades and other system changes. If you don't know what you are doing, then monkeying around with default locations will break Software Center, Update Manager and even some apps themselves that expect to find their settings and configuration files in certain directories only to find them missing.

The best way to "make do" with 4GB is to move your /home directory to another partition. /home is the directory that stores all of your personal info like e-mails, photos, music, etc. and because of this is the one that grows the fastest. The instructions for moving /home in a standard install are [here]("https://help.ubuntu.com/community/Partitioning/Home/Moving"). I have no idea how to do it with a WUBI installation, but I gather that you cannot simply follow the instructions in the link. You should Google for the right method. Or alternatively, you can wait for one of the few WUBI gurus on this forum to help you.

If you do decide to reinstall your OS, I suggest that you give consideration to doing a traditional dual boot rather than WUBI.

---

### Post by heir4c on 2013-10-06
@adithya2: Have you a Wubi install or not? You don't answer that question. That is important. ThanX.

---

### Post by Mark Phelps on 2013-10-06
Ubuntu apps have to be installed to a Linux filesystem -- and "drives" designated with letters are formatted for a Windows filesystem.

So basically, no, you can't install Ubuntu apps to the other "drives".

To see if you have a Wubi installation, look for the file "root.disk" in your Windows partitions.

---

### Post by hakuna_matata on 2013-10-06
In a lot of cases there is no need to increase space for Ubuntu installation. You can store your documents, video files, audio files, ..... on windows drives, too. To see if you need more space, please [use terminal]("https://help.ubuntu.com/community/UsingTheTerminal") and type:
```
df -h
```
e.g.: if first line after header is:
```

/dev/loop0 4G 2G 2G  50% /

```
there is 50% used of your [root file system]("http://en.wikipedia.org/wiki/Root_directory") (/) and if device is /dev/loop0 you'll be running wubi.

---

### Post by adithya2 on 2013-10-09
Yes,I have a Wubi Install.

---

