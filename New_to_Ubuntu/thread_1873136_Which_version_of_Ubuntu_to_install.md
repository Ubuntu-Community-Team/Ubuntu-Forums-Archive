---
title: "Which version of Ubuntu to install?"
date: 2011-10-31
forum: New to Ubuntu
---

### Post by Russ45 on 2011-10-31
I have an Intel i7  Sandy Bridge processor with 16G ram. I am currently using 64 bit Windows 7. Which version of Ubuntu do I need? Thanks in advance for the help

---

### Post by LinuxFan999 on 2011-10-31
You should install 64bit Ubuntu 11.04. It won't be available on the main download page at Ubuntu.com, so go to [http://releases.Ubuntu.com/natty](http://releases.Ubuntu.com/natty) and download from there. If you want the absolute latest software, download 64bit Ubuntu 11.10 from the main download page.

---

### Post by Russ45 on 2011-10-31
Thank You for the reply. When I downloaded the 64bit from the main page it is amd64 in the file name.:)

---

### Post by Sef on 2011-10-31
> You should install 64bit Ubuntu 11.04. It won't be available on the main download page at Ubuntu.com, so go to [http://releases.Ubuntu.com/natty](http://releases.Ubuntu.com/natty) and download from there. If you want the absolute latest software, download 64bit Ubuntu 11.10 from the main download page.

I would either recommend 11.10, which works just fine on my computer: Dell 1545 or if you prefer a long term supported (LTS) software, go with 10.04.

The non-LTS are supported for 18 months for both the desktop and server; the LTS are currently supported for 3 years desktop and 5 years server. However, starting with 12.04, the next LTS, both the desktop and server will be supported for 5 years.

Download the desktop version and run the live cd to see if any problems occur. If they do, then likely they will occur upon installation.

---

### Post by Slim Odds on 2011-10-31
> **Russ45 said:**
> Thank You for the reply. When I downloaded the 64bit from the main page it is amd64 in the file name.:)

It's a legacy thing. The first 64 bit processors supported were AMD.

It will work fine. Go for it.

---

### Post by Joreus on 2011-10-31
I'd go straight for the 11.10 version. I've been running Xubuntu 11.10 since release and I have yet to hit a snag or bug.

10.04 LTS is rock solid stable but the desktop is Gnome 2 which is now a thing of the past. Everything from 11.04 onwards is using Unity now.

If you're going to start out with a new OS, start with one that is going to be similar to future releases.

My 2 cents.

---

### Post by beew on 2011-11-01
I would not recommend 11.10. Many things do not work or are broken in my fresh install (in an external drive for testing). Many features are removed because of switch to gnome3. Firefox is mysteriously sluggish, graphic driver is messed up, cannot open any jpeg or png file etc. Most of these are known bugs awaiting to be fixed so it is not just my setup(I have encountered none of these running 10.04, 10.10 and 11.04) 

I suggest that no one should install the newest release on their work machines until at least 2 months later. New releases are buggy and beta quality, then come several waves of bug fixes and it will be fine.

11.04 is definitely quite solid by now, it is faster and a lot more stable than 11.10 at this point  (except for installation time it seems) It also has a lot better software support in ppas.

The argument that you have to get the latest release to get the latest software is fallacious. You can get the latest softwares from ppas. My softwares in 11.04 are newer than the ones in 11.10 because of the repo freeze and many ppas are either not setup yet for 11.10 or break it (xorg-edgers)

---

### Post by VeeDubb on 2011-11-01
> **beew said:**
> I would not recommend 11.10. Many things do not work and broken in my fresh install (in an external drive for testing). Many features are removed because of switch to gnome3.

Everyone has a different experience, but I've found 11.10 to be extremely stable.  The only missing feature I've found so far is that there is no preinstalled screensaver app.  However, screensavers serve no functional purpose on LCD monitors, and I don't even think you can buy CRT monitors anymore except from goodwill or a specialty shop.  And besides, you can always install a screensaver if you really feel the need.

Also, 11.04 has more missing features than 11.10.  Unity in 11.04 is barely functional in 11.04 compared to the current version available in 11.10

---

### Post by beew on 2011-11-01
> **VeeDubb said:**
> Everyone has a different experience, but I've found 11.10 to be extremely stable.  The only missing feature I've found so far is that there is no preinstalled screensaver app.  However, screensavers serve no functional purpose on LCD monitors, and I don't even think you can buy CRT monitors anymore except from goodwill or a specialty shop.  And besides, you can always install a screensaver if you really feel the need.


Everyone may have different experience but you can just check the bug tracker to see the confirmed bugs. It is just common sense that when a new OS is released it tends to be buggy, this holds true with Windows and Mac and even more so with Ubuntu because it is open source and has to rely on community testing to discover bugs, it doesn't have army of OEMs testing it (like MS) or make its own hardware (like Apple), and Canonical doesn't create the softwares that  it bundles with Ubuntu. By the look of how things are going, I wouldn't even consider installing 11.10 in any productive installation until at least  Jan.

If you want to take a chance with your work machine be my guest, if you are so lucky that everything works out for you more power to you, but I wouldn't recommend gambling as a rule.

