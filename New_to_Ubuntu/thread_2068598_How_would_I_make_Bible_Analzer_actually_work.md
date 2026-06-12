---
title: "How would I make Bible Analzer actually work?"
date: 2012-10-09
forum: New to Ubuntu
---

### Post by Jackalyn on 2012-10-09
I have the whole of Bible Analyzer downloaded and have extracted the files and have an icon that looks as if if I click on it then the program would open and I would be able to use it. Unfortunately,  what happens is that when I click on it -well it closes the finder thing and nothing else happens. 

Is this like the Open Office thing I have where I have Open Office but can only open it using the terminal and if that is the case, what do I put in the terminal to open Bible analyzer? It is Bible Analyzer 4.5. -Or, do I need to do something iwith Wine?

(I also still have  the whole of Calligra Author on my desktop. )This is NOT Calligra 2.5 which I also have and this remains as a tar gz file and I cannot seem to run that either although I clearly have all the files. If anyone has any ideas about that I would still like to try it.))

Gosh when those two are sorted I cannot think of another thing I need. 

:popcorn:


Thx

J

Ubuntu 12.4

---

### Post by oldos2er on 2012-10-09
Did you download the .deb file?

---

### Post by grahammechanical on 2012-10-09
Please, tell us which of these file formats you downloaded?

