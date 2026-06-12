---
title: "installation of vlc media player"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by TheNixObserver on 2011-09-27
I have recently joined the linux community and have installed Lucid Lynx 10.04.  Right now I am struggling to make sense of a totally new environment.  I wanted to install vlc media player and the vlc for Ubuntu says that the package for this version of ubuntu is outdated.  So I downloaded the tar.gz file of vlc 1.1.11 and extracted it using the archive manager.  I didn't know what to do after that.  I read up on the Net and tried to follow the instructions.  I changed to the directory where it was extracted and used "./configure".  After a lengthy output on the terminal window, it finally showed an error saying DBUS not found and wanted to install something else.  I typed "yes" and then the terminal was filled with a "y" on each line and the cursor started blinking.  It was like that for some time and then I closed the terminal.

I tried to install it from the Synaptic Package Manager and under the video software (universal), I could find only the vlc svg packages whatever that means. Apparently this was a plug in to render svg graphics over the video. There is no other vlc listed there.  I tried Multimedia (Universe) and Graphics (Universe).  In the latter there was an entry for vlc but it is for lubuntu.

The net result is that after an hour of labor, I am still nowhere.  I wonder why it is so hard to do even simple things in linux.  The default movie player that comes with 10.04 fails to render some formats and the screen is gradually filled with black squares and rectangles entirely hiding the video.  I thought that it would be a good idea to install vlc, but even that is difficult.  This is so frustrating, can somebody help?

---

### Post by wolfen69 on 2011-09-27
Copy and paste the following into a terminal. It will give you more software choices.
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
Then 
```
sudo apt-get install vlc
```

---

### Post by Paqman on 2011-09-27
Have you tried Ubuntu Software Centre? It cuts down a lot of the confusing packages that Synaptic shows. VLC is in Universe, but it sounds like you've got that enabled.

As for updates, your system will take care of those for you, even for apps. It will pop up a tool called Update Manager that can update anything that you've installed from the repos.

---

### Post by seawolf167 on 2011-09-27
After you install VLC, you may also want to install the [restricted extras package ]("https://help.ubuntu.com/community/RestrictedFormats")since you mentioned that you couldn't play some files.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by ikt on 2011-09-27
> **TheNixObserver said:**
> This is so frustrating, can somebody help?

Installing a program in ubuntu is not hard, practically anyone with more than 5 minutes worth of time running ubuntu can help you.

There is a guide to installing software on linux here:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

and here:

