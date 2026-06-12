---
title: "Problems with PPA"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by DaimyoKirby on 2011-10-22
[SIZE=2]***NOTE:* To view the current question being answered in this thread, please see my post labeled ****Question 2******[/SIZE]

So I'm a real noob with all this system stuff; I'm trying to create a customized livecd (usb) from scratch using the instructions on [ubuntu.com]("https://help.ubuntu.com/community/LiveCDCustomizationFromScratch"). And I ran into some stuff I don't really understand.

> You may edit the sources.list in the chroot to add a  line from a PPA, if you need.  You will need to add the PPA's key to  your chroot's package manager.  On the PPA's overview page you'll see  the PPA's OpenPGP key id. It'll look something like this: 1024/12345678.  Copy it, or make a note of, the portion after the slash, e.g: 12345678.   This key will be added once we enter the chroot.


Important:  Make a backup copy of /sbin/initctl this next step will delete this  file. There is a problem with 10.04 upstart package not containing  /sbin/initctl.distrib and even after you update upstart the directions  for leaving the chroot do not seem to restore this file. 

```
sudo chroot chroot  mount none -t proc /proc mount none -t sysfs /sys mount none -t devpts /dev/pts export HOME=/root export LC_ALL=C sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 12345678  #Substitute "12345678" with the PPA's OpenPGP ID. apt-get update apt-get install --yes dbus dbus-uuidgen > /var/lib/dbus/machine-id dpkg-divert --local --rename --add /sbin/initctl
```There  is a current (for Karmic, Lynx, Maverick and any future versions of  Ubuntu that use Upstart) issue with services running in a chroot: [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430224](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430224). I didn't really understand that first paragraph, so I kinda ignored it. But then, when I was typing the terminal commands above, I got to the line where you have to substitute some PPA thing, and I don't really understand.

What does that PPA stuff mean, and what do I do with it?

---

### Post by haqking on 2011-10-22
> **DaimyoKirby said:**
> So I'm a real noob with all this system stuff; I'm trying to create a customized livecd (usb) from scratch using the instructions on [ubuntu.com]("https://help.ubuntu.com/community/LiveCDCustomizationFromScratch"). And I ran into some stuff I don't really understand.



I didn't really understand that first paragraph, so I kinda ignored it. But then, when I was typing the terminal commands above, I got to the line where you have to substitute some PPA thing, and I don't really understand.

What does that PPA stuff mean, and what do I do with it?

PPA is a personal package archive, or source of packages you may want to add to your system outside of the normal repos for example.

Say you installed pidgin and you wanted the latest then you would add the PPA for it and then it gets updated or checks for updates everytime you do a check update

---

### Post by DaimyoKirby on 2011-10-22
> **haqking said:**
> PPA is a personal package archive, or source of packages you may want to add to your system outside of the normal repos for example.

Say you installed pidgin and you wanted the latest then you would add the PPA for it and then it gets updated or checks for updates everytime you do a check update

So I would find the PPAs for any programs I installed personally, that didn't come packaged with xubuntu, or do I have to find the PPAs for all the programs I want (even if they came pre-installed) since I'm building from scratch?

Also, where would I find these PPAs and the numbers mentioned above?

---

### Post by haqking on 2011-10-22
> **DaimyoKirby said:**
> So I would find the PPAs for any programs I installed personally, that didn't come packaged with xubuntu, or do I have to find the PPAs for all the programs I want (even if they came pre-installed) since I'm building from scratch?

Also, where would I find these PPAs and the numbers mentioned above?

if you wanted a PPA for a given app then you add that PPA

if you want a PPA for another app then you add that PPA

example

