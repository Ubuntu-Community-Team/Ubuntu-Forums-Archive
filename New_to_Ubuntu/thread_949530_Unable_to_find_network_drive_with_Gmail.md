---
title: "Unable to find network drive with Gmail"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by Alexandre76 on 2008-10-16
Hello,

I want to send an email and attach a file to my message from Gmail, but it seems that I am able to browse locally only. It does not find any network places, but when I go to Places, I see my network drives mounted...

Any idea on how to solve this?

Note: I am in a Windows network

Thanks in advance for your help

Alexandre

---

### Post by Tomatz on 2008-10-16
> **Alexandre76 said:**
> Hello,

I want to send an email and attach a file to my message from Gmail, but it seems that I am able to browse locally only. It does not find any network places, but when I go to Places, I see my network drives mounted...

Any idea on how to solve this?

Note: I am in a Windows network

Thanks in advance for your help

Alexandre

Can you just copy the file from the network to the Desktop, then upload it?

---

### Post by Paqman on 2008-10-16
> **Alexandre76 said:**
> 
Note: I am in a Windows network


How have you set this up? Have you actually added the network shares to /etc/fstab, or do you just mount them when you need them through Gnome?

---

### Post by Alexandre76 on 2008-10-16
> **Tomatz said:**
> Can you just copy the file from the network to the Desktop, then upload it?

I'm in a company network, and my company emails are redirected to a Gmail account... I can do like this, but I prefer to have my drives available right away, as I have dozens of them!!!

---

### Post by Alexandre76 on 2008-10-16
> **Paqman said:**
> How have you set this up? Have you actually added the network shares to /etc/fstab, or do you just mount them when you need them through Gnome?

I think i've just mounted them through Gnome (Places > Connect to Server...)

---

### Post by Paqman on 2008-10-16
> **Alexandre76 said:**
> I think i've just mounted them through Gnome (Places > Connect to Server...)

That's why then. You need to add an entry to /etc/fstab that will mount them automatically at boot.

Check out this thread for how to [mount shares over a Windows network](http://ubuntuforums.org/showthread.php?t=288534). It's a pain to have to do it manually, but it's actually pretty straightforward. Once it's done they'll mount automatically, it'll be a lot snappier than browsing to them through Gnome.

---