[http://www.jonathanmoeller.com/screed/?p=1698](http://www.jonathanmoeller.com/screed/?p=1698)

and here:

[http://www.youtube.com/results?search_query=ubuntu+install+software&aq=f](http://www.youtube.com/results?search_query=ubuntu+install+software&aq=f)

and here:

[http://goo.gl/f31jU](http://goo.gl/f31jU)

and here

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

> Ubuntu Lucid Lynx 10.04 LTS
VLC version 1.0.6 in Ubuntu 10.04 is out-of-date. We recommend you install VLC 1.1.x manually.

If you wish to install VLC 1.0.6 anyway, please refer to the instructions above for Ubuntu 10.10. Note that there will be some bugs; you are on your own.

At your OWN risks, install VLC from PPA:

Command line way
% sudo add-apt-repository ppa:lucid-bleed/ppa
% sudo apt-get update
% sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc

So in ubuntu go to Accessories > Terminal and then copy and paste into terminal:

sudo add-apt-repository ppa:lucid-bleed/ppa

then hit enter, then copy and paste in this:

sudo apt-get update

then hit enter, then copy and paste in this:

sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc

then hit enter

then you've installed vlc

> I wonder why it is so hard to do even simple things in linux.

Because you are trying to put a square through a circle, linux is not windows, you need to throw out what you know and start fresh. Google and Youtube are your friends.

---

### Post by TheNixObserver on 2011-09-28
Thanks for all your help.  I installed vlc by following the commands.  However, I am unable to view anything.  It doesn't render the video, just the audio.  What do I do now?

@ikt:  My point still stands. You don't spend one hour trying to do the most basic things and still claim user friendliness. I wasn't trying to do anything complicated, just installation of a freeware program built for linux.


Edit:  After installing the restricted extras, I get this on the terminal screen, I don't know how to get rid of it.

"TrueType core fonts for the Web EULA                                      &#8593; 
 &#9474;                                                                           &#9646; 
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                         &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement       &#9618; 
 &#9474; ("EULA") is a legal agreement between you (either an individual or a      &#9618; 
 &#9474; single entity) and Microsoft Corporation for the Microsoft software       &#9618; 
 &#9474; accompanying this EULA, which includes computer software and may include  &#9618; 
 &#9474; associated media, printed materials, and "on-line" or electronic          &#9618; 
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your      &#9618; 
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be    &#9618; 
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of      &#9618; 
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT.                          &#9618; 
 &#9474;                                                                           &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>                                       
 &#9474;                                               "

I can't believe this.  What does MS got to do with this?  To top it all, I am unable to get rid of this message.  It is apparently an image or screenshot.  I am unable to operate the terminal anymore.  

I tried to close the terminal and it says that a process is still running on the terminal and closing it will kill the process.    I got tired of waiting and closed the terminal.  

Tried to play videos in vlc and it plays some files, but not all.   There is a red button on top of the screen which informs me that there was an error: "Broken Count > 0. This usually means that your installed packages have unmet dependencies" 

I restarted the system and got to play (and view) most of the flv and mp4 files.  Other formats are untested. Some are still problematic.  

So what do I do now?

---

### Post by fooman on 2011-09-28
> **TheNixObserver said:**
> Thanks for all your help.  I installed vlc by following the commands.  However, I am unable to view anything.  It doesn't render the video, just the audio.  What do I do now?

@ikt:  My point still stands. You don't spend one hour trying to do the most basic things and still claim user friendliness. I wasn't trying to do anything complicated, just installation of a freeware program built for linux.


Edit:  After installing the restricted extras, I get this on the terminal screen, I don't know how to get rid of it.

"TrueType core fonts for the Web EULA                                      &#8593; 
 &#9474;                                                                           &#9646; 
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                         &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement       &#9618; 
 &#9474; ("EULA") is a legal agreement between you (either an individual or a      &#9618; 
 &#9474; single entity) and Microsoft Corporation for the Microsoft software       &#9618; 
 &#9474; accompanying this EULA, which includes computer software and may include  &#9618; 
 &#9474; associated media, printed materials, and "on-line" or electronic          &#9618; 
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your      &#9618; 
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be    &#9618; 
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of      &#9618; 
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT.                          &#9618; 
 &#9474;                                                                           &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>                                       
 &#9474;                                               "

I can't believe this.  What does MS got to do with this?  To top it all, I am unable to get rid of this message.  It is apparently an image or screenshot.  I am unable to operate the terminal anymore.  

I tried to close the terminal and it says that a process is still running on the terminal and closing it will kill the process.    I got tired of waiting and closed the terminal.  

Tried to play videos in vlc and it plays flv (at last) but still no mp4.  Haven't tried out other formats as yet.  

So what do I do now?

perhaps mp4's and others do not play because the restricted-extras never installed completely?

run the command to install again,  and when you get to the window to install those fonts....press the "tab" key to select OK,   then press enter to continue.

you may see other, similar windows popping up as the installation proceeds....again,  just press "tab" to select,  then "enter" to continue.

if you encounter any errors along the way....post them here for review before proceeding or closing the terminal.  hope that helps.

---

### Post by seawolf167 on 2011-09-28
Aye - use the [TAB] key to change items, the [SPACE] bar to select/deselect items and the [ENTER] key to have the item follow its default function.

---

### Post by WasMeHere on 2011-09-28
Try this thread: [_**[COLOR="Red"]Comprehensive Multimedia & Video Howto[/COLOR]**_]("http://ubuntuforums.org/showthread.php?t=766683")
It may take some time, but the result is very good, you will get a solid multimedia system.

If you think that it is too complicated to do such things now, maybe it would be a good idea for you to install a system that includes most of the software, that you need. Many multimedia tasks will work out of the box in Linux Mint (even from a live disk). There are 'DVD' live disc iso images that install Mint, which is based on Ubuntu, and can be updated or extended the same way as Ubuntu. I suggest that you download

'linuxmint-11-gnome-dvd-32bit.iso' or
'linuxmint-11-gnome-dvd-64bit.iso'

and make a live DVD or live USB. Otherwise you can try one of the other versions for example the LXDE light-weight desktop.

Mint is quite easy to install and manage (my daughter prefers it while I stay with Ubuntu).

Have fun
Olle

---

### Post by hashimoto on 2011-09-28
> **TheNixObserver said:**
>  What does MS got to do with this?

You are installing packages/software (fonts in this case) that are licenced from MS so you need to accept the terms before the installation can go on.

---

### Post by TheNixObserver on 2011-10-01
I ran the restricted extras command again and got this error:

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

I ran that command and now it seems to work, though if I try to use the full screen mode, I get only a black screen.  

I wish things were simpler.

---

### Post by ppv on 2011-10-01
You may want to give Linux Mint a try. It comes with many codecs that would be required to play multimedia files. It is based on Ubuntu but with these packages already installed.

---

### Post by TheNixObserver on 2011-10-01
> **ppv said:**
> You may want to give Linux Mint a try. It comes with many codecs that would be required to play multimedia files. It is based on Ubuntu but with these packages already installed.

Thanks, I will.  I don't want to go through all this just to install codecs which ought to have been there in the first place.

---

### Post by d2btoo on 2011-10-01
@op have you checked this [http://portablelinuxapps.org/audiovideo/vlc](http://portablelinuxapps.org/audiovideo/vlc)

---

### Post by seawolf167 on 2011-10-01
Couple ideas:
Do you have any graphics drivers for your device enabled/installed? (Power Button -> System Settings -> Additional Drivers)
Are there any update/upgrades available?

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by oldos2er on 2011-10-01
> **TheNixObserver said:**
> Thanks, I will.  I don't want to go through all this just to install codecs which ought to have been there in the first place.

Non-free codecs are not included in the base OS, and I doubt this is going to change any time in the future.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by TheNixObserver on 2011-10-04
> **d2btoo said:**
> @op have you checked this [http://portablelinuxapps.org/audiovideo/vlc](http://portablelinuxapps.org/audiovideo/vlc)

Thanks for the info.  However, it says I have to make an executable and then run.  How do I make that 'executable' ?  In any case, vlc is now finally installed but the picture quality seems degraded, I do not know why.  What is clear in Windows appears grainy in Linux.  Is this something to do with the codecs for linux?

Regarding free and non-free codecs, I suppose we have to live with it.  But I still don't understand the philosophy behind the so called non-free codecs.  vlc is free and so is mp3 and so probably it would be easier for Canonical to have some sort of agreement to include them by default, just as Firefox has been included.  But I understand that these are purely business issues and so best left to the business execs.

Will try and see if any upgrades for graphics drivers are available.

---

### Post by seawolf167 on 2011-10-04
> **TheNixObserver said:**
> However, it says I have to make an executable and then run.  How do I make that 'executable' ?

To make something executable, open a terminal and type the following

```
sudo chmod +x /path/to/file_name.extension
```where you replace "/path/to/file_name.extension" with the appropriate path to your file (or just the filename if you are in the file's directory already)

You can read about the restricted formats in the following links
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[http://www.ubuntu.com/project/about-ubuntu](http://www.ubuntu.com/project/about-ubuntu)

---

### Post by andrew.46 on 2011-10-05
> **TheNixObserver said:**
> I don't want to go through all this just to install codecs which ought to have been there in the first place.

The role of 'codecs' with vlc is often a little misunderstood. vlc can use an external set of windows codecs if it has been compiled with the *--enable-loader* option. This allows vlc to play an extra handful of windows specific files but this option is almost never used with Ubuntu packages so the installing of extra codecs is rarely useful. The true power of vlc actually lies in its ability to utilise shared FFmpeg libraries.

Updating vlc can be a difficult process involving external PPAs, some of which can prove problematic, or compiling your own which can be a little arduous. I believe the safest bet is to wait 2 weeks or so and update your entire system to Oneiric Ocelot which features a [newer version of vlc]("http://packages.ubuntu.com/oneiric/vlc"). Not a small undertaking in itself unfortunately.....

---

