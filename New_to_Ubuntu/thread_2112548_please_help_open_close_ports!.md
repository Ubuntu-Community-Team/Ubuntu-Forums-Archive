---
title: "please help open close ports!"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by Old Jimma on 2013-02-05
Hi Community:

A few days ago, I got paranoid and decided to investigate increasing the security of some things. The thread of that security discussion is found at:

[http://ubuntuforums.org/showthread.php?t=2111909]("http://ubuntuforums.org/showthread.php?t=2111909")

I did a few things like install gufw and a few other things recommended at that thread. Also, I uninstalled gufw.

I've found that my ubuntu machine (12.04), can no longer:
[LIST]
[*]cannot be accessed frm other devices on my network, and
[*]people with whom I shared files on Ubuntu one can no longer see the contents of my shared folders.
[/LIST]

I think I must have inadvertently closed ports or something like that... although I'm not really certain what happened.

Could someone please suggest how I might allow communication from other computers and devices on my home network and fix my problem with other accessing my shared folders on Ubuntu One?

Thanks,
Old Jimma

---

### Post by carl4926 on 2013-02-05
If enable a firewall
You'll need to open no standard ports in the firewall settings

---

### Post by mikewhatever on 2013-02-05
The obvious, if only temporary, moves would be to stop being paranoid, and disable the firewall. Then learn whether you even need one, and if so, learn how to configure it.

---

### Post by Old Jimma on 2013-02-05
I don't have a firewall. gufw and firestarter are not installed.

---

### Post by 3rdalbum on 2013-02-05
> **Old Jimma said:**
> I don't have a firewall. gufw and firestarter are not installed.

Yes, you still have a firewall running.

gUFW and Firestarter are just programs to make it easy to use the inbuilt Linux firewall. Removing gUFW will not turn off the firewall.

Reinstall gUFW and turn off the firewall (allow all incoming and outgoing ports). THEN you can remove gUFW if you wish.

---

### Post by PowerBarry43 on 2013-02-05
Hi

The ubuntu firewall is ufw (Uncomplicated FireWall) and it's command line only. gufw just adds a fancy front end to configure ufw with. If you want to turn off the firewall run from a terminal

```
sudo ufw disable
```

or to open and close ports

```
sudo ufw allow 8022
sudo ufw deny 8022
```

hope this helps!

Barry

---

### Post by furything on 2013-02-05
> Hi

The ubuntu firewall is ufw (Uncomplicated FireWall) and it's command  line only. gufw just adds a fancy front end to configure ufw with. If  you want to turn off the firewall run from a terminal

 	Code:
 	sudo ufw disable 
or to open and close ports

 	Code:
 	sudo ufw allow 8022 sudo ufw deny 8022 
hope this helps!

Barry 	
Or just flush iptables

```
sudo su
iptables -F iptables -X 
iptables -t nat -F 
iptables -t nat -X 
iptables -t mangle -F 
iptables -t mangle -X 
iptables -P INPUT ACCEPT 
iptables -P FORWARD ACCEPT 
iptables -P OUTPUT ACCEPT
```

---

### Post by 3rdalbum on 2013-02-05
> **furything said:**
> Or just flush iptables

```
sudo su
iptables -F iptables -X 
iptables -t nat -F 
iptables -t nat -X 
iptables -t mangle -F 
iptables -t mangle -X 
iptables -P INPUT ACCEPT 
iptables -P FORWARD ACCEPT 
iptables -P OUTPUT ACCEPT
```

I appreciate that you're giving completeness to the answer, but you might confuse the poor chap :-) Just disabling UFW with one command or using gUFW is probably going to be easier for him.

---

### Post by furything on 2013-02-05
> I appreciate that you're giving completeness to the answer, but you might confuse the poor chap :smile: Just disabling UFW with one command or using gUFW is probably going to be easier for him.
Yeah sorry I don't use ufw. Have always gone into the nuts and bolts so to speak.

---

### Post by wlraider70 on 2013-02-05
Since ufw and gufw control iptables I would do this.

sudo service iptables stop

see if that fixes the problem, then you can fine tune it from there. It is not recommended to leave the firewall off.

---

### Post by Old Jimma on 2013-02-05
My sincere thanks to all that replied to this desparate post!

:D

I am very grateful for your replies.

What fixed the problems of closed ports was to turn ufw off simply  by issueing:

> sudo ufw disable

One responder said, '... you might confuse the poor fella with all of that complicaton! Just tell him to turn ufw off!'

Well, I attest that being possibly the very oldest of the old on the forums, it does not take much to confuse me!

The simple fix of disabling ufw worked and ports that were blocked were subsequently opened!

If  y'all are ever near 34° 0' 10" N / 84° 8' 41" W, send me a msg for a free Coke!

Sincerely,
Old old Jimma, the Eldest

---

### Post by deadflowr on 2013-02-05
It's nice that you solved that problem.

For future reference, if you don't remember whether you turned on the firewall or not use

```
sudo ufw status
```

It'll show you if the firewall is active or not.

---

