---
title: "adobe plugins, no sound on youtube"
date: 2013-09-11
forum: New to Ubuntu
---

### Post by SpazCool on 2013-09-11
I have not been able to get any youtube videos to play with sound for a few days now. The videos still play just fine, but no noise is coming out. I've already checked if my sound card is being recognized, they are, and my speakers work just fine for Skype. I suspect the culprit to be the adobe plugins. Unfortunately, I'm really new to Ubuntu so, their installation instructions, which seem simple enough, lack the details I require to pull this off successfully. 

Adobe's Instructions:

> Installation instructions
-------------------------

Installing using the plugin tar.gz:
    o Unpack the plugin tar.gz and copy the files to the appropriate location.  
    o Save the plugin tar.gz locally and note the location the file was saved to.
    o Launch terminal and change directories to the location the file was saved to.
    o Unpack the tar.gz file.  Once unpacked you will see the following:
        + libflashplayer.so
        + /usr
    o Identify the location of the browser plugins directory, based on your Linux distribution and Firefox version
    o Copy libflashplayer.so to the appropriate browser plugins directory.  At the prompt type:
        + cp libflashlayer.so <BrowserPluginsLocation>
    o Copy the Flash Player Local Settings configurations files to the /usr directory.  At the prompt type:
        + sudo cp -r usr/* /usr

Now, I have downloaded the Adobe Flash Player version 11.2.202.310 for Linux 64-bit on Firefox, using this website [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/). I then extracted the contents of the folder to my "home" folder, not knowing what counted as an "appropriate location." After those steps I am wholly and trully lost. I'm not sure what counts as "local" nor do I know how to change the directories using the terminal. And then it asks to unpack the tar.gz file, again. 

Again, I've spent the last couple of days whiling away at this and a couple of other problems with my recent attempt at Ubuntu. I have tried this a couple of times, so perhaps I have downloaded files that are competing with eachother. Also, when I check which version I have on a video I am told that it is 11.2.202.297, so I'm still stuck on that. 

If at all possible I'd like to delete whatever files I have downloaded for this plugin and then start fresh following a much more novice-friendly set of instructions.

Thanks in advance.

---

### Post by Impavidus on 2013-09-11
The best way to install the flash player is using```
sudo apt-get install flashplugin-installer
```(Or use the software centre)
You may have to enable the [s]Ubuntu[/s] Canonical partner repositories first, see *software sources*. This way you'll automatically recieve updates. I just automatically got updated to 11.2.202.310.

Whether installing the latest version of the flash player will solve your problems I don't know.

---

### Post by SpazCool on 2013-09-11
I turned my computer on today with some trepidation. However, I was greeted by an auto-update for Adobe! It was uber-simple and as far as I can tell everything went fine, I'm now updated to 11.2.202.310! 

And, I still can't hear anything....

Due to this and other problems with Ubuntu I have traveled to the Software Sources section of the Software Center. I apparently don't have an option, that should be listed (i.e. Canonical Partners). Whether or not this has something to do with this problem is unknown by me, but if it helps solve this problem, I'm offering up more information.

---

### Post by lee1762 on 2013-09-12
I am having the same issue. I can't get nothing to work with flash. I tried to switch to Chromium and that didn't do anything. I did try to install it from the terminal and it read I already have it. Huh ??? I'm lost

---

### Post by SpazCool on 2013-09-15
Alright guys & gals, I thank you all for your help and ideas. But, it has been more than a week on this install and I'm still drowning in problems; that is, it's time for a re-install. While such an action doesn't help me learn what was wrong to begin with, it has given me a chance to reconsider my views on and desires for Linux. I've installed Ubuntu to help familiarize myself with Linux but, I fear, it is too similar to Windows to really teach me anything about system's internal structure. 

Because of this I will be deleting Ubuntu and replacing it with a "harder" distro; slackware, arch and LFS have all been mentioned to me; and given my novice understanding of Linux I'm sure I'll be drowning in those as well. 

Again, thanks for the help, I'm sure I'll still be on here looking for help with the next distro...and possibly the one after that.

---

