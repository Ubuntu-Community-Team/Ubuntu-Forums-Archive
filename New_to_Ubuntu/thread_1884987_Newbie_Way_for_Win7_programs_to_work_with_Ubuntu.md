---
title: "Newbie: Way for Win7 programs to work with Ubuntu?"
date: 2011-11-22
forum: New to Ubuntu
---

### Post by Beth431 on 2011-11-22
I am brand new to Ubuntu. Installed Ubuntu 10.04.3 version alongside Windows 7. The install went fine. I do have some knowledge of computers. I have been using Firefox, Thunderbird, and OpenQffice for years. I primarily use my laptop for email, browsing the Net, logging contacts on ham radio, and occasionally word processor documents. I store all my saved data on a separate partition on the hard drive from the windows 7 OS.

 And yes, I am sick of WINDOWS and always paying more and more money to Microsoft to correct their mistakes !! They sell me a bad Windows 7 DVD that won't install and then want to charge me $30 plus shipping for a replacement DVD !! I really really want to get away from Microsoft completely.

The only thing that has keeping me from using Ubuntu exclusively is that I am a ham radio operator and have 2 programs I use to log my contacts on the radio using Windows 7.  

I have years worth of contacts (several thousand) and do not want to lose them. These records allow me to win awards from ham radio organizations so they are very important to me. Since Win 7 has crashed again I want to start using Ubuntu exclusively if I can somehow use these logging programs. I have the contacts files saved in my data partition. Of course, the programs do not have versions for Linux OSs.

I use a program called Netlogger and also use another program called TrustedQSL for Logbook of the World from ARRL (Amateur Radio Relay League). 

Is there some way to use these programs with Ubuntu ??  Is there some type of program that will reliably run these programs in Ubuntu without having a operating Windows OS??  Or better yet.... no Windows installed at all on my laptop ??

Please keep answers simple and complete as I am a total newbie at Ubuntu.

---

### Post by Mark Phelps on 2011-11-22
The only way to use Windows apps with Ubuntu is through something known as Wine -- it replaces Windows OS calls with Linux OS calls.

Please note, however, that this is NOT a Windows emulator, that is, it does not run a Windows OS inside Ubuntu.  Thus, how well it works depends critically on the app and version you want to use.

At the link below, you will find an application compatibility database search tool:

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

Enter the app and version and look at the ratings.  Anything that is not listed is untested and is liable NOT to work.  Anything rated GARBAGE will not work.  Bronze means some functions will work, and so forth.

---

### Post by davidryderuk on 2011-11-22
Hi,

I looked up the apps when I read your post. TrustedQSL does have a Linux version, although I couldn't tell you how well it runs, since I have no idea how to use it. You can open the terminal and type:

```
sudo apt-get install trustedqsl
```

to install it.

p.s. You won't have the latest version on Lucid (10.04).

---

### Post by fantab on 2011-11-22
> **Beth431 said:**
> I am brand new to Ubuntu. Installed Ubuntu 10.04.3 version alongside Windows 7. The install went fine. I do have some knowledge of computers. I have been using Firefox, Thunderbird, and OpenQffice for years. I primarily use my laptop for email, browsing the Net, logging contacts on ham radio, and occasionally word processor documents. I store all my saved data on a separate partition on the hard drive from the windows 7 OS.

 And yes, I am sick of WINDOWS and always paying more and more money to Microsoft to correct their mistakes !! They sell me a bad Windows 7 DVD that won't install and then want to charge me $30 plus shipping for a replacement DVD !! I really really want to get away from Microsoft completely.

The only thing that has keeping me from using Ubuntu exclusively is that I am a ham radio operator and have 2 programs I use to log my contacts on the radio using Windows 7.  

I have years worth of contacts (several thousand) and do not want to lose them. These records allow me to win awards from ham radio organizations so they are very important to me. Since Win 7 has crashed again I want to start using Ubuntu exclusively if I can somehow use these logging programs. I have the contacts files saved in my data partition. Of course, the programs do not have versions for Linux OSs.

I use a program called Netlogger and also use another program called TrustedQSL for Logbook of the World from ARRL (Amateur Radio Relay League). 

Is there some way to use these programs with Ubuntu ??  Is there some type of program that will reliably run these programs in Ubuntu without having a operating Windows OS??  Or better yet.... no Windows installed at all on my laptop ??

Please keep answers simple and complete as I am a total newbie at Ubuntu.

Have you considered Dual-Booting Windows with Ubuntu...

Until you find a better Linux alternative or an equivalent to the Windows-ware you use you can Dual-Boot. Use Ubuntu for everything else.

For more info on Dual-Boot [**Read this**]("http://members.iinet.net.au/%7Eherman546/p22.html").  There is lot more information both on the Net and on this forum about dual-booting Ubuntu with windows. Just search for it and learn. You are most welcome to clear if you have any doubts.

---

### Post by Gone fishing on 2011-11-22
I was going to suggest Crossover or running Windows in a Virtual box> however Software center has xlog amateur logging program and trustedqsl. 

Do you need Windows? Linux has quite a few ham radio apps and combining Linux with HAM radio that's got to be uber geeky.

---

### Post by Beth431 on 2011-11-22
Hey guys thanks for letting me know TrustedQSL is available in the software center !!  

I'm just 2 hours into learning Ubuntu 10.04 and really liking it. 

The other program (Netlogger) I am going to try running in wine and hope it will. It was not listed when I looked at the wine compatible list. If that doesn't work then I can boot into win 7 and use it in win 7. I use NetLogger on a daily basis to log contacts when on my favorite ham radio Nets.

Thanks again !!

---

### Post by Beth431 on 2011-11-22
Just installed TrustedQSL from the software center. Now I just need to figure out how to get my certificate (encrypted key) out of win 7 and into the program here. I'm sure I will figure it out soon. Think I can export to my data partition then import to the program in Ubuntu. I'll try that later tonite.

---

### Post by rewyllys on 2011-11-22
@Beth431**

Welcome to Ubuntu!

73 from ex-KC5TS

---

### Post by mastablasta on 2011-11-23
> **Beth431 said:**
> The other program (Netlogger) I am going to try running in wine and hope it will. It was not listed when I looked at the wine compatible list. If that doesn't work then I can boot into win 7 and use it in win 7. I use NetLogger on a daily basis to log contacts when on my favorite ham radio Nets.

 
 
or you can see if there is a linux alternative that reads Netloggers files.

---

