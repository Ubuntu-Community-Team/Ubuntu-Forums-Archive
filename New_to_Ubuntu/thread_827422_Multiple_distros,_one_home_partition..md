---
title: "Multiple distros, one /home partition."
date: 2008-06-12
forum: New to Ubuntu
---

### Post by powerpleb on 2008-06-12
Would it be a good idea to install multiple distros and have them all mounting the same partition as their /home directories? That way I wouldn't have to start from scratch when changing or trying distros.
Or would it just mean that settings that work in say, Fedora but not Ubuntu would make the system unstable?

---

### Post by Joeb454 on 2008-06-12
I would advise against it personally, and have a separate /data partition which would hold anything you want to keep, and not program settings.

If you are just going to be using 1 distro - then yes totally worth just having the 1 /home :) I've had the same /home from 7.10 to 8.04 :)

---

### Post by sam_delta on 2008-06-12
i dont rememeber where, but i read somewhere that this was not a good idea as diferent distros might use different settings. its possible, but would couse problems

still, this is what my memory can recall from another thread, lets see what people say

sam

---

### Post by bruce89 on 2008-06-12
Different distros will likely use different program versions. The newer version will convert its settings to the new format, and then the older one will not load it.

Backwards compatibility but not forwards compatibility.

---

### Post by philinux on 2008-06-12
The only things that have been useful were firefox bookmarks and my emails.

Everything else are just program settings or installed apps.

I'm now using virtualbox to try out distro's.

---

### Post by Yuki_Nagato on 2008-06-12
I generally do share /home partitions between multiple distributions.  It makes the saving of large video and image files a snap between changes.

---

### Post by bodhi.zazen on 2008-06-12
> **Joeb454 said:**
> I would advise against it personally, and have a separate /data partition which would hold anything you want to keep, and not program settings.

If you are just going to be using 1 distro - then yes totally worth just having the 1 /home :) I've had the same /home from 7.10 to 8.04 :)

+1 Joeb454

Each distro will give a different user ID. On some it will be 1000 (Ubuntu). On others it will be 500.

So ...

conflicts in /home come from different versions of an application using the config ( . files) as pointed out by bruce89 as well as conflicting uid (1000 on Ubuntu and 500 on Fedora).

So IMO easiest to give each distro a /home on /

Shared partition for date (/mnt/data)

The share should have permissions like 
owner = root.root permissions = 777

Or better
owner = root.share permissions = 770

With the second option you will need to make a new group "share" on each distro (make share had the same GID # on each distro).

You can then use links or mount --bind 

```
ln -s /mnt/data/music ~/music
```

OR

```
mount -- bind /mnt/data/music /home/user/music
```

======

Alternate is to use a shared /home partition, and give a unique user_name and /home/user_name for each distro.

---

### Post by powerpleb on 2008-06-12
Thanks. I guess I won't be doing it then.

---

### Post by ryan! on 2011-04-28
Would this work if I had ubuntu 10.4 and 11.4 sharing the same /home partition?

---

### Post by bodhi.zazen on 2011-04-28
> **ryan! said:**
> Would this work if I had ubuntu 10.4 and 11.4 sharing the same /home partition?

The comments above still apply ;)

---

### Post by rosencrantz on 2011-04-29
It might be possible to share some components, though - e.g. I have linked my openSuSE KMail user data directory into the Kubuntu one which seems to work OK. There might be similar solutions for bookmarks and settings - the format of those shouldn't change for minor version differences.

---

### Post by srs5694 on 2011-04-29
I disagree with most of the earlier posts.

One must distinguish between the */home directory (or partition)* and *individual users' home directories*. For instance, my own primary home directory on most of my own systems is /home/rodsmith. On some dual-boot systems, though, I share a /home partition (or logical volume in most cases, since I generally use LVM), but I give myself a different home directory for each distribution -- say, /home/rodsmith for one and /home/f14_rodsmith for another. This practice avoids the sorts of problems that others have warned about, but gives me the flexibility of having a single storage space for all my needs, without having to split it up or rely on a separate /data partition (which is re-inventing the wheel and causes more complications in some situations, such as when you've got multiple users on a single computer).

The main caveat to sharing a /home partition between distributions is that you have to know how to create those separate user home directories. The easiest way to do this is to use different usernames in each distribution. It is possible, however, to create accounts with different usernames and home directory names, such as rodsmith as a username and /home/f14_rodsmith as the home directory. I don't know of a way to do this when creating an account when using Ubuntu's GUI account-creation tools, but you can change a user's home directory with the advanced settings after the fact. Alternatively, you could use text-mode tools such as useradd to create the account, or create an account with a username that matches the directory name and then use the usermod text-mode tool to change the username to your preferred username after the fact, as in "sudo usermod -L newname tempname" to change the username tempname to newname. (This last is probably the safest option when doing it with Ubuntu, if you want matching usernames in all distributions.) Some other distributions have much better GUI account-creation tools; Fedora's, for instance, lets you do this from the start (even in the installer).

---

### Post by srs5694 on 2011-04-29
> **ryan! said:**
> Would this work if I had ubuntu 10.4 and 11.4 sharing the same /home partition?

