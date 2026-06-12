---
title: "How Do I Revert Back To A Previous Version Of Adobe Flash Player?"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by tb75252 on 2012-05-05
I am using Ubuntu 12.04 LTS (32-bit).  I am not much of an expert with Linux.  I use Firefox as my web browser.

It appears to me that the current version of Adobe Flash Player (v. 11) installed on my Ubuntu is not working.  For instance, YouTube videos are not playing and I am unable to stream music from some Internet radio stations.  (Everything works fine when I use Windows 7, so...)

Thus I would like to go back to Adobe Flash Player v. 10 which was working fine for me.  (Even though it might be less secure!)

I think I can uninstall the current version (v. 11) of Adobe Flash Player by going to the Synaptic Package Manager and marking "flashplugin-installer" for removal.  (Correct me if I am wrong!)

I need help in locating the Ubuntu package for v. 10 of Flash Player and installing it, _including any dependencies_.  I don't seem to be able to find this package in Synaptic or in Ubuntu Software Center.

Thanks.

---

### Post by pqwoerituytrueiwoq on 2012-05-05
try using flash aid to fix the flash issues

but to answer your question:
[http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html#main_Archived_versions](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html#main_Archived_versions)

you just have to remove flash and put the libflashplayer in this folder ~/.mozilla/plugins you may need to create it
once you put the file there restart your browser
remove flash with 
sudo apt-get purge adobe-flash*

---

### Post by tb75252 on 2012-05-05
> **pqwoerituytrueiwoq said:**
> try using flash aid to fix the flash issues

but to answer your question:
[http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html#main_Archived_versions](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html#main_Archived_versions)

you just have to remove flash and put the libflashplayer in this folder ~/.mozilla/plugins you may need to create it
once you put the file there restart your browser
remove flash with 
sudo apt-get purge adobe-flash*
Thanks for your reply.
Sorry I am fairly new to Linux but from the link you gave me, it would appear that the only version of Flash Player available for Ubuntu in v. 11.  Version 10 of Flash Player does not appear to be supported for Linux and I do not have Red Hat Linux so I cannot install v. 9.
Am I misunderstanding something?

---

### Post by Dennis N on 2012-05-05
> **tb75252 said:**
> ... it would appear that the only version of Flash Player available for Ubuntu in v. 11... Am I misunderstanding something?

At the bottom of that page are the older version downloads - below "Release and Content Debugger archives". Each archive contains versions for all platforms. The Linux versions are clearly identified once you open the downloaded archive. You want the ones ending in 'linux.tar.gz' which is actually another archive with the actual flash plugin inside - libflashplayer.so

Extract and copy it to the same location as the current one.

---

### Post by tb75252 on 2012-05-07
I was able to install Adobe Flash Player v. 11.1.102.62 using Flash-Aid.

Things look good so far:  I am able to stream music from Internet radios and I also can watch YouTube videos.

I used the Advanced Mode of Flash-Aid to install the above-mentioned version.  I downloaded v. 11.1.102.62 from [http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html)

Is there a way to lock libflashplayer.so just in case Update Manager tries to install a more recent version?  Synaptic Package Manager does not show that Flash Player is installed, so I cannot lock it using that route...

---

### Post by ajpearson on 2012-05-13
I am completely stuck with the same problem - go easy on me though as this is all very confusing.

I have the same adobe plugin has crashed.

I have removed flash, downloaded an older flash version, created a plugin folder in mozilla-firefox, and added the flashplayer.iso file. Restarted firefox but still the same problem.

If I try Flash-Aid (which seems to be the best course of action for a fool like me) the wizard seems to work and I export the script and I run through terminal, I restart firefox and I still get the plugin problem.

Is there some simple instructions out there or is the problem different to everyone. Do I have to stop using firefox?

Hoping someone out there can help me.

Thanks
Andrew

---

### Post by jtarin on 2012-05-13
Sometime the flashplayer.so file is not placed in the proper directory.
Can you give us the path where you placed it?

---

### Post by ajpearson on 2012-05-14
The folder is 

home/mozilla/firefox/plugins

Thanks

Andrew

---

### Post by jtarin on 2012-05-14
> **ajpearson said:**
> The folder is 

home/mozilla/firefox/plugins

Thanks

AndrewThere could be also /usr/lib/firefox/plugins or /opt/firefox/plugins.Sometimes home/mozilla/firefox/plugins doesn't work well on some setups. That's why I was asking.

---

### Post by Dennis N on 2012-05-14
Here is a way to find where the plugin directory currently is use is located:

```
1) Start Firefox.
2) Type in the address bar: about:config
3) Click through the warning.
4) In the search bar, type 'expose'
5) Examine 'plugin.expose_full_path'. Double click on 'false' to set the value to 'true' if necessary.
6) Open New tab.
7) Type in the address bar: about:plugins
8) Under the 'shockwave flash' entry, the first line shows the location of (path to) the plugin.
```

Just manually copy the replacement into the same location.

---

### Post by anewguy on 2012-05-14
Not trying to hijack the thread here or anything, but add some additional problems when going back to a previous version:

[LIST]
[*]I downloaded the 10.2.xxxxx version of flash player and extracted the the libflashplayer.so file to my home folder
[*]I followed the instructions posted in the above post to find out where firefox was loading flash from - in my case /usr/lib/flashplugin-installer since I had tried so much in the past, including flashaid, and finally resorted back to the package manager.
[*]I removed all Flash as shown in the above post
[*]I copied the .so from my home folder to /usr/lib/flashplugin-installer (as root)
[*]Firefox now has no entry in the about:plugins for the flash player, no does it show if you just use tools/add-ons/plugins
[/LIST]
I tried copying the .so to my .mozilla/plugins folder - same result.

I believe there is either an incompatability that doesn't allow that version of flash to installed to the current version of firefox, or there is something "hidden" in a config file or one of the .mysql files for configuring mozilla and firefox.

So, I don't have a flash player at all in firefox - going to a site that uses flash comes up with the adobe nag to install flash.

So, I think there must be more involved in reverting back to a previous version - unless it's something to do with me running 64-bit.  My netbook (just sold it) had 12.04 on it and then I went back and tried 10.10 - I still had my same flash problems (documented elsewhere on the forum) and it was 32-bit.

So, since this is a thread about reverting to a previous version, I wanted to throw this out there as I don't think it always works that simply.  I know the OP apparently has their problem fixed so far, but for people searching the forum and seeing this thread title, I think it would be wise to continue it here until additional fixes are found.

I'm hoping someone can point me in a direction that will work!

Thanks in advance!
Dave ;)

---

### Post by ajpearson on 2012-05-15
Thanks for all the help and advice. Although I do not fully understand what I am doing I have been able to follow all the instructions. and drop the libflashplayer.so file into the following location:

usr/lib/mozilla/plugins/

I re-open firefox and still get the same plugin error.

Should I be doing something else - e.g. with Flash-Aid

Thanks

Andrew

---

### Post by alexcckll on 2012-05-15
What really ought to have happened is that rather than Flash 11 being packaged as Flash 10... it should have been packaged separately, and adobe-flashplugin repointed as a meta-package...

Would have then meant we could pin the sod in Synaptic.

---

### Post by anewguy on 2012-05-15
I'm wondering if there is a way to go back to an older version of Firefox as well.  I've tried Chrome, flash does the same thing in it.  I've tried flashaid - same problem.  I actually downloaded 10.3 from Adobe itself and unpacked then copied the .so into the location the new version of flash was in - doesn't even show in Firefox as a plugin.  Copied to the various /usr/lib/..... places I also found the new one - no go.  Put in my home mozilla plugins - no go.

I am wondering if the various little sqllite databases that Firefox has in my home folder contain some entry that I can't override.

OP - don't feel bad if you continue to have problems.  Problems with flash have been ongoing for a while now.  Some people have luck trying one thing or another, some of us don't.

---

### Post by jtarin on 2012-05-15
[To revert to an older version of Firefox.]("http://www.liberiangeek.net/2012/04/how-to-install-previous-versions-of-firefox-in-ubuntu-12-04-precise-pangolin/")

[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/)

---

### Post by anewguy on 2012-05-15
> **jtarin said:**
> [To revert to an older version of Firefox.]("http://www.liberiangeek.net/2012/04/how-to-install-previous-versions-of-firefox-in-ubuntu-12-04-precise-pangolin/")

[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/)

Thanks!  I also installed a couple of sqllite tools and the only reference I found so far was for flashaid.  There is a file that contains flash, but it says the file is generated so not to edit it.  Since I don't know what generates it, I decided against modifying it for now.

Thanks again!  I'll give that all a go tomorrow when I have more time.

Dave ;)

