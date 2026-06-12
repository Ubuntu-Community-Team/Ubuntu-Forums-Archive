---
title: "Can't install Chrome on Ubuntu 14.04"
date: 2014-09-24
forum: New to Ubuntu
---

### Post by snowmobiler on 2014-09-24
As a newbie, I am not quite familiar enough to start installing things via code. I looked up how to install Chrome on 14.04 and one of the options was to download the appropriate .deb file, then launch it. It should open the software center (which it did), but then instead of asking me to install it, i get the following error:

Dependency is not satisfiable:libappindicator1

Is it possible I don't have all the necessary updates for 14.04. I installed it on a pc and I've had to run some updates lately. I just installed on a laptop yesterday via DVD, so not sure if I have all updates. I was trying to launch the 32-bit Chrome .deb file as my system says it is a 32 bit install of Ubuntu.

Thanks in advance.

---

### Post by pfeiffep on 2014-09-24
While this isn't a direct answer I suggest you try the software center and install Chromium.

---

### Post by snowmobiler on 2014-09-24
Well what I would like to have is all my Chrome bookmarks. If I install Chromium, does it work the same way. Do I login to Chrome and will I have all my bookmarks? Otherwise I am fine with Firefox until I can figure out how to get Chrome installed.

---

### Post by sandyd on 2014-09-24
> **snowmobiler said:**
> As a newbie, I am not quite familiar enough to start installing things via code. I looked up how to install Chrome on 14.04 and one of the options was to download the appropriate .deb file, then launch it. It should open the software center (which it did), but then instead of asking me to install it, i get the following error:

Dependency is not satisfiable:libappindicator1

Is it possible I don't have all the necessary updates for 14.04. I installed it on a pc and I've had to run some updates lately. I just installed on a laptop yesterday via DVD, so not sure if I have all updates. I was trying to launch the 32-bit Chrome .deb file as my system says it is a 32 bit install of Ubuntu.

Thanks in advance.

Hi, what do you get when you run
```

sudo apt-get install libappindicator1
```
in a terminal? (Do NOT press Y if it indicates another application is to be removed to install it.

---

### Post by ThatBum on 2014-09-25
Installing libappindicator1 should fix it if there's no other dependencies, which I don't think there are for Ubuntu. Might be another indicator-related package, can't remember.

For the future, try installing gdebi. It's a GUI wrapper for dpkg and has dependency resolution. It's better at installing .debs than software center is. Note that you should always try the repos first, but in this case Chrome isn't into the repos, so yeah.

---

### Post by vasa1 on 2014-09-25
I think that with a regular Ubuntu 14.04 installation, the Ubuntu Software Center should be able to handle debs such as that provided for installing Google Chrome.

I don't know what the Ubuntu Software Center equivalents of **sudo apt-get update** and **sudo apt-get upgrade** are but it maybe helpful to run those commands quite often and to understand their output.

Assuming there aren't any other issues, here's [a nice video]("http://youtu.be/gmzmNriRVqs") for beginners on how to install Google Chrome on Ubuntu and it's made by one of our forum members, [uRock]("http://ubuntuforums.org/showthread.php?t=2243763&p=13119554#post13119554").

---

### Post by Mike_Walsh on 2014-09-25
> **snowmobiler said:**
> Well what I would like to have is all my Chrome bookmarks. If I install Chromium, does it work the same way. Do I login to Chrome and will I have all my bookmarks? Otherwise I am fine with Firefox until I can figure out how to get Chrome installed.

Chromium works **exactly **the same as Chrome. The development work for Chrome is all done on Chromium; so you will certainly be able to access your bookmarks from it. I use both, side by side, since Chrome is usually at least one version ahead of Chromium; but currently, both Chrome & Chromium appear to be on the same version (37.0.2062.120)...


Regards,

Mike.

---

### Post by craig10x on 2014-09-25
@vasa1: quite correct, after downloading the deb file from the chrome site, you just hit "open in software center" which then pops up with it and you hit "install"...done ;)

---

### Post by snowmobiler on 2014-09-25
> **craig10x said:**
> @vasa1: quite correct, after downloading the deb file from the chrome site, you just hit "open in software center" which then pops up with it and you hit "install"...done ;)

From what I saw on Google, the sudo get and sudo install seems to do the same as installing from the software center. I will have to try Sandy's suggestion first. Also as I browsed the forums, it seemed like that was a pretty straight forward and trouble free installation. My concern is that I just had installed Ubuntu and where as I was notified of updates on the PC that it was running on, I haven't been prompted yet on the laptop. Will have to wait for later when I get home from work. Thanks everyone.

