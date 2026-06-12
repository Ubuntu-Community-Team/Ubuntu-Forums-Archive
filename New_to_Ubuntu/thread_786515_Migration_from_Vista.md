---
title: "Migration from Vista"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by fballem on 2008-05-08
I have been using Windows since Windows 3.1. A friend of mine suggested that I give Ubuntu a try, and so far so good. Some questions:

1. I am wondering if I need to run an anti-virus program, and if so, which one should I run. Must be simple to install and reliable. If I've got the terminology right (no guarantees), I am runing Ubuntu 8.04 with GNOME.

2. Does anyone know a way to get an HP Pavilion Webcam up and running? I have an HP Pavilion 9231ca.

3. I used Windows OneCare, which provided my anti-virus, but also provided my backup to a Network Addressable Storage device. The backup is simple to configure and very reliable (the restore has been fully tested on more than one occasion!). Is there something similar that is easy for a Windows user to use in the linux world? Must be easy to install, must be reliable, and must allow for full and incremental backups and restore.

4. I have a large collection of Windows Media (lossless) files. Can I still play these, and if so, how?

5. I have a Creative Zen MP3 Player. Can I still synch this, and if so, how?

This is a place to start.

Many thanks!

---

### Post by NightwishFan on 2008-05-08
1. You will likely not need to run a virus program, Linux is secure by default and viruses are simply not compatible.

2. I do not know about the webcam but perhaps try the program cheese and see if it works out of the box.

3. My main method of backup is using a separate home partition and keeping my important data on a dvd, although I am pretty sure there are backup programs available.

4. Vlc and restricted codecs play .wma I believe, I do not have one to test though. (I use the open source vorbis audio.)

5. Not sure, but Amarok or Rhythmbox music players may have this ability.

My apologies that I do not have all the answers.

---

### Post by billgoldberg on 2008-05-08
> **fballem said:**
> I have been using Windows since Windows 3.1. A friend of mine suggested that I give Ubuntu a try, and so far so good. Some questions:

1. I am wondering if I need to run an anti-virus program, and if so, which one should I run. Must be simple to install and reliable. If I've got the terminology right (no guarantees), I am runing Ubuntu 8.04 with GNOME.

2. Does anyone know a way to get an HP Pavilion Webcam up and running? I have an HP Pavilion 9231ca.

3. I used Windows OneCare, which provided my anti-virus, but also provided my backup to a Network Addressable Storage device. The backup is simple to configure and very reliable (the restore has been fully tested on more than one occasion!). Is there something similar that is easy for a Windows user to use in the linux world? Must be easy to install, must be reliable, and must allow for full and incremental backups and restore.

4. I have a large collection of Windows Media (lossless) files. Can I still play these, and if so, how?

5. I have a Creative Zen MP3 Player. Can I still synch this, and if so, how?

This is a place to start.

Many thanks!

1. No. You should however run a firewall. (try firestarter) There are anti-virus scanners available for linux, but they search for windows viruses and are meant to run on computers that share files with windows computers.

2. Sorry, can't help with that one.

3. Sure, there are loads of great back-up solutions.

I back-up manually, but you might want to try "simple backup"

(install using "applications -> add/remove")

4. Yes, you'll need some codecs.

In a terminal (applications add/remove) copy/paste this:

sudo apt-get install ubuntu-restricted-extras

Take a look at my blog ([link]("http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/")) on how to install the medibuntu repo.

After it's installed, scroll down the page to install the non free codecs.

Then you should be able to play all audio and video files.