---

### Post by jtarin on 2012-05-15
> **ajpearson said:**
> Thanks for all the help and advice. Although I do not fully understand what I am doing I have been able to follow all the instructions. and drop the libflashplayer.so file into the following location:

usr/lib/mozilla/plugins/

I re-open firefox and still get the same plugin error.

Should I be doing something else - e.g. with Flash-Aid

Thanks

AndrewNow that you have a copy in usr/lib/mozilla/plugins/.....Do you also have a copy in your Home folder under /.mozilla/plugins?

---

### Post by ajpearson on 2012-05-16
I do under mozilla/firefox/plugins - should I remove that one?

Thanks

Andrew

---

### Post by jtarin on 2012-05-16
> **ajpearson said:**
> I do under mozilla/firefox/plugins - should I remove that one?

Thanks

AndrewYou can leave it .....it won't hurt. Other Mozilla apps can use it.So you have one in both locations and still no flash?

---

### Post by ajpearson on 2012-05-18
Yes no flash. I tried to follow the guide you left in a previous reply, downloaded the exact old version of firefox, entered the 1st command line in terminal but got this . . . .

ajpearson@ajpearson-laptop:~$ tar xvf ~/Downloads/firefox-3.6.28.tar.bz2
tar: /home/ajpearson/Downloads/firefox-3.6.28.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

