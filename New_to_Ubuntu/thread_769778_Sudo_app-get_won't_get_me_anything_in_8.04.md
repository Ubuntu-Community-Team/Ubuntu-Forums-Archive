---
title: "Sudo app-get won't get me anything in 8.04"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Sealbhach on 2008-04-26
I'm trying to get my Huawei E220 wireless modem working. Not very succesfully. I've seen some workarounds but none of these seem to work.

---------------------------------------------------------

I tried typing in terminal:

sudo apt-get install gnome-ppp

It couldn't get it, is it because I'm not online?

----------------------------------------------------------
Also looked in Synaptic package for:

Install ndisgtk (System &#8594; Administration &#8594; Synaptic Package Manager).

Open ndisgtk (System &#8594; Administration &#8594; Windows Wireless Drivers).

ndisgtk is not there.

------------------------------------------------------------

Also tried:

Check for device recognition
Open Device Manager (System &#8594; Administration &#8594; Device Manager)

Device manager is not there.


------------------------------------------------------------

The Huawei E220 is used by a lot of people in Britain, I thought Ubuntu would be able to install it.

Struggling a bit. Any help would be appreciated.

Thanks.


.

---

### Post by Joeb454 on 2008-04-26
Yes you are right - apt-get will not work because it requires you to be online somehow

---

### Post by st33med on 2008-04-26
Yes, these apt-get or aptitudes need to be online to install stuff from the repositories. You don't think all those programs would be installed on one disk, would you? ;)

---

### Post by st33med on 2008-04-26
You will also need a direct connection to the Internet through a ethernet cable. THEN you can do apt-get.

---

### Post by Sealbhach on 2008-04-26
Ok, thanks.

I'm online in Vista, can I get it somewhere now?

Also, can I get ndisgtk? And device manager?

I could stick them on a thumb drive and start up again in Ubuntu.


.

---

### Post by axor1337 on 2008-04-26
9if you have a nother machine online you can dl the package you need a make a deb install disk

---

### Post by Joeb454 on 2008-04-26
You will need to be online in Ubuntu to use apt-get. If you find modem drivers that don't require apt-get you could definitely put them on a USB drive though :)

---

### Post by Sealbhach on 2008-04-26
> **axor1337 said:**
> 9if you have a nother machine online you can dl the package you need a make a deb install disk

Make a what? A deb? I don't know what that is.

Where is this package you speak of?

Thanks for the replies, much appreciated.


.

---

### Post by SunnyRabbiera on 2008-04-26
> **Sealbhach said:**
> Make a what? A deb? I don't know what that is.

Where is this package you speak of?

Thanks for the replies, much appreciated.


.

a deb is the default installer format for Ubuntu.
You can probably put your dual boot to your advantage, you can read your vista drive in linux right?
and vice versa?

---

### Post by Sealbhach on 2008-04-27
I don't know how to see my Vista drive in Linux.

Anything I need to carry over, I use a thumb drive.

But being able to see Vista files in Linux would be good.


.

---

### Post by Joeb454 on 2008-04-27
Have a look in places - if Vista is a partition on the same hard drive it will be in there :)

---

### Post by 3rdalbum on 2008-04-27
You can download the .deb files for the packages you want, by going to [http://packages.ubuntu.com](http://packages.ubuntu.com). Put the packages onto your thumb drive and then go to your Ubuntu system. A simple double-click will install them.

If Gdebi says that there are additional packages to install first, go back to your Vista machine and put them onto the thumb drive and install those first.

---

### Post by hyper_ch on 2008-04-27
> **Joeb454 said:**
> Yes you are right - apt-get will not work because it requires you to be online somehow

Not really... apt-get will install software from the repos you have added. If all of those repos are online, then you need to be online. However you can use AptOnCD to create your custom repos... you can mirror ubuntu and then have a local repo, you can use the ubuntu-dvd and add that one as source.

---

### Post by Joeb454 on 2008-04-27
I didn't think of this :oops:

I was talking from the point of a standard Ubuntu install. My mistake!

---