---

### Post by snowmobiler on 2014-09-25
> **vasa1 said:**
> I think that with a regular Ubuntu 14.04 installation, the Ubuntu Software Center should be able to handle debs such as that provided for installing Google Chrome.

I don't know what the Ubuntu Software Center equivalents of **sudo apt-get update** and **sudo apt-get upgrade** are but it maybe helpful to run those commands quite often and to understand their output.

Assuming there aren't any other issues, here's [a nice video]("http://youtu.be/gmzmNriRVqs") for beginners on how to install Google Chrome on Ubuntu and it's made by one of our forum members, [uRock]("http://ubuntuforums.org/showthread.php?t=2243763&p=13119554#post13119554").

VASA- that is what I followed. It wasn't the video but it was a link with screen shots of the same thing. When the software center opened, i got libapp error instead of the install option.

---

### Post by craig10x on 2014-09-25
snowmobiler: you are probably right about that (doing it in the terminal) but i can say that every time i have done it the way i described above, it always installed easily and flawlessly, so it seems that method has a pretty good track record...

---

### Post by snowmobiler on 2014-09-25
> **sandyd said:**
> Hi, what do you get when you run
```

sudo apt-get install libappindicator1
```
in a terminal? (Do NOT press Y if it indicates another application is to be removed to install it.

Sandy, when I type that I get a message saying that installer cant find the package. So it might be an update issue or I didn't install the same add-ons like on my desktop. i was just able to install chrome there.

EDIT--- i just checked my installed apps and libappindicator1 and libindicator7 were installed today on my PC - does that mean it was part of Chrome because i just loaded chrome on the PC? If so something is preventing libappindicator1 on my laptop.

---

### Post by vasa1 on 2014-09-25
If you're having problems with installing software on the laptop, let's just talk about that :)

Have you updated software on your laptop or not? 
What happens when you run **sudo apt-get update**?
Then what happens when you run **sudo apt-get upgrade**?

---

### Post by snowmobiler on 2014-09-25
No I havent updated the software as i just installed Ubuntu on Tuesday. I will try the above and see what happens.

I first did the updates, grabbed a whole bunch. What does the upgrade do? I have 14.04 so does it have to do with that?

---

### Post by vasa1 on 2014-09-25
> **snowmobiler said:**
> No I havent updated the software as i just installed Ubuntu on Tuesday. I will try the above and see what happens.

I first did the updates, grabbed a whole bunch. What does the upgrade do? I have 14.04 so does it have to do with that?
The upgrade actually installs the software detected by the update.They're not the most logical names.

Once again, please run those commands and post the output here between code tags.

---

### Post by snowmobiler on 2014-09-25
> **vasa1 said:**
> The upgrade actually installs the software detected by the update.They're not the most logical names.

Once again, please run those commands and post the output here between code tags.

Vasa- sorry, I haven't been doing this long enough to post the output. Don't know what code tags are. Plus since I am learning, I am on the forums on my windows pc while my ubuntu laptop is updating. After I did the get updates, Ubuntu software center notified me that updates are available and it started installing the updates (may have redownloaded too as it was downloading a lot).

---

### Post by snowmobiler on 2014-09-25
As I suspected, after I did some updates, I am now able to install Chrome on my laptop. THis may sound like an odd question. After I did the 'get updates', then I got a message that software updates since ubuntu was released are available. So i used that route to install them. did that message pop-up BECAUSE of what i 'got' or is it just the update message I have been waiting on like on my pc? if so, are the updates that I 'got' sitting in limbo since I didn't 'get upgrade' or should everything be fine?

THanks vasa!

---

### Post by vasa1 on 2014-09-25
I don't use the Ubuntu Software Center myself, but I imagine that it's a two-step process: the first is to let you know that updates *are available*. Depending on whether it suits you at the time, you can then perform the second step which is the actual downloading of the updated software and their installation on your computer. Only after the second step is completed successfully can you consider your computer "up to date" *and as your experience shows, it's preferable to install new software only after ensuring that the rest of your software is up to date*.

When you have time you should read about how apt works: apt is the muscle behind the GUI of the Software Center. This link maybe a little technical but it's not totally geeky: [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

### Post by oldos2er on 2014-09-26
> **snowmobiler said:**
> Vasa- sorry, I haven't been doing this long enough to post the output. Don't know what code tags are. 

You can copy and paste text from a terminal (just make sure you get all of it) into a post here. In the advanced editor mark the pasted text with your mouse then click the # sign to wrap it in code tags, or you can just type [noparse]```
 and 
