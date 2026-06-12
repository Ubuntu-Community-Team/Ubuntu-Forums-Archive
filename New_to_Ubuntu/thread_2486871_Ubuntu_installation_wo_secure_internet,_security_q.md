---
title: "Ubuntu: installation w/o secure internet, security questions."
date: 2023-05-15
forum: New to Ubuntu
---

### Post by grailchild on 2023-05-15
Apple has confirmed that my iPhone is hacked (after telling me what I’m describing/complaining about cannot be true). I have a Dell with an SSD & 8 gigs of ram that has so much stuff running in the background it’s unbelievable. I’m NOT in IT or a programmer. 

I want to get internet in my apt so I can start posting on various websites using a VPN (that actually works). I don’t want my iPhone connecting to a WiFi router whatsoever. My laptop needs to be wiped. It supposedly cannot be updated to window 11 which I don’t want for security purposes. 

I’m looking into hiring an IT person via upwork.com to advise me on my home internet and computer security. I need to have something simple and secure installed on my laptop first. 

How should I go about wiping my laptop and installing Ubuntu w/o a secure internet connection?

Is Ubuntu (and apps/commands) secure; Will they show me everything  & give me root admin control? 

Is Ubuntu O/S getting hacked to all he|| in the background at will via Apple / Google / Amazon / Microsoft just like my PC/iPhone? 

Browsing the apps available for Ubuntu it looks promising. 

 Ive moved to a major metropolitan city but I don’t have 1 person I trust here. My previous experiences have me fearful to use wifi whatsoever; I’ve personally experienced bluejacking / bluebugging multiple times in various parts of the country so the idea of an Internet cafe / anywhere public is likely not a good idea until I know my laptop & iPhone isn’t broadcasting itself like a beacon.

I’d like to physically remove the Bluetooth and wifi hardware from my PC  so I can only direct connect or perhaps build a small raspberry pie type deal? I was looking into routers that are also signal blockers but they’re (signal blockers) illegal to operate in the USA.  

I don’t want to use the  hotspot on my cell to assist with the wipe / install; that would be a mistake. 

My goal is to have a secure device that I can use to securely upload/stream to social media without getting DDOS attacks / hacked. Also I am writing a book that needs to remain confidential for now as the subject matter pertains to matters under us, down below. I sell vintage media related stuff on eBay as well. My point is I’m not doing .onion/DN activities or anything that could be interpreted as illegal. 

Any helpful suggestions would be appreciated.

---

### Post by ActionParsnip on 2023-05-15
You can install Ubuntu just using the ISO on a USSB stick (transferred by Rufus or some other application). You don't need an internet connection to install Ubuntu.
The default config in Ubuntu is sane but no OS is 100% secure. If you stick to the default Ubuntu repos and use root/sudo as little as possible then you'll more than likely be OK

---

### Post by ian-weisser on 2023-05-15
The thing you need to know about computer security is this: It's about safe habits (that's you), and learning (also you). It's NOT about magic bullets. Anybody selling an easy magical solution is likely scamming you.

> **grailchild said:**
> How should I go about wiping my laptop and installing Ubuntu w/o a secure internet connection?

The Ubuntu installer can be downloaded using an insecure connection. In the worst case, the hashes don't match so you don't use the file. (See? You need to learn how to use hashes).


> **grailchild said:**
> Is Ubuntu (and apps/commands) secure; Will they show me everything  & give me root admin control?

This question suggests a lack of research. You will get better answers if you do a bit of research first.
Nothing is 100% secure. It's unclear what you mean by "show me everything." You get "root admin" control...but be warned that it comes without training wheels.


> **grailchild said:**
> Is Ubuntu O/S getting hacked to all he|| in the background at will via Apple / Google / Amazon / Microsoft just like my PC/iPhone?

Lack of research. Not worth answering.
We would prefer that you not attack other organizations here. This is not a clickbait/flamewar site. Keep your strong opinions in check.
We are not here to sell you that Ubuntu is a great choice for you. Maybe it is, maybe it isn't. That's for you to research and decide.

