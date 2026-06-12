---
title: "HOWTO: Buy MP3 music from Amazon.com."
date: 2008-08-04
forum: Outdated Tutorials &amp; Tips
---

### Post by bcrowell on 2008-08-04
**How amazon's system works**

Typically if you search for MP3 files on amazon, you'll get a list of matching tracks with "Buy MP3" buttons, and also possibly some albums with buttons that say "Buy MP3 Album." (See the first screenshot attachment below.) It doesn't matter whether you have 1-click ordering turned on or not; if you're logged in, clicking on the orange button immediately charges your credit card and starts downloading the music.

Amazon used to have two separate mechanisms for downloading music. If you bought an individual track, your browser would simply download it as an MP3 file, whereas if you bought an entire album, it would download a small file in .amz format, which you then had to open with a special downloader application provided by amazon in order to get the actual MP3 tracks of the album. (See the second screenshot attachment below.) Recently (August 2008), however, amazon seems to have changed their system so that all downloads go through the .amz step, even if you're just buying an individual track. For Windows and Mac users, the advantage of the downloader application is supposed to be that it integrates with iTunes or Windows Media Player. It also handles things like resuming interrupted or failed downloads. There is a Linux version of the downloader, and this howto is about solving common problems with getting it to work.

If you buy a track without having the downloader installed on your system, your browser will detect that, and will detect that you're running Linux, and it will offer you links to download various Linux versions of the software. Unfortunately the downloader isn't open-source, so you're limited to the binary versions that amazon provides, and it may be difficult to get these working if you're using a later version of Ubuntu than they anticipated, or if you're on a different architecture, such as a 64-bit machine.

**Clamz**

One way to bypass the problems with amazon's downloader is to use an alternative, open-source downloader written by Benjamin.Moody, called clamz: [http://code.google.com/p/clamz/](http://code.google.com/p/clamz/) It's a command-line program.

To install clamz, click on the link to download clamz-0.1.tar.gz, save it into a directory where you want to work, open a terminal window, and cd into that directory. In the terminal window:

The documentation for clamz says to install the necessary libraries like this:

```
sudo apt-get install libgcrypt11-dev libcurl4-gnutls-dev libcurl4-openssl-dev libexpat1-dev
```

On my system, however, libcurl4-gnutls-dev didn't want to install, so I did this instead:

```
sudo apt-get install libgcrypt11-dev libcurl4-openssl-dev libcurl4-openssl-dev libexpat1-dev
```

Next you have to compile and install clamz:

```

tar -zxf clamz-0.1.tar.gz
cd clamz-0.1
./configure && make
sudo make install

```

Now if you click to buy a song, your browser will offer you a download dialog. Save the .amz file to disk. Next, from the terminal use clamz to download the actual MP3(s):

```

clamz 01\ -\ Better\ Git\ It\ In\ Your\ Soul\ -\ Antibes\ 1960\ -\ Live.amz

```

To avoid having to type the extremely long filename, you can just type the first few characters, then hit the tab key, and your shell should supply the rest of the filename.

**The amazon downloader -- 32-bit machines**
If you prefer to use the amazon downloader, here's how it's supposed to work. From the links supplied on the amazon page that came up after you bought your song, select the .deb file that most closely approximates the version of Ubuntu you're using. Open a terminal window, cd into the directory where you downloaded the .deb file, and do the following:

```

sudo apt-get install libboost-signals1.34.1 libboost-iostreams1.34.1
sudo dpkg -i amazonmp3.deb
amazonmp3

```

The third line is to test whether the program will actually run. It should start up the downloader's GUI.

Although you've installed the downloader, your browser won't automatically detect that fact. When you buy a song, you'll get a web page with an error saying that you need to install the downloader. Way down at the bottom of that page, however, you'll get a very small message saying, "If you have already installed the Amazon MP3 Downloader, click here to enable it for use with this browser." You have to click on that the first time in order to make downloads work. I've sometimes observed that the error message recurs even after you've gone through this step to configure your browser. I think this may be because it uses a cookie to remember the configuration, so if you clear your cookies, you have to do it again.

