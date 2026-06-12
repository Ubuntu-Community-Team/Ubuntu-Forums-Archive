---
title: "ATI video issue - machine unusable so cannot replace driver"
date: 2014-04-21
forum: New to Ubuntu
---

### Post by Chris_Jerome on 2014-04-21
Hi All,

I am converting a Windows XP MCE machine to Ubuntu desktop. I have tried 12.04 and 14.04. My system has an ATI card installed (I don't have the number with me, but it is supported by the proprietary driver). On either Ubuntu version, the problem is that the Dash will not display when clicked on - the screen just flickers. I am assuming what I have is a video driver problem. Because of the problem I cannot implement any solution that requires Dash - and they all seem to. I can't even get to terminal and use command line, because I can't use Dash. I had another (ATI, unfortunately) graphics card lying around, so I put that in instead. Now Dash works, but the screen cycles between a blank screen and the desktop, with the blank screen most of the time and the desktop displaying for only a few seconds. So again, I can't implement any solutions because the system is unusable. I have been pulling my hair out all weekend with this. I am wondering whether to use Putty to access the command line on this machine from another computer, but I am not sure what combination of commands to issue to fix the problem, even if I could get command line access. I have read various solutions to similar problems online, but frankly all of them have been very confusing. I just need a series of commands to issue to get the proprietary driver installed (I think), then I might be able to get it to work. I should add, I am not a complete dummy - I set up an Ubuntu webserver and built a fairly complex website on it successfully; I sort of cookbooked it, but my point is that given reasonably clear instructions I can get things done.

So, here are the solutions I have thought of. Will any of these work? Can someone advise me on the step by step commands? If none of these are likely to work, any other ideas?
1. Putty into the problem machine and fix it from the command line.
2. Install Ubuntu server, install the proprietary driver from the command line, then install desktop on top of it.
3. Is there a way to get Ubuntu desktop to boot to the command line temporarily? Some key combination during boot perhaps?
4. Buy another graphics card - are there any makes that do not have video issues? From what I have read, this kind of problem is common with ATI and NVidia cards.

I would really really like to figure this out. The machine is perfectly adequate for what I need it to do (basically, run a browser to access Netflix - yes, I know, there are some challenges there too). I really don't want to buy a new machine just because XP is dead and I can't get Ubuntu to work. And if I can get it to work, I have a Vista machine I would dearly love to convert to Ubuntu too, but at this point I am leery of trying it...

Thanks for any help!!!

Cheers
Chris

---

### Post by Mark Phelps on 2014-04-21
You do NOT want to force the installation of a proprietary driver.  If that doesn't work, you will be left with NO display.

Since you don't appear to know what video chipset you have, then boot from Ubuntu install media.  When you get to a desktop, open a terminal and enter "lspci" and look for the line containing "VGA".  Post that information back here.

Also, it makes a difference whether you're running 12.04 or 14.04, so we need to know which one you're running when you enter this command.

---

### Post by Chris_Jerome on 2014-04-21
Will do. Thanks. Chris

---

### Post by Chris_Jerome on 2014-04-21
The line says it is an AMD/ATI RV280 [Radeon 200 PRO] (rev 01).
I am currently running 14.04.

The other graphics card I had installed but have now removed was a Radeon X300LP.

Interestingly, tonight I hooked the machine to a Dell monitor using a DVI cable, and the video is solid but very slow to update. When I had the problems I reported earlier, it was hooked to a Sanyo TV using a DVI to HDMI cable (it was plugged into a port labeled HDMI (DVI)). It seems the symptoms differ depending on the hookup.

---

### Post by Mark Phelps on 2014-04-21
Sorry, but both of those are really OLD ATI cards -- and AMD dropped restricted driver support for them YEARS ago.  When you install Ubuntu it scans the hardware and installs the needed drivers.  In your case, these are the default open-source Radeon drivers -- which are all that are available for those cards today.

---

### Post by Chris_Jerome on 2014-04-22
Ha! I'M old (pushing 60) - these things are toddlers!

Seriously, thanks for the help. Looks like I have another Dell doorstop. If I were to replace the video card, are there brands that install with minimal trouble? Or will any modern graphics card work just fine?

Cheers, Chris

---

### Post by mastablasta on 2014-04-22
hmm your chip is fully 3D supported by opensource drivers: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

or at least so they claim. i have a similar issue in one of the computers i installed. for some reason a game didn't work well. after a bit of further chekcing and asking here on the forums i noticed that 3D is not enabled on boto for some odd reason. i am still troubel shooting that one.

unity needs 3D acceleration to work well.

otherwise terminal can  be opened by pressing ctrl+alt+T , while there are 6 virtual terminal available at ctrl+alt+F1  through ctrl+alt+f6. ctrl+alt+f7 will return you to desktop. if oyu use these terminal you need to login with your username and password first.

next i suggest you have a look at lighter distributions (derivatives) such as Xubuntu or Lubuntu it may be more responsive. both are Ubuntu but with a much lighter interface that does not require 3D acceleration. and at leats you might troubleshoot it more easily. the link i provided on top offers first steps in troubleshooting.

it could be your card is supported but the desktop that default Ubuntu uses is just to heavy for them. Ubuntu is aimed at modern systems that can easilly handle these special desktop effects.

yet another option is classic gnome or whatever it is called nowadays. sorry for being so vague, but i use Kubuntu and Xubuntu which have a lot different desktop user  interface.

---

### Post by SeijiSensei on 2014-04-22
> Seriously, thanks for the help. Looks like I have another Dell doorstop. If I were to replace the video card, are there brands that install with minimal trouble? Or will any modern graphics card work just fine?

It depends on whether the machine has a PCI Express slot.  I tried to see which bus that ATI card uses, and it looks to be a PCIe.  Perhaps you can check the specs for the Dell itself or post the machine's model number here.  If you have a PCIe bus, there are many choices, but I prefer [NVIDIA]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600030348&IsNodeId=1&bop=And&Order=PRICE&PageSize=20") cards.

If the machine has only the outdated AGP bus, your options are few and not well supported.  

If you have other computers that you use besides this one, I'd consider using it as a server rather than a doorstop.  Old desktop machines make fine servers.  You don't need a GUI on servers, and processing power isn't typically all that important either.

And by the way, Chris, I'm older than you!

---

### Post by Chris_Jerome on 2014-04-23
Hi All,

Thanks for the suggestions. Ubuntu Forums rock! I was thinking about lubuntu for an old netbook I have here, that's a good idea to try it on this machine. Not sure about the slots, but I noticed these two cards go in different slots, so I might have both. And this Dell box has more juice than the other one I have been using as a webserver, so maybe I will go that route. Som many options, so little time!

Thanks again to all of you. Cheers, Chris

---

