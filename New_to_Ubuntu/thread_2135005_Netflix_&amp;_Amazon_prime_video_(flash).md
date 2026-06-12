---
title: "Netflix &amp; Amazon prime video (flash)"
date: 2013-04-12
forum: New to Ubuntu
---

### Post by ginnyotte on 2013-04-12
I installed tonight; I am a woman of very little needs; I need my Netflix account to work, and I need to be able to watch my Amazon Prime videos.

I managed to figure out how to start a terminal window, AND get the commands to install Netflix.  At the end, I got screen asking me to agree to Micrtosoft's terms, with an [ok] at the bottom.  I could not click on this.  typing ok did nothing.  nothing allowed to to acknowlege that I did, indeed, agree.

I tried again.

I restarted the computer.

I can't re-install, I can't get to where I wanted to go. I don't understand what is being told to me in the terminal window.  I'm simply that new.  However all I can tell you is that I can't get to that [ok] window again.  Until I get past this, I can't watch Netflix movies.

At Amazon, I get three versions of Linux flash versions that I can download.  I need to know the path to Firefox and type in commands, but I have to idea how to find the path to firefox.

This is a steep learning curve for an old chick who just wants to watch movies without Windows 8.  Can anyone assist, please?

---

### Post by ginnyotte on 2013-04-12
It is not just these two programs.  I tried to install a game called Second Life.  I followed the instructions, and nothign happens.  I am obviously doing something wrong.  Once a program is installed, how to I start the program...it is not shouwing up as a program in the dash home menu but rather a folder; when I get to that folder, and open it, the file Second Life says I can just run to start the program...doesn't work.  When I try to install using terminal...doesn't work.  It did tell me once I had to install locally, which is great; so I did.  I still could not start the program.

Is there a tutorial of some sort for someone who has simply never ever used this program?  While I have used DOS, and am familiar with the idea of doing everything in a command line, I haven't really done that since the 1980s. and back then when I typed stuff...stuff happened.  I am used to a graphical interface now, and am looking for a simple install package for programs.  If that is not possible...how does a newbie actually get beyond the install, in order to actually use and enjoy ubuntu without days of outright frustration?

Please help.  I do not wish to go back to Windows 8.  Helping=lifesaving.

Thanks.

---

### Post by Habanero101 on 2013-04-12
I found this for netflix
[http://www.techrepublic.com/blog/opensource/how-to-get-netflix-streaming-on-ubuntu-1210/4019](http://www.techrepublic.com/blog/opensource/how-to-get-netflix-streaming-on-ubuntu-1210/4019)

---

### Post by oldos2er on 2013-04-12
> **ginnyotte said:**
>  However all I can tell you is that I can't get to that [ok] window again.  Until I get past this, I can't watch Netflix movies.


Use the Tab or arrow keys to highlight OK, then press Enter.

If you really need Netflix, I suggest running it in Windows, or if possible you can run Windows in a virtual machine and use Netflix that way. The netflix-desktop package is a "hack" (with all due respect to the person responsible for it) and there are no guarantees that it will work tomorrow, next week, next month, or whenever. Netflix officially does not support Linux.

---

### Post by ginnyotte on 2013-04-12
I finally found the Netflix app in the software center.  Now I just need to figure out why Amazon Prime movies will not display, and why I cannot seem to properly install Second Life. Thanks for responses so far!

---

### Post by send2 on 2013-04-12
this link worked for me: [http://www.techdrivein.com/2012/11/howto-make-netflix-work-ubuntu1204-ubuntu1210-PPA.html](http://www.techdrivein.com/2012/11/howto-make-netflix-work-ubuntu1204-ubuntu1210-PPA.html)

hope that helps. I am running Ubuntu 12.04.....

---

### Post by NotteScura on 2013-04-13
Hello!

So I think we should clear some things up first....

First and foremost, Ubuntu (and Linux as a whole) is not the same as Windows. 

It's a completely different system, so anything you pick up for Windows isn't going to work. There are options to run software/games made for Windows inside Linux using Wine (free) or CrossOver Office (not free), but I'm not get into those at this point, because there would be too much to cover in a single post or even a single forum thread, when you're just starting out. :)

---
For the Netflix issue, as other's have pointed out, the only available option that is working natively within Linux is really just hacked together and there's no telling how long it will stay working. Based on your recent post, it sounds like maybe you already have this installed/going, but please keep the info just mentioned in mind because it may stop working at any time.

The only safe, sure-fire option to watch Netflix in Linux is to use a Virtual Machine program such as Oracle's VirtualBox or VMware's Player. Both are free, and VirtualBox is already in the Software Center, if you do a search for it.

These products allow you to run Microsoft Windows (or many other Computer Operating Systems) inside of a window. This is really only a very basic description of what it does, so we don't go off on any tangents, but suffice it to say, you will still need a valid copy of Windows, and it's unlikely that you can use your computer's Restore CD version to put the copy of Windows that you received in the computer, inside of one of these virtual machines, so it's not very cost-effective.

I, personally, use this method for watching Netflix on my Ubuntu desktop, but I purchased a full version of Windows XP at the time ($100) to do so. Since XP is end-of-life, they won't be selling it, and I'm not sure how much a copy of Windows costs these days.

---
For the Amazon Instant Video trouble, if you go to the Ubuntu Software Center and search for "Flash", you should see the Adobe Flash player plugin listed. Click on it, and then click on the Install button to install it, if it's not already installed (which it doesn't sound like it is). 

