---
title: "How do I give myself permission to access these files?"
date: 2014-05-11
forum: New to Ubuntu
---

### Post by phil28 on 2014-05-11
ok so I have a hard drive I'm trying to salvage data from if it will let me. It's formerly the internal drive from my old Macbook, so I know the username/pw combo that does have permission to access the directories/files I'm interested in. I had to switch out the drives in the macbook when this HD started working unreliably and was never able to get it to work as an external drive with the macbook before accidentally pouring a lot of soda into the macbook and taking it totally out of commission.

Right now I have the drive installed in the expansion bay in my Thinkpad running Ubuntu. It recognized the drive without me doing anything, reads the name of the drive and when I open it I can see the initial directories, but I don't have permission to go any further. Is there a way to be like "hey, permissions, I *am* that guy, just using a different computer"?

EDIT: well as much as I hate to be that guy who asks a stupid question then figures it out for himself right away I *think* that I'm copying the files I'm most interested in without having to mess with the permissions by using sudo (now I know what that does... sort of) and rsync. That being said if there's a way I can dupe this hard drive into letting me just browse around it that would be cool, I'm sure there's stuff on there I'd like to save other than just my old music library. I tried changing the permissions on the files but it said "read only file system", I'm assuming because it came from a Macbook and is formatted differently.

---

### Post by LastDino on 2014-05-11
[http://askubuntu.com/questions/90339/how-do-i-set-read-write-permissions-my-hard-drives](http://askubuntu.com/questions/90339/how-do-i-set-read-write-permissions-my-hard-drives)

---

### Post by coffeecat on 2014-05-12
> **LastDino said:**
> [http://askubuntu.com/questions/90339/how-do-i-set-read-write-permissions-my-hard-drives](http://askubuntu.com/questions/90339/how-do-i-set-read-write-permissions-my-hard-drives)

Unfortunately, that won't work in this situation. See my post below. Also - you may wish to remove that page from your bookmarks. It is full of misguided and unworkable advice and I am surprised that the askubuntu community hasn't picked that up and edited out the many erroneous statements.

---

### Post by coffeecat on 2014-05-12
@phil28, you **cannot** change the permissions on a hard drive from a Macbook but there is a workaround to enable you to copy and backup the files on it. Let me explain the first before the workaround.

A drive from a Macbook will be formatted with the Apple filesystem HFS+. This can only be mounted read only in Ubuntu. Mac OSX and Linux use the same set of Unix permissions and ownership of files is defined by means of a numeric UID. Your UID in the OSX files will probably be 501 and in Ubuntu, 1000. In normal circumstances, to change ownership of files one would run chown on them, and to change permissions one would run chmod. But because the HFS+ filesystem can be mounted read only, you cannot run chown (or chmod) commands on it from Ubuntu. In theory, you could run chmod and chown from another Apple machine, but I suggest a simpler workaround below using Ubuntu.

Note - in fact there is a way of force-mounting HFS+ read-write, but I would not do that myself, and cannot in all conscience recommend it.

**Workaroud**

Simply open a root owned file browser to browse the files on the Mac HD. Open a non-root browser to the destination storage device. Simply drag and drop from source to destination. To open a root browser in Ubuntu, run this from a terminal:

```
gksu nautilus --no-desktop
```

This will open in root's home. You then need to navigate to the mountpoint of the mounted Macbook drive. If you need help with that, post back. I'm assuming you are running Ubuntu and not one of the variants. If you are running Kubuntu or Xubuntu, for example, post back and I or someone can give you the command to open a root browser in the relevant desktop environment.

**Cautionary Note**

If you copy to a Linux filesystem such as ext4 - into your Ubuntu home folder for example - the ownership of the files **may** be changed to root, which will complicate things for you. One way round this is to copy directly to a Microsoft filesystem such as fat32 or ntfs. If you intend to copy directly to an external drive formatted ntfs, for example, that would be a good way to go.

---