[http://www.bibleanalyzer.com/download.htm]("http://www.bibleanalyzer.com/download.htm")

If you downloaded this file:

bibleanalyzer.4.5-5.all.deb then you do not unpack it. You right click it and select Open with Ubuntu Software Centre which will install the program for you and provide an un-install option should you need to remove the program.

Perhaps you should read this:

[http://www.bibleanalyzer.com/linux.htm]("http://www.bibleanalyzer.com/linux.htm")

Regards.

---

### Post by Jackalyn on 2012-10-09
> **grahammechanical said:**
> Please, tell us which of these file formats you downloaded?

[http://www.bibleanalyzer.com/download.htm](http://www.bibleanalyzer.com/download.htm)

If you downloaded this file:

bibleanalyzer.4.5-5.all.deb then you do not unpack it. You right click it and select Open with Ubuntu Software Centre which will install the program for you and provide an un-install option should you need to remove the program.

Perhaps you should read this:

[http://www.bibleanalyzer.com/linux.htm](http://www.bibleanalyzer.com/linux.htm)

Regards.

I did read that one which is why I am confused. Yes .deb files and when I right click on the download it opens Ubuntu Software manager which tells me that the program is installed but when I put bibleanalyzer into the terminal I get
jacky@jacky-Aspire-6930G:~$ bibleanalyzer

************ Starting Bible Analyzer *************
0.59505200386 before aui import
Traceback (most recent call last):
  File "/usr/share/bibleanalyzer/analyzer4.py", line 41, in <module>
    import sessionMan
  File "/usr/share/bibleanalyzer/sessionMan.py", line 30, in <module>
    os.mkdir(ur'%s' % homeUserDir)
OSError: [Errno 2] No such file or directory: '/home/jacky/Documents/BibleAnalyzer'

Press Enter to close terminal

And then I am back where I started because the program is installed........

---

### Post by cortman on 2012-10-09
Hm, would it be as simple as running

```
mkdir ~/Documents/BibleAnalyzer
```

It could be it didn't install right- for downloaded .deb files I prefer to use dpkg rather than the software center- in a terminal run

```
sudo dpkg -i package_name
```

to install.

---

### Post by Jackalyn on 2012-10-09
> **cortman said:**
> Hm, would it be as simple as running

```
mkdir ~/Documents/BibleAnalyzer
```It could be it didn't install right- for downloaded .deb files I prefer to use dpkg rather than the software center- in a terminal run

```
sudo dpkg -i package_name
```to install.

mkdir ~/Documents/BibleAnalyzer comes up as no such file or directory.

---

### Post by Jackalyn on 2012-10-09
> **Jackalyn said:**
> mkdir ~/Documents/BibleAnalyzer comes up as no such file or directory.

sudo dpkg -i package_nameI am never sure what to write into the terminal...is it sudo dpkg-i bibleanalyzer?
  that also came up with no such file or directory....I moved it to home and reinstalled as I discovered I did have the dpkg thing and it reappears on the dashboard but again, when I click on the icon, it just closes the dash board. And again from the terminal:

jacky@jacky-Aspire-6930G:~$ mkdir ~/Documents/BibleAnalyzer
mkdir: cannot create directory `/home/jacky/Documents/BibleAnalyzer': No such file or directory
jacky@jacky-Aspire-6930G:~$ ^C
jacky@jacky-Aspire-6930G:~$ ^C
jacky@jacky-Aspire-6930G:~$ sudo dpkg -i bibleanalyzer
[sudo] password for jacky: 
dpkg: error processing bibleanalyzer (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 bibleanalyzer
jacky@jacky-Aspire-6930G:~$ ^C
jacky@jacky-Aspire-6930G:~$ bibleanalyzer
************ Starting Bible Analyzer *************
0.539342880249 before aui import
Traceback (most recent call last):
  File "/usr/share/bibleanalyzer/analyzer4.py", line 41, in <module>
    import sessionMan
  File "/usr/share/bibleanalyzer/sessionMan.py", line 30, in <module>
    os.mkdir(ur'%s' % homeUserDir)
OSError: [Errno 2] No such file or directory: '/home/jacky/Documents/BibleAnalyzer'

Press Enter to close terminal

---

### Post by jrog on 2012-10-09
> **Jackalyn said:**
> mkdir ~/Documents/BibleAnalyzer comes up as no such file or directory.
This suggests that you don't actually have a ~/Documents folder. Try:

```
mkdir -p ~/Documents/BibleAnalyzer
```

---

### Post by jrog on 2012-10-09
> **Jackalyn said:**
> sudo dpkg -i package_nameI am never sure what to write into the terminal...is it sudo dpkg-i bibleanalyzer?
  that also came up with no such file or directory....
'package_name' should reference the .deb file. So, if the .deb file is in your current directory, you would type:

```
sudo dpkg -i bibleanalyzer.4.5-5.all.deb
```

That will only work if the .deb file is in your current directory, though. If it is elsewhere, you will have to change into the directory where it is or provide the path to the .deb file.

---

### Post by Jackalyn on 2012-10-09
> **jrog said:**
> 'package_name' should reference the .deb file. So, if the .deb file is in your current directory, you would type:

```
sudo dpkg -i bibleanalyzer.4.5-5.all.deb
```That will only work if the .deb file is in your current directory, though. If it is elsewhere, you will have to change into the directory where it is or provide the path to the .deb file.

Press Enter to close terminal
jacky@jacky-Aspire-6930G:~$ sudo dpkg -i bibleanalyzer.4.5-5.all.deb
dpkg: error processing bibleanalyzer.4.5-5.all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 bibleanalyzer.4.5-5.all.deb
jacky@jacky-Aspire-6930G:~$

---

### Post by jrog on 2012-10-09
> **Jackalyn said:**
> Press Enter to close terminal
jacky@jacky-Aspire-6930G:~$ sudo dpkg -i bibleanalyzer.4.5-5.all.deb
dpkg: error processing bibleanalyzer.4.5-5.all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 bibleanalyzer.4.5-5.all.deb
jacky@jacky-Aspire-6930G:~$
Is it in your current directory as it must be? When you type 'ls' (without quotes) at the terminal, does it show bibleanalyzer.4.5-5.all.deb?

---

### Post by Jackalyn on 2012-10-09
> **jrog said:**
> 'package_name' should reference the .deb file. So, if the .deb file is in your current directory, you would type:

```
sudo dpkg -i bibleanalyzer.4.5-5.all.deb
```That will only work if the .deb file is in your current directory, though. If it is elsewhere, you will have to change into the directory where it is or provide the path to the .deb file.

How do I change the directory? If the thing closes on my then I cannot send it to anywhere else???? NOT that I have a clue where the current directory is!

Thanks

---

### Post by oldos2er on 2012-10-09
Can you run ```
sudo apt-get install -f
``` in a terminal, and copy and paste the output here? I think the .deb file was not fully installed.

---

### Post by audiomick on 2012-10-09
> **Jackalyn said:**
> How do I change the directory?... NOT that I have a clue where the current directory is!

Thanks

Someone already posted

```
ls
```

This command lists the contents of the directory you are in. That is to say, when you start the terminal, the system has you in a particular place in your file system.

This is what I get when I just open a terminal and do "ls"

```
mick@mick-laptop:~$ ls
Allen & Heath
Bilder
Bildschirmfoto-Profile of audiomick - Mozilla Firefox.png
Desktop
Dokumente
Downloads
examples.desktop
fromFlashPen03Feb2012
gsmartcontrolresults_26Sep2010.txt
hardrive utility.png
image
image.tiff
img_0266edited.jpg
Musik
Öffentlich
operanewbuttons.png
out.jpeg
out.pdf
out.pnm
qcad-manual-en-2.1.0.0-1.html
qcad-manual-en-2.1.0.0-1.html.zip
recovery mode
rotateouf.png
SMART_values.png
SoftwareandStuff
system monitor.png
Ubuntu One
UkrainePics
Videos
Vorlagen
mick@mick-laptop:~$ 


```

That is the contents of my /home/mick folder, i.e. the /home/user folder for the user that I am logged in as.

This bit
```
mick@mick-laptop:~$ 
```
Shows you where you are at. This thing ~ indicates the /home/user folder. The $ indicates that you are logged in as a non-root user. I think you get a # in it's place if your are operating with root privileges. The rest is "mick" for the user and "@mick-laptop" to show which computer I am dealing with. Seems silly until your remember that you can do things like logging into another computer using SSH, in which case I would see "mick@another-computer-altogether"

To change where you are at, you use
```
cd
```

so, referring back to the list of stuff in my /home/user folder, I do
```
cd Allen & Heath
```
and discover I have stumbled across something that you have to be aware of. In the terminal, you have to make sure that you get the names absolutely correct, and it can't deal with file names that have spaces and other special characters like the & in that directory name. That has a meaning as a command. That means that it is a good practice to not use such things in your file names. I changed that folder name to "Allen_and_Heath", so now we can continue.

```
mick@mick-laptop:~$ ls
Allen_and_Heath
Bilder
Bildschirmfoto-Profile of audiomick - Mozilla Firefox.png
Desktop
Dokumente
Downloads
...
Videos
Vorlagen
mick@mick-laptop:~$ cd Allen_and_Heath
mick@mick-laptop:~/Allen_and_Heath$ ls
iLive_Editor_V1point83
mick@mick-laptop:~/Allen_and_Heath$ cd iLive_Editor_V1point83
mick@mick-laptop:~/Allen_and_Heath/iLive_Editor_V1point83$ ls
EULA.txt                           iLiveINIFile.xml  SessionLock
iLive Editor 1.83.jar              lib               shows
iLiveEditor1.83.sh                 libraries         uninstall
iLiveEditorV1.83LocalEventLog.xml  Readme.txt
mick@mick-laptop:~/Allen_and_Heath/iLive_Editor_V1point83$ cd ..
mick@mick-laptop:~/Allen_and_Heath$ ls
iLive_Editor_V1point83
mick@mick-laptop:~/Allen_and_Heath$ cd ..
mick@mick-laptop:~$ ls
Allen_and_Heath
Bilder
Bildschirmfoto-Profile of audiomick - Mozilla Firefox.png
Desktop
Dokumente
Downloads
...
Videos
Vorlagen
mick@mick-laptop:~$ 

```

Note that I have edited a lot of the contents of /home/mick out of that output to make it shorter. The missing bit is where the ... is. What you can see after the word "vorlagen" is that I used cd to change into the directory Allen_and_Heath, 
ls to see what is in there, and then cd again to change into 
iLive_Editor_V1point83,
and then ls again to see what is in there. At that point, the prompt is
```
mick@mick-laptop:~/Allen_and_Heath/iLive_Editor_V1point83$
```
You can see how the directories line up in the prompt to show you where you are. ~ for the /home/user directory, inside that the directory 
Allen_and_Heath
 and inside that the directory 
iLive_Editor_V1point83
with a / between each sucessive directory and the $ on the end to show which user you are logged in as.

The next thing was to use
```
cd ..
```
to go up a level. You can see how I did that a couple of times to get back to the /home/user directory, at which point the prompt is once again
mick@mick-laptop:~$

Hope that is clear enough. :)

---

### Post by Jackalyn on 2012-10-10
I am pretty confused now lol....
Here is the output of the terminal putting in the things people have suggested.

jacky@jacky-Aspire-6930G:~$ :
jacky@jacky-Aspire-6930G:~$ 
jacky@jacky-Aspire-6930G:~$ mkdir -p ~/Documents/BibleAnalyzer
jacky@jacky-Aspire-6930G:~$ bibleanalyzer
bibleanalyzer: command not found
jacky@jacky-Aspire-6930G:~$ sudo apt-get install -f
[sudo] password for jacky: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  language-pack-kde-en language-pack-kde-en-base kde-l10n-engb
  calligra-l10n-engb libkdepim4 calligra-l10n-zhcn calligra-l10n-de
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
jacky@jacky-Aspire-6930G:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
jacky@jacky-Aspire-6930G:~$ ls
Adobe Digital Editions.desktop       output
adobe-release-i386-1.0-1.noarch.rpm  Personal
bibleanalyzer.2                      Photos
bibles                               Pictures
Calibre Library                      Practice.zip
calligra                             Public
DayJournal                           QuotingPassages.zip
DEBIAN                               RKJNT.zip
Desktop                              RWP.zip
Documents                            sakis3g.gz
Downloads                            Sample Album
Dropbox                              SAOA.zip
eSnipsDownloader.exe                 Smith.zip
ESNIPS WINE DOWNLOADS                StrongsGreek.zip
ESP FILES                            StrongsHebrew.zip
examples.desktop                     TCR.zip
FIREDANCE                            TDavid.zip
gVerse-0.5                           Templates
gVerse-0.5.tar.gz                    TEXT FILES AND GEDIT
Java                                 TFG.zip
jsword-latest-bin.tar.gz             Torrey(1).zip
kde4                                 Torrey.zip
libre and open office installations  TSK.zip
Link to bibleanalyzer.2              Ubuntu One
MAGAZINE TEMPLATE                    UKJV.zip
mods.d                               Untitled Folder
modules                              Untitled Folder 3
Music                                usr
My Digital Editions                  Videos
My eSnips Downloads                  WEBBE.zip
NETtext (3)                          WEBME.zip
NETtext.zip                          WebstersDict.zip
NHEB.zip                             xdg
jacky@jacky-Aspire-6930G:~$ 

But if I go to the home folder and open it, Bibleanalyzer IS there and it the very first file.

---

### Post by audiomick on 2012-10-10
This might get a bit long, but bear with it... ;)

Firstly, when you post a lot of output like in the last post, it is very helpful to use the code tags button. That is the # button at the top of the post window. Click on that and you will see the word "code" enclosed in square brackets, followed by /code also enclosed in square brackets. Paste your output between those and it will appear in a nice box. Most importantly, it will appear exactly as it is without any characters being interpreted as a smiley or something silly like that as happens sometimes.

If you are posting a quote, you can use the button that looks like a speech balloon.

So, on to your post...

Firstly, near the top of your output, I see this

```
jacky@jacky-Aspire-6930G:~$ bibleanalyzer
bibleanalyzer: command not found
```

There are two things there. Firstly, if you just put a word at the prompt, it is assumed to be a command. What I think you wanted at that point is to change into the directory that you had just created with mkdir (the command that means "make directory). To do this, you would have had to do
```
cd BibleAnalyzer
```

Note also the capitals. The terminal is case sensitive. When I am doing things like this, I like to use ls to see what the name of the file or directory in question is exactly and often to actually copy and paste the name of the file into the command.

A little further down there is this
```
jacky@jacky-Aspire-6930G:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

What has happened there is that you tried to use apt-get autoremove as the normal user. You need to put a "sudo" in front of that so that it is executed with root privileges. This applies to all apt-get operations. You would need to do
```
sudo apt-get autoremove
```

It will then do this
```
mick@mick-laptop:~$ sudo apt-get autoremove
[sudo] password for mick: 

```

at which point you type in your password. You wont see what you type. Just type the password and hit enter and it will do it's thing.

There is also this in there
```
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner _binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

So accordingly you would do
```
sudo apt-get update
```

Then there is

```
jacky@jacky-Aspire-6930G:~$ ls
Adobe Digital Editions.desktop output
adobe-release-i386-1.0-1.noarch.rpm Personal
bibleanalyzer.2 Photos
bibles Pictures
Calibre Library Practice.zip
calligra Public
...


```
where you have used ls to generate a list of the contents of the /home/user folder, but I think you know that by now. ;)

I hope that is clear enough.

In your screenshot, I can see a .deb file for BibleAnalyzer. This is, I take it, the file you used to install the program. If I recall correctly, you said in the first post or so that you had right clicked on it and used the Software centre to install it, or that the Software centre said it was already installed.

That brings us back to the issue that you mentioned right at the start that you see an icon that looks like it would start the program but it doesn't. I don't really know what is causing that, but I think you mentioned problems with Open Office along similar lines. Maybe there is an issue that is not directly related to the program itself.

Did you mention which version of Ubuntu you are using? And where exactly is the icon that you can see but doesn't work as you expect?
Also, how did you install the other program that is behaving in an apparently similar manner? Was it from the software centre, installed by default, or installed from a .deb package in the same way that you installed BibleAnalyzer?

---

### Post by Jackalyn on 2012-10-11
Thank you everyone. I have tried everything and beyond the fact that I have the files, yet again, nothing is working which means either my brain is not working or somewhere I missed a vital step, or that there is something wrong with my system.

If I go to my home folder the folder is there. I click on Home and it is the first file I see, given they arrange themselves in alphabetical order.

When I click on properties I get the file name as bibleanalyzer, the type as folder (inode directory) 

Create and delete files is checked and I have permission for executing file checked.

I downloaded as per instructions from here

[http://www.bibleanalyzer.com/linux.htm]("http://www.bibleanalyzer.com/linux.htmhttp://")

I also downloaded the BAmod script, and than is in the bibleanalyzer file.

Following the instructions for the BAmodscript I get

```
 code that will not copy and paste here but says there are no such files
```I have tried everything I can and every suggestion above.  but just cannot get it to work. 

and if I click ls I get
```
jacky@jacky-Aspire-6930G:~$ ls
Adobe Digital Editions.desktop       output
adobe-release-i386-1.0-1.noarch.rpm  Personal
bibleanalyzer                        Photos
bibles                               Pictures
Calibre Library                      Practice.zip
calligra                             Public
C:\nppdf32Log\debuglog.txt           QuotingPassages.zip
DayJournal                           RKJNT.zip
DEBIAN                               RWP.zip
Desktop                              sakis3g.gz
Documents                            Sample Album
Downloads                            SAOA.zip
Dropbox                              Smith.zip
eSnipsDownloader.exe                 StrongsGreek.zip
ESNIPS WINE DOWNLOADS                StrongsHebrew.zip
ESP FILES                            TCR.zip
examples.desktop                     TDavid.zip
FIREDANCE                            Templates
gVerse-0.5                           TEXT FILES AND GEDIT
gVerse-0.5.tar.gz                    TFG.zip
Java                                 Torrey(1).zip
jsword-latest-bin.tar.gz             Torrey.zip
kde4                                 TSK.zip
libre and open office installations  Ubuntu One
MAGAZINE TEMPLATE                    UKJV.zip
mods.d                               Untitled Folder
modules                              Untitled Folder 3
Music                                usr
My Digital Editions                  Videos
My eSnips Downloads                  WEBBE.zip
NETtext (3)                          WEBME.zip
NETtext.zip                          WebstersDict.zip
NHEB.zip                             xdg
jacky@jacky-Aspire-6930G:~$ 
``` so it IS there.,.....

Oh dear is that something that I need to try and fix before anything else and could it be why I am having so much trouble?

Could it also be I need to download some extra python script? I am not really sure what I would have in Ubuntu but thought it probably included what I need. I cannot really see what I  would get from the software manager if I do need it so if I do please can someone tell me what I am looking for? 

I just looked for the bibleanalyzer program using 'Synapse' and it does not appear. 

Could the terminal conflict with the program?

I did notice there are other places on the internet where people are suggesting there have been issues with this program.

[http://www.murga-linux.com/puppy/viewtopic.php?t=65252](http://www.murga-linux.com/puppy/viewtopic.php?t=65252)

(one reason I do want it is because it was useful to me when I was using windows.) This does make it look like it might install under wine but I think I would need help to do that. I do have Wine but have not really figured out how to make things work with it.

---

### Post by Jackalyn on 2012-10-11
It installed perfectly under Wine! First time no problems..........

Ah well I learned a lot on the way for using Linux.

Thank you to everyone who helped me here. Hopefully some other newbie sometime will read this and go to the Wine option first. I don't know why they give a linux version if it does not work.

---

