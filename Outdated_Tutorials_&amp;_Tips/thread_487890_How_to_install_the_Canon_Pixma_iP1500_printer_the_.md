---
title: "How to install the Canon Pixma iP1500 printer the easy way"
date: 2007-06-29
forum: Outdated Tutorials &amp; Tips
---

### Post by Seisen on 2007-06-29
**[SIZE="5"]How TO Install Canon IP1500 Printer[/SIZE]**

This the easiest way to install the Canon iP1500 Printer on Ubuntu. This is the way I set mine up and it works perfectly.

The first step is to open up your source list and add this to it
```
deb http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu ./
```
If you don't know how to open up your source list you can do it by putting this in the terminal

```
gksudo gedit /etc/apt/sources.list
``` you can use whatever text editor you like to edit your source list.

After adding that to your source list you need to do this in the terminal

```
sudo apt-get update
```

Next you need to install these files
```
sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj
```

Cupsys will be automatically restarted and you can select printer in cupsys configuration which is
[http://localhost:631]("http://localhost:631") or if you don't want to do that you can go to System>Admistration>Printer>Add Printer.

To add the printer through the cups, the first thing you do is click on add a printer. The next screen will ask you for the name of you printer, location and description the ony thing you really have to fill in is the name. After you done filling in the information click continue. The next page is asks you to select your printer which should be Canon iP1500 USB # (Canon iP1500). Hit continue and then it will ask you for your driver, select the Canon Pixma iP1500 Ver.2.50 (en) then click on add printer. 

To add the printer the other way once you click on add printer a new window will open up that say's add a printer at the top and Step 1 of 3: Printer connection. As long as your printer is turned on it should show up in **"Use a detected printer"**, if it doesn't you can select it in  **"Use another printer by speciying a  port"** and selecting Canon iP1500 USB # (Canon iP1500) then click forward. The next page is where you select the printer driver. The manufacturer is Canon if it already isn't selected and the Driver is Pixma iP1500 Ver.2.50, then click forward. Finally the next screen is the printer information you don't really have to worry about filling in the rest of the information if you don't want to just click "Apply" and now your iP1500 printer should show up under printers. 

Right click on your  printer and then click on Print a Test Page and your printer should crank out a test page, if it doesn't please let me know and we can try to figure out why.

I know this works on Ubuntu Edgy and Feisty so I anybody wants to try it on Dapper and let me know if it works that would be appreciated. If you run into any problems feel free to ask questions.


[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/]("http://mambo.kuhp.kyoto-u.ac.jp/~takushi/")

---

### Post by PurplePenguin on 2007-06-30
This is a great tutorial.  I have this printer and went crazy trying to get it to work before finding these instructions somewhere else (forget where... although I think it might have been on this site).  Anyway, with these simple steps, it works great.

Looks like you might have a typo, though in this line: gksudo gedit /etc/apt/soruces.list

Anyway, great job on making a quick and simple tutorial!

---

### Post by Seisen on 2007-07-01
That's why I wrote the tutorial, I was having problems trying to get it setup too in Ubuntu. I was trying to write it so it was geared more towards somebody that have very little knowledge of Ubuntu so they wouldn't get frustrated trying to set it up. Thanks for catching the typo I will fix it.

---

### Post by beerstim on 2007-07-03
Thanks not getting this printer to work on ubuntu was the only thing keeping me using windows.  Now I can use Ubuntu all the time.  Thanks

---

### Post by dan_m on 2007-07-04
Thank you very much for your great tutorial.
I have a Canon PIXMA iP 1500;
5 minutes ago I red your tutorial. 1 minute ago my Canon printed the testpage!
Amazing!

10x again,
Dan

---

### Post by Seisen on 2007-07-04
No problem, I'm glad you found it easy to use, that is what I was going for.

---

### Post by chichilalescu on 2007-07-08
this doesn't work on dapper. this is what i got:

root@chichi-laptop:/stuff/chichi/home# apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  bjfilter-2.5: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
  pstocanonbj: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
               Depends: libcupsys2 (>= 1.2.3) but 1.2.2-0ubuntu0.6.06 is to be installed
E: Broken packages

So I guess no printer on dapper, and I'll have to move on to the next version... :)

---

### Post by Seisen on 2007-07-08
At least I know now that it won't work on dapper now, thanks for letting me know anyway. If you have problems getting it to work on Edgy or have trouble upgrading to Edgy let me know.

---

### Post by Neo40 on 2007-07-08
Does this work too for a Canon Pixma IP1800 printer?

---

### Post by Seisen on 2007-07-09
I honestly have no idea, I don't have that printer therefor I couldn't test to if it would work. You can try to see if it will work and let me know if it does or not.I know those drivers work on the iP1000 printer. If that doesn't work, let me know and I will see what I can find out finding some drivers to work.

---

### Post by dark_forest on 2007-07-10
I'm a Windows 95/98 A+ ex-technician who got tired of the security and privacy hassles. Vista and DRM was the last straw. I bought Keir Thomas' book and built a Pentium 4 PC around it. I am brand new to Ubuntu, still just beginning to learn my way around the shell, and without people like you the switch from Windows would be nearly impossible for me. My ip1500 is now working perfectly. Thanks very much.

---

### Post by PurplePenguin on 2007-07-10
Hey, welcome aboard! :D

This is definitely the best forum on the net, as far as I've seen, anyway.  The one thing I really missed when I switched to using Debian Etch was coming to UF.org every day.  Sure, I guess I could anyway, but it just didn't seem right. ;)  But now I've got a laptop running Feisty, I'm back in the game.

