---
title: "Store packages on a CD"
date: 2005-02-20
forum: Repositories &amp; Backports
---

### Post by Cyhatch on 2005-02-20
Suppose I installed *msttcorefonts* (downloaded from the Internet) using *apt-get*.

Suppose I have to format my HD. After I install Ubuntu, I've got to *download* these packages again.

So, how do I save an already-downloaded package to some .zip (or what) file? Has this something to do with *apt-cache*? Is there life on Mars?

---

### Post by kassetra on 2005-02-20
[QUOTE=Cyhatch]Suppose I installed *msttcorefonts* (downloaded from the Internet) using *apt-get*.
  
  Suppose I have to format my HD. After I install Ubuntu, I've got to *download* these packages again.
  
  So, how do I save an already-downloaded package to some .zip (or what) file? Has this something to do with *apt-cache*? Is there life on Mars?[/QUOTE]
  
  Let's answer the big question first: yes there *was* life on mars, but there hasn't been for ages and ages.  heh.  ;)  
  
  Now for the other stuff that's just not as big as the life on mars question:  ;)
  
 If you are using synaptic, in the Settings->Preferences->Temporary Files tab, you'll see an option "Leave all downloaded packages in the cache" ... 
 
 All of the downloaded packages are saved in /var/cache/apt/archives.
 The packages are in the .deb format (kind of like a zip/exe installer file for linux)...
  
  You can burn all of those .deb files to a cd and have them as backups, should you need them.  :)
  
 apt-cache allows you to work with the files that are in /var/cache/apt/archives -- so you can find out information about what you have downloaded via apt. For more information: [how to use apt-cache]("http://www.ccl.net/cca/software/UNIX/updating-redhat/apt-howto/how-to-use-apt-cache.html").

---

### Post by kori.mendocino on 2005-02-20
i suppose u need to copy your .deb files to a cd, and later on, when you reinstall, to add the cd in the repos.

---

### Post by Cyhatch on 2005-02-20
Great! Thanks.

---

### Post by Mishal on 2006-02-13
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

I went through the above link and found it rather complicated. Rather, if I copy the /var/cache/apt/archives folder to some other place, format my drive, reinstall Linux and then recopy the archives back into /var/cache/apt, won't it work?

---

### Post by az on 2006-02-13
[QUOTE=Mishal][https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

I went through the above link and found it rather complicated. Rather, if I copy the /var/cache/apt/archives folder to some other place, format my drive, reinstall Linux and then recopy the archives back into /var/cache/apt, won't it work?[/QUOTE]
No, because you may still have to fetch newer packages form the net and that may require newer packages for their dependancies and so forth.  Also, just plopping these files into the cache directory does not make apt aware of them.  Creating a cd repository and adding that cd to your list of repositories does.

---

### Post by Mishal on 2006-02-13
Hmm....right.

So, is there a way of keeping the files in another partition of my hard drive and not on a CD and then make apt detect that folder to be a repository?

If the CD can be made to detect as a repository, what about a folder on the hard drive?

---

### Post by K.Mandla on 2006-02-14
[QUOTE=Mishal]If the CD can be made to detect as a repository, what about a folder on the hard drive?[/QUOTE]
It's possible. [This]("http://ubuntuforums.org/showthread.php?t=42862") is written for Hoary, but I've used it in Breezy too. I built a [Xubuntu-desktop CD]("http://ubuntuforums.org/showthread.php?t=101790") for an old machine that didn't have an Internet connection. But the idea is exactly like you describe -- building a repository as a directory on a drive.

Of course, you'd have to add the "deb file:/// ..." line to your sources.list file each time you started over. And you'd probably have to build the partition into your fstab to mount each time. But I guess it's less time-consuming than re-downloading. :)

Good luck.

---

### Post by az on 2006-02-14
[QUOTE=Mishal]

If the CD can be made to detect as a repository, what about a folder on the hard drive?[/QUOTE]

Actually, apt-move was made for that.  The howto just helps you put that homemade repo on a cd.

The additional step to putting that repo on a seperate partition are:

1.  Create a seperate partition.  Let's say for example, it is /dev/hdb6

2.  Mount the partition.  Call it /mirrors, since that is the direcotory in the howto:
sudo mount /dev/hdb6 /mirrors
You can also just add a line into your fstab
/dev/hdb6       /mirrors               ext3    defaults     0       0

3.  Create the repo as detailed in the howto
4.  Mount the repo in your other ubuntu install (see step 2)
5.  Add that repo as an apt source

Example (I am not using this currently - correct me if I am wrong):
deb file:/mirrors/debian stable main

---

### Post by Mishal on 2006-02-14
Thanks a lot...I will try it out.

But a question slightly off-topic: how do I prevent Synaptic from reloading information from all my sources when I press reload? If I have 10 repos in my sources.list and I want to add an 11th, I want Synaptic to check for info about the new repo added and not the first 10 that have already been checked many times before.

It may not matter to most people but my internet connection is very slow and it is especially slow with Synaptic. So everytime I press Reload in Synaptic, I am stuck for over half an hour. Any shortcuts please? :)

---

### Post by Mishal on 2006-02-15
Anyone?

---

### Post by az on 2006-02-15
[QUOTE=Mishal]

It may not matter to most people but my internet connection is very slow and it is especially slow with Synaptic. So everytime I press Reload in Synaptic, I am stuck for over half an hour. Any shortcuts please? :)[/QUOTE]

No, you can't.  It will check to see if the file is newer or not - it will not download it again and again if it has not changed.

The first problem is that the file (packages.gz) is updated whenever there is a change to the repository.  Since that happens frequently for some repositories (updates and security-updates) and it should not happen at all for just the regular release, perhaps disabling those repos temporarily would help.

The second problem is that most of the file is unchanged.  If only one package has been changed, you need to download the whole file (several megs for universe) again.  

It has been asked in the past if that can be improved so that apt can fetch diffs.  It is a rewrite of the way the package manager gets it's updates but that means you would not need to download the whole file, but only the differences between your older version and your current one.

This will probably happen eventually, but not right away.  You can check to see the wiki page if you can find this goal and see what progress has been made.  Anyone who can write code can help out, of course, since most of the developers have broadband and this becomes a low-priority for most of them.

---

### Post by Mishal on 2006-02-15
Thanks a lot! Let's hope some developer does not have broadband and takes the initiative to change the situation...hehe. :)

---

