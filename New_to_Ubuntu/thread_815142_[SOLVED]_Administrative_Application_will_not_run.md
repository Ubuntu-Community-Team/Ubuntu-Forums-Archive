---
title: "[SOLVED] Administrative Application will not run"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by Horomancer on 2008-06-01
Hello,
I've recently updated to hardy and am having a variety or problems with it.
First, I can't update. The little icon appears saying 5 new updates are ready for download, and when i hit the install button, nothing happens. The app sits there and runs until I use 'xkill' on it. Force quite didn't seem to work on it so now I have a 'kill' button on my tray.
I then go to the synaptic packet manager and after clicking on the icon a small tab opens on the tab manager at the bottom of my desktop saying 'Starting Administrative Application'. After about 30 seconds this tab closes and nothing happens.
The same thing happens when i click on Administration> Hardware Drivers, Administration> Hardware testing and a few other applications in the Administration tab.
I've tried running

sudo apt-get update

and

sudo apt-get upgrade

in the terminal, but it said that nothing was in need of upgrade, though i still have the upgrade icon on my system tray.

on a side note- After upgrading to hardy from gutsy, will i need to go and re-set my repository list and keys?
Much thanks

---

### Post by SunnyRabbiera on 2008-06-01
hmm, did you try a restart?
perhaps something is hanging.

---

### Post by aysiu on 2008-06-01
Paste this command in the terminal: ```
gksudo update-manager
``` and then post an error messages back here.

---

### Post by Horomancer on 2008-06-01
I cut and pasted the text line into my terminal
Nothing is happening.
the cursor droped down one level after i hit 'enter' and is just blinking there

I've restarted my comp serveral times since i've upgraded

---

### Post by aysiu on 2008-06-01
Try this:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by Horomancer on 2008-06-01
HMMM...
Ok so i closed down my terminal and read through the fixsudo walkthrough
I have not done anything the walkthough said.
I opened a terminal and typed in

sudo update-manager

the update manager opened and installed the 5 files without a hitch. The terminal also gave me this readout

jackmo@time-control:~$ sudo update-manager
sudo: unable to resolve host time-control
[sudo] password for jackmo: 
current dist not found in meta-release file
current dist not found in meta-release file
current dist not found in meta-release file
jackmo@time-control:~$ 

I tried to open Administration> Hardware Drivers and nothing happened again. I'm going to reboot into recovery mode and go through the guide you posted.

---

### Post by Horomancer on 2008-06-01
OK i went through the guide and nothing seemed out of place in my /etc/group and /etc/sudoers files

I just now tested my sudo by 

sudo mkdir /home2

in the terminal and it created that directory.
i can still not access my hardware driver configuration screen.

---

### Post by ]TheNose[ on 2008-06-01
I had the same problem and this fixed it for me:

> **PmDematagoda said:**
> Open the hosts file for editing with:-
```
gksudo gedit /etc/hosts
```
and edit it to make it look like this:-
```
127.0.0.1 localhost
**127.0.1.1 time-control**

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts 
```
save the file.

That should fix the problem.

I changed the second line to your computername: time-control
Other people should change it to their computername.

Log out, log in and everything should work again!

---

### Post by philinux on 2008-06-01
Just post 

cat /etc/hosts

---

### Post by Horomancer on 2008-06-01
YAY!
I can access Synaptic and other Administrative apps now.
The line

127.0.1.1 time-control

was listed as

127.0.1.1 time-control.Mshome

I deleted the .Mshome and things seem to be ok now.

jackmo@time-control:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 time-control

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by aysiu on 2008-06-01
Glad you got it fixed. On an unrelated note, make sure you use *gksu* or *gksudo* instead of *sudo* for graphical applications. More details here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

