---
title: "What to do after downloadin 8.04 ISO??"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by tobias21 on 2008-08-31
Hi, I'm new to linux so bear with me..

Objective: Need to burn install CD and then install on laptop that has mandriva already (want a dual boot system)

I went to one of the FTP sites and downloaded the following (Hardy?). I created folder on desktop and put them in it. I also copied them to my USB flash card as just in case:

debian-cd_info.tar.gz
initrd.gz
vmlinuz

Can somebody help. I'd like to install from terminal.

---

### Post by rogeriopvl on 2008-08-31
Have you downloaded the ISO file ? You just need to burn into a CD (not as a file, but has an image) and then boot the computer from the CD.

Download the ISO from here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by Ryadt on 2008-08-31
This guide will show you how to burn the iso [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

---

### Post by tobias21 on 2008-08-31
Hi Roger and Ryadt, I tried to download from the link you have mentioned over the last three days but it dowloads at 12-13 kbps when my isp has provided me with 2 Mbps line. Eventually after about 8 hours and 35% download later i lose the internet connection and have to restart all over again. Finally I browsed about for an alternative and came across this  forum (I forget how i got there) that mentioned how to download from this FTP website. I downloded the three files that I mentioned but I don't know how to use it/them to burn the CD. The page that Ryadt mentioned is known to me.

---

### Post by solaceinsilence9 on 2008-08-31
Google something like "ISO Burner" or "Magic ISO". What you need to do is find a program that will let you burn your .iso file as a image on a cd. An .iso is bascially just an 'image' of a install CD. Once you burn your image put the cd in your CDROM and boot from it and follow the instructions.

---

### Post by tobias21 on 2008-08-31
Hi solaceinsilence9: thanks. Can you tell me if the three files I downloaded from the FTP site are all that is needed to successfully carry out this project?

---

### Post by coffeecat on 2008-08-31
> **tobias21 said:**
> Can you tell me if the three files I downloaded from the FTP site are all that is needed to successfully carry out this project?

You won't be able to install Ubuntu with those three files.

If you were getting a slow download speed from rogeriopvl's link, the server must have been overloaded. If you look on that page, you'll see a link to [a complete list of download locations]("http://www.ubuntu.com/getubuntu/downloadmirrors"). Choose another mirror from that list and you'll probably get a fast download speed. You need either the ubuntu-8.04.1-desktop-i386.iso for the live CD which you can also install from, or the ubuntu-8.04.1-alternate-i386.iso for the alternate (text-based installer) CD. Or substitute amd64 for i386 in the filename if you want the 64-bit version.

---

### Post by GepettoBR on 2008-08-31
> **tobias21 said:**
> Hi solaceinsilence9: thanks. Can you tell me if the three files I downloaded from the FTP site are all that is needed to successfully carry out this project?

They are not sufficient. You need the Ubuntu ISO, which can be downloaded from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) as per Rogerio's instructions.

---

### Post by Sand &amp; Mercury on 2008-08-31
Bear in mind, if all else fails you can get Ubuntu CDs mailed to you as well. :D

---

### Post by Sealbhach on 2008-08-31
> **tobias21 said:**
> Hi solaceinsilence9: thanks. Can you tell me if the three files I downloaded from the FTP site are all that is needed to successfully carry out this project?

Hi, just to clarify, what you need is a single file with a .iso ending (CD image file).

Once you have it downloaded you need to burn the image to CD.

If you have Nero, that can do it very well but there are other free ISO burners you can get at [www.download.com](www.download.com) if you need them.

Usually you can just right-click in the .iso file and you will get a menu otpion to burn it to CD.

As someone suggested, choosing another download location might speed things up - otherwise just leave it running overnight or something.

Good luck!


.

---

### Post by rogeriopvl on 2008-08-31
solaceinsilence9 , where are you from? I'm sure there's some FTP server in your country that has Ubuntu iso available for download, at much higher speeds.

---

### Post by fidamehran on 2008-08-31
If you have interrupted downloads, you can try torrent downloads also. Torrent downloads are pretty reliable. Also there are no corrupted data and/or broken downloads.

---