I forgot to address this point: Sharing user home directories across Ubuntu versions is inadvisable, since some software components may use different configuration file formats. Thus, when you boot 11.04 (note it's .04, not .4) and run a program with a new configuration file, it might update the old file. When you reboot to 10.04, the software will be mystified by the change and may misbehave. This might be a minor nuisance if this happens in a tool you seldom use, but it could be a much bigger problem if it happens in something like a desktop environment.

Of course, this all becomes a non-issue if you use separate user home directories, as I suggested.

---

### Post by ryan! on 2011-04-29
> **srs5694 said:**
> Sharing user home directories across Ubuntu versions is inadvisable Damn, but at least now I know, thanks guys. > (note it's .04, not .4) Sorry, my bad.

---

### Post by fabricator4 on 2011-04-29
> **ryan! said:**
> Would this work if I had ubuntu 10.4 and 11.4 sharing the same /home partition?

I actually did this when I was trying 11.04 beta 1.  Everything was fine except that sometimes the indicator applets would bomb when going back to 10.04.  No remedial action was required - they would be fine on the next boot.

Generally though, sharing /home is a bad idea, especially for completely different distros.  It's a bit like sharing a bathroom with your flatmates - You're never sure what you will find when go back in there.  ;-)

Chris

---

### Post by bodhi.zazen on 2011-04-29
> **fabricator4 said:**
> Generally though, sharing /home is a bad idea, especially for completely different distros.  It's a bit like sharing a bathroom with your flatmates - You're never sure what you will find when go back in there.  ;-)

Chris

Actually you got this all wrong.

As has been pointed out, there is nothing wrong with sharing /home

But if you do so, each user should have a unique user name on each install.

So share /home with distro A and B, user names foo and bar, no problem

Share /home/foo on distros A and B, without unique usernames, expect problems.

---

### Post by Linjie on 2011-04-29
Hi, I have some questions (absolute absolute beginner): 
 
If /home is not suggested to share between different distros, why not have a larger partition for each distro, without a /home ? Is it better to have a separate /home partition?
And, if I have a NTFS /home partition for ubuntu, will I be able to access it from Windows? 
Thank you very much!

---

### Post by bodhi.zazen on 2011-04-29
> **Linjie said:**
> Hi, I have some questions (absolute absolute beginner): 
 
If /home is not suggested to share between different distros, why not have a larger partition for each distro, without a /home ? Is it better to have a separate /home partition?
And, if I have a NTFS /home partition for ubuntu, will I be able to access it from Windows? 
Thank you very much!

Neither NFS or FAT will work (well) as a /home directory.

Yes, many do what you are suggesting, which would be a shared /data directory.

if the /data direcoty is ntfs it is easy to share with linux or windows.

---

### Post by fabricator4 on 2011-04-29
> **Linjie said:**
> Hi, I have some questions (absolute absolute beginner): 
 
If /home is not suggested to share between different distros, why not have a larger partition for each distro, without a /home ? Is it better to have a separate /home partition?

As has been pointed out to me, having a common /home isn't the problem, but sharing /home/username is.  So... you can have one /home partition and use a different login name on the ones that you need to.  You could then make a symlink to the folders that you want to share - problem solved?

It takes a little more setting up, since you'd also have to have a common group for all users.

> 
And, if I have a NTFS /home partition for ubuntu, will I be able to access it from Windows?

Yes you can, however NTFS is a non-journaling file system, so for this and other reasons it isn't really suitable for a serious Linux installation.  It would be better to use ext4 for /home.  If you really need to access it from your Windows boot you can do so by installing the open source driver called Ext2Fsd.  It works great, though it uses the non-journaling backwards compatibility to ext2.

Chris

---

### Post by Linjie on 2011-04-29
It seems there are more than one solution. I definitely won't make the /home ntfs. I'll try the Ext2Fsd, and probably give Windows a larger partition so I can leave some files there. Thanks guys!

---

### Post by srs5694 on 2011-04-29
(re: sharing a user home directory between Ubuntu 10.04 and 11.04)

> **fabricator4 said:**
> I actually did this when I was trying 11.04 beta 1.  Everything was fine except that sometimes the indicator applets would bomb when going back to 10.04.  No remedial action was required - they would be fine on the next boot.

Please keep in mind that the problem with sharing a user home directory is with *individual applications*. You might have had few problems with *your* mix of programs, but somebody else might. If SuperFoo was updated and uses a significantly new configuration file in Ubuntu 11.04, and if you don't use SuperFoo, then that issue won't affect you; but if I use SuperFoo, then it would affect me if I were to attempt to share a single user home directory between Ubuntu versions.

In other words, if you (not you specifically, fabricator4, the generic "you") are considering sharing a user home directory, *don't* accept any one person's report of success in doing so as evidence that it's safe. In fact, even a dozen reports of success would be meaningless; there's no telling what applications you might use (now or in the future) that these hypothetical reporters haven't used.

---

### Post by fabricator4 on 2011-04-29
> **Linjie said:**
> It seems there are more than one solution. I definitely won't make the /home ntfs. I'll try the Ext2Fsd, and probably give Windows a larger partition so I can leave some files there. Thanks guys!

I also meant to answer your question as to why it's better to have a separate /home from / ("root partition").

The answer is simply that it does give the separation from the rest of the file system.  You can then re-install or upgrade at any time without really worrying about your data.  I go a step further and have /home on a completely different drive altogether: the bigger the better.

The filesystem only needs about 15-20 GB so I have several partitions on the first drive, all of which I can boot off.  I have one of the same distro which I can play with and break, and a couple of different distos (like lubuntu and natty) for testing.  If the worst happened and my main OS got broken then I can simply boot one of the others and fix it, all without worrying about my data which is on a separate drive/partition.

Chris.

---

