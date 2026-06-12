---
title: "ubuntu 8.04.1"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by ulindel on 2008-08-25
I used in the past ubuntu.7 but had difficulty in finding how to install programs, so I deleted it with w98flopy & A;\fdisk/mbr.

Having read about 8.04.1 that it contains all the programs & installs within winXP, I downloaded the iso & installed it on HD.

On the 7 installation emailer & browzer were automatically configured to used them instantly.

1. Not so on 8.04.1, a lot of things are required, that I do not understand, to configure them. I does not find my brodband with wired Netgear modem.

2. Istead of a clean dual boot choice, ubuntu or winXP, I get 4-5 lines with long jiberish before the XP choice.

The first of those lines does boot ubuntu 8.04.1, but with these problems above I feel there is something wrong with my installation.

Can you help pls.

EDIT  
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin
c:\wubildr.mbr="Ubuntu"

---

### Post by billgoldberg on 2008-08-25
> **ulindel said:**
> I used in the past ubuntu.7 but had difficulty in finding how to install programs, so I deleted it with w98flopy & A;\fdisk/mbr.

Having read about 8.04.1 that it contains all the programs & installs within winXP, I downloaded the iso & installed it on HD.

On the 7 installation emailer & browzer were automatically configured to used them instantly.

1. Not so on 8.04.1, a lot of things are required, that I do not understand, to configure them. I does not find my brodband with wired Netgear modem.

2. Istead of a clean dual boot choice, ubuntu or winXP, I get 4-5 lines with long jiberish before the XP choice.

The first of those lines does boot ubuntu 8.04.1, but with these problems above I feel there is something wrong with my installation.

Can you help pls.

EDIT  
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin
c:\wubildr.mbr="Ubuntu"

It might be Wubi, it's been know to cause problems.

If you can, really install Ubuntu onto your HDD (dual boot).

Ubuntu 8.04.1 should have better hardware support because of the newer kernel and better/updated repos.

--

Installing applications is 8.04.1 is the same as in 7.04 and 7.10.

Either using "application -> add/remove" or using "system -> administration -> synaptic" or using "apt" or "aptitude".

Besides that you can install .bin files, .deb files, .tar.gz archives, ...

---

### Post by ulindel on 2008-08-25
as you can see from my post it is on my HD.

I did not run wbi, perhaps it runs automatically?

how to make it see my bband connection, my favourites, address book etc etc?

---

### Post by kpkeerthi on 2008-08-25
> **ulindel said:**
> as you can see from my post it is on my HD.

I did not run wbi, perhaps it runs automatically?

how to make it see my bband connection, my favourites, address book etc etc?

