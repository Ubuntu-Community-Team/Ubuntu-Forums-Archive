---
title: "[SOLVED] &amp;quot;&amp;quot;verizon A595U aircard&amp;quot;&amp;quot;"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by adamogardner on 2008-06-11
I have the verizon A595U aircard.  It's costing me a fortune per month and I haven't been able to make it work.  I have used the forum in the past to solve this problem, but nothing has worked.  The closest I feel like I came to getting it running is through gnome-ppp (whatever that is).  And I'm wondering how can I turn aircard if I'm already on a wireless connection?

---

### Post by stchman on 2008-06-11
> **adamogardner said:**
> I have the verizon A595U aircard.  It's costing me a fortune per month and I haven't been able to make it work.  I have used the forum in the past to solve this problem, but nothing has worked.  The closest I feel like I came to getting it running is through gnome-ppp (whatever that is).  And I'm wondering how can I turn aircard if I'm already on a wireless connection?

Have you tried contacting Verizon?  I would bet that that device does not have Linux drivers.

---

### Post by adamogardner on 2008-06-11
yes verizon has a room full of uncooporative ignorami.  They could tell me nothing but "sorry, we're in bed with windows."  But from what I understand It has been made to work on linux by others before me.  I just don't have any idea how.

---

### Post by Duck2006 on 2008-06-11
Did you get windoze drivers with the "verizon A595U aircard"?
If so you may be able to get it going through wine.

---

### Post by adamogardner on 2008-06-11
ok  now we are talking!  I have a verizon disk that I had to insert into my computer.  I also have Wine  but have no Idea what to do with it.  
Any instruction?

---

### Post by lazyart on 2008-06-11
This is pretty easy, actually.  You'll need to install KPPP.  Although this is a Verizon branded device, take a peek at the Sprint guide for their version of the same unit:

[http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf](http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf)

You can likely skip all the way down to Step 7 as this device should be recognized by Hardy.  When I used my 727 on a Gutsy-based Linux Mint installation it was seen correctly.

The dial string and account info will likely be different but should be easy to find with google.  Wireless broadband is a beautiful thing.

---

### Post by Duck2006 on 2008-06-11
> **adamogardner said:**
> ok  now we are talking!  I have a verizon disk that I had to insert into my computer.  I also have Wine  but have no Idea what to do with it.  
Any instruction?

Not sure my self about install the card, but i see "lazyart" has a link that should install it for you.

---

### Post by adamogardner on 2008-06-11
well it's similar but completely different.  there is no tab called window's accounts or anything like that.  nor is there a button that says new.  So It's not really that easy.  my tabs read "modem, networking and options" and none offer a "new" option.

---

### Post by lazyart on 2008-06-11
Don't use gnome-ppp.  You need KPPP so that you can get all the tabs you need.```
sudo apt-get install kppp
```

---

### Post by adamogardner on 2008-06-11
Ok I think It worked   how do I switch it from netgear to verizon on startup?

---

### Post by adamogardner on 2008-06-11
or not on startup  how about now?  because I'm still on netscape.  where is verizon?

---

### Post by lazyart on 2008-06-11
Use the network manager applet near the clock to disable networking.  It won't affect the verizon connection.

---