5. [http://ubuntuforums.org/showthread.php?t=216191](http://ubuntuforums.org/showthread.php?t=216191)

---

### Post by ad_267 on 2008-05-08
1. No you don't need any antivirus software. You may want to if you are sharing a lot of files with windows users to make sure there are no windows viruses in them. ClamAV is supposed to be good for this.

2. Don't know sorry

3. I think most people use command line applications for this. See [http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

4. Yes. See [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

5. Yes rhythmbox should recognise it automatically if it is just a usb storage device. If it is an mtp device you need to activate the mtp plugin.
Edit: Looks like they are an mtp device. The latest Ubuntu provides pretty good support for mtp devices. Just enable the mtp plugin in rhythmbox.

---

### Post by thenes on 2008-05-08
Hi

First of all, the best way to answer this questions is by trying a dual boot between Ubuntu and Vista. That way you can spend time testing Ubuntu without leaving Vista behind. I am sure there are many good guides for how to dual boot Vista and Ubuntu (I am not the right one to give a guide, as I dual boot Kubuntu and os x).

Your questions:
1. Most people I know run Ubuntu without any anti virus program. Viruses are not a very usual problem on unix-based operating systems (like Ubuntu)

2. [This tread]("http://ubuntuforums.org/showthread.php?t=323730") discuses the webcam you mention. It seems like it is working by the replies.

3. I simply use drag and drop backups to my external hard drive. There are several backup programs available, but I am not right one to tell you about them, as I do not use them. In ubuntu backing up by copying your home folder will usually back up all your personal files (pictures, documents etc).

4. I leave it to somebody else to answer this.

5. [This tread]("http://ubuntuforums.org/showthread.php?t=199250") discusses the mp3-player you mention. I have not tried myself.

---

### Post by Sef on 2008-05-08
> No. You should however run a firewall. (try firestarter) 

A firewall is installed by default.  Firestarter is simply a front-end gui for it.

---

### Post by fballem on 2008-05-08
Thanks all for your help. Some additional information and questions:

1. Dual boot - I'm in the fortunate position of having a couple of machines in the house, so going ubuntu on one of them is not a big deal. The objective is to figure out whether I can work in linux (ubuntu) and what issues I'm going to have.

2. I converted my Outlook e-mail by installing Thunderbird on Windows, moving all of my e-mail, and saving the files on my NAS. When I went to ubuntu (and Thunderbird), I was able to copy the files into the local files folder. Worked really well. Forgot to export my contact list, so that's my next project.

3. Haven't figured out the music issues yet, but I do have some time to do this.

4. Some initial observations (after two days). The learning curve is steep, and as a user, I am finding myself getting a lot more under the covers than I am comfortable with. There's stuff (like the affection that linux users have with Terminal) that I haven't done since my DOS days (yes, I go back that far). I am trying to decide whether to convert the other computers (need to save some money). So far, it's a definite maybe.

5. My initial install was ubuntu 6 (it was from a book I found). Happily, I downloaded the full ubuntu 8 and burned it to CD (really easy!) and redid the installation. Happily, that also picked up my wireless network adapter, and with a bit of configuration, it is working very well.

6. I have no idea what to do with a .tar file, but I'm sure eventually I'll figure it out. I ran into those trying to install Adobe Reader and Adobe Flash Player.

7. I have tested a couple of files (excel and word) in OpenOffice. They seem to work. Haven't tested Visio yet, but that's for another day.

8. It would be nice if HP offered to support the Color LaserJet 2600 directly in linux, but I was able to get it working in CUPS - once I figured out socket. In Windows, the printer is identified automatically and installed. Still, I am able to print, which is important.

9. Still want a backup utility that is graphical and will go to my NAS as the backup device.

10. Still haven't figured out how to get the second drive that's in my machine working, and how to set it up. If I have to bring my media in from the NAS, then it needs to go on the second drive.

Not bad for a couple of days work. This will be a pick-away project for a few weeks before I make my decision.

I never did figure out how IRC chat works, but was pleasantly surprised that I am able to continue with my Windows Live Messenger account.

Again, thanks to all of you, and I'd like to keep this thread going for a while.

---

### Post by hessiess on 2008-05-08
convert your music to FLAC, it has much better Linux support.

---

### Post by tjwoosta on 2008-05-08
for music use amarok or exaile (both awesome music players)

video i would use either VLC or Mplayer

as for playing .wma and .wmv they both work fine after you install the w32codecs (or w64codecs if u use 64bit ubuntu)

---

### Post by drsox1899 on 2008-05-08
Try dual booting with this HowTo :

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

As time goes on I'll bet you will need to use Windows less and less and one day you'll get rid of it altogether.

Luck

---

### Post by 0faber on 2008-05-08
For #6: Go to system > administration > synaptic package manager, click search type "flash," select "flashplayer-nonfree," This will download and install flash automatically. 

Generally, this the best way to install programs in Ubuntu. (If you do download something directly off of a website without using synaptic, you need to get a .deb file not a .tar file.)

---

### Post by newbuntuxx on 2008-05-08
I second what Ofaber said. Being a newb myself, the best way in ubuntu to download software is either the synaptic manager or get-apt in terminal. I prefer the latter, as it is faster and accurate.

Do not download tars/debs unless you are unable to find what you are looking for in the ubuntu repositories. 

This was very difficult to grasp when I made the switch from XP to ubuntu. In windows, you needed to install motherboard, card drivers etc...from a cd. And then you need to start downloading programs from all around the cyberspace and install them. Which is really a waste of time.

ubuntu: everything you need is already installed. And if it so happens that you need additional software, well, its all in the ubuntu repositories!

kudos ubuntu (well, all linux distros have that i think)

---

### Post by fballem on 2008-05-08
This will be interesting - apparently the w32codecs will not read Windows Media (lossless). It looks like I'll have to use something to convert them. Is there a lossless format in Linux?

---

### Post by NightwishFan on 2008-05-08
Flac is lossless.

---

### Post by fballem on 2008-05-08
Hessius had what turns out to be an excellent suggestion. There is an MS Windows program called DBPowerConverter that is free and can convert Windows Media Lossless to FLAC. It takes a long time, but it is certainly faster than re-ripping all of those CDs. There is also a codec that will run FLAC in Windows Media, so sounds like I will be enjoying my music sooner than I expected.

---

### Post by fballem on 2008-05-09
Found this really useful thread on media. As a happy result, I can listen to my Gameday Audio on MLB.COM, although the display looks a little weird (possibly due to Silverlight).

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by fballem on 2008-05-09
I have installed WINE - my children have some PC games that they want to continue using. It is adequate for our purposes - the games are not the highly interactive type.

Impressions: very favourable!

On the plus side: This was easier than I thought it would be, particularly once I got to ubuntu 8.04. Everything works. Particularly helpful are: 

1. Thunderbird, which I installed in Windows and brought down my e-mails. I forgot to bring down my contacts, but I do have a way to get those. I will be using Thunderbird and the Calendar attachment going forward to replace Outlook.
2. The conversion program to copy the WMA (Lossless) media files to FLAC. I installed the program on the Windows machine, downloaded the two codecs that were required, and used the batch mode to do the conversion. It is slow, but definitely faster than re-recording all of the CDs.
3. The link to the information about media that I referenced in one of my posts. The instructions were clear and very logically presented.
4. The suggestions and encouragement that I received during this series of posts - many thanks to all of you.
5. Pigeon - still allows me to use my MSN Messenger.

On the minus side:
1. The lack of support for Visio files. I will be using dia, but it does not support, nor will it open, Visio files. Hopefully, at some time in the future, that problem will be solved. In my situation, it is not huge, but it is an inconvenience.

An observation, if I may. Those of us who are coming from Windows are not comfortable with Terminal. You have all become comfortable with Terminal, probably because there weren't GUI based tools to do the job. Your first instinct is to use Terminal or some of the other command-line type tools, but I would like to suggest that if there is a GUI-based alternative, then that should be suggested to those of us coming from Windows. It will encourage us to make the leap - and maybe we too will become comfortable with Terminal.

That being said, the support has been amazing, and I thank you all.

Yours sincerely,
Flavelle
ex-Windows User

---

### Post by drsox1899 on 2008-05-10
> **fballem said:**
> 

An observation, if I may. Those of us who are coming from Windows are not comfortable with Terminal. You have all become comfortable with Terminal, probably because there weren't GUI based tools to do the job. Your first instinct is to use Terminal or some of the other command-line type tools, but I would like to suggest that if there is a GUI-based alternative, then that should be suggested to those of us coming from Windows. It will encourage us to make the leap - and maybe we too will become comfortable with Terminal.

That being said, the support has been amazing, and I thank you all.

Yours sincerely,
Flavelle
ex-Windows User

When you are editing system setup files,(e.g. *.conf),  then instead of "sudo" in root, use "gksudo gedit" in root.  This will open the text editor in GUI mode with full functionality including saving/modifying system files.

---

### Post by fballem on 2008-05-10
> **drsox1899 said:**
> When you are editing system setup files,(e.g. *.conf),  then instead of "sudo" in root, use "gksudo gedit" in root.  This will open the text editor in GUI mode with full functionality including saving/modifying system files.

Thanks - another nugget of useful information. This will take me a while to absorb, but the leap is well underway.

---

### Post by Stefanie on 2008-05-10
i'm a newbie myself, but i find the archive manager useful when using .tar, .zip or other compressed formats.
this guide [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) has also helped me a lot.

i have no idea what to do with your visio files, i'd like to know that, too.

i think you should really try simple backup, it's very straightforward to use. 

about your second drive: when i open nautilus (places -> home) i see all my partitions in the left column. you can also click places -> computer.

---

### Post by fballem on 2008-05-10
> **Stefanie said:**
> i'm a newbie myself, but i find the archive manager useful when using .tar, .zip or other compressed formats.
this guide [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) has also helped me a lot.

i have no idea what to do with your visio files, i'd like to know that, too.

i think you should really try simple backup, it's very straightforward to use. 

about your second drive: when i open nautilus (places -> home) i see all my partitions in the left column. you can also click places -> computer.

Stephanie:

Thanks for the guide. I think that it will be most helpful

Visio seems to be a common problem. Fortunately, I have very few of them. I read in the Dia forum that someone is working it, but there is no ETA. It's not critical for me.

The mount that was discussed in another post (additional drives) seems to be working.

I have simple backup working and you're right - it is relatively simple. Be careful with the exclusions - there's one based on size by default. I'm not sure how many I have that exceed that size (not many), but I removed that exclusion anyway.

Regards,
Flavelle

---

### Post by fballem on 2008-05-11
I was having some problems with setting up additional drives and with accented characters in filenames. The solutions are in the following post: [http://ubuntuforums.org/showthread.php?p=4932265#post4932265](http://ubuntuforums.org/showthread.php?p=4932265#post4932265)

---

### Post by rburkartjo on 2008-05-11
fb to get the zen player to work. go to applications/add-remove/make sure 
that the show button on the top left is set to all available appl/in search box type in gnomad2/click the box and hit the apply changes/ this will install gnomad2. it will be located in applications/sound and videos.then right click on the icon and select add this launcher to desktop. it works like a charm right out of the box. did this for my daughter/cheesemaker

---

### Post by fballem on 2008-09-06
> **rburkartjo said:**
> fb to get the zen player to work. go to applications/add-remove/make sure 
that the show button on the top left is set to all available appl/in search box type in gnomad2/click the box and hit the apply changes/ this will install gnomad2. it will be located in applications/sound and videos.then right click on the icon and select add this launcher to desktop. it works like a charm right out of the box. did this for my daughter/cheesemaker

Thanks for the information. For me, the loading of my music to my MP3 player is a three-step process. I first rip CDs on to my computer in lossless format (Sound Juicer), then copy the lossless to MP3 (Sound Converter), then transfer the MP3s (gnomad2).

---

### Post by Bucky Ball on 2008-09-06
Hey, fballem - I just read your first post in this thread and you sounded like you were pretty experienced in the Windoze world but just needed to get your head around some very different concepts in the Linux one (something you see a lot).

I could see where things were going so I just went straight to your last post in the thread and missed all the rest (straight to the destination missing the journey) and sure enough ... straight up the learning curve you went and sounding right at home! Welcome and enjoy! \\:D/

---

### Post by fballem on 2009-05-09
> **fballem said:**
> I have installed WINE - my children have some PC games that they want to continue using. It is adequate for our purposes - the games are not the highly interactive type.

Impressions: very favourable!

On the plus side: This was easier than I thought it would be, particularly once I got to ubuntu 8.04. Everything works. Particularly helpful are: 

1. Thunderbird, which I installed in Windows and brought down my e-mails. I forgot to bring down my contacts, but I do have a way to get those. I will be using Thunderbird and the Calendar attachment going forward to replace Outlook.
2. The conversion program to copy the WMA (Lossless) media files to FLAC. I installed the program on the Windows machine, downloaded the two codecs that were required, and used the batch mode to do the conversion. It is slow, but definitely faster than re-recording all of the CDs.
3. The link to the information about media that I referenced in one of my posts. The instructions were clear and very logically presented.
4. The suggestions and encouragement that I received during this series of posts - many thanks to all of you.
5. Pigeon - still allows me to use my MSN Messenger.

On the minus side:
1. The lack of support for Visio files. I will be using dia, but it does not support, nor will it open, Visio files. Hopefully, at some time in the future, that problem will be solved. In my situation, it is not huge, but it is an inconvenience.

An observation, if I may. Those of us who are coming from Windows are not comfortable with Terminal. You have all become comfortable with Terminal, probably because there weren't GUI based tools to do the job. Your first instinct is to use Terminal or some of the other command-line type tools, but I would like to suggest that if there is a GUI-based alternative, then that should be suggested to those of us coming from Windows. It will encourage us to make the leap - and maybe we too will become comfortable with Terminal.

That being said, the support has been amazing, and I thank you all.

Yours sincerely,
Flavelle
ex-Windows User

One year on - May-9-2009:

[LIST=1]
[*]It took me a long time to finally make up my mind - kept re-installing Vista, then missing some of the things that were so easy in ubuntu, so I would install.

[*]I always had issues with two programs: MS Visio and Enterprise Architect from Sparx Systems. There is no Linux equivalent for either program. I have made the decision to live without Visio on my main computer, and Enterprise Architect runs very well under Wine.

[*]After futsing with Thunderbird and Lighting (the calendar add-on), I decided to use Evolution. Two reasons: 1) It looks and works like Outlook, and 2) If I put an alarm in my calendar, then it will pop-up on my desktop whether or not Evolution is running (can't do that in Windows/Outlook).

[*]Bought the fluendo codecs ([http://www.fluendo.com](http://www.fluendo.com)), which plays Windows Media Lossless. I haven't run into a video or audio file that I can't play - combination of the ubuntu-restricted-extras and the fluendo codecs.

[*]I am now using 64-bit ubuntu 9.04. I managed to customise the themes (I use Nimbus from the OpenSolaris website), which was a good learning exercise on themes.

[*]I've converted a couple of my small clients to ubuntu - it was either buy a new machine or convert them. They seem to be running well with no major problems.

[*]I really find the two panels (top and bottom) to be most useful, and I also make frequent use of the multiple desktop feature. In fact, I really miss them both when I have to work on a Windows machine.

[*]Installation time (Windows) - from the time that I first put a Windows Vista CD into the drive and start the pc up until the time that I have completed the installation, including installation of all programs, drivers, and devices and configuration of various options in my programs, it used to take me about 1-1/2 to 2 days - and that's on a machine that I know well and have full backups of all data for. 

[*]Installation time (ubuntu) - from the time that I first put an ubuntu CD into the drive and start the pc up until the time that I have completed the installation, including installation of all programs, drivers, and devices and configuration of various options in my programs, it now takes me about 3-1/2 hours - on a machine that I know well and have full backups of all data for. On one client's pc, that I don't know well, I backed up the data, installed ubuntu, all programs, drivers, devices, and configuration of various options in their programs and restoration of all data took me about 8 hours. Another 3 hours were spent working with the client to make sure that they were comfortable.

[*]I have tried Fedora and OpenSUSE, both of which are highly regarded in this forum. I prefer ubuntu because it is easier in small ways. One of the small things that I really like in ubuntu is that the root account is disabled by default. Anything that I need to do, I can do using sudo/gksudo (in a terminal) or Synaptic for the GUI installations. I prefer that because it's one less password for me to lose (or change on a periodic basis).
[/LIST]

Hope this helps,

---

