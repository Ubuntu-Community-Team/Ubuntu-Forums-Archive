---
title: "50 / 50 Partition"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by gotanothergrot on 2008-10-20
When i installed Hardy Heron I didn't know how much space to allocate for the install so i just halved it 

[LIST]
[*]ie vista= 160 gig 


[/LIST][LIST]
[*]ubuntu= 160 gig
[/LIST]

Was this OK?

---

### Post by chanavs on 2008-10-20
Thats Great. More than enough

---

### Post by gotanothergrot on 2008-10-20
Hooray!!!

 I didn't do it wrong?!!


Thanks

---

### Post by meho_r on 2008-10-20
I have 20 GB partition for my Ubuntu installation (have installed Gnome, KDE3.5 and KDE4.1) so I think this is enough space for the installation apart from \home directory for storing your files for which I created a separate partition (about 80 GB). But if your home directory will be on the same partition as other ubuntu dirs, then 160 GB looks OK to me (though it's good idea to have a separate partition at least for \home).

---

### Post by neba on 2008-10-20
> **gotanothergrot said:**
> Hooray!!!

 I didn't do it wrong?!!


Thanks

I don't think so. I only have 100gb hd, and I did 50/50 also. When  I start to run out of space, I just move movies, songs, and pis to an external hd.

---

### Post by gotanothergrot on 2008-10-20
> **meho_r said:**
> I have 20 GB partition for my Ubuntu installation (have installed Gnome, KDE3.5 and KDE4.1) so I think this is enough space for the installation apart from \home directory for storing your files for which I created a separate partition (about 80 GB). But if your home directory will be on the same partition as other ubuntu dirs, then 160 GB looks OK to me (though it's good idea to have a separate partition at least for \home).

So preferably i should shrink vista and use the spare space for some home files?

---

### Post by drowner on 2008-10-20
I don't think you need to do that. You have plenty of space for Ubuntu. You don't *really* need a seperate home.

---

### Post by gotanothergrot on 2008-10-20
Thanks, Ill leave things alone.

---

### Post by AndyCooll on 2008-10-20
> **drowner said:**
> I don't think you need to do that. You have plenty of space for Ubuntu. You don't *really* need a seperate home.
Depends on your preference. 

As you say you don't _have_ to have a separate /home partition. However if you want to do a fresh re-install and keep your old settings then a separate /home partition could prove useful. Otherwise you then need to backup your /home partition (which is a good idea anyway) and then start manually re-adding your settings files for each app.

If you go in the separate /home partition direction then 10 or 20gb max for your root partition is plenty. I only set aside 10gb, but only use the GNOME DE, others may have mileage which differs.  

:cool:

---

### Post by meho_r on 2008-10-20
> **drowner said:**
> I don't think you need to do that. You have plenty of space for Ubuntu. You don't *really* need a seperate home.

You don't HAVE to, but if you want to reinstall ubuntu later for some reason, don't forget to burn your files from home dir since they'll be lost after reinstall. The benefit of having \home dir on a separate partition is that you don't have to move your files every time you do reinstall/fresh install. Note that all your settings are stored in \home dir too (although hidden so easily missed).

So, the minimum recommended partition scheme for Linux is:

1. a swap partition (generaly adviced to be 2 x RAM)
2. a \ ("root") partition 
3. a \home partition

And one more advice: Windows partition should ALWAYS be the first one and PRIMARY. Linux partition as well as partition for storing documents can be logical, not necessary primary (only 4 primary partition are possible).

Sample scheme:

1. win partition (~160 GB)
2. swap partiton (~4 GB or more/less, depends on your qty of RAM)
3. linux root partition (~20 GB, ext3)
4. \home partition (~136 GB, ext3 or if you want Windows sees it then ntfs).

Or another one:

1. win partition (~160 GB)
2. partition for storing documents both windows and linux (~130 GB), ntfs, just make symbolic links from dirs inside your home folder (i.e. Documents, Music, Pictures etc.) to this partition. This way you can have all your docs in one place.
3. swap partiton (~4 GB or more/less, depends on your qty of RAM)
4. linux root partition (~20 GB, ext3).

To conclude, you should consider always having a separate partition for your documents no matter is it Linux or Windows you're using because sometimes systems crash and in some cases that means losing all your hard work.

---

