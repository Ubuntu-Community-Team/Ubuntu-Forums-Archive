---
title: "Recommended apps to install"
date: 2013-03-14
forum: New to Ubuntu
---

### Post by sparklyballs on 2013-03-14
inside of a week still since my ubuntu installation, and was wondering what applications people would consider as essential, whether they're utilities or whatever. 

i'm not much of a command line type (done a small amount as a legacy of my mac background), i'd call myself an enthustiac dabbler, are there any helper type apps for this area of linux ?

or is it book is best, if so can anyone recommend a good (relatively inexpensive) book for a beginner.

---

### Post by sparklyballs on 2013-03-14
oh great, really shouldn't post just afer waking up, just seen the sticky about command line helping.


i'll expand on the original question somewhat then, i really would like to get to grips with compiling as it looks like i am going to need a few driver modules that aren't off the shelf so to speak.

---

### Post by Kopkins on 2013-03-14
For sure there's some software you'll want just to have. 

ubuntu-restricted-extras - this is for mp3's and flash and stuff like that.
openjdk-7-jre and icedtea-7-plugin - if you want java support.

Then some others that you might like.

rhythmbox - my favorite music player
vlc - my favorite video player
geany - favorite code editor
asunder - rip cd's
bleachbit - for cleaning unneeded files
gufw - a firewall if you want it
deluge - my favorite bittorrent client
fortune-mod - display fortunes via command line

You can look at these in the software center and install them or you can install them on the command line. To install packages you use `apt-get' and the arguement `install'. Because it need root privelidges, you use sudo, which is   **S**  uper **U** ser**DO**  . The super user is the root user, but you can't use that account like your own, it's only there for `administration'.

So the command all together would be ```

sudo apt-get install
```But you need to tell it which packages too so it really is ```
sudo apt-get install package-name package2 ... packageN
#and to remove
sudo apt-get remove package-name
```
you can update and upgrade packages too using this method. Using ```
sudo apt-get update
#and
sudo apt-get upgrade
```



To view the manual page for a command use the man command. ```
man <command_you_want_to_know_about>
```
I recommend at least skimming the apt-get man page.

Best of luck with Ubuntu/Linux. Welcome to Ubuntu. If you want more information on using the Ubuntu desktop, go to the dash and type help and press enter. If you don't know what the dash is, press the windows key, or command key if you're on a mac.

And just for fun, the [Advanced Bash Scripting Guide]("http://tldp.org/LDP/abs/html/"). Its pretty useful, at least after you've learned a lot of it. :D

Kopkins

---

### Post by sparklyballs on 2013-03-15
thank you for your reply kopkins, I shall look at that link you sent a little later.

---

### Post by mörgæs on 2013-03-15
Changed the thread title to a more informative one.

---

### Post by mastablasta on 2013-03-15
> **sparklyballs said:**
> i'll expand on the original question somewhat then, i really would like to get to grips with compiling as it looks like i am going to need a few driver modules that aren't off the shelf so to speak.


you will need build essentials for compiling. and instructions are usually provided in the packaged driver module (such as how to do it, prerequisites...).

---

### Post by deadflowr on 2013-03-15
> **sparklyballs said:**
> inside of a week still since my ubuntu installation, and was wondering what applications people would consider as essential, whether they're utilities or whatever. 

i'm not much of a command line type (done a small amount as a legacy of my mac background), i'd call myself an enthustiac dabbler, are there any helper type apps for this area of linux ?

or is it book is best, if so can anyone recommend a good (relatively inexpensive) book for a beginner.

synaptic package manager.

I don't think there is such a thing as must have, but if you want to try out a bunch of different apps, installing through synaptic is far easier and quicker than the software center.

---

### Post by gordintoronto on 2013-03-15
If you have a webcam, Cheese
From the Google site, Chrome
GIMP
Audacious
ubuntu-manual

As previously (but inaccurately) suggested, build-essential

What makes you think you might need driver modules?

---

### Post by nwalkey on 2013-03-15
If you want to learn about compiling then you could check out [linux from scratch]("http://www.linuxfromscratch.org/"). It will teach you how to compile a linux distro from source.

---

### Post by Kevin McCready on 2013-03-16
unetbootin  for making bootable linux USB stick
pdf reader = evince (not helpfully named Document Viewer) good for cut and paste from pdf
scribus pdf convertor
clementine for recording off internet stream
jack for cd ripping 
libreoffice-writer (closer to Microsoft word functionality and much better than abiword or openoffice)
Dolphin as File Manager (file manager (PCManFM 0.9.9 not pcfman) is awful and slow (sorry guys)) 
leafpad (brilliant little text editor for HUGE text files)
gnumeric (spreadsheet)
ibus-pinyin (for chinese IME)
clipit (so that stuff cut to clipboard buffer is available after you quit the application)
fbreader for epub files

I don't know why you'd want to fiddle with drivers either?

---