For convenience, you'll probably want to configure your browser so that it automatically associates the filetype .amz with the amazon downloader. Here's how to do that in Firefox. When you buy your first song, you'll get a dialog box saying "You have chosen to open foo.amz ... What should Firefox do with this file?" Choose "Open with" "Other...", and in the dialog box that pops up, choose /usr/bin/amazonmp3. Then check the box that says "Do this automatically for files like this from now on." To change this file association later, go to Edit>Preferences>Applications>AmazonMP3 download queue.

**The amazon downloader -- 64-bit machines**

On a 64-bit machine, the method above may not work, because amazon only supplies the downloader as a 32-bit application, which needs 32-bit libraries. In this case, if you run the amazonmp3 program from a terminal window, you'll get an error message something like this:

```
amazonmp3: error while loading shared libraries: libgtkmm-2.4.so.1: cannot open shared object file: No such file or directory
```

There is a script called getlibs that's designed to help you get around this problem: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790) The 32-bit instructions above have to be modified like this:

```

sudo apt-get install libboost-signals1.34.1 libboost-iostreams1.34.1
sudo dpkg -i --force-all amazonmp3.deb
which amazonmp3
getlibs /usr/bin/amazonmp3
apt-get install lib32nss-mdns
amazonmp3

```

The line to install lib32nss-mdns is necessary in order to get rid of a mysterious-seeming error. If you don't have this package installed, then every time you try to use the downloader you'll get messages saying "Can't connect. Please check your internet connection..."

**Other problems**
I've seen the following problem reported by other people, but haven't encountered it myself. It may be a bug that amazon has already fixed. The bug is that when you download a .amz file, your browser puts it in /tmp and makes it read-only. Then when the downloader app tries to open it, the first thing it does is try to delete it (so that it won't be left behind when the process is complete). This fails because the file is read-only, and the downloader then fails without any informative error message.

**Redoing a download after having a problem**
If you've had a problem with a download and want to retry it, you have a couple of options.

One method is simply to start amazonmp3 again from the command line (rather than from your browser). It should retry any downloads that are still outstanding.

If you prefer clamz, or can't get amazonmp3 to work, you can also go to the amazon web site, move your mouse over the down-arrow next to "Your lists" (don't click on the words "Your lists," which will do something different), then click on "Your media library." Hover your mouse over the down-arrow in the "Downloads" tab, and click on "Amazon MP3." If you click on the underlined link for a particular song or album, it will give you some information about the track, such as when you bought it, and whether you've already downloaded it. If you click on the Download button on the right, it should let you download it. (If it thinks you've already completed the download, it won't let you download it again.)

**Problems with albums that come with extra materials (liner notes, videos, etc.)**
When you buy one of these, it may say that you have to install the downloader. Clicking on the link saying you've already installed the downloader doesn't work. It can look as if your whole setup for buying music from Amazon is suddenly, mysteriously broken, but actually this is only because this particular album comes with extra materials. To get around this problem, you have to use one of the following two techniques to convince amazon that you have the right version of the downloader:
(1) Go to amazon's home page and type this in the url bar: javascript:document.cookie='dmusic_download_manager_enabled=1.0.9;expires=Fri, 21 Dec 2012 12:00:00 UTC; path=/; domain=.amazon.com'
(2) Go to this url: [http://www.amazon.com/gp/dmusic/after_download_manager_install.html?AMDVersion=1.0.9](http://www.amazon.com/gp/dmusic/after_download_manager_install.html?AMDVersion=1.0.9)
I have tested #1 and found that it worked. According to Benjamin Moody, the developer of clamz, #2 is the officially supported method. Note that in both cases there is a version number, 1.0.9. In the future when amazon raises the minimum version number, you'll have to bump this up.

---

### Post by Bigfork on 2008-09-10
> **bcrowell said:**
> 
The line to install lib32nss-mdns is necessary in order to get rid of a mysterious-seeming error. If you don't have this package installed, then every time you try to use the downloader you'll get messages saying "Can't connect. Please check your internet connection..."


Thanks!!  Just what I needed!

'Fork

---

### Post by CFBauer on 2008-12-11
Thanks. Amazon really needs to do something about their downloader. I sent them an email.

---

### Post by oimon on 2008-12-16
agreed, amazon should sort this out.
running 32-bit 8.10, i also had to install the following in addition to the instrucctions above

 sudo apt-get install libboost-thread1.34.1 libboost-date-time1.34.1 libboost-regex1.34.1  libboost-filesystem1.34.1

---

### Post by newlinux on 2008-12-19
> **oimon said:**
> agreed, amazon should sort this out.
running 32-bit 8.10, i also had to install the following in addition to the instrucctions above

 sudo apt-get install libboost-thread1.34.1 libboost-date-time1.34.1 libboost-regex1.34.1  libboost-filesystem1.34.1

Had to do this too on hardy. Way back on Feisty The Debian etch version worked for me. I should have tried that on Hardy first. I have another Hardy machine, maybe I will.

---

### Post by binbash on 2008-12-19
> **oimon said:**
> agreed, amazon should sort this out.
running 32-bit 8.10, i also had to install the following in addition to the instrucctions above

 sudo apt-get install libboost-thread1.34.1 libboost-date-time1.34.1 libboost-regex1.34.1  libboost-filesystem1.34.1

THanks ;)

