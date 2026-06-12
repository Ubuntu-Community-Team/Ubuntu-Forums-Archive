---
title: "Would my internet work on linux?"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by Kombaiyashii on 2012-08-02
Hi,

I really want to run my computer on ubuntu.

However, I am a little worried about installing it and then the internet not working on it. My current service provider said that they don't support linux operating systems...

Another question,

I play poker professionally and I was wondering about the security of my computer if I can get it all working properly...Would there be anyways for hackers to see my cards etc?

Thanks.

---

### Post by jfreak_ on 2012-08-02
Unless you have dial-up connection (unikely), Ubuntu does work on broadband. 

Security on Ubuntu is very good.

---

### Post by Paqman on 2012-08-02
> **Kombaiyashii said:**
> 
However, I am a little worried about installing it and then the internet not working on it. My current service provider said that they don't support linux operating systems...


Internet technology is platform-independent (that's sort of the point of the internet, it allows different machines to communicate). Your ISP won't be able to provide phone support for internet problems, but your connection will work fine.

What can sometimes be a problem is wifi, although it's rare these days. You can try Ubuntu before you install it, just download and burn it to a CD or USB, then boot up into it and try out your hardware. Any problems you do find, we can sort for you. Chances are you won't need us though ;)

> 
I play poker professionally and I was wondering about the security of my computer if I can get it all working properly...Would there be anyways for hackers to see my cards etc?


Generally security on Linux is excellent, which is one of the reasons why big companies like Amazon and Google prefer it to run their infrastructure. There are no known viruses in the wild that threaten Linux, although you're still at risk from things like phishing and social engineering.

As always the weakest link is the user. If you can keep a Windows system safe, you'll have no problem adapting to keeping a Linux one safe, because much of the best practice is the same.

---

### Post by Kombaiyashii on 2012-08-02
I see I can order a cd of ubuntu or download it...If I download it, will I be able to install it on my pc and also uninstall my current version of windows?

---

### Post by evilsoup on 2012-08-02
Ubuntu will almost certainly work with your internet, but if you're unsure just create a disk (I'd recommend a USB if you have a spare stick) using the instructions on the Ubuntu website and boot up a live environment.

By this, I mean plug in the memory stick (or insert the CD), restart your computer, and when Ubuntu boots up select the option 'try Ubuntu without installing'.

A useful guide with scrrenshots etc is: [here]("http://www.psychocats.net/ubuntu/usb") - that whole website is a good one to remember when you're getting used to Ubuntu.

Also, if you want to try out Ubuntu for a while, you can install it within WIndows at no risk to your Windows install with [WUBI]("http://www.psychocats.net/ubuntu/wubi"). That is a temporary solution though - wubi isn't intended for a long-term installation, so after a few months, if you find you like Ubuntu, you should reinstall on a separate partition (or even replace Windows entirely).

As for your other question: 'out of the box' Ubuntu is pretty secure, and the software in the Ubuntu Software Centre is also safe. You should be fine, so long as you don't install anything dodgy.

---

### Post by yoreei on 2012-08-02
Hi, [Kombaiyashii]("http://ubuntuforums.org/member.php?u=1715306")! There shouldn't be a problem with the Internet because Linux is an open source OS so many developers around the world are submitting code and even reverse engineered drivers for it. But, of course, no OS is perfect. That's one of the reasons the live CD was made - so you can see if everything works properly and then install the OS if you like it.
I am not very sure what your ISP whats to imply by saying that it doesn't support Linux. It's most likely that they won't help you if you have a problem with the Internet that is Ubuntu related. But don't you worry about that because you can always ask the Ubuntu community for such problems.

Linux has always been my favourite OS not only because of being open source, fast and flexible but also because I don't have to install anti-virus software. Why? Almost all of the viruses are focused on Windows. + A Windows virus can't harm you Linux powered computer. Most of the time you will install software from the Ubuntu Software Center. The programs there are proven to be virus-less. I would also recommend that you stick to open source software so that you are sure there isn't anything hidden in it that might be spying on you

As for the poker... This mainly depends on whether your connection with the poker server is encrypted (While playing poker, check if the browser shows an HTTPS connection, not HTTP).
I also wouldn't recommend running a server (e.g. a website server) on the same computer that you play poker on. Famous server software is secure, but hackers are hackers, you never know what they are capable of.

And by the way. If by any chance you can't connect to the Internet by wireless while using Ubuntu, you should check the ndiswrapper package. I have never used it because I never had to but I've heard that it helps when your Internet-related hardware doesn't support Linux.

