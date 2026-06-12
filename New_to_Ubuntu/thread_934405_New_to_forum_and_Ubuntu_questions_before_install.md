---
title: "New to forum and Ubuntu questions before install"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by wenbill on 2008-09-30
Hello, I am going to install Ubuntu 8.04 on a seperate,new 320gb harddrive. My mission is to try Ubuntu Studio for audio. I have a Dell Inspiron 530 with Intel Core2duo 2ghz G33 chipset, Nvidia 8300GS,Vista Home Basic. I picked up a Maudio Revo 5.1.
I have tested my Video card and audio card on the Live Cd 64amd.
 What is the best path to Ubuntu Studio for a newcomer to Ubuntu.  Should I go Ubuntu Studio altenate CD, or just start with plain Hardy and bring in Studio seperatly.
Does I386 vs 64amd have any bearing on the Nvidia video drivers ability to work with a real time linux kernel.
 I would like to experiment with some other distros, in particular 64 studio and the upcoming intrepid. Is there a partioning scheme that is better for adding distros later.
 My main concern is the Grub entry on my C: drive. From what I understand. If I choose manual install, select dev/sdb,(my 2nd drive I can then partition I can let grub reconize windows. Have there been issues with Vista and grub menu list.

 Any tips would be apreciated. thanks.

---

### Post by blithen on 2008-09-30
If you have a dual core go with 64bit ubuntu. Unless you heavily depend on Java, which is basically crap, infact it's a miracle if you can get it work in 64bit. Other that it's absoulutly perfect. Nothing wrong with it at all, in my opinion its even seems to copy and run faster in 64bit. Sorry getting of topic, it will run the video drivers just fine.

---

### Post by markbuntu on 2008-09-30
If you are going to use the nvidia proprietary drivers, install them AFTER you get ubuntu Studio up and running with the rt kernel. This is because the rt kernel installer may fail trying to install the nvidia kernel modules and the rt kernel may not work. This can also happen with the ati proprietary drivers. These drivers will work just fine when installed after the kernel.

Also, there has been a some complaints here on the forums from people trying to install from the UbuntuStudio dvd so it may just be easier to install Ubuntu and then just get the studio meta-packages. Do not try to install UbuntuStudio on Intrepid 8.10, use Hardy 8.04.

Oh, and get the 64 bit version definitely, UbuntuStudio runs much better on 64 than 32. I run them both and this has been my experience.

---

### Post by jemate18 on 2008-09-30
> **blithen said:**
> If you have a dual core go with 64bit ubuntu. Unless you heavily depend on Java, which is basically crap, infact it's a miracle if you can get it work in 64bit. Other that it's absoulutly perfect. Nothing wrong with it at all, in my opinion its even seems to copy and run faster in 64bit. Sorry getting of topic, it will run the video drivers just fine.

So you say java on 64bit ubuntu is crap? What errors or bugs you have encountered? I'm using 32bit and planning to go 64bit, but I do depend heavily on java..

Thanks

---

### Post by iansane on 2008-09-30
> 
What is the best path to Ubuntu Studio for a newcomer to Ubuntu. Should I go Ubuntu Studio altenate CD, or just start with plain Hardy and bring in Studio seperatly.


Wouldn't it be easiest to use the full ubuntu studio 8.04 DVD from ubuntustudio.org?

jemate18,

It installs openjdk by default and some apps won't work with it. They need the real Java Jre and JDK. Get errors like "wrong version of java" even after installing Jre6.
Programs like frostwire and other 3rd party apps. Also there were problems with java plugin for firefox and adobe flash for firefox on 64 bit. Don't know if those are fixed yet.

---

### Post by markbuntu on 2008-09-30
There are stickys at the top of the x86 64-bit users forum about getting java and flash to work on 64 bit. I followed them and have had zero problems with either in my 64 bit install.

---

### Post by wenbill on 2008-10-01
Thanks for the replies. I will go 64 bit.

---

