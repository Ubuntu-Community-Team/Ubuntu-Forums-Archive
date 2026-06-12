---
title: "How can I send and receive fax?"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by Friccy on 2008-09-26
Hi guys!

I have an HP laptop, running Ubuntu Hardy.
I need to receive some very important fax and would like to use my laptop.
This was possible in the old XP era, so must be possible in UBUNTU.
Please let me know, how?
Thanks!

---

### Post by Kevbert on 2008-09-26
If you have a fax modem you could try efax along with it's front end efax-gtk.  You can find it via Synaptic Package Manager (just search for fax).

---

### Post by Friccy on 2008-09-26
> **Kevbert said:**
> If you have a fax modem you could try efax along with it's front end efax-gtk.  You can find it via Synaptic Package Manager (just search for fax).

I have tried efax but for some reason it's not working. I am attaching a file that I want to send and it say "File does not exist".
It's not accepting the telephone number I am introducing to where I want to send the fax.
Could you help me with this?!

---

### Post by Rorke on 2008-10-02
Did you solve this? I need to send a fax too!

---

### Post by stalkingwolf on 2008-10-02
there is an online service that I used for sometime called send2fax.
you send faxs from your account on their site and receive them in your email.  That is about all I can tell you right now as I have not used the service for some time.

---

### Post by gizmobay on 2008-10-03
I tried efax as well and it never worked properly as I ended up with transmission errors thus the fax was canceled while sending or receiving. 

I just installed Hylafax with AvantFax and it works very well. There's a hylafax package in the repo but there isn't one for AvantFax. AvantFax is a web frontend for Hylafax.

Assuming you've got the modem setup, Hylafax was fairly painless to get going. AvantFax was trickier. If you don't have the modem setup and it's a Winmodem, then you'll probably need martian.

---

### Post by mamut0o1 on 2008-10-21
FRICCY
I remember having a problem like that. are you trying to send a JPEG file? or what kind of file are you trying to send?

mamut

---

### Post by brian mcgee on 2008-11-02
> **gizmobay said:**
> I just installed Hylafax with AvantFax and it works very well. There's a hylafax package in the repo but there isn't one for AvantFax. AvantFax is a web frontend for Hylafax.

Assuming you've got the modem setup, Hylafax was fairly painless to get going. AvantFax was trickier. If you don't have the modem setup and it's a Winmodem, then you'll probably need martian.

If you want to skip AvantFax and don't mind managing hylafax-server by terminal, try gfax as a simple client for HylaFax.

```
apt-get install gfax
```

In gfax prefs, you'll have to tell it to use hylafax and localhost (sounds like hylafax-server is running on your laptop, which you send/receive from as well).

---