### Post by tobias21 on 2008-08-31
Hello everyone, I am back. I am locatged in india and have tried the FTP site for india : ([ftp://ftp.iitm.ac.in](ftp://ftp.iitm.ac.in)). Trouble is i did not know what links to download. So i read the manifest file, and downloded what i thought were the relevant files for 8.04, Many thanks for all the suport... 

- Yes I think I'll try the downlod option again. Though I am very pessimistic at the moment of the download speed and the stability of my connection.

- Can you tell me more about Torrent. I mean I don't know much about linux.

- Out of curiosity: If the files I dowloaded from the FTP site are not enough then what did I miss?

---

### Post by GepettoBR on 2008-08-31
> **tobias21 said:**
> Hello everyone, I am back. I am locatged in india and have tried the FTP site for india : ([ftp://ftp.iitm.ac.in](ftp://ftp.iitm.ac.in)). Trouble is i did not know what links to download. So i read the manifest file, and downloded what i thought were the relevant files for 8.04, Many thanks for all the suport... 

- Yes I think I'll try the downlod option again. Though I am very pessimistic at the moment of the download speed and the stability of my connection.

- Can you tell me more about Torrent. I mean I don't know much about linux.

- Out of curiosity: If the files I dowloaded from the FTP site are not enough then what did I miss?

You only need one file, a .ISO file to burn to a CD. It is probably called "ubuntu-8.04.1-desktop-x86.iso" or something similar.

Torrents are a method for downloading files from peers that allows you to interrupt the download and resume it later if you want/need to.

---

### Post by tobias21 on 2008-08-31
Thanks. How do i go about doing this Torreent downlod?

---

### Post by Ryadt on 2008-08-31
First you need to download and install a torrent client, utorrent is a good one. Then download the torrent file from here:[http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)
You then open the torrent file with the torrent client.
That's it.;)

---

### Post by GepettoBR on 2008-08-31
There is no Linux version of uTorrent, and no reason to go through a WINE setup just for downloading a iso.

Being a large distribution, Mandriva probably comes with a torrent client pre-installed. Some major clients to look for, in case it doesn't, are Deluge, Transmission, KTorrent and Azureus (also called Vuze).

---

### Post by tobias21 on 2008-08-31
You're right: Mandriva comes with Ktorrent. Thanks. I'll try the torrent download and maybe the usual download from the Ubuntu website. I have already tried the mirrors(?) from Russia, Turkey and I think Taiwan -  all averaging 12-13 kbps speeds. Singapore didn't work. I'll keep you posted.

---

### Post by GepettoBR on 2008-08-31
Alright, good luck!

---

### Post by tobias21 on 2008-08-31
A very quick question: My downloads go to my desktop automatically. Is this OK or do I have to make some sort of download_directory (I saw this on the example for MD5SUM and was wondering), and if I need to, where do I create it? I am talking both, for the torrent downloads and the regular downloads from the regular ubuntu web site.

---

### Post by solaceinsilence9 on 2008-08-31
> **tobias21 said:**
> A very quick question: My downloads go to my desktop automatically. Is this OK or do I have to make some sort of download_directory (I saw this on the example for MD5SUM and was wondering), and if I need to, where do I create it? I am talking both, for the torrent downloads and the regular downloads from the regular ubuntu web site.

Im not sure about uTorrent but if it is similar to BitTornado, which is what I use, you should just be able to choose a spot on your harddrive to save the file to. And yes, it is ok to have your downloads goto your desktop. The destination will not matter. It is completely up to you if you decide to make a download directory. If you do decide to make one, again its up to you where you put it. Im assuming your using Windows? If so, then you could put it in the Documents folder for your user account. But again, it really doesnt make a difference.

---

### Post by GepettoBR on 2008-08-31
> **tobias21 said:**
> A very quick question: My downloads go to my desktop automatically. Is this OK or do I have to make some sort of download_directory (I saw this on the example for MD5SUM and was wondering), and if I need to, where do I create it? I am talking both, for the torrent downloads and the regular downloads from the regular ubuntu web site.

You can save the file to whatever location you want, don't worry. :)

MD5 checksums (MD5SUMS or just MD5 for short) have nothing to do with where the files are stored. They're a way to check if the file you downloaded didn't get corrupted along the way. If you download via torrent, you don't have to worry about that since the download client always checks each piece before writing it to disk, but if you do a regular download, you should check it. This is how:

The same server that has the file should also have a file named "<original filename>-md5.txt" or similar. If you open that file, you'll see a random-looking sequence of numbers and letters like this:

e85cdbc4e20417067c9707a8a1f138b8

Now, open a Terminal and change directories to where you downloaded the ISO (if it's in your Desktop, type "cd Desktop", then hit Enter) and type "md5 <filename>", then Enter. After a while, the Terminal will also generate a sequence of numbers and letters. If both sequences are equal, then the file downloaded without problem. If not, unfortunately you'll have to re-download. But don't worry; nine times out of ten they match.

---

### Post by billgoldberg on 2008-08-31
> **tobias21 said:**
> Hi, I'm new to linux so bear with me..

Objective: Need to burn install CD and then install on laptop that has mandriva already (want a dual boot system)

I went to one of the FTP sites and downloaded the following (Hardy?). I created folder on desktop and put them in it. I also copied them to my USB flash card as just in case:

debian-cd_info.tar.gz
initrd.gz
vmlinuz

Can somebody help. I'd like to install from terminal.

I'm sure this has been told to you, but I can't be bother to read the whole thread now.

The only thing you need is the .iso file. Look for the i386 .iso.

Then you burn that .iso to a cd rom as an image (google "burning iso image").

You can download the iso over the internet or using a torrent client. For large file I prefer a torrent download.

Guide to torrents:

[http://forums.afterdawn.com/thread_view.cfm/229385](http://forums.afterdawn.com/thread_view.cfm/229385)

--

If you need to back up any files on your computer, now is the time to do so.

After you installed Ubuntu on you computer, everything else will be gone (unless you partition the drive and install ubuntu on a different partition).

No put the cd into the cdrom player, restart the pc. 

The live cd should start and then you can follow instructions.

If it doesn't start, you will need to set your bios to boot from cd first.

If you don't know how to do that, google "bios boot from cd".

After it is installed, follow the guide on "Codecs in Ubuntu" from my signature and google "installing applications in Ubuntu".

Then you are set to go.

---

### Post by halitech on 2008-08-31
if you want the torrent file, here they are:

alt cd install
[http://releases.ubuntu.com/8.04/ubuntu-8.04.1-alternate-i386.iso.torrent](http://releases.ubuntu.com/8.04/ubuntu-8.04.1-alternate-i386.iso.torrent)

regular desktop install
[http://releases.ubuntu.com/8.04/ubuntu-8.04.1-desktop-i386.iso.torrent](http://releases.ubuntu.com/8.04/ubuntu-8.04.1-desktop-i386.iso.torrent)

---

### Post by tobias21 on 2008-08-31
Thanks. I am downloading from an australian mirror. I notice two icons on my desktop - one has an image of a cd and another of a pencil. are these the ones for the iso and MD5SUM? Can't see the entire file name - and don't want to touch them untill the download is done.

---

### Post by tobias21 on 2008-08-31
Damn: I just lost my internet connection at 41% download. Could this be an ISP thing - losing my connection after considerable download? It is always at about 35 -40%? *#@?&!. It loks like I will start all over again.

---

### Post by GepettoBR on 2008-08-31
> **tobias21 said:**
> Damn: I just lost my internet connection at 41% download. Could this be an ISP thing - losing my connection after considerable download? It is always at about 35 -40%? *#@?&!. It loks like I will start all over again.

If you are losing the connection so often, try torrents. Even if you lose the connection, you can continue from that point when you get back online instead of starting over.

---

### Post by fidamehran on 2008-09-01
> **GepettoBR said:**
> If you are losing the connection so often, try torrents. Even if you lose the connection, you can continue from that point when you get back online instead of starting over.

That's what I said earlier. Try Torrents. Speed should also be pretty much ok. Plus you get the surety that it will not be corrupted.

---

### Post by tobias21 on 2008-09-01
Just to update: I gave up on the regular mirrors and have ordered for the CD - there's an agent in my area selling 'em!
But, as I do like downloading and then burning them to disk..installing from the command prompt.. and so on, I am going to Torrent download (right now the server is not reacvhable) and do all this that I leaRNT. I have copied a lot of your mails onto my flash card for future reference, and will keep you posted.

---

### Post by tobias21 on 2008-09-01
Thank you for everything!

---

### Post by GepettoBR on 2008-09-01
You're welcome! We're all very glad we could help!

---

### Post by tobias21 on 2008-09-02
This point came to my mind while reading about checksums in your mails on burning that iso cd. on which i'll keep you posted:

Here's the situation:
My mandriva dvd was burnt by an acquaintance.
On verification of all files (rpm -Va command) I found many files corrupted attributes.

Some of them:
.M?.....    /etc/rc.d/init.d/alsa
.M?.....    /etc/rc.d/init.d/sound
..?.....  c /etc/sudoers
..?.....    /usr/bin/sudo
..?.....    /usr/bin/sudoedit
..?.....    /usr/sbin/visudo


For reinstallation i type:
rpm -ivh <package name>

For Upgrading i type:
rpm -Uvh <package name>

In both cases I got:
error: open of sound-scripts-0.49-1mdv2008.0 failed: No such file or directory

I was signed in as root.

Incidentally, my dvd playback is ok in a little window but not so good in full screen. Curiosly enough mandriva's screen savers produce excellent color in full screen. I have totem and lindvd. Can you help me with this, please?

---

### Post by Sealbhach on 2008-09-03
This is about Mandriva?

You might get help more quickly on a Mandriva forum. I don't know anything about rpm files, although perhaps many Ubuntu users do.



.

---