```[/noparse] respectively.

---

### Post by snowmobiler on 2014-09-26
> **oldos2er said:**
> You can copy and paste text from a terminal (just make sure you get all of it) into a post here. In the advanced editor mark the pasted text with your mouse then click the # sign to wrap it in code tags, or you can just type [noparse]```
 and 
```[/noparse] respectively.


```
Thanks Ann
```

---

### Post by deadflowr on 2014-09-26
> **snowmobiler said:**
> As I suspected, after I did some updates, I am now able to install Chrome on my laptop. THis may sound like an odd question. After I did the 'get updates', then I got a message that software updates since ubuntu was released are available. So i used that route to install them. did that message pop-up BECAUSE of what i 'got' or is it just the update message I have been waiting on like on my pc? if so, **are the updates that I 'got' sitting in limbo since I didn't 'get upgrade'** or should everything be fine?

THanks vasa!


If you ran the command line apt-get update, that only refreshes the lists of available packages, which you currently have installed on your system.
To actually apply those updates, you need to run the apt-get upgrade command.

And yes when you refresh the package list, the software updater saw the new packages and acted on that to inform you that new packages were available.

Something to look at, maybe, would be how the system is set to look for updates.
Open the Program "Software and Updates, then go to the section marked Updates and look over the settings there for how you are getting updates.
Sometimes, it might be set to never, or something odd like that.
I personally set mine, or make sure it is set, to Daily, and display immediately for security updates(Or if I feel confident, download and install), and the other updates, commonly known as feature updates to whenever, since those tend to be of less system critical importance.

Hope the helps, maybe?

---

### Post by chirag7 on 2015-02-16
Download and Install the following packages

libappindicator1
[http://ftp.cn.debian.org/debian/pool/main/liba/libappindicator/libappindicator1_0.4.92-3.1_amd64.deb](http://ftp.cn.debian.org/debian/pool/main/liba/libappindicator/libappindicator1_0.4.92-3.1_amd64.deb)

libindicator7
[http://ftp.cn.debian.org/debian/pool/main/libi/libindicator/libindicator7_0.5.0-2_amd64.deb](http://ftp.cn.debian.org/debian/pool/main/libi/libindicator/libindicator7_0.5.0-2_amd64.deb)

Now, install Google Chrome. It will install perfectly.

Cheers :p

---

### Post by Mohsini172 on 2015-03-25
> **snowmobiler said:**
> As a newbie, I am not quite familiar enough to start installing things via code. I looked up how to install Chrome on 14.04 and one of the options was to download the appropriate .deb file, then launch it. It should open the software center (which it did), but then instead of asking me to install it, i get the following error:

Dependency is not satisfiable:libappindicator1

Is it possible I don't have all the necessary updates for 14.04. I installed it on a pc and I've had to run some updates lately. I just installed on a laptop yesterday via DVD, so not sure if I have all updates. I was trying to launch the 32-bit Chrome .deb file as my system says it is a 32 bit install of Ubuntu.

Thanks in advance.

I was having same problem. Thanks to CLOUDMAN for solving this problem.
[http://blog.technotesdesk.com/ubuntu-14-04-issue-to-install-google-chrome-dependency-problems/](http://blog.technotesdesk.com/ubuntu-14-04-issue-to-install-google-chrome-dependency-problems/) 
actually you need to install depedencies. You can download these dependencies and can install either terminal or by software center.

---

### Post by danh-h on 2015-05-01
> **sandyd said:**
> Hi, what do you get when you run
```

sudo apt-get install libappindicator1
```
in a terminal? (Do NOT press Y if it indicates another application is to be removed to install it.

I wrote in yesterday that this did not work, because i got this error message:

 The following packages have unmet dependencies: libappindicator1 : Depends: libindicator7 (>= 0.4.90) but it is not going to be installed

But actually, the error message also advised me to do 'sudo apt-get -f install'.

After i executed that second command (sudo apt-get -f install), then the first command worked, and chrome installed.

---

### Post by J0nDaFr3aK on 2015-05-19
I had the same problem. I fixed it by changing the update download server. the default server for me was the Italian one, which seemed to be down. I selected the main server and i was able to install chrome (along with all the missing dependencies).

I'm in Ubuntu MATE 15.04. Go to *System > Preferences > Other > Software & Updates*. Look for the option labeled *Download from* and select *Main server* from the drop-down menu. this worked for me. Hope it helps.

---

### Post by jRoadie on 2015-09-17
Your dependency is not up-to-date. Update your repo as following:[B]
Open Software & Updates > Other Software tab > [/B]select** Canonical Partners **and** Canonical Parters (Source Code)**
Then try to install again.

Thanks

---

