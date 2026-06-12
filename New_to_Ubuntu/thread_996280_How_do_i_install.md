---
title: "How do i install?"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by simsek49 on 2008-11-28
Need to download network manager so i can get my wireless network working.

I think i downloaded the right file but i dont have a clue how to install it, it has instructions with it but they dont make sense to me.

1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.

How do i even do that?

How come its so complicated?

---

### Post by sstusick on 2008-11-28
There is a network manager installed in Ubuntu by default. There should be an icon in the upper right hand corner of the screen (next to the clock) that will allow you to connect to your network.

---

### Post by Kareeser on 2008-11-28
Hi simsek49. Welcome to the world of Linux!

First of all, forget everything you know about Windows. You won't need it. You'll have to learn everything again. We were all newbies at once point, so we understand where you're coming from, but there's a lot you need to learn before unix becomes easy for you to use :)

If that seems alright to you, then the answer to your question is the terminal. It is a command line interace (instead of the graphical one you're used to).

You can open it from (Application -> Accessories -> Terminal)

"cd" is the command you need to enter a directory... so assuming you downloaded the files to your desktop:

```

cd ~/home/[your username]/Desktop

```

---

### Post by simsek49 on 2008-11-28
> **sstusick said:**
> There is a network manager installed in Ubuntu by default. There should be an icon in the upper right hand corner of the screen (next to the clock) that will allow you to connect to your network.

Ah, i see there is but it doesnt allow me to connect to a wireless network.

---

### Post by ugm6hr on 2008-11-28
> **simsek49 said:**
> Ah, i see there is but it doesnt allow me to connect to a wireless network.

Unfortunately, the first thing to find out is to ask the right question!

If your wifi doesn't work, you'll have to supply more information.

Here's a list of stuff that's useful for us to help you:
[http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1)

---

### Post by simsek49 on 2008-11-28
> **ugm6hr said:**
> Unfortunately, the first thing to find out is to ask the right question!

If your wifi doesn't work, you'll have to supply more information.

Here's a list of stuff that's useful for us to help you:
[http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1)

My problem is trying to connect via wireless, currently connected via ethernet no problem, but dont have a clue how to connect wirelessly. I have wireless button on and i was hoping it would just pick up a signal ask me to enter the WEP and of i am but it doesnt and i dont know what i should do.

---

### Post by a0u on 2008-11-28
> **simsek49 said:**
> My problem is trying to connect via wireless, currently connected via ethernet no problem, but dont have a clue how to connect wirelessly. I have wireless button on and i was hoping it would just pick up a signal ask me to enter the WEP and of i am but it doesnt and i dont know what i should do.

Do what ugm6hr suggested and follow the instructions at [http://ubuntuforums.org/showpost.php...25&postcount=1]("http://ubuntuforums.org/showpost.php?p=5024425&postcount=1") to provide the necessary information for us to diagnose the problem.

Most likely the cause of the trouble is the wireless driver.

Check to see if there is any documentation relating to your wireless card:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

