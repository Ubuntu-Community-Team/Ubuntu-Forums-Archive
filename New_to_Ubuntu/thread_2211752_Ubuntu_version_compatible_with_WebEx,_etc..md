---
title: "Ubuntu version compatible with WebEx, etc."
date: 2014-03-17
forum: New to Ubuntu
---

### Post by AbleTassie on 2014-03-17
[SIZE=3]I was unable to attend a WebEx Meeting for a LGO (Large Government Organization) recently. Tech support at WebEx tells me the problem is with my operating sytem (see [SIZE=3]MORE BACKGROUND INFO below)[/SIZE]. I was using, Lubuntu 13.10. WebEx tech support said that there is no official LGO/WebEx support for Ubuntu past 10 or 11. So it looks like to be sure I can attend a future meeting I have to install Ubuntu 10x or 11x (Gnome) or some other OS like Fedora 15 or 16 32-bit or Windows XP SP3.

QUESTION(S): Is it possible to download and install these older versions of Ubuntu (or Linux)? Any recommendation for which one would be the best? I just want to be able to attend WebEx meetings with this LGO.

Thanks,

R.

MORE BACKGROUND INFO: 

WebEx tech support sent me the following link: 
( [https://uspto.webex.com/docs/T28L/mc0806l/en_US/support/xplatform.htm#OSSUpport](https://uspto.webex.com/docs/T28L/mc0806l/en_US/support/xplatform.htm#OSSUpport) ) that describes support for various operating systems.

[/SIZE][TABLE="class: body, width: 100%"]
[TR="bgcolor: #efefef"]
[TD="width: 12%, align: center"][/TD]
[TD="width: 14%, align: center"][/TD]
[/TR]
[TR="bgcolor: #ffffff"]
[TD="align: left"]**Operating          Systems**[/TD]
[TD="class: bodySmall"][B]Windows
[/B]XP SP3, 2003 Server,         
        Vista 32-bit/64-bit, 
       Windows 7 32-bit/64-bit,
     Windows 8 32-bit/64-bit[/TD]
[TD="class: bodySmall"]**Mac OS X* **10.5, 10.6, 10.7, 10.8, 10.9[/TD]
[TD="class: bodySmall"][B]Linux

[/B]Ubuntu   10x and 11x (Gnome),
        Red Hat 5, 6, 
        Open SuSE 11.4
        Fedora 15, 16 (all   32-bit)[/TD]
[/TR]
[/TABLE]
[SIZE=3]
And the notes at the top of the page 
( [https://uspto.webex.com/docs/T28L/mc0806l/en_US/support/xplatform.htm](https://uspto.webex.com/docs/T28L/mc0806l/en_US/support/xplatform.htm) ) say:

[/SIZE]**Notes**: 

 WebEx       will support any Linux distribution as long as it meets the following       requirements:
 
[LIST]
[*]Kernel:        2.6 or later 
[*]X        Lib: X11R6 or later compatible 
[*] C++        Lib: libstdc++ 6 
[*]Desktop        Environment: XFce 4.0 or later, KDE, Ximian, Gnome 
[*]GDK/GTK+        version: 2.0 or later 
[*]Glib:        2.0 or later 
[*]Java 1.6 
[/LIST]
[SIZE=3]

[/SIZE]

---

### Post by TheFu on 2014-03-17
You did the right thing by contacting WebEx. THEY are on the hook for supporting current OSes. If they choose NOT to do so for business reasons, there isn't much we can really do. They don't support Win2000 or Win95 either.

As far as which Linux to install - I would NEVER suggest that you install any Linux that is not currently supported with active security patches especially when Java is involved. None of those Ubuntu versions are supported today, so that is NOT an option.

Fedora 20 is the current 6month support Fedora. It is meant for developers, IMHO, not end users. If Redhat 6 is still supported, that would be my suggestion. I know that RHEL 6 is still supported and will be for years.  I think it may be less expensive to install Windows7/8. [http://www.redhat.com/products/enterprise-linux/desktop/](http://www.redhat.com/products/enterprise-linux/desktop/)

Just thought of another option.  CentOS-6.  See, CentOS strives to be binary compatible with RHEL of the same release.  CentOS is GNU licensed for the effort of a download.  I'd get the latest CentOs - 6.5 and try that inside a KVM or Virtualbox VM. [https://www.centos.org/download/](https://www.centos.org/download/)

---

### Post by Old_Grey_Wolf on 2014-03-17
TheFu beet me to it. I was going to suggest CentOS 6.5 as well.

---

### Post by bluefrog on 2014-03-17
webex seems to be working with 14.04. (haven't tried and won't try 13.10)

I installed the oracle java jre then the plugin for firefox.

---

### Post by AbleTassie on 2014-03-17
> **TheFu said:**
> 
As far as which Linux to install - I would NEVER suggest that you install any Linux that is not currently supported with active security patches especially when Java is involved. None of those Ubuntu versions are supported today, so that is NOT an option.

Fedora 20 is the current 6month support Fedora. It is meant for developers, IMHO, not end users. If Redhat 6 is still supported, that would be my suggestion. I know that RHEL 6 is still supported and will be for years.  I think it may be less expensive to install Windows7/8. [http://www.redhat.com/products/enterprise-linux/desktop/](http://www.redhat.com/products/enterprise-linux/desktop/)

Just thought of another option.  CentOS-6.  See, CentOS strives to be binary compatible with RHEL of the same release.  CentOS is GNU licensed for the effort of a download.  I'd get the latest CentOs - 6.5 and try that inside a KVM or Virtualbox VM. [https://www.centos.org/download/](https://www.centos.org/download/)

Thanks Fu,

I only plan to use the OS just for the one activity of doing WebEx interviews with the one LGO for a short period of time, not cruising the internet. I would likely be uninstalling the OS in a month or two. So maybe using an OS that is not supported by active security patches is not so much of a security risk. What do you think?

Is Redhat 6 free? How do I determine if Redhat 6 is still supported?

Why do you like CentOs - 6.5? 

Would it be possible to use CentOs - 6.5 without a virtual machine set-up? 

I only have 1.25 GB of RAM, so I think a Virtualbox is not really an option. And I would guess that neither is KVM, but I don't know.

Do you think CentOs 6.5 meets the criteria in the WebEx "Notes" section I posted?

Thanks,

R.

---

### Post by AbleTassie on 2014-03-17
> **bluefrog said:**
> webex seems to be working with 14.04. (haven't tried and won't try 13.10)

I installed the oracle java jre then the plugin for firefox.

Thanks James. My Ubuntu 12.04 LTS and Lubuntu 13.10 work fine with JAVA 1.7.0_51 for using _my own_ free basic WebEx account for a desktop sharing interview. However, for the large LGO, according to WebEx, Ubuntu 12.04 LTS and Lubuntu 13.10 are not officially supported. I guess they are too new, although maybe they do meet the criteria in the "Notes" section I posted.

Thanks,

R.

---

### Post by monkeybrain20122 on 2014-03-18
Not officially support doesn't mean it won't work. Just that it is not guranteed to work. 

Yeah if it works for RHE6 it will most likely work with Centos-6.5. Redhat is not free but Centos is, basically the same thing for most part minus the technical support from Redhat and the branding. Centos is the 'community spin' of Redhat.

You don't need VM to isntall Centos, carve out a small partition may be 6-7 G (probably can do with less, but just be comfortable) and you can easily set up a dual boot with Ubuntu (not pesty like dualbooting Windows) Just don't install any bootloader in the process and when done, boot into Ubuntu to update grub ("sudo update-grub")

Edit: to install java [http://www.if-not-true-then-false.com/2010/install-sun-oracle-java-jdk-jre-7-on-fedora-centos-red-hat-rhel/](http://www.if-not-true-then-false.com/2010/install-sun-oracle-java-jdk-jre-7-on-fedora-centos-red-hat-rhel/)

---

### Post by AbleTassie on 2014-03-18
> **monkeybrain20122 said:**
> Not officially support doesn't mean it won't work. Just that it is not guranteed to work. 

Yeah if it works for RHE6 it will most likely work with Centos-6.5. Redhat is not free but Centos is, basically the same thing for most part minus the technical support from Redhat and the branding. Centos is the 'community spin' of Redhat.

You don't need VM to isntall Centos, carve out a small partition may be 6-7 G (probably can do with less, but just be comfortable) and you can easily set up a dual boot with Ubuntu (not pesty like dualbooting Windows) Just don't install any bootloader in the process and when done, boot into Ubuntu to update grub ("sudo update-grub")

Edit: to install java [http://www.if-not-true-then-false.com/2010/install-sun-oracle-java-jdk-jre-7-on-fedora-centos-red-hat-rhel/](http://www.if-not-true-then-false.com/2010/install-sun-oracle-java-jdk-jre-7-on-fedora-centos-red-hat-rhel/)

Thanks MonkeyBrain,

I take it that this JAVA link ( [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html) ) only works for Ubuntu and not Centos, correct?

Does Centos meet the WebEx "Notes" specs [SIZE=3][SIZE=2] at
( [https://uspto.webex.com/docs/T28L/mc.../xplatform.htm]("https://uspto.webex.com/docs/T28L/mc0806l/en_US/support/xplatform.htm") ), see below:
[/SIZE]
[/SIZE]**Notes**: 

 WebEx       will support any Linux distribution as long as it meets the following       requirements:
 

[LIST]
[*]Kernel:        2.6 or later 
[*]X        Lib: X11R6 or later compatible 
[*] C++        Lib: libstdc++ 6 
[*]Desktop        Environment: XFce 4.0 or later, KDE, Ximian, Gnome 
[*]GDK/GTK+        version: 2.0 or later 
[*]Glib:        2.0 or later 
[*]Java 1.6 
[/LIST]
Thanks,
R.

---

### Post by monkeybrain20122 on 2014-03-18
> **RMcGinnis said:**
> Thanks MonkeyBrain,

I take it that this JAVA link ( [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html) ) only works for Ubuntu and not Centos, correct?



That link works only for Ubuntu obviously as the webupd8 ppa is only for Ubuntu and Centos doesn't use apt-get. :)

> Does Centos meet the WebEx "Notes" specs [SIZE=3][SIZE=2] at
( [https://uspto.webex.com/docs/T28L/mc.../xplatform.htm]("https://uspto.webex.com/docs/T28L/mc0806l/en_US/support/xplatform.htm") ), see below:
[/SIZE]
[/SIZE]

If Redhat 6 does then Centos 6 does. They are basically the same.

Edited: To make a live usb for Centos in Ubuntu use unetbootin, the startup disk creator works only for Ubuntu.

---

### Post by monkeybrain20122 on 2014-03-18
BTW, you can install Centos in a usb drive so you don't even need to dual boot. You probably need to do a real install instead of live usb because you need to install packages and may be update kernel etc.. A 8 g usb flash drive partitioned to ext4 would be good enough, when you need it just plug it in and boot from it and you can use it on different computers. Since it is a single purpose installation the performance of flash drive is probably not a factor.

---

### Post by TheFu on 2014-03-18
Sorry - had to sleep.  So monkeybrain20122 is providing good advice.
Nothing will predict whether CentOS works or not like installing it. I'd give it 10G - java always needs a little more disk.  I helped someone install it on a laptop a few days ago - took about 20 minutes. During the install it provides lots of options - choose "desktop" and I would pre-setup the single partition you need before. Reuse the swap partition already on the machine. That is fine, unless you hibernate either systems.

You asked if I would be concerned running an unsupported/non-patched OS - YES!  Attacks do not just come from the outside world. They come from any device on your internal network.  TVs, media players, any connected devices, including computers, smartphones. Be afraid.

If Ubuntu 12.04 is "too new" for WebEx to support - they have huge management issues.  That is not it. I think Redhat 6 is newer. It is purely a business decision, I'm certain.  The US-DoD uses Redhat, therefore it is supported. Until a very large "paying" WebEx client uses Ubuntu - it will not be officially supported.  WebEx is from Cisco. Very large US-based corporations use it, including the US gvmt, so those companies dictate which OSes are supported.  I've worked inside a few of these and they definitely work closely with all the big hardware/software makers to get what they want.

Oh - and USB will be slow. Even USB3 is slow. It might be just fine, only you can decide.

---

### Post by AbleTassie on 2014-03-18
> **monkeybrain20122 said:**
> BTW, you can install Centos in a usb drive so you don't even need to dual boot. You probably need to do a real install instead of live usb because you need to install packages and may be update kernel etc.. A 8 g usb flash drive partitioned to ext4 would be good enough, when you need it just plug it in and boot from it and you can use it on different computers. Since it is a single purpose installation the performance of flash drive is probably not a factor.

Thanks MonkeyBrain,

I cannot boot from my USB, my PC is too old. I think I'd have to use a DVD to install Centos on my internal hard drive. 

I don't think booting off a live Centos DVD is a realistic option. I think navigating around in a pdf document during a WebEx desktop document sharing interview would be slow, probably too slow with my older PC. I need the JAVA plug-in for the WebEx interview too and I don't think comes on the live Centos DVD.

QUESTION: Or maybe the JAVA plug-in does come with the Centos live DVD. Do you think it does?

Thanks,

R.

---

### Post by TheFu on 2014-03-18
It is possible to install software while running an Ubuntu Live CD. I would be surprised if that wasn't the situation for CentOS too.

Instead of asking questions, it would have taken less time to just-try-it. Then you'd know.

---

### Post by AbleTassie on 2014-03-18
> **TheFu said:**
>  You asked if I would be concerned running an unsupported/non-patched OS - YES!  Attacks do not just come from the outside world. They come from any device on your internal network.  TVs, media players, any connected devices, including computers, smartphones. Be afraid.

If Ubuntu 12.04 is "too new" for WebEx to support - they have huge management issues.  That is not it. I think Redhat 6 is newer. It is purely a business decision, I'm certain.  The US-DoD uses Redhat, therefore it is supported. Until a very large "paying" WebEx client uses Ubuntu - it will not be officially supported.  WebEx is from Cisco. Very large US-based corporations use it, including the US gvmt, so those companies dictate which OSes are supported.  I've worked inside a few of these and they definitely work closely with all the big hardware/software makers to get what they want. 

Thanks Fu,

I appreciate the specifics in your advice. I only connect my PC to the internet via DSL (I don't feel inferior about this when I recall that Alan Turing didn't even have a PC.) I'm still concerned though. 

I have complained to WebEx tech support about not being able to attend the meeting with Lubuntu 13.10. And I plan to complete a written WebEx customer survey that complains about this as well. So maybe that will help some with WebEx support for Ubuntu in the future.

Thanks again,

R.

---

### Post by monkeybrain20122 on 2014-03-18
live cd doesn't have persistence, so every time you reboot everything is lost. I would suggest you make a small partition to set up Centos and your software. Take about half an hour for the whole thing.

---

### Post by AbleTassie on 2014-03-19
> **monkeybrain20122 said:**
> 

Edit: to install java [http://www.if-not-true-then-false.com/2010/install-sun-oracle-java-jdk-jre-7-on-fedora-centos-red-hat-rhel/](http://www.if-not-true-then-false.com/2010/install-sun-oracle-java-jdk-jre-7-on-fedora-centos-red-hat-rhel/)

MonkeyBrain,

I have now installed CentOS 6.5 and am using it to write this post. I went to the link above and tried to install JAVA, but it is not working as described below in more detail. 
                           
First I downloaded jre-7u51-linux-i586.rpm as the site suggests. I downloaded the file into the download folder,

then I ran the terminal command "rpm -Uvh /path/to/binary/jre-7u51-linux-i586.rpm"

but I get the error message: "error: open of /path/to/binary/jre-7u51-linux-i586.rpm failed: No such file or directory"

QUESTION: What am I doing wrong? It appears the PC cannot find the file.

Thank you,

R.

---

### Post by TheFu on 2014-03-19
rpm -Uvh /path/to/binary/jre-7u51-linux-i586.rpm

That must point to the location (download folder?) where the RPM was placed.  Also, sudo will be needed to install a package.

---

### Post by AbleTassie on 2014-03-19
Fu and Monkeybrain,

I figured out how to make the path correct and installed JAVA. I contacted WebEx tech support and I just tested CentOS 6.5 with the JAVA plug-in in a simulated WebEx meeting at the LGO (Large Govt Organization). And it worked, I was able to attend the meeting. So your hunch that CentOS would work seems to have been correct.

Thank you so, so much,

I will mark this as SOLVED.

R.:p

R.

---