---

### Post by goodman_m_w on 2009-03-01
Thank you! I had found the getlibs solution from another source, but they made no mention of the lib32nss-mdns package. Now all is working on 64bit Jaunty alpha5.

---

### Post by MrWizard on 2009-03-03
If anyone is interested in helping me out, I wrote an Amazon.com MP3 downloader in Python and any feedback would be appreciated.  Thread here:
[http://ubuntuforums.org/showthread.php?t=1085987]("http://ubuntuforums.org/showthread.php?t=1085987")

---

### Post by ogryn on 2009-07-23
Thanks. The Clamz package help got me over some hurdles on a 64bit 9.04 :)

---

### Post by giomark on 2009-07-23
Me too..I always like to buy on amazon or ebay.

---

### Post by rs3 on 2009-09-18
I ran into that "mysterious-seeming error" and only had to install lib32nss-mdns to get the 32-bit client working with 64-bit Jaunty.  Thank you so much!

---

### Post by ezekiel000 on 2010-06-02
Not sure if anyone wants this but I compiled & packaged clamz 0.4 for my own use, I run Ubuntu 10.04 amd64 so I can't be sure it works on any other version of Ubuntu.
I've zipped it as strangely you can't attach deb's here.

---

### Post by akshunj on 2011-02-27
You know what sucks? I would pay like $5 to download and use clamz from something like a Ubuntu app store. I'm a linux vet, but I'm also getting old and lazy. And I LOVE the simplicity of the Android app store, but there's nothing like it for Ubuntu.  Just thinking out loud...

---

### Post by kiddykoff on 2011-02-27
Theres an easier way to buy from Amazon. Just use Banshee. I'm using their ppa, so you might have to do the same or you can wait til Naty comes out.

> **akshunj said:**
> You know what sucks? I would pay like $5 to download and use clamz from something like a Ubuntu app store. I'm a linux vet, but I'm also getting old and lazy. And I LOVE the simplicity of the Android app store, but there's nothing like it for Ubuntu.  Just thinking out loud...

Aksuhnj, there is the ubuntu software center. I remember reading that there was a deal recently made between different distros to make it more approachable or have more apps available. i don't remember the details.

---

### Post by magna_maxima on 2011-05-23
Amazing! The little trick at the end helped me download an album with extra materials after I'd been smacking my head. Thank you so much!

---

### Post by kiran11 on 2011-05-24
If you choose to save your purchases to Amazon Cloud Player__, they are saved directly to your own personal Cloud Drive space.  Files stored in Cloud Drive are accessible using the Amazon Cloud Player, Amazon Cloud player for Anaroid Music can be downloaded to any computer or Android device using the Amazon MP3 Player. You can choose to set up automatic download for all new purchases on your computer through your Setting Page. For more information see Downloading Music.

  [Buy Cheap   Battefield 3 CD key]("http://www.battlefield3cdkey.com/")

---

