---
title: "installing  Thunderbird from Mozilla download .tar.bz2"
date: 2014-06-11
forum: New to Ubuntu
---

### Post by Nosphky on 2014-06-11
I'm using UbuntuStudio 14.04

I would like to use a version of Thunderbird linked to their update channel.  I followed a description in a mozilla doc describing the process of download and installation.  This lines up with the last post on an old thread in this forum (/ubuntuforums.org/showthread.php?t=1484264&highlight=installing+Thunderbird).

I downloaded the .tar.bz2 file and extracted it with 'Archive Manager' into a sub-directory of my home directory.    I checked that the thunderbird shell script was executable and that I had libstdc++5 installed.  From a terminal opened in the home/me/thunderbird, I typed thunderbird.   I got the response :

"The program 'thunderbird' is currently not installed. You can install it by typing:  sudo apt-get install thunderbird"

When I did that, I ended up with the latest Ubuntu Thunderbird, not on the mozilla update channel.   I removed that installation and repeated the download to start again.  The old thread referenced above mentions the need to  ./configure, make, install  but this contains stuff I don't yet understand.  

I tried the ./configure part but the response was "configure: command not found"

Obviously, the installation process in linux is not the same as in Windows.  Can someone please tell me what I've missed / or get wrong here ?

Thank you.

---

### Post by Vladlenin5000 on 2014-06-11
> **Nosphky said:**
> The old thread referenced above mentions the need to  ./configure, make, install  but this contains stuff I don't yet understand.  

That means compiling from software sources. If you don't understand what it is, what it entails, what your system needed to start with, etc., etc., etc., ..., then the answer that logically follows is: Don't!

> I tried the ./configure part but the response was "configure: command not found"
 That is to be expected if you are anywhere but in the folder where you extracted it in the first place.


PS - Is there a reason for you to want to do things the hard and potentially hazardous way? You don't sound like an expert/coder/developer interested in helping debug the software, hence my question...

---

### Post by Nosphky on 2014-06-11
Hi Vladlenin5000

   I said that the old thread referenced 'configure,  make install'  but I also mentioned that at the end of the old thread,  the simpler advice (which I followed) was to simply extract into a  subdirectory and run from there.

   I am not a developer or code expert  but I've used Thunderbird and Firefox for many years on windows and I'm  used to installing the latest updates of both as soon as they're  available - that's all.

  And being new to linux, there is a lot to learn  and I'm trying to do that.

   Here follows the last post of the old  thread which I mentioned :

  "the easiest way is to right click on the  tar.bz2 you got from mozila, then select "extract here". The files will  be extracted into a new folder "thunderbird". In this folder there is  file "thunderbird". What you have to only do is to create a launcher on  the desktop/menu to this file. In doing this thunderbird will be run  from your home directory not installes system-wide. The updater will  upgrade when new version is released. "

  This is what I tried first.  I  couldn't run thunderbird because, as the message in the terminal  informed me  'The program 'thunderbird' is currently not installed. You  can install it by typing: sudo apt-get install thunderbird'

  The advice I  quoted above from the old thread is almost the same as in a thread on  the mozilla website help pages about the same subject.   Maybe they are  both wrong or both quoting from the same wrong source, it's always  possible ?

---

### Post by steeldriver on 2014-06-11
If you are trying to run an executable that is not in one of the directories listed in your current environment's PATH variable, you need to give the path explicitly. To run an executable that is located in the terminal's *current* directory, you can use the shorthand relative path ./ i.e.

```

**./**thunderbird

```

---

### Post by Nosphky on 2014-06-11
Thanks for that info Steeldriver.  

So the .tar.bz2 file was extracted into a subdirectory of my home directory called thunderbird.  I opened a terminal in /home/me/thunderbird .  I presume that is what you meant by the terminal's current directory.  And then I used your code.  This is the result :

me@me-desktop:~/thunderbird$ ./thunderbird
bash: ./thunderbird: No such file or directory
me@me-desktop:~/thunderbird$ 

