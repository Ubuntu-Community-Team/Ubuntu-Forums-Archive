---
title: "Confusion over partitons (access to &amp; from Vista)"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by Paddy Landau on 2008-06-03
Last night I attempted to install Ubuntu 8.04 from a disk.

So, now, I'm really confused about partitions! Of course, I've read posts on this forum but I remain confused.

My situation:

[LIST]
[*]I have a 70Gb partition where my Vista is stored.
[*]I have 40Gb empty free space where nothing is stored. I intend to load Ubuntu there.
[/LIST]
This is how I understand it:

[LIST=1]
[*]In the 40Gb free space, create a **2Gb** "**swap**" partition. *This can be a logical partition.*
[*]Create another **10Gb** "**ext3**" partition for "**/**". *This must be a primary partition.*
[*]Finally, create a partition for the remaining **28Gb** as "**/home**" as an **NTFS** partition (so that I can access it from Vista). *This can be a logical partition.*
[/LIST]
**Question 1**: Please tell me where I've gone wrong in my understanding, or add any clarifications that might help.

**Question 2**: Now, the installer doesn't have "NTFS" as an option. So, is it possible to create the "/home" partition as NTFS? The purpose of this is to allow Vista to access my Ubuntu data; perhaps there is a better way?

**Question 3**: One final question: Ubuntu can access my Vista files. So, is there any point in even having the "/home" partition? Can I do without it, and just save all my data files on the Vista partition from Ubuntu? (That way, my existing backup program will back up my Ubuntu data.) If I go this route, what are the potential pitfalls -- apart from Windows viruses!

---

### Post by Cypher on 2008-06-03
Depending on the amount of RAM you have, 2GB of SWAP might be more than you need. If you have about 1-2G of RAM, you can easily get away with 512MB of SWAP. I would recommend that you use EXT3 for both / and /home. 

You can access your Vista NTFS partition from Linux using the ntfs-3g package. In Vista, you can use [FS-Driver]("http://www.fs-driver.org/") to access the EXT3 partition through an Windows Explorer like program.

It's always good to use the native FS type in a particular OS and use "extra" software to access the FS of a different OS rather than force the OS to use a non-native FS..

---

### Post by rossmoore on 2008-06-03
I presume you're using an Ubuntu Live CD. I thought I might make my home directory an NTFS partition, but I don't think that is supported by the Live CD. I use an ext3 partition for my home directory, and then there's some freeware available (fs-driver.com) to allow Vista to read an ext3 drive. This works fine for me, although I barely use Vista at all at the moment.

You have to have the /home directory - configuration information for your user goes in there. If you don't mind setting up your programs to look in non-default places for your photos / music etc, then you can not set up a specific partition from /home and leave it to be created automatically in the install process directly within the root filesystem.

I don't think any of the the Ubuntu partitions need to be primary. Vista does need to be on a primary partition though. When I installed Ubuntu on a Vista machine a month ago the installer configured Grub to correctly pick up Vista (and Dell MediaDirect). Are you finding that it's missing your Vista install that's already present?

---

### Post by ChameleonDave on 2008-06-03
> **Paddy Landau said:**
> 
[*]Finally, create a partition for the remaining **28Gb** as "**/home**" as an **NTFS** partition (so that I can access it from Vista).

Argh!  No!

NTFS is a Microsoft trade secret.  You cannot expect Linux to reliably use it for something as important as your home directory.

Format your home partition as "FAT" (an old Microsoft file system which is well-documented), and Linux will be able to access it without trouble.  However, FAT is missing some key Linux features.  You ought to make format it with Ext2 or Ext3 instead.  You can install drivers onto Windows that allow the operating system to access Ext2/Ext3 partitions.

Note that the most important thing that your home directory will contain is all the configuration files.  You own personal files (documents, music, etc) don't need to be there.  They can be on a separate partition mounted within your home directory.

---

### Post by Paddy Landau on 2008-06-03
Wow, thanks for all the responses!
 
> **Cypher said:**
>  It's always good to use the native FS type in a particular OS and use "extra" software to access the FS of a different OS rather than force the OS to use a non-native FS..
Excellent point.
  
I didn't have a problem accessing my Vista files when I experimented using WUBI, so I imagine that there'll be no problem after a native installation. If I do have a problem, I'll look up [ntfs-3g]("http://www.ntfs-3g.org/index.html").
   
> **rossmoore said:**
>  I presume you're using an Ubuntu Live CD. ... Are you finding that it's missing your Vista install that's already present? ... If you don't mind setting up your programs to look in non-default places for your photos / music etc...
Yes, I created a Live CD from a download. The installer finds my Vista partition without any problem. I was just confused about how to partition the free space.

> **rossmoore said:**
>  If you don't mind setting up your programs to look in non-default places for your photos / music etc...
Nah, I think you're right. I'll stick to the defaults.

> **ChameleonDave said:**
> Argh!  No!
 NTFS is a Microsoft trade secret. You cannot expect Linux to reliably use it for something as important as your home directory.
  LOL. We all know about MS's closed formats! I didn't realise that NTFS was one of them.

Once installed, I'll look up the [FS Driver]("http://www.fs-driver.org/") for Vista to be able to access my Ubuntu data files.
  

So, that leads to my next question: *Is it really necessary to have two separate partitions for "/" and "/home"?*

[LIST]
[*]If so, are the sizes that I mentioned appropriate (10Gb for "/" and the rest for "/home")?
[*]If not, then I'll just create a swap partition (I guess 1Gb to be safe -- I have 1Gb RAM) and the rest for "/home".
[/LIST]

As a final note, I guess that I should put my swap partition right at the end of the drive. That will give me the freedom to change partition sizes later should I start to move all my Vista data over to Ubuntu (which I hope to do in time!). Imagine... a life without Vista's problems!

---

### Post by rossmoore on 2008-06-03
It's not at all necessary to have 2 separate partitions for "/" and "/home". It is handy though - you can reinstall Linux and keep your config.

10Gb should be plenty for "/" unless you plan on installing some crazy stuff. I know that you can get away with less - personally I have a pretty big drive so I've got about 20Gb for "/" to make sure I'll never have to think about it again, but that's just me.

---

### Post by rossmoore on 2008-06-03
Oh, and ntfs-3g is included in Hardy, so you'll automatically have read-write access to NTFS partitions if you mount them as read-write. It's pretty reliable - I've never had a problem, anyway.

---

### Post by Paddy Landau on 2008-06-03
Thanks for the reply.

Well, I'm off to do my install now. Wish me luck!

---

