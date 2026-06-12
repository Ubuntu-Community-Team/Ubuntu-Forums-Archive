---
title: "wifi card setup"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by nynoah on 2008-08-16
A little bit of a different problem.  A friend of mine just installed Ubuntu onto a computer that lacks a ethernet connection.  He can not get his wifi working.  Is there any way that we can get the drivers, burn them on a disk and them upload them to his computer that way?

its for a  linksys wireless g with speed boost wmp45g

Thanks all

---

### Post by Cresho on 2008-08-16
yes you can!  as long as you get all the dependent files (you will have to hunt down vigorously for this).  place them on cd and install them mannually.

Easiest way is lug the pc to a ethernet cable connection and install everything from there.

tutorial on another wifi i setup
[http://ubuntuforums.org/showthread.php?p=5562566#post5562566](http://ubuntuforums.org/showthread.php?p=5562566#post5562566)

---

### Post by nynoah on 2008-08-16
From what he tells me there is no card for ethernet connection.  I am on IM with him right now.  He is using his MAC book to talk to me over distance.  Converting another user to Ubuntu............Yea  so if he is on a MAC and has to get it to his PC.........what can we do, or where do we look to get the dependecies

---

### Post by nynoah on 2008-08-16
I am trying the method of downloading NDIS from sourceforge and then getting the driver for that card from the windows world.  Am I going a good route in my thinking?

---

### Post by Cresho on 2008-08-16
well, first off, you need to use the windows wireless driver and madwifi

if you are lucky, someone created a windows wireless driver deb file and a madwifi deb file.  even deb files have some dependencies needed.


if you used synaptic, you can easily install these 2 applications with the search and install.  NOthing else needed

ubuntu users are so spoiled.

---

### Post by nynoah on 2008-08-16
Forgot about Mad Wifi thanks will look there next.

Problem is I can not get him on synaptic without the wifi set up.  Chicken and egg problem......lol  Believe me, if I could just get him on the net with a ethernet card I would most likely find all my answers in synaptic.

---

### Post by Cresho on 2008-08-16
ya its possible but you will need to look for dependencies

hey im looking for the deb ones so you wont hav eto do much

---

### Post by nynoah on 2008-08-16
any way to get dependencies outside of synaptic?

---

### Post by nynoah on 2008-08-16
can you resend that zip cresho

---

### Post by Cresho on 2008-08-16
im curious.  Let me know if it worked.  I know other dependencies might be needed.

---

### Post by nicedude on 2008-08-16
well, first off, you need to use the windows wireless driver and madwifi if you are lucky, 

*** SAYS WHO ( if you use windows drivers that is NDISWRAPPER & if you use madwifi that is madwifi the 2 don't mix ) -> Windows drivers are windows drivers and madwifi is a set of linux drivers for Atheros based wireless networking devices ( which I use ). It all depends on who makes the chipset your friends wifi adapter contains and how it is conected to his PC ( madwifi does not support USB based devices ). So figure out what chipset it uses first and then figure out what your linux driver options are and go from there. If you post the chipset in use I will even look it up myself if you can't find the info.

---

### Post by Cresho on 2008-08-16
8)

---

### Post by Harisz750 on 2008-08-16
i believe the problem can be solved quite easy... i came across such a problem in the past..   Just buy a usb to ethernet adapter and plug it.. it's plug and play.. so don't bother.. and it is cheap

---

### Post by Cresho on 2008-08-16
hmmm...I just looked at your profile.  If you are using a 64 bit os, i am going to assume that so is your buddies install, the deb files will not work.  you will need to get the 64 bit version.

---

### Post by nynoah on 2008-08-16
I think he is running the 32 bit OS.  This is all a little too hard.  I think he is getting frustrated.  I am going to go to his place with my extra wifi card.  I will let him use that and reload Ubuntu so it will pull down the correct drivers.

---

