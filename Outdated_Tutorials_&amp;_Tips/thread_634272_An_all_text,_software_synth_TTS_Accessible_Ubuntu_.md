---
title: "An all text, software synth TTS Accessible Ubuntu 6.10 System"
date: 2007-12-07
forum: Outdated Tutorials &amp; Tips
---

### Post by sedition on 2007-12-07
**Background:**

* **** Note: any *** you may see are annotations for me to go back and expound or edit, so disregard. I have a couple that I need to clarify because I'm at work, but after I'm done... Hopefully, I got them all!*

The following instructions will entail directions on how to install a text-only, software-spoken installation of Ubuntu Edgy Eft 6.10. The motivation for this was to let a friend of mine test-drive a reliable, user-friendly Linux distro, who no longer has his sight. I wanted to set up a live cd for him to be able to drop into his tray and run it without effecting his Windows/JAWS installation.
This installation/distribution/mutation utilizes speakup, speech-dispatcher, speechd-up and finally, espeak as the software synthesizer for TTS (text to speech). It seemed that flite had too much latency and was slightly garbled once the speed was turned up. I plan on eventually trying Festival as well, but espeak is the synth of choice for now.
The script created at the end of the process runs after boot and notifies the user that the system is ready for log in. All programs in the system are run from, and utilize only, text and the command line. Further refinement to these instructions would include:

1. Removing erroneous installed files and shrink the installation size, i.e. non-english documents for english users via localepurge and apt-get clean.
2. Adding help files to make the transition from DOS/Windows easier, as well as, define some basic Linux usage, a quick-start for speakup commands, apt-get usage, volume control, etc.
3. Changing the prompt so users aren't spammed with login info everytime a command is completed.
4. improving the boot-speed and some additional system optimization
5. utilizing remastersys to create a live cd from the iso
6. Adding repositories for w32codecs (medibuntu) and remastersys (linuxmint)
7. Spelling and punctuation updates

I've tried to include all of the original links that I used to create this howto, so all of the credit duely goes to the original creators, developers of the software and community at large. I merely compiled all of this into one, hopefully, useful package. Some day soon, I hope to have the live cd available for download so that the non-sighted can independantly download, burn and run for themselves, rather than require the assistance of a sighted user to actually go through this process.
Edgy Eft was utilized as this is the latest release of Ubuntu that (I know of) that allows the loading and use of kernel modules prior to that ability being removed. This whole process has been kind of expedited just to get my friend up and running and I have yet to try to compile speakup, myself, into a recent kernel. Hopefully, when I have a weekend free, I can get to this.

As I said, this has been greatly expidited and this how to has been mainly just thrown out there so others can try and use the information that I've compiled. There is a lot of refinement that could be done to this and any input would be greatly appreciated. I've only been a Linux user for about a year, so I'm still a noob as far as I'm concerned, and by no means perfect or extremely knowledgable. ;)


** Requirements:**
1. Computer as dictated by Edgy requirements with ALSA supported soundcard and cd burner
2. Ubuntu 6.10 Edgy Eft i386 Alternate cd
3. blank cd
4. Internet connection
5. Some time, patience and possibly even a cup of coffee or a beer (depending on your age, mood, religion and time of day)


** How to (Steps):**
1. Install Edgy (user name created was user with password password, referred to below)
2. Enable all repos and removed the references to the cd
2a. add medibuntu repository:
     ```
sudo wget http://www.medibuntu.org/sources.list.d/edgy.list -O /etc/apt/sources.list.d/medibuntu.list     
```     Add the medibuntu GPG key:
     ```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
2b. add linuxmint repository:
     *** deb [http://linuxmint.com/repository](http://linuxmint.com/repository) romeo/
3. Update your system and packages:
```

sudo apt-get update
sudo apt-get install kernel-patch-speakup speechd-up espeak libdotconf-dev libasound2.0-dev
sudo apt-get upgrade
wget http://www.freebsoft.org/pub/projects/speechd/speech-dispatcher-0.6.5.tar.gz
tar -zxvf speech*
cd speech*
./configure
sudo make install clean
sudo nano /usr/local/etc/speech-dispatcher/speechd.conf

```4. *** change default synth to espeak-generic, disable addmodules flite and festival, and change path for logging?


** Testing installation(s):**
1. test the installs
```

espeak "espeak is working"
sudo speech-dispatcher
spd-say "speech-dispatcher is working"
modprobe speakup_softsyn

```2. Verify speakup and speakup_sftsyn is loaded with:
```

lsmod

```3. Now get this box talking:
```

sudo speechd-up &

```4. your system should now be talking


** Getting it running:**
1. Making a script to load everything on boot:
```

sudo nano /usr/bin/speak

```2. Put this into the file:
```
 
sudo speech-dispatcher
spd-say "System is now booted. To log in, please enter user name user and password password."
modprobe speakup_softsyn
sudo speechd-up &

```3. chmod the file to make it executable
```

chmod +x /usr/bin/speak

```4. Make the file run on boot
```

sudo nano /etc/rc.local

```5. add the following on a line before exit 0 to call our shell script
```

/usr/bin/speak

```6. to test our whole process
```

sudo reboot

```Make it useable:
1. Install some packages:
```

sudo apt-get install tf alpine w32codecs

```2. Sighted users unplug your monitor, so you can fix any problems your user may run across
3. Everyone, enjoy!


** Explanations/Notes:**
1. speech-dispatcher was compiled from source as the package did not seem to drop stuff in the places they were supposed to and this rendered the package unusable by me
2. Quick explanation of the apps:
* tf        mud client
* alpine        email client
* vi/vim/nano    word processing
* w3m        text-only web browser
* ???        media player/radio tuner
* tesseract    Convert docs and pdfs to text files for TTS translation

---

