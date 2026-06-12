---
title: "Universe/Multiverse? what are these? Me newbie :("
date: 2006-02-07
forum: Repositories &amp; Backports
---

### Post by AdonisV on 2006-02-07
Hi all! Im new to linux after deciding it's time to stop using Windows P.E. (Pirate Ed. \\:D/  ) and play it clean by using what's actually free in the first place. 

I have few understandings of linux and what I heard is ubutu is a great O.S. to begin with.. the problem is it is not doing things I enjoyed with windows.
-Can't play MP3
-Can't detect my modem automatically/connect to dial up internet easily
-can't play my vcd/some dvd
-hard to install new programs (bin is like exe right? what is the thing bout making a bin file executable? why are some executable and some not and how do I know if it is?) :confused: 

I know there is a way to do these though but I had ony a few ideas being just 3 days testing it after going home from work. I read the guides about enabling the MP3 and setting my modem. It says "Enable the Universe and Multiverse" done that and my fresh booted ubuntu on 2 different computers react the same way. when You add these repositories an error will occur that some files are unupdated or the repository does not exist. some are looking at [http://something](http://something) and says please reconfigure network...blah blah.. What?! I had to enable this so called repository to set my modem to connect to a network but to enable the modem i had to activate the repository that's requesting a connection?? how will that happen when they need each other at the same time? :confused:

---

### Post by bikeboy on 2006-02-07
Ok for a start, Universe/Multiverse are extra "repositories" which have lots of software for your computer. The software in these areas is not officially supported by  the Ubuntu developers, but is instead supported by the community. To install software you don't have to worry about executables and .bin files etc as it's all done automatically via the internet. It's easy but more on that later when we get your dialup issue solved...

Can you determine what type of modem you have from this? (borrowed from Ubuntu wiki)
> 
Basically, there are two types of modems:

   1.

      Software modems (Winmodems), which are usually delivered as PCI or USB devices or builtin with desktop PCs and laptops these days: Some of these are not supported under Linux, some are. If you bought your computer or modem recently (since ~ 2000), chances are, that you have one of this kind. A Winmodem is a combination of hardware known as chipset (much less than in a true pure hardware modem) and software (written for the infamous Windows operating systems family). A Linmodem is a Winmodem working under the famous Linux operating system. This can be accomplished thanks to the Linmodems.org project.
   2.

      Hardware modems, which are connected to the serial port for example and process the raw modem commands themselves: they have become very rare, but are well supported.


---

### Post by AdonisV on 2006-02-08
Yups, the winmodem I think since It's an internal modem is that right? :KS 

so d you mean that to add these repositories I need to connect online first? :o
Is there also a way to add repositories like these offline?

---

### Post by bikeboy on 2006-02-08
Modem part seems right, I would guess winmodem refers to internal like yours.

The way reopositories it works is that when you add a repository it's has a sort of database of what software is in there. It will download the software from the reopsitory and install it only when you ask it to. But yes, this requires a working internet connection.

So therein lies a problem. You can probably download the necessary drivers with another computer and copy them accross but I wouldn't know how to work out the driver you need. Hopefully someone more knowledgable can help out a bit more there and get your Ubuntu online.

Until then, have a search through [http://wiki.ubuntu.com](http://wiki.ubuntu.com) for dialup topics.

---

### Post by AdonisV on 2006-02-08
k tnx man \\:D/  I'll try to check that. I wish ubuntu just installed all of them in the first place since either way we will do it anyways.. :-D 

I've tested 4 linuxs so far Mandrake (Live, powerpack and move), Suse (Live) , Ubuntu(Live and full) and the aLinux(..which sucks.. can't install it. tried it 5 times and it misses some stuffs and won't load even if the md5sum is correct).. also tried solaris but it hanged on the phase 2 which is insert disk2.. I guess when the first disk was installed and it rebooted.. the driver for the cd rom was no longer recognized :-k 

If the ubuntu won't work i'll try the suse 10 I just got. all I need in the O.S. are:
-Easy Instalation
-Internet Access (Yahoo msgr, Chat, Browsing, etc)
-HW Support (Video cards, Printers, Sound Card, Web Cams, USB)
-Entertainments (DVD, Mp3 , etc..)
-Development (Java, JSP or any dinamic website builder)
-Database support (My Sql, etc.)
-Office tools
-Imaging Tools

For mandrake move I've tried playing DVD's and it's ok and I did not even go through such problems but I did not test the dial up net in any of them yet. So far I like Ubuntu and Suse's GUI the most. I guess I have to look into both which I should go with but I need to test the full 5cd instalation of Suse to see what makes it so big unlike ubuntu's 1 cd O.S. \\:D/

---

### Post by AdonisV on 2006-02-08
Based on you explanation I'm getting an idea.. correct me if I'm wrong

1. Ubuntu is an o.s basicaly and some formats are not supported by it.
2. The repository is the Ubuntu version of Windows Update
3. The Database of the repository you are refering is online and not offline in my machine.
4. To get a list and not the software itself I must connect online to get an 'Updated List' of available repositories.
5. when i select a an item 'Mark for instalation' if it is in the universe/multiverse then it will be downloaded online so I need the internet connection first?

Are these correct \\:D/

---

### Post by aysiu on 2006-02-08
[QUOTE=AdonisV]
1. Ubuntu is an o.s basicaly and some formats are not supported by it.[/quote] Ubuntu is a free operating system--in cost and license. No proprietary formats (like MP3) are included with the default installation. You need to add those in if you need them. You can do that manually if you'd like. There are also special scripts (like [Automatix](http://ubuntuforums.org/showthread.php?t=66563)) that will make it extremely easy for you to do this (not manually).

If you find this a big pain and feel like writing off all of Linux because of it, I would encourage you to try Mepis, PCLinuxOS, Blag, or Linspire. These Linux distributions come with a lot of proprietary codecs out-of-the-box. The first three are cost-free. The last costs money.

> 
2. The repository is the Ubuntu version of Windows Update Yes and no. Windows update will update only the operating system. The Ubuntu repositories will update all the programs you've installed via apt-get or Synaptic (or Adept).

> 
3. The Database of the repository you are refering is online and not offline in my machine. Most useful repositories are online. Technically your installer disk is also a repository, but it's not a very useful one, especially after you've already installed Ubuntu.

> 
4. To get a list and not the software itself I must connect online to get an 'Updated List' of available repositories. Just a list? No, go to [http://packages.ubuntu.com](http://packages.ubuntu.com)

> 
5. when i select a an item 'Mark for instalation' if it is in the universe/multiverse then it will be downloaded online so I need the internet connection first? Yes. An internet connection is an absolute must for easy Linux use. Synaptic (apt-get/Adept) not only downloads the applications but also installs them for you.

---

### Post by AdonisV on 2006-02-08
Wow! that's cool \\:D/ 

so the only thing that's really giving me a hard time was the way to connect online only and once I do that all those games/drivers/codecs in the list of packages.ubuntu.com are available using my synaptics right? :KS 

> The Ubuntu repositories will update all the programs you've installed via apt-get or Synaptic (or Adept).
What's adept and get-apt? :-k  synaptics I know is the one in the settings>Add new(synaptics)

Right now I could'nt activate my universal/multiverse repository because the modem could'nt be detected. in the documentation by UBUNTU Wiki it said..

> Gunzip will 'unzip' the file, chmod will make it an executable (similar to an "exe" file in windows), and ./scanModem will run it. If it tells you to do something as Root by using su - root, instead just enter the commands it wants following a "sudo", e.g. $ sudo modprobe snd-intel8x0m. scanModem will scan your modem and tell you what it is and how to configure it. It will not configure it for you. But after running, you will see a number of new folders, including a 'Modem' folder. Read read1st.txt and modemdata.txt in there, praying that it recognized your modem. This is admittedly not a straight-forward read and might need some more reading around on above mentioned page to find out which drivers your modem needs. Then scan through the following sections to find out about the easiest way to install that driver under Ubuntu. 

Note: For many of the following drivers, you will need to enable the universe/multiverse repositories. See AddingRepositoriesHowto. 

Now the question is if I have one f those in the 'Note:' kind of modems how can you install a modem whose driver (is that what it's really called in linux? :eek: ) is online and to get online I need to make my modem to work first..

Is modem exist ---> true --->enable repositories & get files--> problem ends
         \/
      False
         \/
|Enable Universe/multiverse|
         \/
Is the Repository Enabled -- > True? (Imposible! Look at Comment1)
         \/                                              
       False
(Coz we can't go online having no installed modem)

Comment1= "How can you get it when it's  online and your modem is the one we're tryin t fix in the first place."

Take note that I have'nt tested out yet how to set my modem via the scanmodem file but rather the detect modem in setting>networks but I'll try later on. just in case it still does'nt it would be great to hear from someone in case I encounter the question above.

---

### Post by AdonisV on 2006-02-08
Oh yese.. another question :
In the packages.ubuntu.com there are

warty 
hoary 
hoary-backports 
breezy 
breezy-backports 
dapper 

I think the only thing I need to understand are the breezy parts right?
and there are 2 of them.. so what's a backport anyway? I keep hearing it but the guides dn't make sense for me s far about them. why are they categorized in 2.. is there a difference between breezy and breezy-backport files? \\:D/

---

### Post by bikeboy on 2006-02-08
Apt-get is another way of installing software, but without the gui. If you installed breezy then don't worry about the others. Backports is a repository where newer versions of software are put when they are made to work with breezy (simple explanation). Don't worry about it yet either.

Can I suggest you start a new thread in the hardware section about your modem problem as that is what is preventing you from having a complete working system. Or search the forums for dialup related threads.

---

### Post by manicka on 2006-02-08
You may find these pages useful

[http://help.ubuntu.com/starterguide/C/index.html](http://help.ubuntu.com/starterguide/C/index.html)

and this

[http://doc.gwos.org/index.php/BreezyStarterGuide](http://doc.gwos.org/index.php/BreezyStarterGuide)

---

### Post by AdonisV on 2006-02-08
oki tnx guys. I tried the scanmodem tool lastnight and it created a folder called modem on my desktop. it has only txt files and it says smething bout supported but it did not give any instructions (or any non technical information) about how to easily install the modem. so I went to setting>administration>net5working 
I clicked the modem Icon and set the modem to 'dev/modem' and it gave an error that it was not found. next I tries "dev/tty0" it acceted but I still had not tested it to connect online coz it was so late 12pm and i'm really sleepy. maybe I'll try that later.. \\:D/ 

again tnx for the help guys :D

---

### Post by sylvester_0 on 2006-02-08
OT: Not to be a smart(person) but I sure hope you're not actually using Windows PE for your main desktop. It reboots every 24 hours!

[http://en.wikipedia.org/wiki/Windows_pe](http://en.wikipedia.org/wiki/Windows_pe)

---

### Post by AdonisV on 2006-02-09
nop, Am using windows XP (P.E. Piracy Edition) It's legal in the phil to use any pirated products even if they say it's not. you can actually see pirated products on store shelves and streets. the piracy busting the media here films are just shws created to fool the foreigners. actually the owners of these stores are government family members so you can't touch them.. even bill gates can't \\:D/  but of course I think it's time I go a different path since It is unethecal in a way to join the crowd when there is a right way to do the same thing. \\:D/

---

### Post by locoHost on 2006-02-14
I'm still noob myself so this isn't a very helpful reply. I use a wifi network in my house so I can't help much with modems. Switching from Windows to Linux was kinda tough for me too. Had wifi card and MP3 troubles but I eventually found the answers. Search and search and search, eventually you'll find a post or an article that will solve your problem. You're going to -very- happy with Ubuntu very soon.

Good luck Adonis. Don't give up! :-)

---