---

### Post by OldHarbottle on 2012-08-02
This is more a customer service issue. In most cases if they say they don't support Linux (unless there is a real technical reason), it's because they cant be bothered to test it. 

The conversion goes something like:

big boss: does this new due Hickey support Linux
tech guy: should be fine
big boss: have we tested it?
tech guy: not yet
big boos: damn it, just say we don't support it, there's not money in Linux

---

### Post by OldHarbottle on 2012-08-02
You could always try a live dvd just to see how you get on

---

### Post by yoreei on 2012-08-02
> **Kombaiyashii said:**
> I see I can order a cd of ubuntu or download it...If I download it, will I be able to install it on my pc and also uninstall my current version of windows?
You will have an option to install it alongside Windows or replace it while running the installer

---

### Post by Kombaiyashii on 2012-08-02
thanks for the replies...

I was also wondering, I use Holdem manager 2 to collect and store my hands which uses postgresql...I really don't know what all this means but I really need that application to work. It also displays my opponents stats and updates them after every hand.

Does anyone know if this application runs well on linux?

Thanks.

---

### Post by jockyburns on 2012-08-02
What it boils down to is your ISP provider expects that their users are either on Windoze, or Mac OS. Most connection problems are software related so their helpdesk people follow a script and ask you to try differing things to resolve connection issues (but only with Win or Mac OS's)
As has been suggested, try downloading Ubuntu to a USB stick, then boot your computer from the USB stick and select try Ubuntu. If you like it and have no connection problems, you can always install it to dual boot. This means at start up, you have the option to use your normal OS or use Ubuntu. 
Just remember, Windows programs won't run in Ubuntu (at least not without Wine or Play on Linux installed) But if you choose to dual boot, you can still use your Windows programs in Win environment. 
My only regret about using Ubuntu, is , I can't now play my favourite online game,, Eve Online. 
For everything else though, I find Ubuntu is an excellent OS. 
Libre Office, does everything MS Office does. Thunderbird email client is every bit as good as Office Outlook (and supports multiple email accounts)

---

### Post by Dawnbandit on 2012-08-02
> **Kombaiyashii said:**
> Hi,

I really want to run my computer on ubuntu.

However, I am a little worried about installing it and then the internet not working on it. My current service provider said that they don't support linux operating systems...

Another question,

I play poker professionally and I was wondering about the security of my computer if I can get it all working properly...Would there be anyways for hackers to see my cards etc?

Thanks.
Wireless will probably work and a hacker would have a super hard  time trying to hack your computer.

---

### Post by Cheesemill on 2012-08-02
I think that the main issue here is whether your poker applications will run on Ubuntu.

I don't know of any poker sites that provide Linux versions of their software.

You can get *some* Windows applications to work on Ubuntu using Wine, but by no means all of them. Hold'em manager v1 doesn't work at all and no-one has tested v2 yet, you can search to see which applications will work with Wine [here]("http://appdb.winehq.org/").

At the end of the day Ubuntu is not a free version of Windows, it is a completely different operating system that runs its own different set of applications.

---

### Post by docshawnc on 2012-08-03
> **Kombaiyashii said:**
> thanks for the replies...

I was also wondering, I use Holdem manager 2 to collect and store my hands which uses postgresql...I really don't know what all this means but I really need that application to work. It also displays my opponents stats and updates them after every hand.

Does anyone know if this application runs well on linux?

Thanks.

The is a program called 'Wine' which allows windows programs such as the one you mention to run on linux.  You should still be able to use your program.

---

### Post by zombifier25 on 2012-08-03
> **docshawnc said:**
> The is a program called 'Wine' which allows windows programs such as the one you mention to run on linux.  You should still be able to use your program.

The problem being Wine's performance varies depending on software. OP, you can look your software upon [http://appdb.winehq.org](http://appdb.winehq.org) and see if your software is supported. If not, then use VirtualBox or VMWare to run Windows software.

---

### Post by KaizerLinux on 2012-08-03
I've used Viking Bet poker and Poker Stars in Wine without significant problems, and that was...3 or so years ago. I doubt support has gotten worse in that time :P 

Unfortunately info on whether or not Holdem Manager 2 works in Wine seems to be scarce, as HM 2 isn't even on the Wine DB, and 1.x hasn't been tested since 2009, on Ubuntu 8.04. You'll just have to try it out.

If all else fails you can, as has been suggested, use Virtual Box or something similar to run both the poker client and HM2.

---