If you want to get started with Ubuntu, you may want to spend some time reading this webpage: [https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by BTMark on 2008-08-25
> **ulindel said:**
> I used in the past ubuntu.7 but had difficulty in finding how to install programs, so I deleted it with w98flopy & A;\fdisk/mbr.

Having read about 8.04.1 that it contains all the programs & installs within winXP, I downloaded the iso & installed it on HD.

On the 7 installation emailer & browzer were automatically configured to used them instantly.

1. Not so on 8.04.1, a lot of things are required, that I do not understand, to configure them. I does not find my brodband with wired Netgear modem.

2. Istead of a clean dual boot choice, ubuntu or winXP, I get 4-5 lines with long jiberish before the XP choice.

The first of those lines does boot ubuntu 8.04.1, but with these problems above I feel there is something wrong with my installation.

Can you help pls.

EDIT  
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin
c:\wubildr.mbr="Ubuntu"

It looks like you ran the installer through Windows, which would install via Wubi (which it is showing).

[_Here_]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm") is a nice comprehensive guide on dual-booting with Windows XP installed on your hard drive already. **[COLOR=Sienna]Please note: This is an offsite link.[/COLOR]**

---

### Post by ulindel on 2008-08-25
installed through winXP

The last ubuntu bootup showed XP or Ubuntu, but after choosing ubuntu a WArning:unrecognised partition table for drive 80. Rebuild with MS FDISK tool (error=10). Current C/H/S=16383/255/63
& then lot of text choises come up before ubuntu loads.

BTW 101 updates started loading. I thought 8.04.1 had it all?

For importing it does not recognise IE favourites or OE or Yahoo mail adress book.

I wish I could carry on this conversation (posting) within ubuntu instaed having to reboot to XP each time.

Thanks for the offsite link

---

### Post by porchrat on 2008-08-25
8.04.1 does have it all in that it has more than 8.04 did (e.g. a full version of firefox as opposed to the beta 5), but you have to understand that updates become available almost every day so considering its been a month or more since 8.04.1 was released it does have a little catching up to do.

---

### Post by Dougie187 on 2008-08-25
For your favorites and email accounts, what format did you export them as?

Also, the text choices are all the different kernels you have installed right now.

---

### Post by ulindel on 2008-08-25
thanx all again,

I used "Import" in ubuntu but for contacts & favourites says no recognisable programs detected.

In XP I use Yahoo mail (& OE not used recently), & browser is IE6 or 7.

Also I tried to run in ubuntu various programs like Google etc I have in XP with no luck.

I thought it was all win compatible for files & progs.

---

### Post by ulindel on 2008-08-25
BTW
email accounts I exported them in text file (.csv) .& I think in another form OE gives. None is known to ubuntu.

favorites exported in the usual file IE does (bookmark8Jan08.htm). 

Can I not run Googleearth?, ubuntu does show some files/icons with googleearth ivews which are zoomable.
yuli

---

### Post by Dougie187 on 2008-08-25
To start. Your ubuntu is not going to recognize your email and bookmarks from a seperate OS. Firefox would recognize your bookmarks if it was installed in windows, but the only way to get your email and bookmarks on your ubuntu is to copy them to the partition and then manually import them.

In Evolution the import wizard is under File->Import.

In Firefox you can import your bookmarks by selecting Bookmarks->Organize Bookmarks

Then after the bookmark manager opens, select Import and Backup->Import HTML

There is a package called google-earth i believe. if you want to install it just open a terminal and type sudo apt-get install google-earth.

---

### Post by ulindel on 2008-08-30
Thanx a lot, I am bound to get it right now, BUT alas......

managed to install 8.04.1 within winXP & used it 3-4 times when it started hunging on boot up.
Reinstalled twice with no effect.

It even hungs when I try to run it from the CD-RW I burned.

verbose runs down up to:- 
48,717996 Driver "sd" needs updating, use bus type methods

The same with the grafix choice, upt to 47,..................

Can the .ISO be burned into a DVD-R or DVD-RW? Mine only accepted to burn it in a CD-RW.Can the problem be because I used CD-RW?
nick

---

### Post by ulindel on 2008-08-30
Lo & behold,
I burned the .iso on a CD-R this time, installed 8.04.1 from scratch again using this CD-R and bootted ubuntu without hungung.

Managed, to get favourites & addresses as sugested, 

What I cannot find in Help file is how to configure my accounts. I do not understand what I should put in the various entry boxes, like in Server Config, so although I create an account cannot send or receive as the Send / Receive is grayed.

For Yahoo & Hotmail I guesed it should be IMAP server type, & hotmail.com POP.

Any help on this? pls...........nick

---

### Post by ingeva on 2008-08-30
> **ulindel said:**
> Lo & behold,
I burned the .iso on a CD-R this time, 

Congratulations on a wise decision!
After all, isn't the point of using Linux that you can finally be free from Windows? :)

About transferring accounts, address books etc. from Windows:
Install Thunderbird and FireFox in Windows. Use them to import from Outlook (Express) and IE favorites, and then export again to files that you can import in the same programs under Linux.

I had some trouble configuring Evolution mail and ended up with Thunderbird anyway. I needed to do some trial and error but soon everything worked nicely.

Setting up mail accounts is usually fairly easy. Use standard server names and ports unless you're instructed to do otherwise. gmail uses some special ports and so does probably yahoo etc (to bypass your local ISP and provide better security) but the setup should be quite well documented by those providers.

Give yourself max. two weeks before you remove Windows and all old filesystems from your computer (Just joking).

---

### Post by ulindel on 2008-08-31
What for Viking? if you are one,
the ruddy thing packed up after 2-3 bootups & will not boot again.

The world is lterally running on windows. 
Some respect for two genious kids who, in their parents garage 20-30-40 yrs ago, worked so hard to build machines & devise DOS etc for the likes of me & you to have such fun the last 20yrs.

I tried Linux as it fascinated me to see what wizard young men created and generously offered it to the world for free, despite that from No.7 onwards I could not make it work, Y E T......

It would be fun to use it for word prossesing, em & the web.

But for an old man a lifetime aviator, only MS can provide FS9 in such glorious way that with good hardware gives those clouds etc etc, so unbelievably realistic.

WELL WELL.......
reburned the .iso on a CD-R this time, installed on HD, booted OK 2-3 times even imported addresses & favourites & the ruddy thing packed up again & won't boot.

Goes up to six travels of the orange line & hungs.

It even wot't boot from the CD-R.

Could it be my system?

Home build
Asus A8N 32 sli deluxe
Chipset nF4 SLI x16
AMD 64 3.5+ Venice 2.2ghz
Corsair twinx 2x512mb
MSI 6600gt 128 PCI-E
Maxtor sata 160gb
PSU EZ cool 550w, X45
XP pro sp2

---

### Post by ingeva on 2008-08-31
> **ulindel said:**
> What for Viking? if you are one,

I like to thinik that I am -- although an old one, and not big and strong any more! :)