Screensaver is a missing function,--whether it serves any purpose is not for you to decide, it is a function that is taken for granted in all OSes, some people like it,--but not the only one. Say how to do you create a custom command on the "open with menu" if your app is not on the list? (You can do that, I know how to, but it is ridiculous to have to do such things manually), there are also other customization options that are missing and you need to install gnome-tweak-tool to recover simple functions like changing theme and font size. Another irritant that  just randomly comes to mind is that application icons don't go to the right categories in the dash (in Gnome Shell they do), so in order to change that behaviour you would need to manually edit the .desktop files.

---

### Post by VeeDubb on 2011-11-01
> **beew said:**
> Everyone may have different experience but you can just check the bug tracker to see the confirmed bugs....

Let's all relax a touch here.  I'm just providing my personal opinion and experience.  No more, no less.  

I never said the missing screensaver wasn't a missing feature, I said it was a missing feature that served no technical purpose on modern hardware and was easily replaced, both of which are quite true and correct (not something I 'decided').  

I also never said that it was the only missing feature; just that it was the only one I had noticed.  I have found 11.10 to be so full of new and improved features, that in my personal opinion, the average user would be far happier with it than with 11.04 and the woefully incomplete version of Unity it runs by default.

I certainly agree that if you're running a mission critical work machine, you should install an older version, although I'd recommend something older and more stable than 11.04.  By the same token, I suspect that a person looking for the right version to install on a mission critical work machine, would have asked the question in a different way.


In any case, I'm sure that healthy and civil discussion about varying opinions will help the OP and others with the same question to choose the version that's right for them.

---

### Post by beew on 2011-11-01
> **Sef said:**
> I would either recommend 11.10, which works just fine on my computer: Dell 1545 or if you prefer a long term supported (LTS) software, go with 10.04.
.


I would disagree that the choice is only between the newest release (even when it is barely 2 week old!) and LTS which may be a  dinosaur by now.

The non LTS releases are very good, I see no difference with the LTS in terms of performance and stability, they are just not supported that long,--but why would non corporate users want to run 3 year old OS is beyond me, 3 year is several lifetimes in open source development. But Ubuntu (LTS or no) is usually buggy at release time and even more so for 11.04 and 11.10 because of some drastic changes. I would definitely recommend 11.04 at this point, it is at a very sweet spot where most bugs have been fixed and is enjoying rich and up to date software supports through ppas etc.

---

### Post by viperdvman on 2011-11-01
Well, it really depends on what desktop environment you want to run... and how long you want to run that particular Ubuntu.

If you want to run GNOME, then [COLOR=Black]**Ubuntu 11.04**[/COLOR] fits the bill *(remember when you log into "Ubuntu Classic" desktop environment)*. Don't turn away from GNOME 2.x because it's not supported anymore. It's extremely customizable and can be made to look and act like either a Windows, Mac OS X, or anything you want it to look and act. Pair it with Compiz and Screenlets, and it has almost as much eye candy as KDE Plasma and Windows Vista/7.

If you want to run Unity, and **just** Unity, then install either **Ubuntu 11.04** or **Ubuntu 11.10**. Ubuntu 11.04 is pretty stable for the most part, but 11.10 has a much more refined Unity. Unity is also very high on eye candy (not quite as much as KDE Plasma, in my opinion), and has a dock and global app menu (a la Mac OS X) integrated into the user interface. It's not very customizable, but it works well out-of-the-box for most people.

If you want to run KDE Plasma, then install **Kubuntu 11.10**. I test drove it for a little while, and I had absolutely no problems running it. Its pre-installed apps and appearences are marginally better than Kubuntu 11.04. And it's every bit as customizable as GNOME 2.x is, with even more eye candy to boot. It also has "Activities", which are multiple desktops that are each customized almost any way you want them to (widgets, wallpapers, desktop interface and netbook interface, etc.... different than multiple workspaces which are just different desktops to place open windows.

If you want to run Xfce, then install **Xubuntu** **11.10**. I haven't test driven it myself, but I hear a lot of good testimonials regarding this distro, especially the latest version. The Xfce desktop is as close to the old GNOME 2.x as it gets. It runs faster than both GNOME and KDE, yet still has a decent amount of eye candy. It also keeps a more traditional desktop interface like KDE Plasma, but unlike Unity and the newest GNOME **3.x**. 

Then, there's **Lubuntu 11.10** if you want a fast operating system. It doesn't have as much eye candy as the others, but it's very lightweight, keeps it simple, and thus makes it very fast. It can be run on everything from Pentium II systems to the latest Sandy Bridge i7's, and as little as 128MB of RAM. Like Xfce and KDE Plasma (and the older GNOME 2.x), it keeps a traditional desktop interface. There are plenty of users on these forums who stand by it as a spartan yet reliable OS that does the job very well on most any computer.

And then... do you want the latest OS, or do you want tried-and-true stability? If you want the latest, then go with the newest version of each *(Ubuntu 11.04 if you want to run GNOME, Ubuntu 11.10 if you want to run Unity)*. If you want the tried-and-true OS that will be supported all the way until April 2013, then go for **version 10.04**, which are the long-term service releases.

And last... try to install the 64-bit version of whatever version of Ubuntu you choose if possible so you can make use of all 16GB of your RAM. Look for "amd64" in the filenames. 

Good luck with your choice :)

---

### Post by vicshrike on 2011-11-01
Try some different live versions and see what you like the most.

---

