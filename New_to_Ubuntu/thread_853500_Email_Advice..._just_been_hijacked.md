---
title: "Email Advice... just been hijacked"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by shadowake on 2008-07-08
Hi guys,

What is the most secure email client for Ubuntu? I've just set up a new account with neo mailbox which provides me with an offshore account with SSL encryption etc (just had my passwords hijacked for ebay etc :( so I'm really battening down the hatches). I've set up new email addresses/user names etc but now want a decent secure mail client. I'm planning to use Ubuntu for all my web browsing/email now and just use Vista for games. Any suggestions?

:confused:

---

### Post by LowSky on 2008-07-08
Emial client doesn't really mater just make sure it supports SSL. Both Thunderbird and Evolution can support it. 

The best way to secure you accounts is to use strong encripted password with upper and lower case letters, numbers and symbols when allows. and don't use names or actual word.
```
For Example: m9V6%aP
```
If you are really forgetful use words but use numbers and sumblos inplace of simular letters
```
For Example: D0l1@rB!1L
```

---

### Post by forger on 2008-07-08
If you were hijacked there's a big chance your system is floating with rootkits :(

1) do a **[COLOR="Red"]complete format[/COLOR]** (yes, home and everything) - painful, but safe :)
2) install ubuntu on clean partitions
3) don't use wifi
4) change all your passwords, email and user login password
5) System > administration > software sources > Updates > check "install security updates without confirmation"
6) If you have other operating systems on your machine, like Windows, I suggest a checkup with several antivirus products, or even complete format/install

Doing one of these is not an option, do **all of the above**

Here's a good password-maker:
```
sudo apt-get install apg
apg
```

---

### Post by shadowake on 2008-07-08
> **LowSky said:**
> Emial client doesn't really mater just make sure it supports SSL. Both Thunderbird and Evolution can support it. 

The best way to secure you accounts is to use strong encripted password with upper and lower case letters, numbers and symbols when allows. and don't use names or actual word.
```
For Example: m9V6%aP
```
If you are really forgetful use words but use numbers and sumblos inplace of simular letters
```
For Example: D0l1@rB!1L
```

Yeah my password was just random letters and numbers so its a bit worrying how they got it. I'm an IT tech so not lack when it comes to security. But still my new passwords are much longer and I've added more upper/lower case and symbols.

Which out of thunderbird and evolution do people think is best filter wise? Does one have more settings than the other or are they about on par?

---

### Post by shadowake on 2008-07-08
> **forger said:**
> If you were hijacked there's a big chance your system is floating with rootkits :(
1) do a complete format (yes, home and everything) and start again
2) install ubuntu on clean partitions
3) don't use wifi
4) change all your passwords, email and user login password

Full system scan shows up clean on Kapersky on Vista, I've never used ebay on Ubuntu and its a recent install so no worry there. To be honest when I spoke to ebay they said a lot of users had had their accounts passwords 'guesses' in one hit. Sounds to me more like an ebay problem or a mass attak rather than a virus on my machine. I always patch my OS, have links turned off in emails and dont use any dodgy websites so have no idea how they got my password.

---

### Post by LowSky on 2008-07-08
Thunderbird (with Lghtning extention) is my favorite and is more customizable than Evolution and seems to work with spam assasin better. But Evo can be used with Microsoft exchange.. so it apples to oranges

As for what forger said, I don't think you need to go as far as erasing all your data and starting over. What I would do is uninstall firefox or what ever borwser you use, then delete the  /mozilla (and/or /firefox) directory then reinstall firefox. Use a more secure wireless connection, and change your routers settings to only accept your registered computer.

---

### Post by forger on 2008-07-08
> **shadowake said:**
> Full system scan shows up clean on Kapersky on Vista, I've never used ebay on Ubuntu and its a recent install so no worry there. To be honest when I spoke to ebay they said a lot of users had had their accounts passwords 'guesses' in one hit. Sounds to me more like an ebay problem or a mass attak rather than a virus on my machine. I always patch my OS, have links turned off in emails and dont use any dodgy websites so have no idea how they got my password.

I updated that post, read it again :)
By the way, one antivirus product for windows won't do, try:
1) sav32sfx - [http://www.sophos.com/tools/sav32sfx.exe](http://www.sophos.com/tools/sav32sfx.exe) - some general info on how to run it are here: [http://www.sophos.com/support/disinfection/klezh.html](http://www.sophos.com/support/disinfection/klezh.html)
2) sysclean - [ftp://ftp.antivirus.com/products/tsc/sysclean.com](ftp://ftp.antivirus.com/products/tsc/sysclean.com)
[ftp://ftp.antivirus.com/products/tsc/readme.txt](ftp://ftp.antivirus.com/products/tsc/readme.txt) [ftp://ftp.antivirus.com/products/tsc/](ftp://ftp.antivirus.com/products/tsc/)
 * OR * [http://housecall.trendmicro.com/](http://housecall.trendmicro.com/)

It's your call actually, if you want to live with the thief or not. You're not sure, and most certainly no-one else is:)
The suggestions I provided are the best way will provide you a clean recovery 99,9% of the time

---

### Post by aikiwolfie on 2008-07-08
Ebay are infamous for weak security. So it's not so surprising. As for Windows Vista. Well Windows is also infamous for poor security. The two combined, especially if you were using IE is just a disaster waiting to happen.

Personally I use Thunderbird. It's junk filter is pretty good and of course you can set your own filters as well. I've never used Evolution so I can't really comment there.

---

### Post by aikiwolfie on 2008-07-08
When hunting down virus in Windows I used to run several anti-virus apps. The idea is to use one application to expose the virus and the other to catch it or to let one app pick up the slack where another falls short.

With Windows you really need the full gambit of tools and a few tricks up your sleeve to catch the blighters.

---

### Post by tjwoosta on 2008-07-08
> When hunting down virus in Windows I used to run several anti-virus apps. The idea is to use one application to expose the virus and the other to catch it or to let one app pick up the slack where another falls short.

even with Windows viruses should never be that big of a problem!

its all bout paying attention to what you click on and especially what you download

i have been running the same install of windows for over a year now, while only using the free "avast antivirus" and free "safer-networking: spybot search and destroy" 

i have never encountered a problem and i download **alot of torrents**

i have been warned by avast plenty of times when downloading torrents that were infected or other files from the net
(just simply delete the  downloaded file, do a system scan and your good to go) **Avast has a huge database**

another thing that really helps is if you immunize your system with Spybot

(then whenever **any** program tries to make a registry change spybot will block it, untill you choose to allow)

---