Having threads hanging around here for things like the Canon ip1500, webcams, all sorts of different software, etc. is so incredibly useful.

I'm sure it won't be long before your Windows security and privacy issues become vague memories. :D

---

### Post by flamacue on 2007-07-22
I'm setting up an Ubuntu PC for my folks, they have the iP1500.  Your guide is very clear and concise.  Thanks!

On a related note...does anyone know of any tools (preferably GUI-based, but not necessary) to check the ink level on this printer from Ubuntu (Gnome)?

---

### Post by Yellowdog428 on 2007-07-22
Worked like a charm!  Thanks!

---

### Post by Seisen on 2007-07-24
> **flamacue said:**
> I'm setting up an Ubuntu PC for my folks, they have the iP1500.  Your guide is very clear and concise.  Thanks!

On a related note...does anyone know of any tools (preferably GUI-based, but not necessary) to check the ink level on this printer from Ubuntu (Gnome)?

Its called bjcupsmon but I can't get to build. If and when I get it to build correctly or somebody else does,  I will post the .deb file.

---

### Post by diggerOS on 2007-07-24
Hello everyone! I need help with getting my Canon Pixma ip1500 running. I am running Feisty amd64. I've done everything like you wrote in tutorial, but when i try to: 'sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj' it says:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libcnbj-2.5

Tnx!

---

### Post by Seisen on 2007-07-24
It can't find that one file or is it for all of them?

---

### Post by milosz.galazka on 2007-08-18
> **diggerOS said:**
> Hello everyone! I need help with getting my Canon Pixma ip1500 running. I am running Feisty amd64. I've done everything like you wrote in tutorial, but when i try to: 'sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj' it says:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libcnbj-2.5

Tnx!
**apt-get update** after editing /etc/apt/sources.list?
then you can look for it using **aptitude**

---

### Post by milosz.galazka on 2007-08-18
hello,

Couple days ago I upgraded my kubuntu box to new shiny gutsy version. Today I spend couple of hours trying to get this printer (IP 1500) working. I don't know why (even turboprint driver wasn't working). But now it works just after taking a long break from computer. Weird

---

### Post by Seisen on 2007-08-18
I had the same problem you did just recently, I also you Gutsy the solution that worked for me was
```
sudo aa-complain cupsd
``` it was discussed here. 

[http://ubuntuforums.org/showthread.php?t=522276&highlight=printer](http://ubuntuforums.org/showthread.php?t=522276&highlight=printer) 

It has something to do with apparmor.

---

### Post by fordexplorerdotnet on 2007-08-19
This is making me a bit crazy...

> 
jesse@HPsucks:~$ sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libcnbj-2.5


I can't get this to work.  I followed all previous steps.

---

### Post by umberstark on 2007-10-10
Worked flawlessly for me in Gutsy beta, thanks! :)

---