> **ulindel said:**
> But for an old man a lifetime aviator, only MS can provide FS9 in such glorious way that with good hardware gives those clouds etc etc, so unbelievably realistic.

Of course different people, with different computers, will have different experiences. I bought this Dell computer because I knew they sold it with Ubuntu installed in the US. I had to install it myself, and with 7.10 I had problems and couldn't make the WiFi work. Before that I had also tried Debian and another one that I don't remember now. However, with Ubuntu 8.04.1 everything worked out of the box -- at least what was installed as "standard". I had some problems installing the Apache server, but I can only blame my own lack of understanding for that (The documentation assumes that you know most from before and is not easy to learn from).

> **ulindel said:**
> reburned the .iso on a CD-R this time, installed on HD, booted OK 2-3 times even imported addresses & favourites & the ruddy thing packed up again & won't boot.
Goes up to six travels of the orange line & hungs.
It even wot't boot from the CD-R.
Could it be my system?

Could be, but I'm not qualified to say. I have tried to install Ubuntu on two portables, one an 7 year old Dell and the other a 4 year old Acer TravelMate 8100. No luck on either.

---

### Post by ulindel on 2008-08-31
One must be a masohist to stick with this ridiculous thing

---

### Post by halitech on 2008-08-31
> **ulindel said:**
> One must be a masohist to stick with this ridiculous thing

then call me a masochist as I've been using Ubuntu for over 2 years and I love it. No viruses to worry about, no hunting down drivers, uptimes of 30+ days, no random freezes with an error message that means absolutely nothing to anyone (including the microsoft support reps) and a system that does what I tell it to, not me doing what it tells me to (or not allowing me to do)

now, having said that, Ubuntu (or linux in general) is not for everyone and you have to decide for yourself if you want to use linux. As another poster said when asked why use linux, use it because you want to.

---

### Post by ingeva on 2008-09-01
> **halitech said:**
> then call me a masochist as I've been using Ubuntu for over 2 years and I love it.

I agree completely. People are different, and everyone should have their choice.
I wouldn't try to convince someone that Linux will be better for them, but it would be smart to find out for themselves.

Personally I'm glad I finally took the step and spent some time figuring out the best distribution for me and my computer, and the final choice was Ubuntu.

I admit that not everything works as desired, but when did THAT ever happen? You have to weigh for and against, and I think I've said it before: For me Ubuntu wins in most ways, compared to other Linuxes that I have tried, and MASSIVELY compared to Windows, with its high prices and bad performance (and all its blings and unnecessary paste-ups).

