---
title: "two unrelated questions"
date: 2024-08-18
forum: New to Ubuntu
---

### Post by cryofreeze666 on 2024-08-18
have used ubuntu off and on in the past, but when win 10 decided i can't  use parts of my computer and i ended up having to disconnect from the net  just to reinstall 7 i became a tinfoil hat believer.  been using ubuntu regularly now, about 6  weeks.  was only using windows for games, why i went back to 7.

question 1) what is up with jammy jellyfish?  i try to dual load with win7, i tell ubuntu to install along side win7, and it blows both o.s.'s up. i can't access either o.s at boot after installation of ubuntu.  ubuntu used to be an easy installation from boot device, why'd it change?  it was so nice back when it asked which partiction, then installed it and created subsequent partitions for boot.  what's with it trying to behave like win 10/11?  seems like it would be easier to create a disk to boot from an open win7 window.  has anyone else had this problem?  no it's not my old magnetic drive, i switched to ssd's a while back.  but i have tryed installing those o.s.'s may 7 to 10 times last week, using every variation outside of installing ubuntu first since i don't know how to manually install linux, i usually auto installed, from boot device to a partition.

question 2)  i took a screen shot today ON PURPOSE.  i enlarged the square because the first screen shot was small and illegible at 100% magnification.  now i have a light and dark screen, that coincides with the area i designated for the screen shot.  how do i stop that (what seems like it's going to be) 24/7 annoyance?

---

### Post by oldfred on 2024-08-18
If previously a Windows 7 system with BIOS/MBR configuration, better to use a lightweight flavor. Ubuntu now is for newer systems with more RAM, and faster SSDs. But even an old system works much better with an SSD upgrade.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)
I use Kubuntu which is more mid-weight but has worked with external SSD on my old laptop with only 1.5GB of RAM. Ubuntu would not even install on that system. But I primarily use Kubuntu on 2017 desktop build with NVMe drive.

Are you installing both systems in same boot mode.
It became more complicated when Windows switched to UEFI boot with gpt partitioning in 2012. Windows 7 systems were BIOS with very old MBR partitioning. Systems have to be installed in same boot mode, or major issues.
But Windows 7 is very obsolete and should not be connected to Internet.

---

### Post by cryofreeze666 on 2024-08-18
ok, what about question 2?  like i haven't heard that all before about 7's insecurity.  read the publications for IT professionals, they have nothing good to say about windows updates or it's current direction.

