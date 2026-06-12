---
title: "How to &quot;roll back&quot; Firefox?"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by scruffyeagle on 2011-11-18
I'm running Ubuntu v10.04 LTS 32-bit on a Dell Inspiron 9400 laptop.

My copy of Firefox was updated recently via the Update Manager, as part of a massive update download. Today, I realized that the updated FF (v3.6.24) won't retain any tweaks I make on the toolbar. I can't get rid of that blasted Google search box, and I can't get the icons I need to stay in the toolbar. I can tweak the toolbar's contents, but when FF is closed then restarted all the tweaks are lost.

Is there any way to "roll back" FF to the way it was before that update occurred?

TIA.

---

### Post by rosencrantz on 2011-11-18
If the older version still available in your repository choices, try in a terminal,
apt-cache policy firefox
to find the available version numbers. Example output:
```
firefox:
  Installed: 7.0.1+build1+nobinonly-0ubuntu0.11.04.1
  Candidate: 7.0.1+build1+nobinonly-0ubuntu0.11.04.1
```
Afterwards, you can install a specific version with e.g. 
sudo apt-get install firefox=7.0.1+build1+nobinonly-0ubuntu0.11.04.1
However, you have to hold the package in order to not have it updated immediately again:
echo "firefox hold" | sudo dpkg --set-selections

---

### Post by raja.genupula on 2011-11-18
I think we can't . better to reinstall the desired version.
in system at /var/cache/apt your old firefox deb file can be found .

first uninstall present firefox completely with purge after taking necessary backups like bookmarks etc.

```
sudo apt-get remove --purge firefox 
```

then take the main file of firefox from the above folder location. place it on your home folder.

```
sudo dpkg -i filename.deb
```

do this & dont worry about the dependencies , if you got any error abt dep's
then run 

```
sudo apt-get install -f
```

and then execute the command again i have given above. 
it will be fine.
all the best.

---

### Post by scruffyeagle on 2011-11-20
Rosencrantz & Raja: Thank you for your replies. Between when I posted my message & now, I got fed up with using the disfunctional version of FF. I didn't know about the "hold" command, so I thought that even if I reinstalled the previous version, I'd end up dealing with this updated problem again. So, I decided to try something completely different. I uninstalled & purged FF, and then installed Sea Monkey. I'm still exploring it, but so far I don't have any complaints. The only FF feature I really miss at this point, is the one that failed in the updated FF - the ability to customize the toolbar by adding things like "Full screen", Cut/Copy/Paste icons, etc. But it is interesting to have the associated/bundled email utility in a Netscape style. I haven't decided yet whether I prefer it over the Evolution email utility, but it's interesting at least.

---

### Post by scruffyeagle on 2011-11-20
An extra update to my little saga...

After using Sea Monkey for a few hours, I got fed up with that also. I don't know if it was the fault of the Add-ons or not, but the browser crashed repeatedly. I'd be working with it for a while without any problem, then I'd click on a link or a window control and it would just immediately close all windows without any warning or message - just, suddenly gone. I decided this simply wasn't acceptable, so I started searching again for a better browser.

I found, downloaded, and installed iceweasel v1.5. It seemed to work okay, but the FF Add-ons I've come to rely on wouldn't work because the v1.5 was incompatible. I knew there were versions up to v7 out there, some of which could use the Add-ons, but I couldn't find more recent copies to use.