The file, thunderbird, is present in the thunderbird sub-directory.  Its type is shown as executable and its properties show that permissions are set to allow it to run as a programme.  So what does it mean 'no such file or directory' ?

There must be something I haven't understood here.

---

### Post by Vladlenin5000 on 2014-06-11
I don't understand either but here's the thing: The current version in Ubuntu is 24.5. The one you're trying so hard to run is 24.6. This version will be available and automatically updated in Ubuntu as soon as the audit process finishes. Please read the changelog here [http://www.mozilla.org/security/known-vulnerabilities/thunderbird.html#thunderbird24.6.0](http://www.mozilla.org/security/known-vulnerabilities/thunderbird.html#thunderbird24.6.0) and ask yourself if it's worth the trouble (and potential risks for your OS due to the use of untested/unaudited software).

---

### Post by Vladlenin5000 on 2014-06-11
If you REALLY want the bleeding edge version then there's an easy way: [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

Note: Use it at your own risk. ** You have been warned **

---

### Post by Nosphky on 2014-06-12
Hi Vlad :  

No I'm not really stuck on having the bleeding edge version  and if I can't get my installation of Thunderbird then I'll certainly  use the Ubuntu release.   I'm not stuck on a philosophical point but  rather just trying to understand and be comfortable with a new os (at  least new to me).

And I don't worry too much about screwing up the os.  I've already installed UbubtuStudio three times, once due to catastrophic hardware failure.  My data files are all well backed up and some of my work is now on UbuntuStudio and the rest still on Windows 7 pending a complete changeover.   I'm not in a hurry but would like to understand what I'm doing.

In this continuing process of transfer, I've just downloaded a linux version of another application i've been running under Windows for a couple of years.  I changed the download to executable and clicked. Installation wizard opened and installation completed. I went to the subdirectory concerned and clicked on the startup file - and it ran just as it has done under windows. 

I thought from the pre-checking I did on Thunderbird that the process would be as easy.  But I've run into snags I don't yet understand.

---

### Post by mastablasta on 2014-06-12
> **Nosphky said:**
> 

No I'm not really stuck on having the bleeding edge version  and if I can't get my installation of Thunderbird then I'll certainly  use the Ubuntu release.   I'm not stuck on a philosophical point but  rather just trying to understand and be comfortable with a new os (at  least new to me).

In Linux all programs get updates along with other security updtaes. so you don't need to worry about updating each individual program. In case of browsers it Will give latest version that is considered stable.

PPA (perosnal package archive) exists for development version if you want beta stuff. every 6 months the whole system get's major upgrade. along with new software,kernel etc.. you can follow that path or use PPA and stay on the LTS version. in Windows there is a new kernel when they release new windows version. which is not so often.

> 
In this continuing process of transfer, I've just downloaded a linux version of another application i've been running under Windows for a couple of years.  I changed the download to executable and clicked. Installation wizard opened and installation completed. I went to the subdirectory concerned and clicked on the startup file - and it ran just as it has done under windows. 

I thought from the pre-checking I did on Thunderbird that the process would be as easy.  But I've run into snags I don't yet understand.

it means the application you are talking about had a binary precompile installer. what you are doing with thunderbird is you downloaded source code and you need to compile for Ubuntu Linux whatever bit system it in order to install it. when there is another updtae you need to repeat the whole thing. now all this is done for you if you install it form software center and when new version arrives it will be in the updtaes manager.

bottom line if at all possible avoid compiling from source (especially wiht browsers) and use repositories. if the latest version you want is not in repositories use PPA's instead. 

oh and dump the Windows way. this is Linux. dated but still valid: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by Nosphky on 2014-06-12
Thank you for the information, Mastablasta.  I'm going to consider this thread closed and get on with life using the Ubuntu thunderbird release.   And I'll try and get onto the links you provide.  It's all a bit of a steep learning curve - unfortunately sometimes life gets in the way of learning.

Thanks to everybody who helped along the way.

---