so what your telling me is that linux no longer boot installs?  all this headache because windows thinks bios is obsolete?  not because their trying to block usage of non microsoft products (mircosoft was busted for anti trust law violation in the late 90's early 2k so don't say i need a tinfoil hat). do i gotta go find the cat head ubuntu and update it?

   don't get me started on win security.  if you can figure out how to talk to the dead, ask john mccaffe.  he created his programs after publishing the correspondence between he and microoft, about the holes in the program and microsofts need to ignore them back in the 80's.  win10/11 is what the computer was factory installed with, it just wasted to many resources and ended up being slower than 7 on my laptop (which is now almost 15 yrs. old, an old 17" toshiba satellite).  win10 gutted to the bone, awesome speed and efficiency, to bad windows won't allow you to remove their bloatware and keep it off.

   lastly, for those concerned about security, stop worrying about convenience first.  there is no way to secure convenience 100%.  best security for ANY o.s. first don't leave stuff in your computer you dont want people to have.  second, create a document with passwords, card numbers, and addresses to commonly shopped sites, store it on a thumb drive to be copied and pasted when needed, then removed, and again only connect it when you use it.  THIRD AND LASTLY turn your computer off when your not using it.  a firewall is nothing more than a scren door keeping bugs out of the kitchen. and yet gnats always make it to the peaches.

---

### Post by Impavidus on 2024-08-20
Can we have some information about your hardware? CPU, RAM, graphics, HDDs/SSDs? UEFI or legacy? GPT or MBR partitioning? Windows ties UEFI to GPT, legacy to MBR; Linux doesn't really care. UEFI and GPT are considered better now, but some computers of around 2012 don't conform to standards and make UEFI hard to use, even when available. Windows 7 was normally installed in legacy mode, but I think it's supposed to support UEFI too. Windows and Linux should be installed in the same mode. I haven't installed dual boot ssytems in a while.

As for question 2: this looks like a graphics driver problem. Does it persist after log-off and log-on? Or after a reboot? Maybe better to handle it in a separate threat.

---

### Post by cryofreeze666 on 2024-08-20
cpu, amd hexicore, can't tell you anything else i cant get the operating systems to stop eating each other

ram 32 gb

graphics nvidia geforce rtx 3060 lhr

primary drive western digital 250gb ssd secondary drive isn't an issue yet, haven't gotten the opportunity to load or format since o.s's are eating each other.

it has both uefi and legacy capability, saw that while i was making changes for the fresh install

partitioning is whatever win7 creates, cause i haven't learned how to manually install linux yet so no partition change there yet.  the version of windows 7 for my laptop supported legacy.  that copy of windows is what i am using to delete all the partitions and create a fresh install every time, i can't get a dvd or thumb drive to work after the operating systems eat each other.    not looking forward to factory resetting cmos, don't know where to buy a jumper in town and the motherboard didn't come with one that i remember (always the first thing i install so it's not lost)
my problem is that fresh install, thumb drive or dvd, doesn't matter, i went back to the last linux version i dual loaded from dvd (20.04 the cat head) just to make sure i hadn't messed some something with the install process and nothing.

this is what shows at boot when i try to run straight from ssd:

error: no such device: eb5dd190-9b83-4e8e-ad11-12bcdd035e2e.
error: unknown filesystem
entering rescue mode...
grub rescue>


 i'm thinking the last update for win10 changed my bios and i have to default cmos.

---

### Post by oldfred on 2024-08-20
If that new of a system, it should be UEFI with gpt partitioning.
Microsoft required that for all new systems with Windows 8. Windows 7 could be UEFI/gpt but only if Secure Boot off. Early versions of Windows 7 ISO did not support UEFI/gpt, but updated version did.

Are you going to use a newer Windows?
If not just use gparted on live installer and create gpt labeled drive and then install in UEFI boot mode. 
How you select to boot live installer UEFI or BIOS is then how it installs. Most tools create an installer that is UEFI or BIOS, but some may make it one or the other.
You then have to have system set to boot in the mode you installed, so if UEFI, change UEFI settings to default boot in UEFI mode.

Windows 7 may be too old for that system, so that is why you are having issues.
Whether Windows or Linux your distribution needs to be newer than the hardware, so that you have kernel & drivers that support that newer hardware.
Better then to use 24.04, or if system from 2020 or so maybe 22.04.

---

### Post by cryofreeze666 on 2024-08-28
UPDATE ON QUESTION 1 AND A NEW QUESTION:

  well i accidently found the problem while i was getting ready to uninstall and reinstall everything, for some reason 22.04 was being installed on my 2nd hard drive.  never had that problem in the past with my "off and on" usage of ubuntu, it always installed alongside windows without having to disconnect the drive that was just weird.  now win7 is up and running again, ubuntu is installed properly and i am now at 2 computers with linux, though only the gamer is dual loaded.

NEW QUESTION:  the second computer will be a crypto miner once i understand more.  my question is this, because the terminology and wording seems a bit misleading when i read.  (but then again reading an internet page is distracting at best with all the flashy adds probably misinterpreted what i read) the crypto mining operating systems, are they operating systems in a true sense?  the way i am interpretting it, makes it seem like you need an O.S. for them to run properly.  if they are an operating system why would they?  are they a dual load legitimately like what you would have with windows and ubuntu, or are they run from a thumb drive that allows you access to your primary linux O.S. and access things like wallets and exchanges?  i've asked this question of both rave os and minerstat approaching a week ago.  i have received no answer; not even a hey dumb ass we got your e-mail we'll get back too ya.  which is why i'm now asking in here.  i'm really close to getting this thing running, i'm sure of it.  i have figured out where my wallet addresses are in the exchange, got the bank account set up to receive when i sell, just trying to figure out if i have to take 20 minutes or so, to install the mining o.s. as an actual o.s., or if it's a program i run out of the thumb drive.  

JUST IN CASE IT'S NEEDED. INFO FOR COMPUTER I TURNED INTO A MINER:

new:
amd x570 motherboard
amd ryzen 9 5900x 12 core x24
250 GB m2 ssd
2 TG m2 ssd

cannibalized from old gaming computers
64 GB DDR4 RAM
radeon rx 6800
(2) geforce 1050 ti

---

