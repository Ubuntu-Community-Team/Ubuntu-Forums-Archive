---
title: "More than one antivirus"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by shinjimx on 2008-09-03
I've read some antivirus posts on this forum but I have this question.
Although a virus attack is (almost) impossible on Linux, I have an AV because all of the other PCs on my office run Win-doze and there is this nasty virus (an infected Autorun.inf) traveling on USB flash drives. I tried to clean them with the linux Avast version, but didn't find it. It is supposed that you can't (shouldn't) install more than one antivirus on Windows, is it the same on Linux? I want to try Panda and ClamAV along with Avast to clean the USB mess, any thoughts?

Thank you.

Greetings from Puebla, Mexico.

---

### Post by alzie on 2008-09-03
Its not a good idea to run more than 1 antivirus. But you could install it and not active scan,  just use it to scan on command.

You may get false positives when (if) you do a scan on your computer.

I hope this is a help to you.

---

### Post by Oldsoldier2003 on 2008-09-03
> **alzie said:**
> Its not a good idea to run more than 1 antivirus. But you could install it and not active scan,  just use it to scan on command.

+1 this advice is sound regardless of what OS you are using.

---

### Post by gandaran on 2008-09-03
you can install more than one (maybe all) antivirus in linux as long as they are not running real time scanning (which most don't or is not possible due to conflicting issues with other linux security applications, avg linux free is an example, very good complete antivirus with real time scanning but very difficult to set up real time scanning), remember, linux antivirus applications are very limited, most of them only scan for windows virus and some of them with a very small antivirus data base (like AVAST), one linux free antivirus with the full windows virus, spyware and adaware updates every hour is BitDefender Linux Scanner, it's just a command line scanner, I recomend Bitdefender, if you can handle it, no gui, but can be integrated to nautilus with a script and I also got evolution to use it for incoming email scan.

---

### Post by Oldsoldier2003 on 2008-09-03
> **gandaran said:**
> you can install more than one (maybe all) antivirus in linux as long as they are not running real time scanning (which most don't or is not possible due to conflicting issues with other linux security applications, avg linux free is an example, very good complete antivirus with real time scanning but very difficult to set up real time scanning), remember, linux antivirus applications are very limited, most of them only scan for windows virus and some of them with a very small antivirus data base (like AVAST), one linux free antivirus with the full windows virus, spyware and adaware updates every hour is BitDefender Linux Scanner, it's just a command line scanner, I recomend Bitdefender, if you can handle it, no gui, but can be integrated to nautilus with a script and I also got evolution to use it for incoming email scan.

Agreed, running more than one active scanner is always a dicey proposition. its the same in any OS.

---

### Post by billgoldberg on 2008-09-03
> **shinjimx said:**
> I've read some antivirus posts on this forum but I have this question.
Although a virus attack is (almost) impossible on Linux, I have an AV because all of the other PCs on my office run Win-doze and there is this nasty virus (an infected Autorun.inf) traveling on USB flash drives. I tried to clean them with the linux Avast version, but didn't find it. It is supposed that you can't (shouldn't) install more than one antivirus on Windows, is it the same on Linux? I want to try Panda and ClamAV along with Avast to clean the USB mess, any thoughts?

Thank you.

Greetings from Puebla, Mexico.

Why don't you just format the usb disks? That way the viruses will be gone.

---

### Post by oilchangeguy on 2008-09-03
running a/v software on any computer uses system resources. and since there are many out there who install linux on older less powerful computers adding an av program can cause un-needed performance loses. while in theory it makes good sense to want to protect the computers running windows from viruses that may be transfered from a computer running linux. in practice it's the windows user who should scan all files transfered to their computers before installing them. there is no need to run av software on a linux computer. it only scans for .exe files, and these won't run in the linux world. and if there is a linux virus out there it would have to be written to target a certain distro. so the point is, don't waste system resources by running un-needed software.

---

### Post by Nepherte on 2008-09-03
> **billgoldberg said:**
> Why don't you just format the usb disks? That way the viruses will be gone.
That still doesn't take care of the, by now, widely spread virus copies on all the other computers.

---

### Post by oilchangeguy on 2008-09-03
> **Nepherte said:**
> That still doesn't take care of the, by now, widely spread virus copies on all the other computers.

do these other computers not have av software installed? a good free av is avg [http://free.grisoft.com](http://free.grisoft.com) i use it on my windows computers, and have had no problems.

---

### Post by shinjimx on 2008-09-03
> **billgoldberg said:**
> Why don't you just format the usb disks? That way the viruses will be gone.

> **Nepherte said:**
> That still doesn't take care of the, by now, widely spread virus copies on all the other computers.

Yup, I still have to identify which machine is the cause of this... uhm... virus nightmare

> **oilchangeguy said:**
> running a/v software on any computer uses system resources. and since there are many out there who install linux on older less powerful computers adding an av program can cause un-needed performance loses.

And yes, a lot of PCs on my office are really old (5 to 10 yrs old), they got them Panda, but some barely can run Win XP... guess I have to spend some time with them...

Thank you all for your advice.

---

