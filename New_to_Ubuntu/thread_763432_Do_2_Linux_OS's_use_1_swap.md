---
title: "Do 2 Linux OS's use 1 swap?"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by mishathegoat on 2008-04-23
Hi all,
I am interesting in Dual-booting Xubuntu and Archlinux on my laptop. I was wondering if I needed to create a new swap partition or if both OS's can use the same one.

Thanks
Misha

---

### Post by joshrobinson on 2008-04-23
> **mishathegoat said:**
> Hi all,
I am interesting in Dual-booting Xubuntu and Archlinux on my laptop. I was wondering if I needed to create a new swap partition or if both OS's can use the same one.

Thanks
Misha

you can share a swap partition

---

### Post by TreeFinger on 2008-04-23
i believe you can also share your /home directory. you may know this already

---

### Post by joshrobinson on 2008-04-23
> **TreeFinger said:**
> i believe you can also share your /home directory. you may know this already

that i wouldnt do, say they OS's have 2 different versions of gnome. or different applications it could cause some issues

---

### Post by mishathegoat on 2008-04-23
@JoshRobinson Ah cool alright thanks for the speedy response

@TreeFinger I didn't know you could share directories between both of them thanks for that bit

---

### Post by subzero316 on 2008-04-23
Yes you can definitely share the swap partitions :KS

---

### Post by jakupl on 2008-04-23
> **TreeFinger said:**
> i believe you can also share your /home directory. you may know this already


Uuuh but that would come in very handy if beta testing right?? :) I will remember that in time for the Intrepid Ibex.

---

### Post by mishathegoat on 2008-04-23
So would I choose the partition labeled "Extended" or "Linux Swap / Solaris" if an installer asked me which partition to choose.. I'm guessing Linux Swap out of common sense but I just wanna make sure

Fdisk says they're both the same size

---

### Post by joshrobinson on 2008-04-23
> **mishathegoat said:**
> So would I choose the partition labeled "Extended" or "Linux Swap / Solaris" if an installer asked me which partition to choose.. I'm guessing Linux Swap out of common sense but I just wanna make sure

Fdisk says they're both the same size

you want to install ubuntu on the extended, filesystem type ext3 mountpoint / 

it should automatically notice and use the swap partition

your swap partition might be a bit large though, the general rule is to use 2x the amount of ram you have
i have 1gig of ram, so my swap is 2gig

---

### Post by Oldsoldier2003 on 2008-04-23
> **joshrobinson said:**
> that i wouldnt do, say they OS's have 2 different versions of gnome. or different applications it could cause some issues

I have a seperate home, but i do agree that you do have the chance of messing up configs if you use the same user name between distros. Its a lot less likely if they are from the same family ( say Debian and Ubuntu ) than if they are from completely different variants, (for instance RHEL and Debian). Either way the config issues are minor and a separate /home is less useful than having a separate data partition and making the habit of saving your data on the partition instead of in /home. Softlink the data partition to your home dir and all is good.

---

