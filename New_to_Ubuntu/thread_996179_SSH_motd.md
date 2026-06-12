---
title: "SSH motd?"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by B34ST1Y on 2008-11-28
I cant seem to find anywhere that I can edit my default MOTD for the package "ssh" (server) that i'm running. Currently it spits out ```
Linux serverz0r 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
```


and I dont want it to say that....perhaps just say "welcome to the mainframe terminal....or something to that effect

---

### Post by jpkotta on 2008-11-28
It's in /etc/motd.  In Intrepid, they made this dynamic; it gets regenerated every 10 minutes with scripts in /etc/update-motd.d/.

---

### Post by B34ST1Y on 2008-11-28
how would I go about sending a disclaimer message BEFORE they log in? (like...say "if you are a government agency, or not authorized to be here, please leave NOW!")

---

### Post by a0u on 2008-11-28
> **B34ST1Y said:**
> how would I go about sending a disclaimer message BEFORE they log in? (like...say "if you are a government agency, or not authorized to be here, please leave NOW!")

The relevant file is /etc/issue.net
[http://ubuntuforums.org/showpost.php?p=4837568&postcount=8](http://ubuntuforums.org/showpost.php?p=4837568&postcount=8)

---

### Post by spiderbatdad on 2008-11-28
You remove /etc/motd. mv/rename /var/run/motd. Write new /var/run/motd. Create new symlink to /etc/motd.

sudo ln -s /var/run/motd /etc/motd

---

### Post by B34ST1Y on 2008-11-29
> **spiderbatdad said:**
> You remove /etc/motd. mv/rename /var/run/motd. Write new /var/run/motd. Create new symlink to /etc/motd.

sudo ln -s /var/run/motd /etc/motd


can you please clarify the commands you just issued? I'm terribly confused at the syntax of how its written

---

### Post by spiderbatdad on 2008-11-29
> **B34ST1Y said:**
> can you please clarify the commands you just issued? I'm terribly confused at the syntax of how its written

Doesn't appear to stick anyway. The /var/run/motd must get re-written...more research required.

EDIT:[http://ubuntuforums.org/archive/index.php/t-354514.html](http://ubuntuforums.org/archive/index.php/t-354514.html)

---

### Post by spiderbatdad on 2008-11-29
```
# Update motd
	uname -snrvm > /var/run/motd
	[ -f /etc/motd.tail ] && cat /etc/motd.tail >> /var/run/motd

```
The above is located in /etc/init.d/bootmisc.sh  commenting out should prevent updating motd each boot. Then rewritting /var/run/motd and linking it to /etc/motd should work. Of course /etc/motd must be removed before making the new link.

So this should work for you:
move /etc/motd.tail by renaming it, so you have a backup```
sudo mv /etc/motd.tail /etc/motd.tail.bak
```Edit the file called /var/run/motd ```
sudo nano /var/run/motd
```Put in your motd. ctrl+o to save, hit enter, ctrl+x to exit. Remove /etc/motd ```
sudo rm /etc/motd
```Make a symlink ```
sudo ln -s /var/run/motd /etc/motd
```also write /etc/motd.tail ```
sudo nano /etc/motd.tail
```Have it match what you want /var/run/motd to write to /etc/motd. Now edit /etc/init.d/bootmisc.sh ```
sudo nano /etc/init.d/bootmisc.sh
```

make this: ```
	# Update motd
	uname -snrvm > /var/run/motd
	[ -f /etc/motd.tail ] && cat /etc/motd.tail >> /var/run/motd
look like this:

	# Update motd
	#uname -snrvm > /var/run/motd
	[ -f /etc/motd.tail ] && cat /etc/motd.tail >> /var/run/motd


```Reboot your machine, and your motd should be what you wrote to motd.tail. If you want a banner prior to login, that is in /etc/issue.net and the option must be uncommented in /etc/ssh/sshd_config

---