---

### Post by jtarin on 2012-05-18
> **ajpearson said:**
> Yes no flash. I tried to follow the guide you left in a previous reply, downloaded the exact old version of firefox, entered the 1st command line in terminal but got this . . . .

ajpearson@ajpearson-laptop:~$ tar xvf ~/Downloads/firefox-3.6.28.tar.bz2
tar: /home/ajpearson/Downloads/firefox-3.6.28.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting nowThat message means exactly what it says. You are in the wrong location or your file is mis-named.

Try: (this command will put you in the Downloads folder)
```
ajpearson@ajpearson-laptop:~$cd Downloads 
```
Then the command line should look similar to this:
```
ajpearson@ajpearson-laptop/Downloads:~$
```
Now your in the Downloads folder.

Then issue the command:```
tar xvf firefox-3.6.28.tar.bz2
```
Now your file is extracted in the Downloads folder.

---

### Post by ajpearson on 2012-05-19
I am really sorry that you have to deal with me, I am sure that I am doing something really stupid. Whenever I download stuff it is dropped on my desk top and not in a folder - I am not sure that is relevant. When I carry out your first instruction in terminal I get the following messag:

ajpearson@ajpearson-laptop:~$ cd Downloads
bash: cd: Downloads: No such file or directory

---

### Post by jtarin on 2012-05-19
If things are downloaded to your "Desktop" then substitute "Desktop" for "Downloads in the previous command I gave you. When your terminal opens you are always in your home directory. 

You can designate in Firefox Preferences the location of your downloads......usually it is "Downloads" by default in your home directory.

---

### Post by ajpearson on 2012-05-19
Getting somewhere - Thanks - the flash now works on firefox and video content plays ok. However this version of firefox (3.6) seems to have a scroll type language instead on english. I am finding it hard to find any settings where the language maybe updated. Example below . . . 

Gmail
&#2990;&#3007;&#2985;&#3021;&#2985;&#2974;&#3021;&#2970;&#2994;&#3009;&#2965;&#3021;&#2965;&#3006;&#2985; Google &#2951;&#2985;&#3021; &#2949;&#2979;&#3009;&#2965;&#3009;&#2990;&#3009;&#2993;&#3016;