if you want pidgin PPA then you would add it following instructions here [https://launchpad.net/~pidgin-developers/+archive/ppa/+packages](https://launchpad.net/~pidgin-developers/+archive/ppa/+packages)

if you wanted clementine PPA you would follow instructions here [https://launchpad.net/~me-davidsansome/+archive/clementine-dev](https://launchpad.net/~me-davidsansome/+archive/clementine-dev)

ad nauseum ad infinitum

---

### Post by sadaruwan12 on 2011-10-22
PPAs are mostly used to keep your apps on the most recent version but most of the apps we install are from the repos but most apps are out dated packages so for that if theres a particular app that we use regularly and love to keep it updated to the newest version we could add a PPA.

By adding a ppa we can receive the newest updates before the repose get updated most of the time repos keep way behind.

---

### Post by DaimyoKirby on 2011-10-22
So I just started at the top of my applications menu, and I'm going to go and find the PPAs for the programs I want, and I started with *File Roller*, xubuntu 11.10's archive manager.

I found the launchpad page for it - [https://launchpad.net/ubuntu/+source/file-roller](https://launchpad.net/ubuntu/+source/file-roller) - but I don't know where to go from there. There don't seem to be any instructions, or any numbers I can use.

(I apologize I'm such a noob about all this.)

---

### Post by haqking on 2011-10-22
> **DaimyoKirby said:**
> So I just started at the top of my applications menu, and I'm going to go and find the PPAs for the programs I want, and I started with *File Roller*, xubuntu 11.10's archive manager.

I found the launchpad page for it - [https://launchpad.net/ubuntu/+source/file-roller](https://launchpad.net/ubuntu/+source/file-roller) - but I don't know where to go from there. There don't seem to be any instructions, or any numbers I can use.

(I apologize I'm such a noob about all this.)

That isnt a PPA, there isnt always a PPA for an app

---

### Post by mike555 on 2011-10-22
you should not add ppa 's unless you need to your operating system might break , ubuntu updates most apps automatically , that is because not all ppa 's are secure (most are) if you use a ppa to upgrade an app doesn't mean the newer app will work properly ...

---

### Post by DaimyoKirby on 2011-10-22
Ok, I think I got all the ppas. I have another question though.
Is it alright if I just add the question here, since it is still about the same topic, still about creating a livecd from scratch?

---

### Post by haqking on 2011-10-22
> **DaimyoKirby said:**
> Ok, I think I got all the ppas. I have another question though.
Is it alright if I just add the question here, since it is still about the same topic, still about creating a livecd from scratch?

sure go for it as long as on topic

---

### Post by DaimyoKirby on 2011-10-22
[SIZE=3]*****Question 2*****[/SIZE]

Well, do you know of any user-friendly instructions for how to make a custom iso? These instructions are all well and good, if not a little confusing, but all I want to do is make a startup disk based on my current installation.

Anyway, if you don't, here's my next question about the instructions.
It says in the instructions:
> Install packages needed for Live System: 
```
apt-get install --yes ubuntu-standard casper lupin-casper
apt-get install --yes discover1 laptop-detect os-prober
apt-get install --yes linux-generic
```
In Maverick, discover1 was renamed to discover. Adjust the preceding lines accordingly. When I tried to run
```
apt-get install --yes discover laptop-detect os-prober
```I got an error:
Why isn't it installing right? Is it not necessary anymore or something?

---

### Post by haqking on 2011-10-22
> **DaimyoKirby said:**
> [SIZE=3]*****Question 2*****[/SIZE]

Well, do you know of any user-friendly instructions for how to make a custom iso? These instructions are all well and good, if not a little confusing, but all I want to do is make a startup disk based on my current installation.

Anyway, if you don't, here's my next question about the instructions.
It says in the instructions:
When I tried to run
```
apt-get install --yes discover laptop-detect os-prober
```I got an error:
Why isn't it installing right? Is it not necessary anymore or something?

see here [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

or you could remastersys which has been forked now into re-linux

---

### Post by DaimyoKirby on 2011-10-22
Ok, I'll try that. Thanks for your help.
Also, I liked your links in your signature; the one about antivirus was especially helpful.

**Thread Closed**

---

### Post by haqking on 2011-10-22
> **DaimyoKirby said:**
> Ok, I'll try that. Thanks for your help.
Also, I liked your links in your signature; the one about antivirus was especially helpful.

**Thread Closed**

no worries, good luck.

As for your thread closed statement at then end, if you feel thread is solved then use thread tools menu to mark as solved, cheers.

Good luck

---

### Post by DaimyoKirby on 2011-10-22
Woops, sorry, forgot about that.

---