When I tried installing Linux on those old laptops I had the following choice: Either Linux in them or they in the bin. I took the hard-disk out and they are now being recirculated.

---

### Post by fidamehran on 2008-09-01
The age old Windows-Linux fight. Why don't people understand that primary users of Windows and primary users of Linux are bound to have different views of choice.

Using Ubuntu/Linux is a matter of choice and a matter of inquisitive mind. A matter of zeal to explore and do things by yourself.

If Windows can make certain things easy for you, if you can bear with the crash probabilities, and upgrade/repair costs and have the money to buy and maintain (softwares included) Windows, then why not use it?

It is a fact that still the best softwares are made for Windows. And anyone with elementary knowledge of clicking and occasional typing can use Windows. So why not let people enjoy that if they prefer?

---

### Post by Bucky Ball on 2008-09-01
Linux is not for everyone. A bit of research before hand, backup all your valuable data, arm yourself with your windoze disk and your Hardy disk, get a coffee, scotch, beer or whatever takes your fancy along with a piece of paper and a pen and work out what partitions you are going to need. Ie:

Windoze partition
Linux partition
Swap partition (2x your RAM usually)
Any other partitions you may need for storage (music, vid, data etc)

Then go for it! Install Windoze where it should go (always first)
Install ubuntu from the disk into the second partition (or a separate drive, even better)
And with any luck you will be in business and ready to learn more ...

Sounds like windoze is there already, so you could use Administrative Tasks->Disk Management to create a partition for your Ubuntu install. (from memory).

But I will finish as I started - Linux is not for everyone. It is by no means a passive user experience, if I may put it that way. And in the end, Windoze might just be the easiest for you.

---

### Post by ulindel on 2008-09-01
Well said by all masochists,

& I must be one, as in desperation the bagar not to beat me I did the mem tests discovered in one of the menus & for the last 4-5 bootups it worked.

Now how do you go about this "WINET" or something to run fs9 on ubuntu?

I must have foxed Firefox & ended up with 5600 favourites , 4900 dublicates. I got the a thing to remove them but takes too long as it works on one by one.

I will now delete 8.04 yet again & reinstall to get rid of them, what did you say of windows.......
nick

---

### Post by ingeva on 2008-09-01
> **fidamehran said:**
> It is a fact that still the best softwares are made for Windows. And anyone with elementary knowledge of clicking and occasional typing can use Windows. So why not let people enjoy that if they prefer?

What you say about clicking etc. is no different for Linux.
The problem is not that they prefer Windows, but that they
don't know the alternative.

So let them check out the alternative. I think the majority of users would prefer Linux after using it for a while. It's as intuitive as Windows; in some cases more so.
And you can DO much more with Linux. After all, it IS based on the Unix architecture, and much of its coding.

I do miss some things in Linux, but I can learn to live without them. Some are fundamental enough to require kernel and/or filesystem changes, but if you want something better, you must accept that it might still not be perfect.

---

### Post by Bucky Ball on 2008-09-01
[quote=ulnidel]Now how do you go about this "WINET" or something to run fs9 on ubuntu?[/quote]

Wine allows you to run windoze programs in Linux. I did a little research a few hours ago about it for you and it seems FS9 is not one of them. Results have been pretty poor (for the moment but that could change!).

There are a couple of Linux alternatives I believe, one called FlightGear, but FS9 fans seem a little let down by it and dual boot just to run FS9 in windoze. If you go to:

**Applications->Add/Remove**

... and do a search for** FlightGear** you could give it a test flight and see what you think (to install, just tick the box and 'Apply Changes'). If you don't like it, repeat the above instructions and untick to remove. That simple. Good luck and happy flying. :)

---

### Post by ulindel on 2008-09-01
Thanx bucky,will try it when settled.
had to unistall & reinstall to get rid of favourites.

1. How to make them come side by side instead of that long line down?

2. trying to achieve this with no luck, how do you do it?  Where do you go to chsnge this?

a.Change to the {install_path}/program directory.
b.Enter: ./spadmin
c.Click New Printer. This opens the Add Printer dialogue.

