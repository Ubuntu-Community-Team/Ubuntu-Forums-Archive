---
title: "How do you install applications?"
date: 2013-10-06
forum: New to Ubuntu
---

### Post by zRW8b6z on 2013-10-06
I have no idea how ubuntu works, sorry if this question is dumb. All I really need is skype, google chrome, and minecraft. Any help is appreciated thank you :)

---

### Post by whitesmith on 2013-10-06
Hi **zRW8b6z** and welcome! Your question isn't dumb. In Linux, software for installation is assembled into entities called packages. One way of installing a package is to go to the Ubuntu Software Center, select it, and click install--nothing could be easier. You could do that with Google Chromium right now. You can uninstall (remove, as we prefer to say) from the same place. There are other methods of installing/removing software, working with .deb packages for example, but USC is the easiest. To work with a .deb, you download the package and then open a terminal and type:```
dpkg -i /fully/qualified/path/to/package.deb
``` Hope this helps you.

---

### Post by grahammechanical on 2013-10-06
Yes, we have the Ubuntu Software Centre for installing applications. It is easy to use and we have the confidence that the application code has been audited to make sure that the applications does not do anything nasty. But, you will not find those three applications in the Ubuntu Software Centre. You will find Chromium but not Chrome. I guess the reason for this is that those applications may be free but they are not open source. And that is a big difference in Ubuntu.

So, basically you need to download the application and it must be in a package format that can be installed in Ubuntu and that is the deb (from Debian) format. Then you browse to it with the File Manager and right click on the deb file and select Open with Ubuntu Software Centre and the Software Centre will install it for us. That put simply is the way to do it.

[https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/)

[http://www.skype.com/en/download-skype/skype-for-linux/](http://www.skype.com/en/download-skype/skype-for-linux/)

Minecraft? I do not know and I do not want to know. It seems much more complicated than I would wish for.

[https://minecraft.net/download](https://minecraft.net/download)

Proprietary applications are not the responsibility of Ubuntu developers.

Regards.

---

### Post by zRW8b6z on 2013-10-06
When I was getting GOogle Chromium from the software center I was stopped with this error:
The following packages have unmet dependencies:

chromium-browser: Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
                  Depends: libudev0 (>= 147) but 175-0ubuntu9.4 is to be installed
                  Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu4 is to be installed



How do you think I could fix it?

---

### Post by ubudog on 2013-10-06
You could try running the command:
```
sudo apt-get install libgcc1 libudev0 zlib1g
```

And then retry your original command.

---

### Post by zRW8b6z on 2013-10-06
admin@ubuntu:~$  sudo apt-get install flashplugin-installer gsfonts-x11
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 flashplugin-installer : Depends: libnss3-1d but it is not going to be installed
                         Depends: libnspr4-0d but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


I just did your command, then typed this one to get flash (I NEED YOUTUBE D=) and the issue doesn't seem to be fixed how to I correct this problem. I don't know what it means by broken packages. :\

---

### Post by whitesmith on 2013-10-06
> **zRW8b6z said:**
> I just did your command, then typed this one to get flash (I NEED YOUTUBE D=) and the issue doesn't seem to be fixed how to I correct this problem. I don't know what it means by broken packages. :\I believe youtube has converted all their stuff to HTML5 so you no longer need Flash. It was a huge security problem. Bring up something on youtube under Chromium and see what happens.

---

### Post by zRW8b6z on 2013-10-06
I can't get chromium, the same error occured.


chromium-browser: Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
                  Depends: libudev0 (>= 147) but 175-0ubuntu9.4 is to be installed
                  Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu4 is to be installed


Ubuntu seems great so far. Thanks to everyone that is helping :)

---

### Post by mastablasta on 2013-10-06
install ubutnu restricted extras package from software center (you get flash, fonts, codecs...)

---

### Post by zRW8b6z on 2013-10-06
haha, I already did, that was the first thing I got :P

---

### Post by newb85 on 2013-10-06
> **zRW8b6z said:**
> When I was getting GOogle Chromium from the software center I was stopped with this error:
The following packages have unmet dependencies:

chromium-browser: Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
                  Depends: libudev0 (>= 147) but 175-0ubuntu9.4 is to be installed
                  Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu4 is to be installed



How do you think I could fix it?

Those dependency complaints seem nonsensical.  In all three cases, the versions to be installed are newer than the minimum requirement.

It looks like you've tried installing Chromium (which for the record isn't Google signed), but you haven't tried Google Chrome.  I would suggest you try downloading and installing from Google's website.  You want the Debian/Ubuntu version, not the Fedora/RedHat version.  Ubuntu should open the .deb file you download with USC, and installing from there should point-and-click easy.  It will add Chrome's repository to your source list, so after that, updates will be handled automatically by Ubuntu's package management system.

By the way, not all software in the repositories is open source.  The Restricted and Multiverse repos are made of closed-source software.  Skype and Chrome were probably both excluded because they are proprietary software.

---

### Post by carusoswi on 2013-10-06
> **grahammechanical said:**
> You will find Chromium but not Chrome. I guess the reason for this is that those applications may be free but they are not open source. And that is a big difference in Ubuntu.



I've been away from Ubuntu since I first tried to upgrade to 12.10.  It was an upgrade attempt that went sour, then, I became very busy in my day job (that forces me to the Windows side of things), and just never got around to re-installing until this morning when I finally installed 13.04 on my machine.

I quickly searched 'chrom' and installed Chromium without even noticing that it isn't Google Chrome, LOL.  It works just fine, however, so, I'm in no hurry to download Goggle's version.

The "Software Center" has truly simplified acquisition/installation of software in Ubuntu.

You type some interest in the search bar and up comes any number of choices for you to review.  If you want to try something, click the "Install" button and give it a go.  If you decide that item isn't really for you, just go back to the "Software Center", search for the item again, click "remove" and it is cleanly uninstalled.  How elegant.

Newb85, you didn't state what brought you to try Ubuntu, but for me, it was during one of those times when my Windows machine had gunked up and wasn't working properly, and I had decided that a rebuild would be easier than trying to deal with all the problems.  In those days (not all that long ago, really), I configured my Windows machine for easy re-build, making certain to keep all data where it was safe from anticipated re-installations (I don't really blame Windows for these system gunk issues.  Getting viruses or getting tangled up by trying bunches of new things just seemed the norm with Windows in those days).

At any rate, during one of these periods, I decided, what the heck, I think I'll try a different operating system just for fun.

Installed the current version of Ubuntu (6.04, I beleive), and was just swept away that such a sophisticated OS could be had for free.

Which (finally) brings me to the point.  When first working with Ubuntu, like you, I could not figure out how to do anything.  Couldn't figure out how the @!#$ you install software, etc.

My brain was totally wrapped around the Windows way of doing things (not saying that yours is, however).

Then, as now, this forum existed to help me rapidly gain the knowledge necessary to make working in Ubuntu as simple as could be.

Today, if you like simplicity, nothing could be more straightforward than the "Software Center."  If you want to tinker under the hood, you can still do so, and you will, like me, find all manner of help available to you on this forum.

I still don't consider myself an expert, but I love playing and working (whenever possible) in Ubuntu, and I would like to welcome you to this new OS, this forum, and the Linux world.

I assume you come from Windows, and I think that, as you gain experience with Ubuntu, you will find much that enriches your Windows experience, as well.

I can 'blame' Ubuntu for introducing me to open source office suites and, perhaps the most valuable to me, The Gimp, which is an open source photographic editing application (ironically, no longer integrated into the Ubuntu installation, but still just a click away in the "Software Center.")

I apologize for the length of this post (I didn't intend to be so lengthy when I started).

Happy computing, and welcome once again.

Caruso

---

### Post by heir4c on 2013-10-07
@zRW8b6z, What version of Ubuntu is installed on your computer?

---

### Post by craig10x on 2013-10-07
For Chrome...just go to google's web site and get the appropriate linux deb file (64 bit or 32 bit depending on your computer)....save the deb file and go to your download folder in the file manager....
right click and select "install using ubuntu software center" it will install it for you and you are all set....

To find Chrome, open the dash search and start typing the name Chrome...you will see it...click it to open chrome...then lock the chrome icon on your unity dock using the right click...

You will be all set with Chrome..easy as can be!

Chromium that is in the Ubuntu software center does not have the built in flash plug in and pdf reader which Chrome does have...also Chrome will send automatic updated versions to your software updater...

---

### Post by newb85 on 2013-10-07
> **carusoswi said:**
> Newb85, you didn't state what brought you to try Ubuntu, but for me, it was during one of those times when my Windows machine had gunked up and wasn't working properly, and I had decided that a rebuild would be easier than trying to deal with all the problems.  In those days (not all that long ago, really), I configured my Windows machine for easy re-build, making certain to keep all data where it was safe from anticipated re-installations (I don't really blame Windows for these system gunk issues.  Getting viruses or getting tangled up by trying bunches of new things just seemed the norm with Windows in those days).

No, I didn't.  It didn't occur to me to state that, and if it had, it would have seemed off-topic.

---

