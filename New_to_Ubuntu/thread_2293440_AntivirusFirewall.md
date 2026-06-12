---
title: "Antivirus/Firewall?"
date: 2015-09-05
forum: New to Ubuntu
---

### Post by Crackers.sl on 2015-09-05
I have been temped by Linux over a few years but now win10 is out and I am told it is fully of spywear and in here I read it again I will try and get to understand Ubuntu.
Firstly what is a good and recommended  Internet Security Suite program for Ubuntu? Firewall/virus
 With Windows I used AVG, 
Thanks for any help.
I see there is a place with a lot of softwear so will have a look in there.

---

### Post by QIII on 2015-09-05
Moved to its own thread.

---

### Post by coldraven on 2015-09-05
You can use Clam AV, it should be in the Software Centre.
 AFAIK Ubuntu by default has all ports closed but you can enable UFW for fine control.
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by mikewhatever on 2015-09-05
There is no "recommended Internet Security Suite". The general mindset is something like: ...why would you need one?
Now, it's not that Ubuntu is immune, and you can even use AVG on Ubuntu, but that's not going to make it more secure.

---

### Post by howefield on 2015-09-05
> **Crackers.sl said:**
> Firstly what is a good and recommended  Internet Security Suite program for Ubuntu? Firewall/virus.

Have a browse at this [Basic Security]("https://wiki.ubuntu.com/BasicSecurity") wiki page..

---

### Post by Crackers.sl on 2015-09-05
Thanks for the advise

---

### Post by Topsiho on 2015-09-06
I support the advise given above, fully. Please read the Basic Security Wiki page given by Howefield, however, it is a lot of reading which might give you the impression that antivirus and an extra firewall is an issue in a Linux computer, which it generally is not.

As is, Ubuntu is quite safe already, and normally you don't need to take any actions. Except:

1. If you run a server, such as a mail server or so. Then you need to enable ufw (Ubuntu Fire Wall) once:

sudo enable ufw.

to give you a better protection. Ufw is already installed but disabled by default (!), as it is not considered necessary really.
See also man ufw for more information (in a terminal type: man ufw )

