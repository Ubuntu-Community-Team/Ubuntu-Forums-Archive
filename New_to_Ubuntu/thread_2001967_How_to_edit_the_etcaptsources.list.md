---
title: "How to edit the /etc/apt/sources.list?"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by Fishercats on 2012-06-11
Hi.

I've been using Lubuntu 12.04 for about a week, and haven't routinely used a command line or terminal since before PCs had GUIs.

I'm trying to install a screen saver package "http://packages.debian.org/squeeze/xscreensaver-data-extra" using either Synaptic or the Lubuntu Software Center.  I don't care which one I use, but the package I'm looking for isn't listed on either one.  The download pages for the package imply that if I edit the /etc/apt/sources.list to include the URL of one of the mirror sites, the process will work in Synaptic.

My questions:
1.  Where can I find the architecture for my box?
2.  Does it matter that there's a difference in name between the package the screen saver is missing (xscreensaver-extras) and the one that's available for download (xscreensaver-data-extra)?  
3.  Will software originally written for Debian generally run on Lubuntu?
4.  How do I find and edit the /etc/apt/sources.list?
5.  Can you recommend any other Lubuntu documentation resources than this:  "https://help.ubuntu.com/community/Lubuntu/Documentation" and the FAQ?

I'll appreciate any help you can offer, but I know absolutely nothing.  Please spell things out for me (literally - I don't know any of the acronyms I've seen in the forums).

Thanks!

---

### Post by spikoley on 2012-06-12
1. Where can I find the architecture for my box?

Open up a terminal and use the command *uname -a*.

2. Does it matter that there's a difference in name between the package the screen saver is missing (xscreensaver-extras) and the one that's available for download (xscreensaver-data-extra)? 

Probably not, but I am unsure.

3. Will software originally written for Debian generally run on Lubuntu?

Most of the time there shouldn't be an issue.  It is a best practice to install from the repository.

4. How do I find and edit the /etc/apt/sources.list?

In the terminal type *gksudo gedit /etc/apt/sources.list*.

5. Can you recommend any other Lubuntu documentation resources than this: "https://help.ubuntu.com/community/Lubuntu/Documentation" and the FAQ?

Sorry, I don't have any.  Just search the internet for what you are looking for with Lubuntu added to the search.

---

### Post by wilee-nilee on 2012-06-12
Putting a debian squeeze link in is not a good idea period.

Find the equal in the ubuntu world or at least something close.

This is available in ubuntu but as a targz it looks like. Lubuntu and Ubuntu are basically the same in this area.

[https://www.google.com/search?q=%28xscreensaver-data-extra+ubuntu&btnG=Search&sclient=psy-ab&hl=en&site=webhp](https://www.google.com/search?q=%28xscreensaver-data-extra+ubuntu&btnG=Search&sclient=psy-ab&hl=en&site=webhp)

---

### Post by zombifier25 on 2012-06-12
I wonder why you're going through the trouble of searching for an old xscreensaver package on Debian anyway, while there are packages in Ubuntu's own repo. There are 2 reasons you should not do that:
1. Too much trouble. It's like killing a fly with a cleaver.
2. It may not work (in this case, I would say WILL NOT work, because the package is for Debian Squeeze, while Ubuntu 12.04 is based on Wheezy)

---

### Post by Fishercats on 2012-06-12
*3. Will software originally written for Debian generally run on Lubuntu?*

> Most of the time there shouldn't be an issue.  It is a best practice to install from the repository.I thought I was trying to expand the repositories that came with my (pretty minimal) install of Lubuntu.  Or did you mean it's best practice to install new packages only from the repositories that are standard for your build?

---

### Post by Fishercats on 2012-06-12
> **wilee-nilee said:**
> Putting a debian squeeze link in is not a good idea period.

Find the equal in the ubuntu world or at least something close.

This is available in ubuntu but as a targz it looks like. Lubuntu and Ubuntu are basically the same in this area.

[https://www.google.com/search?q=%28xscreensaver-data-extra+ubuntu&btnG=Search&sclient=psy-ab&hl=en&site=webhp](https://www.google.com/search?q=%28xscreensaver-data-extra+ubuntu&btnG=Search&sclient=psy-ab&hl=en&site=webhp)
Okay, thanks.  I'll find an Ubuntu version, now that I know they're available.

What's a targz?  Is it something I can install using Synaptic or the Lubuntu Software Center?

---

### Post by Fishercats on 2012-06-12
> I wonder why you're going through the trouble of searching for an old  xscreensaver package on Debian anyway, while there are packages in  Ubuntu's own repo. The short answer is, I didn't know there were any.  

I did a pretty minimal install of Lubuntu.  The screen saver was included; its data files were not.  When I tried to change screen saver settings, I got an error message mentioning a couple of packages it didn't have.  I searched for those package names, found the developer's page, which led me to the Debian stuff.  The developer mentioned the following possibilities for downloading what I needed:  RPM and Debian packages, and manual install and compiling, which he strongly cautioned against.  I found out what RPM was, and that Ubuntu is a Debian descendant, and went from there.

As I said, I know nothing, so I didn't realize I should include my flavor of Linux (distro?) as a search term when I'm looking for packages.  I do now, so thank you.  :-)

---

### Post by wilee-nilee on 2012-06-12
> **Fishercats said:**
> Okay, thanks.  I'll find an Ubuntu version, now that I know they're available.

What's a targz?  Is it something I can install using Synaptic or the Lubuntu Software Center?

A tar.gz is a file type, not needed most of the time in a Ubuntu setup but on occasion people will install using them. Personally if I am trying to find a out of the repos package I look for a deb that can be installed through the software center or with a app like gdebi which is in the repos.

Here is google meta search for you to look around in. The install of this type is done with a terminal.

[https://www.google.com/search?q=tar.gz&btnG=Search&hl=en&output=search&sclient=psy-ab&gbv=1](https://www.google.com/search?q=tar.gz&btnG=Search&hl=en&output=search&sclient=psy-ab&gbv=1)

---

### Post by Fishercats on 2012-06-12
> **wilee-nilee said:**
> A tar.gz is a file type, not needed most of the time in a Ubuntu setup but on occasion people will install using them. Personally if I am trying to find a out of the repos package I look for a deb that can be installed through the software center or with a app like gdebi which is in the repos.

Here is google meta search for you to look around in. The install of this type is done with a terminal.

[https://www.google.com/search?q=tar.gz&btnG=Search&hl=en&output=search&sclient=psy-ab&gbv=1](https://www.google.com/search?q=tar.gz&btnG=Search&hl=en&output=search&sclient=psy-ab&gbv=1)
Great, thank you.   

I think for the time being, I'm going to try to stick to packages that can be installed using Synaptic or the Software Center, as I've already used those successfully.  I'm sure I'll end up using the terminal for stuff eventually, but absorbing a new OS takes time, and it's still a bit overwhelming.  I'm not used to putting 4-5 hours of skull sweat into finding out how to do something as trivial as making changes to the screen saver.

Thanks again for the advice; I appreciate it.

---

### Post by Fishercats on 2012-06-12
So, it turns out all I needed to do was use less-specific search terms in Synaptic; the packages I needed were there, after all.  Searching for "xscreensaver" instead of "xscreensaver-extras" got me what I needed.

Thanks to everyone who offered advice.

---