---

### Post by BBQdave on 2023-05-16
> **grailchild said:**
> My goal is to have a secure device...

As stated previously (and in depth) start with a secure iso. Make sure your downloaded iso matches the hash value.

Then you can install offline. Or pull packages online while installing, the Ubuntu installer will pull packages from trusted repos.

Finally, user habits. If you are installing trusted packages (Ubuntu default) from trusted repos, that helps in keeping your system hardened from attack. To a certain degree, you are even protected from surfing the web, as Firefox is sandboxed (snap package) by default. But again, your safe use goes a long way in keeping your system hardened against attack.

I would also offer, that any repos you add, research the security. I add Google Chrome, for the browser and suite of applications. I researched this, and am confident in the security of Google's repo. Overall, I would use Ubuntu repos for trusted packages and applications.

---

### Post by zebra2 on 2023-05-16
I consider a Ubuntu install to be safe and secure within the limits already expressed in this thread. I have been using a default install of Ubuntu for thirteen years without a security issue.  Your biggest challenge will be to adapt to the available software packages, meaning weening yourself from Mac/Win software.  If you use the included software center you will be ok but there is also a vast amount of Premium apps outside of the Ubuntu stream that can also be used.  The point is to aim for a complete Linux transition. It took me a couple of years to accomplish that goal.  There is also the challenge of becoming familiar with the Linux command terminal which can be compared to the ancient MSDOS command line. A lot of Windows users don't even know that the Windows CMD still exists but it does and is very useful.  Using problem solving suggestions in the Linux environment will most often be given in command line format.  My suggestions is to take notes on what you learn. Linux has a reputation for being kind of "techy" which it deserves. You can get by without knowing much but you won't get very far knowing nothing. Good luck and welcome.

---

### Post by Rubi1200 on 2023-05-16
If you are looking for a stable, secure installation out of the box, you will not find many distros better than Ubuntu. But, as others have rightly pointed out, there will be a learning curve. If you are willing to accept that, then power to you. If not, you will struggle and become very frustrated.

The best place to start is first try some Linux distros from a live medium, such as USB. Doing so allows you to test them out, see what you like or don't like etc. before deciding whether to install or not.

The forums is a great place to ask questions and receive good answers from an experienced and educated community.

---

### Post by grahammechanical on 2023-05-17
I have no experience with smartphones.

In Ubuntu we use System  Settings to disable WiFi and Blue tooth. The motherboard has a memory  chip that stores details of the hardware on the motherboard. On old  machines it is called BIOS (Basic Input/Output System). On modern  machines it is called UEFI (Unified Extensible Firmware Interface). We  can access the UEFI setting utility when we switch on the machine and  before the operating system loads. In the UEFI we can disable the WiFi  and Blue tooth hardware.

If you really want to be secure when  travelling about with the machine then power it down. If you are going  to use the machine when you are not at home then only power it up when  you need to use it and switch off WiFi and Blue tooth.

Ubuntu  will connect to a home modem/router with an encrypted connection which  is password protected. I do not know if businesses that offer free WiFi  use encrypted connections. I have never used them. 

Ubuntu is  based upon the Linux kernel. This is open source software. It means that  researchers can study the source code and report any security flaws  they find. The Linux developers fix security flaws before they a taken  advantage of by the criminals.

Ubuntu developers publish a Weekly  Newsletter. It lists updates and security vulnerabilities that have  been fixed and pushed out to Ubuntu users by means of a system update.

[https://ubuntuforums.org/showthread.php?t=2486702](https://ubuntuforums.org/showthread.php?t=2486702)

In  the Ubuntu Software & Updates utility we can set the system to  check for updates at  different periods of time. But we cannot disable  the check for security updates. That check will take place every time we  switch on the machine.

I think that I am correct in saying that  the biggest threat to a machine's security is the user visiting unsafe  web sites and downloading software from sources that should not be  trusted.

Regards

---

