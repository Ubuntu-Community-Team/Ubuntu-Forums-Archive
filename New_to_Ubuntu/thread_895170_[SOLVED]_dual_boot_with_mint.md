---
title: "[SOLVED] dual boot with mint"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by LTFC2020 on 2008-08-19
hi
I run 8.04 but am considering trying a dual boot with mint, but I have a question
As its ubuntu based will I be able to transfer my settings across to the mint partition?

---

### Post by LTFC2020 on 2008-08-19
oh
and share media across the partition (my videos and music etc)
thanks

---

### Post by LTFC2020 on 2008-08-20
ok
well seems no one has a answer for this heh..
anyway I tried it and am now dual booting with mint
basically it is ubuntu with some cosmetic tweaks (and maybe some other I hav'nt found yet) but I think looks much better (personal preference)
so sharing files between the two is easy as the ubuntu partition shows up as a drive
maybe this happens with all linux dual boot systems but I hav'nt tried so I wouldn't know

---

### Post by Paqman on 2008-08-20
Your data is no problem. You can share media across any two distros (and most of it will share between completely different OSes)

You can have as many different distros as you like on your machine, no problem. If they share the same /home partition, make sure you set up different user names on each distro, to prevent any potential problems.

---

### Post by coffeecat on 2008-08-20
> **LTFC2020 said:**
> I run 8.04 but am considering trying a dual boot with mint, but I have a question

There is one GOTCHA I have already discovered from having Ubuntu 8.04 and the latest Linux Mint on different partitions on my laptop and having two different installations of 8.04 (don't ask! :wink: ) on different partitions on my desktop. When there was a kernel upgrade, Synaptic stopped during the installation asking me which version of grub's menu.lst I wanted. From memory I think it was the package maintainer's. Whatever - it got in a right muddle with two versions of the same Ubuntu (it sees Mint as Ubuntu) on the one machine, and menu.lst was written with the correct UUID for the root partition, but the wrong grub root reference (hdx,y). Or it might have been the other way around. :? Whatever - Ubuntu wouldn't boot. Fortunately I knew enough to suss out what was happening and edit menu.lst to get Ubuntu back on its feet, but this would floor a newcomer.

Advice. If you get a kernel upgrade with an Ubuntu/Mint multi-boot, be careful at the Synaptic questions stage. If you get an unbootable system, boot up with a live CD (or a bootable Linux on another partition) and start a help thread, posting the contents of /boot/grub/menu.lst from your unbootable Ubuntu or Mint.

---

### Post by LTFC2020 on 2008-08-20
opps
I put the same user name on each partition
How do I change the user name?

---

### Post by LTFC2020 on 2008-08-20
I mean oops!:rolleyes:

---

### Post by LTFC2020 on 2008-08-20
oops again
I started a new thread on this then saw you both had over 1000 posts each so maybe I should have stuck here (definately maybe)
Can I change my user name and then delete the old user name home folder while getting a new one myself?
will not be doing any updates until I get this sorted
spent all day yesterday doing a fresh install of 8.04 and today decide to go for mint
glutton for punishment I think

---

### Post by MarkieB on 2008-08-20
no longer participating in ubuntuforums.org

---

### Post by Paqman on 2008-08-20
> **LTFC2020 said:**
> opps
I put the same user name on each partition
How do I change the user name?

Easiest thing to do would be create a new user and delete the old one. If the old user has stuff in their /home you want to keep (settings, bookmarks, etc) then just copy the contents of /home/username over to the new user's /home/username and change the owner to the new user. You can either do that in the terminal with sudo or GUI-style with: 

```

gksu nautlius

```

---

### Post by coffeecat on 2008-08-20
Why do you want different usernames for Ubuntu and Mint? It won't be a problem having the same username. Both my main desktop and my laptop are set up as multiboots, and I have Gentoo, Mandriva and a couple of other distros as well as Ubuntu and Mint spread across them, and I use the same username in each. I find that useful because it helps me to remember who I am. :p At my age that's becoming important to me. :wink:

But if you do change your user account on one installation, you are going to run into a different problem. It's all about the UID (user identity). This is a number assigned to each user for permissions purposes. In both Ubuntu and Mint, the first created user is going to have the UID of 1000. That means that if you are in Ubuntu and you mount the Mint partition, you will be able to access, write to and delete your own personal files in Mint. But if you create a second account in Mint (say), this will have the UID of 1001. Now, if you try to access 1001-owned files using your Ubuntu 1000-UID account, you'll get an access denied error.

Worth thinking about.

Also - if you set up non-Ubuntu-based distros, watch out for UIDs. Fedora, Mandriva and PCLinuxOS assign the default UID of 500 to the first created user. It's 1000 for openSUSE and several others. Some distros allow you to choose the UID when you first install. Again, you need the same UID if you share files across distros using a Linux filesystem.

**Edit:** I've just come across your other thread and posted on it. **Please** re-read my earlier post in this thread. I was **not** talking about usernames. :(

---