I do want to note that I ran into a problem this morning, and have seen a few posts from the last few days, where the latest version of Flash that Ubuntu includes has broken the ability to watch Amazon Instant Video and the only option at this point is to go back to the older version. Again, to avoid making this post extremely lengthy or overwhelming, it's probably going to be best to just wait until another update is released that fixes the problem. (No idea when it will be, but I imagine if enough users run into it, then it won't be long.)

---
For Second Life, it's going to be best to install the native Linux version, instead of trying to install the Windows version that it sounds like you have tried to do.

According to this post: [http://askubuntu.com/questions/53766/how-do-i-install-secondlife](http://askubuntu.com/questions/53766/how-do-i-install-secondlife)  , they offer a native Linux client on their site. You will need to be sure that you install the 32-bit compatibility libraries, unless you downloaded and installed the 32-bit version of Ubuntu.

To check which version you have, from your terminal window, run:
```
uname -m
```

If that says "x86_64" then that means you have the 64-bit version and you'll need to run the following command also in your terminal window:
```

sudo apt-get install ia32-libs

```

If it says "i686" or something similar, then you can just ignore that.

Here is a direct link to their latest Linux version client: [http://download.cloud.secondlife.com/Viewer-3/SecondLife-i686-3.5.0.273444.tar.bz2](http://download.cloud.secondlife.com/Viewer-3/SecondLife-i686-3.5.0.273444.tar.bz2)

Once downloaded, in your terminal window run:
```

cd ~
tar -xzf ./Downloads/SecondLife-i686-3.5.0.273444.tar.bz2
ln -s SecondLife-i686-3.5.0.273444 SecondLife
cd SecondLife
./secondlife

```

The first line makes sure that you're in your "Home" folder, the second unzips it, the third makes a link from the long name with the version number to something shorter, so it's easier to get to, the fourth changes the directory/folder to the extracted folder, and the last line runs it. 

I'm afraid I don't run Second Life, so I don't really know much about it, but if you run into errors, I recommend making another post and putting any of the errors you run into in that so that others see it and can respond (since this post only asks about Netflix and Amazon in the subject). :)

Welcome to Linux! 
Be sure to keep your arms and legs inside the vehicle at all times because it's going to be a bit of a bumpy ride to freedom. :D

(P.S. Sorry, if this post is a bit "basic" in nature. Based on your initial post, I didn't want to overwhelm with too much information all at once. It's best to pick up things "slowly but surely".)

---

### Post by ginnyotte on 2013-04-13
Thank you!  I will definitely have to do this one thing at a time, it is a little overwhelming learning a new operating system while getting all of my beloved programs to work not impossible, but overwhelming.  Overall, not as painful as going from DOS to Windows in the 1990s. But that is a different story.

I am going to bookmark this thread and return to it after I get the more important issue done; when I boot the computer sometimes it does not start and I must try over and over again.

I rn a program last night tht reported that the boot files are far from the start of the disc, and I must create a boot partition (ext4, .200MB, start of the disk).  I have a url of [http://paste.ubuntu.com/5703597](http://paste.ubuntu.com/5703597)  I downloaded and installed gparted, and now need to figure out how to use it, and make the boot partition where it is supposed to be.  It might be just out of my abilty to jerry-rig on my own at this point, as I am a newbie.

I also installed wine, and between that and installing a third party Secondlife program discovered that I need a "new" video card driver.  So I have to figure out how to do that, too.

---

### Post by ginnyotte on 2013-04-14
Thank you, unfortunately it did not work.  I need to update the video driver.  I have no idea how to get the video driver for an Intel HD Graphics 4001 card to no avail.

---

### Post by ginnyotte on 2013-04-15
after horribly rooting around and making things very, very bad, I brought my computer to my IT guy at work who helped me out by repairing newbie errors. we did learn something though, and that is that while we can't get Amazon P rime instant videos to run at all in ubuntu, all I need to is boot to a live cd with puppy linux on it, and amazon prime works. i do not know why and neither does he, but for anyon who really wants to use amazon prime...until amazon  this your easiest workaround is booting puppy linux off of a live cd.

---

### Post by scottro on 2013-04-26
Because Amazon made an upgrade that broke streaming video for most Linux users.  Some people have fixed it by downgrading flash, (though this has risks, as flash always has vulnerabilities and not updating it can leave you open to various things), or adding HAL (hardware abstraction layer) which is deprecated.  Many people have been complaining, their customer service people have been saying they are forwarding the complaints to tech, but it seems to be hit or miss at the moment.  I can play it on CentOS 6.x, but on Ubuntu or a variant, even downgrading flash or installing HAL has been hit or miss.  I will get the error about upgrading flash, then it shows the pause button if I hit that the play arrow shows and I can play it, but not well.  

So, it probably works on puppy because it's either got HAL running by default or uses an older version of flash.  Regardless, updating puppy may break it eventually. 

Ironically, supposedly (that is, not researched by me, saw it on slashdot or Amazon forums or something) this is due to the DRM that rights holders insist on having in the videos.  As usual, it doesn't stop any of these things from being pirated, but only angers the ones who legitimately buy it.

---