3. when I go o Terminal & type "....sudo blaablaablaa.."
it asks for password, I enter my ubuntu one but is not accepted. Do I miss something?

nick

---

### Post by sTpny on 2008-09-02
A lifetime aviator! You need to get linux installed on that box of yours. One of the best things about linux is that you can get involved, and I'm sure the people at the sabre project would love to hear from you. Sabre is a flight simulator, and pretty good too, but it is a work in progress. There's actually quite a few flight simulators available, some are really good, others really fun, and all of your microsoft flight simulators should run even better under wine than they do under windows. since you seem to be having problems installing, I'd say it doesn't like something about your hardware or your hardware setup. Does windows install and run on that box? post the results of a sudo lshw, but in the forum for installations. The gurus hang out there more than here. Tell them your installation woes, and in the meantime, hang in there. You'll be soaring though digitized clouds soon enough.

---

### Post by Bucky Ball on 2008-09-02
[quote=sTpny]all of your microsoft flight simulators should run even better under wine[/quote]

I repeat, the flight simulator in question (Microsoft Flight Simulator 9) is a work in progress and *doesn´t* run under wine. (poorly at best).

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2819&iTestingId=2523](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2819&iTestingId=2523)

[http://ubuntuforums.org/showthread.php?t=766986](http://ubuntuforums.org/showthread.php?t=766986)

:)

---

### Post by fidamehran on 2008-09-02
> **Bucky Ball said:**
> I repeat, the flight simulator in question (Microsoft Flight Simulator 9) is a work in progress and *doesn´t* run under wine. (poorly at best).

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2819&iTestingId=2523](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2819&iTestingId=2523)

[http://ubuntuforums.org/showthread.php?t=766986](http://ubuntuforums.org/showthread.php?t=766986)

:)

I agree.

I still need Windows to play my games. Also to use Nokia PC Suite for data transfer to my Nokia mobile. Also to use the SPSS statistical software for Research data analysis. Who will give me Linux alternatives for that.

Wine? I don't think so for all cases.

---

### Post by ulindel on 2008-09-02
Thanx all for fs9.

I am trying to use faxing & downloaded Efax-gtk, can anybody decipher this in openoffice help?:-
"....Using Fax Functionality
If you have installed a fax package such as Efax or HylaFax on your computer, you can send faxes with the OpenOffice.org software.
1.Change to the {install_path}/program directory.
2.Enter: ./spadmin
3.Click New Printer. This opens the Add Printer dialogue.
4.Select Connect a fax device. Click Next......"

Now the browzer windows will not close, either from the "X" or from file>close window (Ctrl+Shift+W).

Can anybody help with the two above? untill I sort myself out.

PS. Hi STPNY, managed to keep it booting after I did a mem test as a last resort, & seems to work, keep toes crossed.

---

### Post by miXcu on 2008-09-10
Hello to everyone , first of all I'm a new Ubuntu 8.04.1 user.. i got familiar with it in minutes... but after a day or so , when I've tried to boot ...

i got " try (hd 0,0) : NTFS5 : no wubildr 
        try (hd 0,1) : NTFS5 : _          ,,

I've waited for 5 min to see if anything happens , but ... nothing. What can i do ?! I've read some topics around here and i didn't get it to work.

Excuse my English :) 
And sorry if I've posted in the wrong topic.

Cheers

---

### Post by Bucky Ball on 2008-09-10
miXcu: For some reason seems to be looking in the wrong place for your Ubuntu. You should probably post this in the 'Installation and Upgrades' forum. It will be top of the list and you will get specific help. Here, it is 3 pages in and not many will see it (the topic for this thread is not very specific either).

Sounds like you are booting with Wubi and you maybe haven't got the disk with Wubi in the drive. Is Ubuntu installed properly on your hard drive or are you using it from Wubi disk?

Anyhow, name your new post something descriptive of your problem like 'Can't boot Ubuntu', include your machine details, Ubuntu version and anything else you can think of that might help us fix your problem. Post here:

[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

Good luck. :)

---

