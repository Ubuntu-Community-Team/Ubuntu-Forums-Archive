---
title: "[SOLVED] More Questions About Dial-up Connections"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by lhb1142 on 2008-06-19
Several days ago I posted two questions (see my previous post entitled "Connecting to Internet via Dial-up"), one concerning playing encoded DVDs on my Ubuntu Linux computer (an Acer Extensa 5620-6419) and this question was answered quickly and accurately. The process for installing the necessary program (codec) to allow playing these discs was quite easy, far easier and more comprehensible to me than the instructions found in the two books I own - UBUNTU LINUX by William von Hagen [2007] and THE OFFICIAL UBUNTU BOOK Second Edition by Benjamin Mako Hill et. al. [2007]. I wish to thank < fatality_UK > for his clear and easy instructions.

Unfortunately, I am still unable to establish a dial-up connection. Evidently my Acer computer has a WinModem which Ubuntu Linux cannot recognize. I tried going to the sites suggested in order to "enable" my modem but I am completely overwhelmed by the suggestions found there.

I just don't understand what I am supposed to do!!

So, in light of that, I have some further questions:

Would I be able to use an external modem to connect via EarthLink dial-up? If yes, which external modem currently available new would be suitable for this purpose?

If I am unable to obtain a suitable modem or configure the one I have, my next question is: Is it "safe" to conduct online banking and credit card purchases on a hotel's unsecured wireless access point (or even a hotel's wired LAN) when using Ubuntu Linux? In other words, would a "hacker" be able to see what I'm doing? Would a "key logger" or other nefarious program be able to interpret what I am typing (including passwords and account numbers) on a Ubuntu Linux computer?

In other words, does using Ubuntu Linux make a difference in such a case?

My banking and credit card services all claim that their sites are encrypted - would this make any difference? (Frankly I feel much safer doing online financial transactions via dial-up when I am away from home.)

I thank any and every person who will reply to me.

---

### Post by phil66 on 2008-06-19
I have two serial external modems that I use to connect via Linux or Windows

One is a USRobitics 56k faxmodem v.92
The other is a Zoom 3049c v90

I have used these on 3 different ISP's without any problems

It has only been a matter of setting the proper modem software.

These modems stated they were compatible with Linux

Hope this helps

---

### Post by Sarah L on 2008-06-19
An unsecured wireless network allows any nearby person with a wireless card to capture all of the packets that you are sending to the router. Basically, they can see which sites you are going to and what you are sending and receiving.

Most online banking sites use an HTTPS connection, which encrypts your data, making it difficult to read even if someone manages to capture it. However, it's never a good idea to send out your sensitive information openly in the air. The wired LAN is probably a better idea if you're going to use a hotel's connection for banking.

Linux computers can indeed harbor keyloggers and other nasties, but they will generally have a hard time getting installed onto your system due to Ubuntu's excellent security policies. As long as you don't visit any untrusted websites or install any suspicious software, you should be OK. You do get a better degree of protection with Linux than you do with Windows.

As for the modem, can you post some more detailed info about it? Try the command "lspci -v" in a terminal and see if you can find the entry for your modem.

Best regards,
Sarah

---

### Post by lhb1142 on 2008-06-20
I wish to thank phil66 and Sarah L for their helpful answers. It is much appreciated by this Ubuntu Linux "newbie." Thanks again.

---