Searching again in Google, I discovered a link for a page having instructions for dl'ing & installing FF v8, including some trouble-shooting comments from users. ( [http://news.softpedia.com/news/How-to-Install-Firefox-8-in-Ubuntu-10-04-and-10-10-232859.shtml](http://news.softpedia.com/news/How-to-Install-Firefox-8-in-Ubuntu-10-04-and-10-10-232859.shtml) ) I decided to give it a try. Iceweasel didn't seem to be any improvement over the other options, so I removed it using ```
sudo apt-get purge iceweasel
``` (I'm pretty sure that was the command I used...) I followed the instructions on the web page, and installed FF v8.0 canonical 1.0. So far, it's working great, and I've got control of the toolbar again!

If I discover any problems, I'll come back here and post an update - but for now, I think I found the solution I needed.

---

### Post by lovinglinux on 2011-11-24
For future reference, instead of downloading other versions and brands, close Firefox, delete the file *localstore.rdf* from your FF profile under ~/.mozilla/firefox/<profilename> and restart Firefox. It will reset the toolbars completely and fix the problem.

---

### Post by scruffyeagle on 2011-11-26
> **lovinglinux said:**
> For future reference, instead of downloading other versions and brands, close Firefox, delete the file *localstore.rdf* from your FF profile under ~/.mozilla/firefox/<profilename> and restart Firefox. It will reset the toolbars completely and fix the problem.

Are you referring to the original problem, where FF wouldn't retain any changes I'd made customizing the toolbar?

---

### Post by lovinglinux on 2011-11-26
> **scruffyeagle said:**
> Are you referring to the original problem, where FF wouldn't retain any changes I'd made customizing the toolbar?

Yes.

---

### Post by scruffyeagle on 2011-11-29
> **lovinglinux said:**
> Yes.

Okay. Thanks for the info! It's a bit of a moot point, now that I'm working w/ FFv8 - but, I think it's still useful to know. I took a few moments to track down the file in my system, and found it w/o problem.

Maybe you could answer a different question about FF? The other day when I used the Update Manager, it found "ubufox" & "xul-ext-ubufox" as updates. I didn't download & install them, because I wasn't sure they actually pertain to an installation of FFv8. I downloaded & installed v8 directly from Mozilla, instead of through the Ubuntu Software Center or the Synaptic Package Manager. So, I was also worried that if I installed these unknowns, that they might somehow revert FF to an earlier version, making me lose the v8 installation in favor of v3 or v4.

"ubufox
 transitional dummy package"

Details specify
"Changes for the versions:
 0.9~rc2-0ubuntu2.1
 0.9.2-0ubuntu0.10.04.1~mfn4"

"xul-ext-ubufox (New install)
 Ubuntu-specific configuration defaults and  apt support for Firefox"

Details specify
"Changes for the versions:
 None
 0.9.2-0ubuntu0.10.04.1~mfn4"

Do you know if these 2 unknowns are appropriate for use w/ my FFv8 installation?

---

### Post by vasa1 on 2011-11-29
> **scruffyeagle said:**
> ...

Searching again in Google, I discovered a link for a page having instructions for dl'ing & installing FF v8, including some trouble-shooting comments from users. ( [http://news.softpedia.com/news/How-to-Install-Firefox-8-in-Ubuntu-10-04-and-10-10-232859.shtml](http://news.softpedia.com/news/How-to-Install-Firefox-8-in-Ubuntu-10-04-and-10-10-232859.shtml) ) I decided to give it a try. ... I followed the instructions on the web page, and **installed FF v8.0 canonical 1.0.** ...

> **scruffyeagle said:**
> ...
... **I downloaded & installed v8 directly from Mozilla**,...

What exactly have you done?

---

### Post by I2k4 on 2011-11-30
I suggest you go to Synaptic Package Manager and search for Ubufox - it will explain what it does.  Nothing important so far as I can tell.  I used apt-get in the terminal to get Firefox beta (now version 9) for my Lubuntu installation and it did not install Ubufox.

I think a little online research will convince you that you are much better off now with FF8 than any 3.x version - version 4 was a major speed and reliability enhancement, and the following updates have improved it incrementally.

---

### Post by lovinglinux on 2011-12-01
> **scruffyeagle said:**
> Okay. Thanks for the info! It's a bit of a moot point, now that I'm working w/ FFv8 - but, I think it's still useful to know. I took a few moments to track down the file in my system, and found it w/o problem.

Maybe you could answer a different question about FF? The other day when I used the Update Manager, it found "ubufox" & "xul-ext-ubufox" as updates. I didn't download & install them, because I wasn't sure they actually pertain to an installation of FFv8. I downloaded & installed v8 directly from Mozilla, instead of through the Ubuntu Software Center or the Synaptic Package Manager. So, I was also worried that if I installed these unknowns, that they might somehow revert FF to an earlier version, making me lose the v8 installation in favor of v3 or v4.

"ubufox
 transitional dummy package"

Details specify
"Changes for the versions:
 0.9~rc2-0ubuntu2.1
 0.9.2-0ubuntu0.10.04.1~mfn4"

"xul-ext-ubufox (New install)
 Ubuntu-specific configuration defaults and  apt support for Firefox"

Details specify
"Changes for the versions:
 None
 0.9.2-0ubuntu0.10.04.1~mfn4"

Do you know if these 2 unknowns are appropriate for use w/ my FFv8 installation?

Ubufox is an extension that add custom Ubuntu stuff to Firefox like customized home page, customized search engines, some gnome support stuff like apturl handling and as far as I know some KDE customization stuff like button positions on FF dialogs.

There is also Global Menu Bar Integration extension, that enables Global Menu in Firefox.

Go ahead and update.

---

### Post by Ms. Daisy on 2011-12-01
Scruffyeagle, I would encourage you to constantly install all the updates for whatever browser you end up choosing.

---

### Post by scruffyeagle on 2011-12-02
> **vasa1 said:**
> What exactly have you done?

I installed FFv8 directly from Mozilla, instead of using the version provided through the Synaptic Package Manager. (NOTE: This required registering the Mozilla FF repository as a software source.) So far, I've had absolutely no problems at all with it.

However, I'm a little puzzled that the Update Manager is finding updates being provided for software that didn't originate in the standard repository. Perhaps these updates are being found via the Mozilla site?

---

### Post by lovinglinux on 2011-12-02
> **scruffyeagle said:**
> I installed FFv8 directly from Mozilla, instead of using the version provided through the Synaptic Package Manager. (NOTE: This required registering the Mozilla FF repository as a software source.) So far, I've had absolutely no problems at all with it.

The repository you registered in the software sources is not from Mozilla. Despite the fact that is has "mozillateam" on it's name, it is a repository maintained by the Ubuntu developers who are responsible for Firefox and Thunderbird. So this repository, although not official, is maintained by the same people that maintain Firefox in the official Ubuntu repository.

> **scruffyeagle said:**
> However, I'm a little puzzled that the Update Manager is finding updates being provided for software that didn't originate in the standard repository. Perhaps these updates are being found via the Mozilla site?

That is how it works. If you add a third-party repository to the software sources, it will get any update from it, as long as the version number is superior than the official repo. Keep in mind that particular ppa repository you included will update only Firefox related applications, which includes ubufox.

There is nothing to worry about. Go ahead and continue updating your Firefox and related packages.

For more info see [Firefox 8 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247).

---

### Post by scruffyeagle on 2011-12-06
Thank you, each & all, for your replies, explanations, and advice.

Between my last post & now, I'd figured out that the Ubufox(etc.) updates were being served out of the Mozilla repository, and were geared to my FFv8. So, I performed the update. Is IS reassuring to know, that it's actually the same people populating that repository and the standard Ubuntu repositories (less risk of conflicting code, I think).

Thanks!

---

### Post by sydjf on 2012-01-04
I have exactly the same problem where the customized icons go missing from the toolbar in firefox after closing and opening firefox.I tried to do what was suggested in post #6 by lovinglinux but was unsuccessful.[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

                                  **Re: How to "roll back" Firefox?**             
                                                                For future reference, instead of downloading other versions and brands, close Firefox, delete the file *localstore.rdf* from your FF profile under ~/.mozilla/firefox/<profilename> and restart Firefox. It will reset the toolbars completely and fix the problem.
                                                                                               __________________

I could find the file localstore.rdf by doing a search in the file browser but these files have locks on them so I couldn't delete them. Could someone do an explanation for a computer dummy on how to find this file and delete it?
Cheers
sydjf

---

### Post by scruffyeagle on 2012-01-05
> **sydjf said:**
> I have exactly the same problem where the customized icons go missing from the toolbar in firefox after closing and opening firefox.I tried to do what was suggested in post #6 by lovinglinux but was unsuccessful.[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

                                  **Re: How to "roll back" Firefox?**             
                                                                For future reference, instead of downloading other versions and brands, close Firefox, delete the file *localstore.rdf* from your FF profile under ~/.mozilla/firefox/<profilename> and restart Firefox. It will reset the toolbars completely and fix the problem.
                                                                                               __________________

I could find the file localstore.rdf by doing a search in the file browser but these files have locks on them so I couldn't delete them. Could someone do an explanation for a computer dummy on how to find this file and delete it?
Cheers
sydjf

I didn't try what lovinglinux suggested, because I'd already found a different solution - upgrading to FFv8. But, reading your inquiry I did a search and found the following page:
[http://www.labtestproject.com/linuxcmd/rm.html](http://www.labtestproject.com/linuxcmd/rm.html)

Although the page is intended for users of Fedora, I think what it instructs will also fit Ubuntu. So, I think that page will have the info you need for understanding deleting a hidden &/or protected file. You can verify the FF profile name on your system by using your file browser w/ the "View hidden files" option active. To do what I'm going to suggest, you'll need to do it from a command line console. I think the following command will do the job for you.

```
sudo rm -f ~/.mozilla/firefox/<profilename>/localstore.rdf
```

Be aware that "rm" is a very powerful command, and I'm NOT an expert. Use it at your own risk. Read & understand the related material on the page before using "rm".

---

