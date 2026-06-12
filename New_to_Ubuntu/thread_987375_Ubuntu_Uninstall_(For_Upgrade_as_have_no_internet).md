---
title: "Ubuntu Uninstall (For Upgrade as have no internet)"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by IBUA on 2008-11-19
Hey,

I'm trying to uninstall Ubuntu 8.04 to upgrade it to U. Studio 8.10 to reinstall it as my internet USB wireless adaptor won't work with ubuntu (even though it's supposed too)

And for somereason everytime i go to attempt to uninstall it the programs won't work.

E.G when i go to the Ubuntu Folders the UNINTSTALL program thingy just does nothing when i click on it,

When i put the installation CD it just asks to install.

Can anyone help me in how to fix this?

Cheers.

(BTW the Ubuntu files were installed onto a EXternal HDD and i dual boot it on the computer with Windows XP)

---

### Post by wolfen69 on 2008-11-19
just install ubuntu studio and tell it to install to the partition regular ubuntu is installed on. choose manual partitioning. no need to uninstall ubuntu first.

---

### Post by NullHead on 2008-11-19
You can simply erase the partition ubuntu is located on and that'll do the trick. Then you want to install Ubuntu studio.

---

### Post by IBUA on 2008-11-19
> **NullHead said:**
> You can simply erase the partition ubuntu is located on and that'll do the trick. Then you want to install Ubuntu studio.

How do i do that?

Do i just delete all the files under the UBUNTU folder?

BTW i forgot to say that other data is on the External HDD (All my music :S)
So how do i rid Ubuntu without deleting the music?

---

### Post by IBUA on 2008-11-19
> **wolfen69 said:**
> just install ubuntu studio and tell it to install to the partition regular ubuntu is installed on. choose manual partitioning. no need to uninstall ubuntu first.

I can't do this as for somereason Wubi won't load (like the uninstall programm thingys)and i want to install it through wubi.

It seems that all the Linux based/purposed installers won't work?

---

### Post by LowSky on 2008-11-19
studio doesn't have wubi, studio is only a Text based installer. If you want, Use Regular Ubuntu 8.10, and then install ubuntustudio-desktop from synaptic.

Its basically the same thing in the end

---

### Post by IBUA on 2008-11-19
> **LowSky said:**
> studio doesn't have wubi, studio is only a Text based installer. If you want, Use Regular Ubuntu 8.10, and then install ubuntustudio-desktop from synaptic.

Its basically the same thing in the end

I thought WUBI had an option to choose which type you could download?

The Desktop Environment option? Or is that something different?

But i don't have the internet so i can't use the synaptic manager.

And also i want to update to 8.10 anyway... (i'm on 8.04 atm anyway)

---

### Post by jenkinbr on 2008-11-19
There are ways of using synaptic offline.
See the following:
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)
[https://help.ubuntu.com/community/Synaptic/Offline](https://help.ubuntu.com/community/Synaptic/Offline)

I do this all the time and have no problems, although it is very tedious.  I usually have download managers do the dirty work for me.

By the way, I am working on a tutorial that does this for us folks who don't have access to an online ubuntu computer, but it is at a very raw stage at the moment, but I will work on getting it up within the next month.

Cheers.

---

### Post by IBUA on 2008-11-19
> **jenkinbr said:**
> There are ways of using synaptic offline.
See the following:
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)
[https://help.ubuntu.com/community/Synaptic/Offline](https://help.ubuntu.com/community/Synaptic/Offline)

I do this all the time and have no problems, although it is very tedious.  I usually have download managers do the dirty work for me.

By the way, I am working on a tutorial that does this for us folks who don't have access to an online ubuntu computer, but it is at a very raw stage at the moment, but I will work on getting it up within the next month.

Cheers.

Awesome!

Thats very useful

Thanks!

But can anyone still help with me uninstalling Ubuntu 8.04 because i want to upgrade to 8.10???

---

### Post by Paqman on 2008-11-19
> **IBUA said:**
> 
But can anyone still help with me uninstalling Ubuntu 8.04 because i want to upgrade to 8.10???

Have you tried it from the Windows Add/Remove Software menu?

---

### Post by Elfy on 2008-11-19
If the add/remove doesn't work then - 
[https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) do I manually uninstall Wubi?

---

### Post by Keen101 on 2008-11-19
> Have you tried it from the Windows Add/Remove Software menu? 

Yeah, if you have 8.04 installed with WUBI, then you have to remove ubuntu from within windows add/remove programs from the control panel.

---

