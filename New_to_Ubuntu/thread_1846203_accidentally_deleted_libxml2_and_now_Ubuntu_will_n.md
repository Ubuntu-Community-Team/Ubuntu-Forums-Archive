---
title: "accidentally deleted libxml2 and now Ubuntu will no longer boot"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by phadaphado on 2011-09-18
Hello,

I am a total newbie, which I think will become obvious considering what I have done.

I am using Ubuntu 10.04. I noticed that I had older versions of libxml2 on my computer and this was getting in the way of me compiling another program (I think).  So, through synaptic I decided to uninstall the older version of libxml2.  After doing this, most of my programs stopped working and when I rebooted, gnome no longer starts up.

Does anyone have any ideas about how I can get Ubuntu up and running again.

Thanks for any help you can give.

phadaphado

---

### Post by TeoBigusGeekus on 2011-09-18
Boot up in recovery mode from grub and, once in command line, give
```
sudo apt-get install libxml2
```

---

### Post by phadaphado on 2011-09-18
I tried "sudo apt-get install libxml2" but I got the error message "Unable to fetch some archive"

Is it possible that deleting libxml2 has affected my ability to access the internet?

phadaphado

---

### Post by TeoBigusGeekus on 2011-09-18
Try
```
sudo apt-get install libxml2-dev
```

---

### Post by phadaphado on 2011-09-18
OK, I tried "sudo apt-get install libxml2-dev" and I got the same error messages and gnome still doesn't start up when I reboot.  I think that synaptic uninstalled more than just libxml2.  I tried reinstalling gnome with "sudo apt-get install ubuntu-desktop" but I get several pages of error messages.  I still think that I am unable to connect to the internet.

phadaphado

---

### Post by Lisiano on 2011-09-18
Go to Recovery and select "Root Shell with Networking" or something like that.
Assuming you are root during recovery (# instead of $), if not, append every command with sudo
This will turn on your Wired connection
```
ifconfig eth0 up
```
Connect
```
dhclient eth0
```
Check that we are online
```
ping -c 4 google.com
```
If we are not online, no need to continue with the commands since they will error out.
Update the package list, re-install the default Ubuntu-Desktop and libxml2
```
apt-get update
apt-get install ubuntu-desktop libxml2
```
And finally reboot.
```
reboot
```

---

### Post by phadaphado on 2011-09-19
Ahhhhh...yes that worked.  Thank you Lisiamo, that was incredibly helpful.

Also, thank you TooBigusGeekus for your previous comments.

Now I get clean up my mess and get everything back to the way that it was.

Thanks again,

phadaphado

---

