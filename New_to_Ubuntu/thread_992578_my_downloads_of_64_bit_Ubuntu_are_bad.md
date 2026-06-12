---
title: "my downloads of 64 bit Ubuntu are bad"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by abrand888 on 2008-11-24
Hello,

I will appreciate help in checking correctly the winMD5Sum's (Nullriver software) of the 64-bit version of Ubuntu 8.1. I am using the WINMDSUM program installed on my hard drive. I downloaded this version twice yet every time I run this program, the md5 sums are wrong. What I did is download the Ubuntu 8.1 on to my hard disk and sent it winmd5sum program and have errors. What am I doing wrong ? I even check the hash numbers by running just MD5sums, saw the MD5 hash, compared it to the Winmdsum program and they are the same numbers and letters. My computer system is a Intel q6600 cpu capable of running 64-bit programs. 

Please let me know the correct steps should be. Indidentally the two 64-bit versions I downloaded have the same identical amount of bytes. What is the correct amount of bytes I should have downloading the 64-bit version.Will the 64-bit version fit on a standard CD ?

Thanks.

---

### Post by taurus on 2008-11-24
Try downloading it again using torrent client.

---

### Post by abrand888 on 2008-11-24
Where do I get this software torrent client and how do I use it ? I am unfamiliar with this.

Thanks

---

### Post by adult swim on 2008-11-24
if you are using windows go to [www.utorrent.com](www.utorrent.com) and download/install that.  next go to releases.ubuntu.com/intrepid and go to the link  ubuntu-8.10-desktop-amd64.iso.torrent  which is towards the bottom.  click that link and it should ask you to open it with utorrent.  then it should download.

---

### Post by abrand888 on 2008-11-24
Hi adult swim.

Thanks for answering so fast. I appreciate it. As I type, it is downloading so I will test the MD5sum tommorrow morning and hopefully it will be good. Will this file fit on a cd or do I have to use a dvd disc ?

Thanks

---

### Post by adult swim on 2008-11-24
it will fit on a cd

---

### Post by abrand888 on 2008-11-24
adult swim,

I finished downloading the torrent version, ran WINmdsum and it said that the checksums are different. I then burned the image on a cd-rw disc and it wouldn't load at all. 

Abrand888

---

### Post by jimreynold2nd on 2008-11-25
That IS weird.... Either your ISP/neighbor/brother is injecting something into your download, or your HDD is acting funny, or Windows/some Windows apps is doing something to your files (I would watch out for antivirus softwares).

Anyway, did you try the hashcheck function built into utorrent? If it returns good then your torrent download is good.

It is also possible that the hashing program you are using is not the correct one to use. If utorrent reports a good download, then it should be good. And if you cannot boot from it still, then try burn again - CD/burner/drive may be bad. Or it's a problem with your specific computer. Anyway, if utorrent reports a good download, then it's gonna be a totally different issue.

And watch out, some computer (like my Thinkpad T22) cannot boot from CD-RW but can boot from CD-R

---

### Post by abrand888 on 2008-11-25
> **jimreynold2nd said:**
> That IS weird.... Either your ISP/neighbor/brother is injecting something into your download, or your HDD is acting funny, or Windows/some Windows apps is doing something to your files (I would watch out for antivirus softwares).

Anyway, did you try the hashcheck function built into utorrent? If it returns good then your torrent download is good.

It is also possible that the hashing program you are using is not the correct one to use. If utorrent reports a good download, then it should be good. And if you cannot boot from it still, then try burn again - CD/burner/drive may be bad. Or it's a problem with your specific computer. Anyway, if utorrent reports a good download, then it's gonna be a totally different issue.

And watch out, some computer (like my Thinkpad T22) cannot boot from CD-RW but can boot from CD-R
Hi,

I ran a virus check and the download is ok. I do not know how to run the hash check function in utorrent. In the meantime, I will copy the iso file to my USB drive and burn the file to a cd-rw disc on my other computer and will report back.
Thanks

---

### Post by abrand888 on 2008-11-25
I connected my usb drive to my other computer, HP. I checked the file with a different virus checker on my HP and it was clean. I then burned a cd-rw on my Memorex external burner connected to my HP and tried it in my other computer. It started to boot up and then I got a white screen and nothing happened after that. I remember trying earlier a burned dvd-rw disc of the iso file I downloaded earlier didn't run any md5sum programs and also got the white screen. My dvd writer on my first system was bought last week but it is wierd that I couldn't make a decent cd-rw on the Intel computer I tried earlier.

Look forward to your suggestions.

---

### Post by jimreynold2nd on 2008-11-25
Try my suggestion: Use a CD-R instead of a CD-RW. If you can, try downloading it with another computer too. And I said **disable **antivirus, not **using** it on the .iso o.o

---

### Post by evilkastel on 2008-11-25
I understand some system are unable to boot the livecd from an CD-RW. if you have another PC you can also try to boot the LiveCd there, and there insert a blank Pendrive and go to System>Administraton>create a USB startp disk. Select your iso, that you should locate in the local drive on that machine.And wait. When booting the pc you want to turn into ubuntu, change the Boot priority to check USB pendrives before the hard drive, and you should be able to install ubuntu.

---

### Post by abrand888 on 2008-11-25
How do I run the hashcheck function in utorrent ? I think this should be the first test to evaluate the iso file. I could turn off the Kapersky anti virus and try and download it again but I think the hashcheck should be my first priority since I keep getting mdsums programs give me differentresults.

If I get the correct numbers, then I will try and burn a cd-r and try again. I am interested in running Ubuntu 8.1 in a livecd format for the time being. I wan't to explore it. 

Thanks

---

### Post by abrand888 on 2008-11-26
Hello,

I made  cdr and it failed. There is something weird going on. I checked the integrity of the cdr and it passed but I do not know really how to check the integrity of the hash. I burned the cdr on my Memorex external burner connected to my HP, not my Intel system where I would like to use the Ubuntu on.

Just for the fun of it, I downloaded Fedora 10 LiveCD and I also got a white screen and the mdsums were different.

Look forward to your new suggestions.

---

### Post by abrand888 on 2008-11-26
Hi,

I think I am on the trail of my problems. I made a text file of the hash numbers listed on the Ubuntu page after going through the download procedure. I installed on a computer at work winMD5sum program. I highlighted the 

ubuntu-8.10-desktop-i386.iso I downloaded and ran the calculate button. It gave me the hash numbers of 

ubuntu-8.10-desktop-amd64.iso not for the ubuntu-8.10-desktop-i386.iso so there is no way that they can be compared.I burned a cd-rw cd of the iso file I downloaded and the burn program verified my burning of the iso file and it started to run and locked up with the rectangle going across the screen. I think both versions of Ubuntu 8.1 have problems because I was unsuccessful in getting the 8.1 version to work at all.

I downloaded version 8.04, made a cd-rw cd on my Intel computer and guess what, it boots up and I am running it as a live Ubuntu 8.04. I fail to see where I made any bad downloads.

I look forward to your thoughts.

---

### Post by abrand888 on 2008-11-26
Hi,

I ran md5sum in dos mode and the hash number is for the 
ubuntu-8.10-desktop-amd64.iso not the ubuntu-8.10-desktop-i386.iso
and the hash numbers for winmd5sum from nullriver were the same.

I ran in dos mode or command prompt mode md5sub -c and the name and many files failed to open so I think the 8.10 32 or 64 bit versions are questionable.

---

