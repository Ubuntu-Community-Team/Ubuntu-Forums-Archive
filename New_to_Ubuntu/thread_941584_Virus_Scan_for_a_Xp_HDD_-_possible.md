---
title: "Virus Scan for a Xp HDD - possible?"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by flameproof on 2008-10-08
Hi,

I have the tough to remove srosa.sys on my Xp PC. The virus diabled S&D and FreeAV (this is not a valid win32 application) and Ican't start in safe mode either. Some Xp directories are not visible now (i.e. system32/drivers)

I took out the HDD and hooked it up on my Ubuntu PC. I can see all directories and could remove some files.

Is there a virus scanner/cleaner for Ubuntu that I can use to scan/clean the hooked up Xp HDD?

I use now the internal Ubuntu scanner and let it run overnight. 

Will an online scanner work? Or is there something better I should try tomorrow morning?

---

### Post by tuxxy on 2008-10-08
ClamAV, Avast are both available

---

### Post by ayenack on 2008-10-08
Not available anymore it seems. I thought that it was but it turns out that it's not. Disregard the message bellow.

I'd go for AVG Free Edition that should do the job.

It can be downloaded here.
[http://free.avg.com/download?prd=afe](http://free.avg.com/download?prd=afe)

---

### Post by SuperSonic4 on 2008-10-08
I believe you should also run it as root and be sure it scans /media

---

### Post by chaosdesigner on 2008-10-08
> **ayenack said:**
> Not available anymore it seems. I thought that it was but it turns out that it's not. Disregard the message bellow.

I'd go for AVG Free Edition that should do the job.

It can be downloaded here.
[http://free.avg.com/download?prd=afe](http://free.avg.com/download?prd=afe)


On the ClamAV homepage it looks like its available. I think it's even includet in Ubuntu so you just need to type:

```

sudo apt-get install clamav

```

You will find more here: 
[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

You can also go to the offical page:
[http://www.clamav.net/download/packages/packages-linux](http://www.clamav.net/download/packages/packages-linux)

Edit:

[All ubuntu virus scanner](https://help.ubuntu.com/community/Antivirus)

---

### Post by ayenack on 2008-10-08
> **chaosdesigner said:**
> On the ClamAV it looks like its available. I think it's even includet in Ubuntu so you just need to type:

```

sudo apt-get install clamav

```

You will find more here: 
[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

You can also go to the offical page:
[http://www.clamav.net/download/packages/packages-linux](http://www.clamav.net/download/packages/packages-linux)

Edit:

[All ubuntu virus scanner](https://help.ubuntu.com/community/Antivirus)

No i meant that AVG Free Edition is not available for Linux anymore. ClamAV is available and is installed as you pointed out.

The only problem with ClamAV (at least last time I used it) is that it shows false positives when scanning windows partitions and cause a great amount of damage if you don't know what you're doing. Not sure if this problem still persists but I know it was a problem last time I used it, which was admittedly quite some time ago know (a year or two.)

---

### Post by flameproof on 2008-10-08
Is there anything I can run from an USB stick?

---

### Post by chaosdesigner on 2008-10-08
Ok sorry i missunderstood you.

@thread starter

You basicly have these Options:


ClamAV Antivirus 

AVG Antivirus

Panda Antivirus 

F-Prot Antivirus 

BitDefender Antivirus 

avast! Linux Home Edition 


which one you choose is up to you, they are all good and all have positiv aspects. 

(ClamAV has the advantage that it's opensource)

Edit:

I'm pretty sure that you can make all of these bootable of an usb stick, you just need to find out how :D. Google might help you.

---

### Post by ayenack on 2008-10-08
> **chaosdesigner said:**
> Ok sorry i missunderstood you.

@thread starter

You basicly have these Options:


ClamAV Antivirus 

AVG Antivirus

Panda Antivirus 

F-Prot Antivirus 

BitDefender Antivirus 

avast! Linux Home Edition 


which one you choose is up to you, they are all good and all have positiv aspects. 

(ClamAV has the advantage that it's opensource)

Edit:

I'm pretty sure that you can make all of these bootable of an usb stick, you just need to find out how :D. Google might help you.

AVG is not available anymore for linux.

---

### Post by Keen101 on 2008-10-08
You could create a live-usb with this.

[https://launchpad.net/liveusb](https://launchpad.net/liveusb)

Then I'd probably install clamav with synaptic and a GUI front end for clam av so you can configure it. Then put it in the xp machine and select boot from usb in your BIOS.

Of course since this will be a live-USB you will have to re-install clamav everytime you boot it. You will need a USB with at least 700mb 1gig recommended. But, it would really be better if you had a 4gig usb drive or bigger in which you could just install to from the live-cd, but you probably don't have one of those.

---

### Post by chaosdesigner on 2008-10-08
[http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl)

:confused:

---

### Post by ayenack on 2008-10-08
> **flameproof said:**
> Is there anything I can run from an USB stick?

You could install a LiveCD to USB stick with persistent partition then install one of the above mentioned Anti Virus scanners.

Download IceBuntu this guide was written for IceBuntu 1v1 but should work with newer versions.

[https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu#Release%202.3](https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu#Release%202.3)

Follow the guide bellow.

How to IceBuntu on USB.

[http://icebuntu.6.forumer.com/viewtopic.php?t=24](http://icebuntu.6.forumer.com/viewtopic.php?t=24)


There are also a few LiveCD's that do the same thing have a look at these.

[http://www.f-secure.com/linux-weblog/2008/06/19/f-secure-rescue-cd-300-released/](http://www.f-secure.com/linux-weblog/2008/06/19/f-secure-rescue-cd-300-released/)
[http://www.e-fense.com/helix/](http://www.e-fense.com/helix/)

---

### Post by ayenack on 2008-10-08
Not sure but you might have some problems if you're running a 64Bit OS. I notice you have a 64Bit CPU. You should research this to be sure.

---

### Post by ayenack on 2008-10-08
> **chaosdesigner said:**
> [http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl)

:confused:

It's an old version and as far as I know not supported or soon to be not supported. Could be wrong though.

---

### Post by stalkingwolf on 2008-10-08
This is a good online scanner, but as I recall you must use Internet explorer.[http://housecall.trendmicro.com/]("http://housecall.trendmicro.com/")

---

### Post by bumanie on 2008-10-08
The easiest thing to do is either run clamav from your ubuntu install or to run it off the live cd. If you add the gtk front-end you will have a gui that will allow you do a recursive scan of any part of windows - clamav is often more up to date than some of the commercial av programs and it does remove/delete suspect files, not just quarantine them.

---

### Post by SunnyRabbiera on 2008-10-08
> **bumanie said:**
> The easiest thing to do is either run clamav from your ubuntu install or to run it off the live cd. If you add the gtk front-end you will have a gui that will allow you do a recursive scan of any part of windows - clamav is often more up to date than some of the commercial av programs and it does remove/delete suspect files, not just quarantine them.

actually klam is a better front end, I dont like the clam GTK interface.
Klam is in the repositories.

---

### Post by sleepingdragon on 2008-10-08
I personally going to gun for Avast!. The interface is a little rough, but gives good detail of the scan, it's also pretty quick too. 

I'm often scanning Win HDDs, Avast! certainly works for me.

---

### Post by aysiu on 2008-10-08
I know this isn't going to be a popular opinion, but I think your best bet with a compromised machine is to reinstall Windows. That's the only sure way to know you've cleaned out all the malware. It may also take about the same time as cleaning it up with an anti-virus anyway. Just my two cents. You don't have to listen to me if you don't want.

---

### Post by ayenack on 2008-10-09
> **aysiu said:**
> I know this isn't going to be a popular opinion, but I think your best bet with a compromised machine is to reinstall Windows. That's the only sure way to know you've cleaned out all the malware. It may also take about the same time as cleaning it up with an anti-virus anyway. Just my two cents. You don't have to listen to me if you don't want.

+1

If you're sure you've got an infection then that's the way to go I'd have to agree. It's hard to be sure at times if the system is infected or not so maybe run a virus scanner on it to find out then if positive re-install.

---

### Post by flameproof on 2008-10-10
Here is an update:

Symptoms on my Xp PC:

Can't see some directories (windows/system32/drivers/ )
Spybot and FreeAV won't start (this is not an Win32 apllication)
I was not able to re-install Spybot and FreeAV

What I did:
Put the HDD as 2nd HDD to my Ubuntu PC
did a virus scan 
Found some infected files and deleted them
Could also see all hidden directories

then moved HDD back to my Xp PC
removed and re-installed Spybot and FreeAV
Searched registry for srosa, hldrrr, etc and deleted them manually
did a scan with spybot and freeAV (and deleted a lot of stuff)
Today did a check with IceSword (nice tool!)

Xp PC seems to run OK now. Still can't see the hidden directories though, but it's not a major issue.

I am sure there is still some bad stuff hidden somewhere.

OK, any idea how I can unhide those now hidden directories?

---

### Post by bumanie on 2008-10-10
I can see all those things on xp from within ubuntu on my computer. Are you sure they are not hidden from within windows? Boot into windows and ensure you have clicked to unhide everything. You then should be able to scan with clamav from ubuntu. In theory, you should be able to scan every bit of windows from within ubuntu, hence the reason there are so many linux-based rescue tools around that are specifically aimed at repairing/fixing windows installations.

---