&#2990;&#3007;&#2985;&#3021;&#2985;&#2974;&#3021;&#2970;&#2994;&#3006;&#2985;&#2980;&#3009; &#2990;&#3007;&#2965; &#2951;&#2991;&#2994;&#3021;&#2986;&#3006;&#2985;&#2980;&#3006;&#2965;&#2997;&#3009;&#2990;&#3021;, &#2949;&#2980;&#3007;&#2965; &#2980;&#3007;&#2993;&#2985;&#3009;&#2975;&#2985;&#3009;&#2990;&#3021;, &#2986;&#2991;&#2985;&#3009;&#2995;&#3021;&#2995;&#2980;&#3006;&#2965;&#2997;&#3009;&#2990;&#3021;, &#2990;&#2965;&#3007;&#2996;&#3021;&#2970;&#3021;&#2970;&#3007;&#2965;&#2992;&#2990;&#3006;&#2965;&#2997;&#3009;&#2990;&#3021; &#2951;&#2992;&#3009;&#2965;&#3021;&#2965;&#2997;&#3015;&#2979;&#3021;&#2975;&#3009;&#2990;&#3021; &#2958;&#2985;&#3021;&#2986;&#2980;&#3016; &#2990;&#2985;&#2980;&#3007;&#2994;&#3021; &#2965;&#3018;&#2979;&#3021;&#2975;&#3015; Gmail &#2953;&#2992;&#3009;&#2997;&#3006;&#2965;&#3021;&#2965;&#2986;&#3021;&#2986;&#2975;&#3021;&#2975;&#2980;&#3009;. Gmail &#2965;&#3018;&#2979;&#3021;&#2975;&#3009;&#2995;&#3021;&#2995;&#2980;&#3009;: 

I wonder if I need to carry out the same process but for a more up to date version of firefox?

Thanks

---

### Post by jtarin on 2012-05-19
Go into Firefox preferences and choose the Content tab. Your settings for fonts and language are there. This is not an Ubuntu tweak.

---

### Post by ajpearson on 2012-05-20
Thanks - tried changing language settings before but it did not work. I have decided not to revert back to a previous firefox version and stick with the current correct version. At least I have a firefox that is in english. Yes I still have the video content problem and adobe crashes, but I will try to find an answer for that.

Can I just thank jtarin for all the support and help. I am sure the answer is in his advice somewhere, I am just not knowledgable enough to work it out at the moment. I have had ubuntu for about 4/5 years and would not go back to microsoft. I have found answers to all my problems in the past (e.g printer not working, audio not loud enough) so I will not let this new issue beat me.

I think I need to read some of the other threads on, what must be, this common issue, and maybe start a new thread at some point.

Thanks again - I would be completely lost without your support.

Andrew

---

### Post by ajpearson on 2012-05-20
Just wanted to finally add - loaded Google Chrome web browser and I have no adobe flash problems at all. So Chrome it is!

---

### Post by jtarin on 2012-05-20
Nothing wrong with chrome  :P

---

### Post by rlkee888 on 2012-11-09
> **tb75252 said:**
> I was able to install Adobe Flash Player v. 11.1.102.62 using Flash-Aid.

Things look good so far:  I am able to stream music from Internet radios and I also can watch YouTube videos.

I used the Advanced Mode of Flash-Aid to install the above-mentioned version.  I downloaded v. 11.1.102.62 from [http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html)

Is there a way to lock libflashplayer.so just in case Update Manager tries to install a more recent version?  Synaptic Package Manager does not show that Flash Player is installed, so I cannot lock it using that route...


Thank you so much for this, I have almost given up:popcorn:

---

### Post by mmino on 2012-12-22
Posting additional information to help other with this flash issue.

Google chrome comes with built-in flash. If chrome not working just enable it as shown in the following link
[http://support.google.com/chrome/bin/answer.py?hl=en&answer=108086](http://support.google.com/chrome/bin/answer.py?hl=en&answer=108086)

Hope you find this solution helpful.

---

