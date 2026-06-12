---
title: "MS office on wine- help needed"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by Lingadharini on 2012-09-23
I recently installed wine on my lucid lynx(10.04) with the terminal command sudo apt-get install wine.
The installation was successful. I tried installing a game 'Exotic farm' which is an .exe file. It installed. When I tried to open it from Applications->Wine->Programs-> Gametop->Exotic farm, my taskbar shows 'opening exotic farm' but after sometime it goes off without opening or showing any message.
I tried installing MS office 2010 with wine. It showed some MSXML parser error. I got that file from the microsoft website and installed it. Then I began MS office installation. It didnt get installed completely. Said that some unknown problem has prevented it from installing.

Next I tried installing MS office 2007. It got installed. Now when I try opening Ms Word from app->Wine->Programs->MS office menu it began with starting MS office..but later showed a dialog box that some unexpected error occurred.

Whats wrong?

Is that a problem with my wine installation? or do I have to install any more softwares to make windows softwares work with lucid?

I need MS office desperately..I am opeing windows just wen I have to worrk on MS office...Kindly tell me wats wrong..and What I have to do.

Thanks.

---

### Post by RikoW on 2012-09-23
Hi,

check this post as reference for a successful MS Office 2010 install:

[http://ubuntuforums.org/showthread.php?t=1885051]("http://ubuntuforums.org/showthread.php?t=1885051")

If you desperately need MS Office to work, you may consider purchasing a wine version tailored to run Office:

[http://www.codeweavers.com/]("http://www.codeweavers.com/")

If you only need Word, Excel, Powerpoint you are probably fine with the wine references. Outlook usually causes more trouble, where CXoffice is of help. I use it since several years because I also need the full Office compatibility and I'm very satiesfied with CXoffice.

Cheers,
           Riko

PS: The wine sub-forum here may be the better place to post: [http://ubuntuforums.org/forumdisplay.php?f=313]("http://ubuntuforums.org/forumdisplay.php?f=313")

---

### Post by Wim Sturkenboom on 2012-09-23
Check here how well MS Office is supported: [http://appdb.winehq.org/appview.php?appId=31](http://appdb.winehq.org/appview.php?appId=31)

The installer for 2010 (64bit) is rated 'garbage' (implying it does not work); 32 bit version seems perfect (platinum). The installer for 2007 is rated silver.

You can also find the individual components (word, excel, ...) there.

---

### Post by Mark Phelps on 2012-09-23
Windows software, in general, does not work well with Wine or any of its companion products.  MS Office products have an especially bad reputation.  

The link to the WineHQ website is something you need to use BEFORE trying to install any MS Windows product.  If you need to rely on an MS Windows product, any rating less than Gold is going to be a waste of your time.

If you need to rely on MS Windows products daily, then staying with MS Windows is your best bet.  That is the ONLY thing that is 100% compatible with MS Windows.

And yeah, you can install MS Windows in Virtualbox, but that requires (1) full installation media (which does not come bundled with a PC preinstalled with MS Windows), and (2) complete reinstallation from scratch -- including all apps and data.

---

### Post by TheMTtakeover on 2012-09-23
> **Lingadharini said:**
> I recently installed wine on my lucid lynx(10.04) with the terminal command sudo apt-get install wine.
The installation was successful. I tried installing a game 'Exotic farm' which is an .exe file. It installed. When I tried to open it from Applications->Wine->Programs-> Gametop->Exotic farm, my taskbar shows 'opening exotic farm' but after sometime it goes off without opening or showing any message.
I tried installing MS office 2010 with wine. It showed some MSXML parser error. I got that file from the microsoft website and installed it. Then I began MS office installation. It didnt get installed completely. Said that some unknown problem has prevented it from installing.

Next I tried installing MS office 2007. It got installed. Now when I try opening Ms Word from app->Wine->Programs->MS office menu it began with starting MS office..but later showed a dialog box that some unexpected error occurred.

Whats wrong?

Is that a problem with my wine installation? or do I have to install any more softwares to make windows softwares work with lucid?

I need MS office desperately..I am opeing windows just wen I have to worrk on MS office...Kindly tell me wats wrong..and What I have to do.

Thanks.

Wine is a 32-bit program so be sure that you aren't trying to run 64-bit applications in it, because they won't work. I had Office 2010 running in Crossover and I have to say that if you rely on those programs alot, you are better just run them on Win or Mac.

---