### Post by GraFF on 2007-10-28
> **fordexplorerdotnet said:**
> This is making me a bit crazy...



I can't get this to work.  I followed all previous steps.

+1. Can't find that package

---

### Post by devonj on 2007-10-28
It Finally Works ....... ;) After Edgy and Feisty. Finally, Gutsy it works. Thanks!!!!

---

### Post by flyingfree on 2007-10-29
I had problems with the printing being off center and won't print in landscape anyone else with this problem.  I switched the system from edgy to fiesty and then xubuntu.

---

### Post by Seisen on 2007-10-29
> **GraFF said:**
> +1. Can't find that package

If you can't find the packages open up synaptic and search for them they should be in their.

---

### Post by GraFF on 2007-10-30
oh but they aren't

---

### Post by Seisen on 2007-10-30
I just tried it and worked for me , did you guys reload your repository list?

---

### Post by atezun on 2007-11-01
Kubuntu users, install is exactly the same, however you'll need to configure it through the cups web interface.

[http://localhost:631/admin](http://localhost:631/admin)

Click on find printers and select your PIXMA 1500

When it asks for your driver find the PIXMA 1500 v2.50 and select it

KDE should now see the printer, I have no idea why it doesn't see the drivers after apt installs them.

---

### Post by dthuk on 2007-11-02
I have a slightly different problem: I get the following



```
dave@laptop:~$ sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  pstocanonbj: Depends: libcupsys2-gnutls10 (>= 1.1.23-1) but it is not installable
E: Broken packages
```


But this doesn't mean a lot to me. Following a similar install when I used Feisty used to work but now in Gutsy it doesn't. Does any kind soul out there have any clues what could be happening? Thanks.

---

### Post by GraFF on 2007-11-23
> **Seisen said:**
> I just tried it and worked for me , did you guys reload your repository list?

yes. this is persistent..

---

### Post by Seisen on 2007-11-23
Here is a link to be able to download that package, that is still weird why it isn't showing up anywhere.

[http://repo.ugm.ac.id/printer/takushi/ubuntu/]("http://repo.ugm.ac.id/printer/takushi/ubuntu/")

---

### Post by GraFF on 2007-11-24
> **Seisen said:**
> Here is a link to be able to download that package, that is still weird why it isn't showing up anywhere.

[http://repo.ugm.ac.id/printer/takushi/ubuntu/]("http://repo.ugm.ac.id/printer/takushi/ubuntu/")

I've just thought of something.. I'm not familiar wit the way synaptic works, so might it be that it filters packages not for my architecture? I'm on 64bit.

---

### Post by Seisen on 2007-11-24
Unfortunately the way the packages were built they do not support 64-bit Ubuntu. I have a laptop that is 64-bit and I couldn't even get the printer to work either so I just use 32-bit Ubuntu.

---

### Post by GraFF on 2007-11-25
> **Seisen said:**
> Unfortunately the way the packages were built they do not support 64-bit Ubuntu. I have a laptop that is 64-bit and I couldn't even get the printer to work either so I just use 32-bit Ubuntu.

32 bit ubuntu doesnt even start the livecd on my machine. :(

---

### Post by wljflikkema on 2007-11-27
How can I download Canon Pixma iP1500 driver i Fedora 7.

---

### Post by nugrahadi on 2007-12-11
> **Seisen said:**
> Here is a link to be able to download that package, that is still weird why it isn't showing up anywhere.

[http://repo.ugm.ac.id/printer/takushi/ubuntu/]("http://repo.ugm.ac.id/printer/takushi/ubuntu/")

do you know another mirror ?? because of the system failure I lost the repository in trepo.ugm.ac.id, so if anyone of you know other place mirror those driver I would like to mirror it again. I've check to [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/) but it shows 403 forbidden.

---

### Post by texasjim on 2008-03-06
YEE-HAW ! !   I've beating my head against this printer for a couple of days, and this post got it workin' in 10 minutes. Thanks a bunch.

Jim

---

### Post by Seisen on 2008-03-12
> **texasjim said:**
> YEE-HAW ! !   I've beating my head against this printer for a couple of days, and this post got it workin' in 10 minutes. Thanks a bunch.

Jim

No problem.:)

---

### Post by bloke3142 on 2008-04-12
Thanks. Quick and easy. Now I've no need to go back to Windows to print! Didn't want to spend good money on a new printer when I've got one that works.

---

### Post by prosperoa on 2008-04-22
Thanks a ton

I'm a n00b and was struggling getting my ip1500 to work - I said i'd give it one last try and found this thread!

Whoo Hoo!

---

### Post by lucas.cgc on 2008-05-18
Those packages work well on 64-Bit, but you need to download the packages direct from the repository website, install with:

```
sudo dpkg -i --force-architecture *
```

If dpkg report a error with requeriments, you to install then with apt-get, the ones that you don't find there, you download at packages.ubuntu.com and install with dpkg.

---

### Post by Chrissy on 2008-06-08
I followed the instructions on the first page of this thread - everything works except for that I can't print in grayscale. I'm not sure where the option to set this would be (I'm still very much a linux newbie) - I tried going to System > Administration > Printing > Printer Options, under color model, but all I see is "RGB", no other options. I'm using hardy heron.

---

### Post by freddyg on 2008-06-29
hey, thanks for the howto, trying to install an ip1800 on hardy, thought i might have some luck, but no. 

user@comp:~$ sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pstocanonbj: Depends: libcupsys2-gnutls10 (>= 1.1.23-1) but it is not installable
E: Broken packages

dotn know how to fix the broken dep, any thoughts?

---

### Post by Seisen on 2008-06-30
> **freddyg said:**
> hey, thanks for the howto, trying to install an ip1800 on hardy, thought i might have some luck, but no. 

user@comp:~$ sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pstocanonbj: Depends: libcupsys2-gnutls10 (>= 1.1.23-1) but it is not installable
E: Broken packages

dotn know how to fix the broken dep, any thoughts?

Try installing libcupsys2 and then try to install the packages and see if that meets the dependencies you need.

---

### Post by pa0lo87 on 2008-08-11
Hi, i had followed the istructions (sorry for my english), i try but my computer respond this:

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x90227c0>,
 'cups_instance': None,
 'cups_queue': 'iP1500',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Canon/iP1500',
                       'printer-info': u'',
                       'printer-is-shared': True,
                       'printer-location': u'pa0lo87-desktop',
                       'printer-make-and-model': u'Canon PIXMA iP1500 Ver.2.50',
                       'printer-state': 3,
                       'printer-state-message': u'Unable to start filter "pstocanonbj" - No such file or directory.',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167948,
                       'printer-uri-supported': u'ipp://localhost:631/printers/iP1500'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': 'Unable to start filter "pstocanonbj" - No such file or directory.',
 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_job_status': [(2, 'iP1500', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': 'Unable to start filter "pstocanonbj" - No such file or directory.',
 'printer-state-reasons': 'none'}

Can someone help me? thanks

---

### Post by Seisen on 2008-08-12
Did you make sure that the packages installed correctly?

---

### Post by Mati_Jero on 2008-09-03
Thanks great!!!!!! tutorial

---

### Post by ice_nine on 2008-09-20
Do these packages work on Hardy?

---

### Post by Orographic on 2008-10-06
> **ice_nine said:**
> Do these packages work on Hardy?

Yeah, as mentioned on this page, they do. Like someone else has mentioned, I can't print in greyscale either and can't do any test or maintenance things either.

Any more thoughts on this?

Thanks so much for this thread, I'm new to Ubuntu after getting into Linux a tiny bit with my Eee PC.  :)

---

### Post by mendozaro on 2008-10-18
The tut works like advertised!

I still have a problem... the printer has the only setting "600 dpi". Anyone knows how to add more options? Like atleast 300dpi (so i could print faster)?

---

### Post by zobo on 2008-10-25
Seisen,

Thank you for the very clear, easy-to-follow, and accurate instructions. They worked like a charm, and my printer now works in Ubuntu!

---

### Post by uprichukalaa on 2008-10-26
Hello Seisen
your tutorial looks wonderful. I have become very optimistic about activating my canon pixma ip1000 printer in ubuntu 7.0.3.6
do u have anything for me?
I have started trying ubuntu frou hours ago.
And it took me three hours to get connected to internet.
I am a novice in the world of open source softwares.
I don't even know how to get and install driver for my samsung 591s monitor and ATI Radeon 9550 AGP.
I can't plat any movie file or DVD. 

I am feeling very sad.

Irfan

---

### Post by stmcc on 2008-12-06
I have installed the Canon ip1500 driver and it works fine for anything that is on my computer. Spread sheets, Office docs ,etc. It will not print anything from the Internet. Bank statements,receipts, tickets,etc. ???
MAC

---

### Post by zfh on 2008-12-26
is there anyone whom can figure out HOW TO PRINT IN GRAYSCALE?

I am a cheapscaper, and I only buy BLACK inks, without the grayscale option, it is just as without a working driver.

Thanks in advanced if anyone knows how!

---

### Post by Tavathlon on 2008-12-29
Hey guys!

I have not yet tried this tutorial, since the printer is not at the same place as I am - it is also an iP1300, but I've been told that the driver for the 1500 should work for the 1300 as well. Anyhow, I have a somewhat different but still related question.

The owner of the printer is my sister, and she is not an ubuntu-user at the moment - she is not a very skilled computer user at all, actually. She is willing to use ubuntu if the stuff she want would work on ubuntu, though. I tried to install everything for her one year ago, but ran into trouble with her printing needs. I did manage to get the printer working, although not really quite as good as I wanted it to be. But it worked, at least (I think it was another tutorial that I followed that time, though). The problem I ran into however, was that she wanted to be able to use the printing software that came on a disc along with the printer. This software is for windows, and I did not manage to get it to work properly with wine. I don't remember things clearly right now, but it might have been a program from Canon themselves - I guess that you guys who have a similar printer knows what program it is? So my question to you is whether anyone of you know a way to get this program working in ubuntu, or (perhaps even better) know of any open source program for linux that is equivalent? An easy-to-use printing-tool that is able to handle photo printing.

Anyone got any idea?

---

### Post by zfh on 2008-12-29
Tavathlon,

Use Wine, or get helps on other threads. This thread is about PIXMA ip1500.

Wine works for some stuff, but there is no guarantee for all Windows stuffs. Peace out.

---

### Post by OmarVeg on 2008-12-29
Printing in grayscale: Go to Administration>Printers and right-click over your pixma  then select "properties". There you'll find everything you need and more. It worked for my IP3500.

---

### Post by OmarVeg on 2008-12-30
Also, I got my IP3500 working very easily. I just installed Ibex amd64 on my new laptop and everything worked like a charm right out the box. As I always do, I enabled the partner repos and added the openprinting repo along with medibuntu and others. Then sudo apt-get dist-upgrade. After a reboot, I connected my IP3500 and almost instantly got detected. I was surprised as to how many options I have. It´s crazy. This might work for the IP1500 too.

---

### Post by zfh on 2008-12-30
OmarVeg,

No, it is not working for ip1500:
*************************************************
System>>Administration>>Printing
then you will find ip1500, but there is no such option for "properties", (atleast I don't see this option on my machine). GOOD FOR YOU that it works for your ip3500. 
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

My question is, I will restate here, does anyone out there figured out how to print in grayscale with PIXMA ip1500. Thanks in advanced!

---

### Post by dondrup on 2009-05-25
thanks for this. i tried all of this for my ip1300 on ubuntu 9.04 but no luck. it indicates that a test page has been successfully printed - the power button flashes as if it is printing but nothing mechanical happens. any suggestions would be appreciated.

thanks, stephen

---

### Post by mlissner on 2009-07-25
Hmmm...I'm having the exact same problem with my ip1500 on Jaunty. I've tried just about every guide out there, and nothing seems to work.

The closest I've come is for it to say it prints successfully, but for nothing to happen mechanically, like you say...

---

### Post by thane1 on 2010-06-17
I too would like to thank you Seisen for the help here.  Between your post and the following link        [http://swiss.ubuntuforums.org/showthread.php?t=1310654](http://swiss.ubuntuforums.org/showthread.php?t=1310654)        to help install the missing dependency ( libcupsys2 ), I have now gotten my parents' new 10.0.4 lucid installation to work happily with their old Canon Pixma MP130 printer (colour and all!) using the iP1500 driver.  Many thanks.

---