2. Though Linux generally and Ubuntu in particular are not threatened by any virus, and if you are careful (don't install from anywhere else than from the Ubuntu repositories) by malware, files that you send to a Windows computer may contain viruses and other that are harmless for your Linux, but not so for Windows. In that case you may want to scan such files first using Clamav before sending them to the Windows computer. Clamav is in the repositories, and is always fully updated if you do install all updates as soon as they pop up.

See also: [http://askubuntu.com/questions/250290/how-do-i-scan-for-viruses-with-clamav](http://askubuntu.com/questions/250290/how-do-i-scan-for-viruses-with-clamav)

Topsiho

---

### Post by HermanAB on 2015-09-06
Linux pretty much *is* a firewall.

The default install of Ubuntu is secure enough, you don't need to add anything.

Relax and enjoy your new system.

---

### Post by bashiergui on 2015-09-06
> **HermanAB said:**
> Linux pretty much *is* a firewall.
Except when it isn't. Linux will do whatever you configure it to do. In no circumstances would I describe a vanilla installation of Ubuntu *as* a firewall. The desktop default installation *has* a firewall, but in no way *is* it one. To say Linux is a firewall is deliberately misleading, or it indicates that you don't know what a firewall is. [quote=Crackers.sl]I have been temped by Linux over a few years but now win10 is out and I am told it is fully of spywear and in here I read it again I will try and get to understand Ubuntu.[/quote]Windows isn't designed for privacy out-of-the-box, but neither is Ubuntu. Both default installations have been accused of having "spywear". The designers would say that these features enhance the user experience. Regardless of your opinion on the matter, you can configure both to be more private. Here's how in Windows:
[http://lifehacker.com/how-to-configure-windows-10-to-protect-your-privacy-1716204024](http://lifehacker.com/how-to-configure-windows-10-to-protect-your-privacy-1716204024)

And here's how in Ubuntu:
[http://www.techrepublic.com/blog/linux-and-open-source/how-to-change-your-privacy-settings-in-ubuntus-unity-dash/](http://www.techrepublic.com/blog/linux-and-open-source/how-to-change-your-privacy-settings-in-ubuntus-unity-dash/)

Simply changing operating systems from one vanilla version to another won't improve your privacy. Unless you switch to Tails or another operating system specifically designed for privacy.

---

### Post by tristan16 on 2015-09-06
> **bashiergui said:**
> Except when it isn't. Linux will do whatever you configure it to do. In no circumstances would I describe a vanilla installation of Ubuntu *as* a firewall. The desktop default installation *has* a firewall, but in no way *is* it one. To say Linux is a firewall is deliberately misleading, or it indicates that you don't know what a firewall is. Windows isn't designed for privacy out-of-the-box, but neither is Ubuntu. Both default installations have been accused of having "spywear". The designers would say that these features enhance the user experience. Regardless of your opinion on the matter, you can configure both to be more private. Here's how in Windows:
[http://lifehacker.com/how-to-configure-windows-10-to-protect-your-privacy-1716204024](http://lifehacker.com/how-to-configure-windows-10-to-protect-your-privacy-1716204024)

And here's how in Ubuntu:
[http://www.techrepublic.com/blog/linux-and-open-source/how-to-change-your-privacy-settings-in-ubuntus-unity-dash/](http://www.techrepublic.com/blog/linux-and-open-source/how-to-change-your-privacy-settings-in-ubuntus-unity-dash/)

Simply changing operating systems from one vanilla version to another won't improve your privacy. Unless you switch to Tails or another operating system specifically designed for privacy.

If you read the legal notice, **[COLOR=#000000][FONT=Ubuntu]Unless you have opted out (see the “Online Search” section below), we will also send your keystrokes as a search term to productsearch.ubuntu.com... [/FONT][/COLOR]**[COLOR=#000000][FONT=Ubuntu]

[SIZE=2]So even when online results are included in the dash, your search is kept private. Canonical gets your search term and IP, which is what Google, Bing, Yahoo!, or any other search engine would get. Your search is then sent from productsearch.ubuntu.com to the third parties.

The third parties just get a search request from productsearch.ubuntu.com. If you're concerned about privacy, you should be concerned about the first party (Canonical), and if you're concerned about that, you either shouldn't be using Ubuntu, or you shouldn't use the internet.[/SIZE]
[/FONT][/COLOR]

---

### Post by DuckHook on 2015-09-06
At the risk of getting on my soapbox (yet again&#8213;some might say), I would only add that by far the biggest risk in computing is not the OS or the tools we use, but our own irresponsible and risky computing habits. No hardened OS or AV or Magic App will help if the user is intent on inviting trouble, or acting like a fool.

So, the challenge that most Windows migrants have when coming to Linux is not the apparent dearth of "tools", but the change in mindset from the old: "do whatever fool thing I want and let AV look after the consequences" mindset to a new: "no AV but act wisely and take responsibility for consequences" mindset. The latter requires a commitment to learning about real security and acting with discipline and accountability, but it has the advantage of being a true solution rather than the false one pushed by proprietary OS and AV vendors.

Linux *does* have security tools. They are excellent and, in my opinion, far better than those in the proprietary space. But they are very different than what you are used to, because they are designed with the expectation of this Linux accountability.

This question comes up recurrently on these forums all the time. Rather than repeating the same things endlessly, you might find [this]("http://ubuntuforums.org/showthread.php?t=2184758&p=12833795#post12833795") old thread useful.

---

### Post by tristan16 on 2015-09-06
Very well said, @DuckHook.

---

### Post by Aidan_Owen on 2015-09-06
Internet security software generally isn't required for Linux considering it's a much more secure platform compared to Windows. Viruses and spyware are nearly nonexistent for the platform, likely because of it's low demographic (but it's growing, so that's something to consider) as well as the secure core, as I already said. I'd only really recommend an anti-virus application if you sincerely feel you need one or are downloading software from shady, unknown repositories. Of course, as said above by others, you can enable the firewall if you feel it is necessary, with ```
sudo enable ufw
```

TL;DR it's not really necessary. Linux is a very safe platform. Relax and enjoy your new OS. Cheers! ):P

---

### Post by bashiergui on 2015-09-07
> **margaretcogburn said:**
> You don't need antivirus software in Ubuntu, Linux Mint and Debian. Because a *_Windows_* virus can't do anything in Linux. Mainly because _*malware designed to run on Windows won't run on linux (unless you're running Wine).*_
You almost had it. I have modified your statement so that now it's true.
> The best protection against viruses is this:
- install a well-supported Linux, like Ubuntu or Linux Mint;
- check daily for updates;
- install only software from the official software sources;
- simply use your common sense.Reasonable advice.

---

### Post by Habitual on 2015-09-08
> **Crackers.sl said:**
> Security Suite program for Ubuntu? Firewall/virus With Windows I used AVG,
Security on either OS is not a program. ;)

[Herman is right.]("http://ubuntuforums.org/showthread.php?t=2293440&p=13351243#post13351243") Relax and Enjoy.

---

