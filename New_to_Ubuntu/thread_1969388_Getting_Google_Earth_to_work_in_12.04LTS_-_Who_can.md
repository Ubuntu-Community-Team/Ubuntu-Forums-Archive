---
title: "Getting Google Earth to work in 12.04LTS - Who can help?"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by suomalainen on 2012-04-30
Ubunteros,

I did a fresh install of 11.10. Then I immeadiately upgraded to 12.04 LTS. I installed Google Earth following the instructions here:

[http://www.liberiangeek.net/2012/04/install-google-earth-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/install-google-earth-in-ubuntu-12-04-precise-pangolin/)

Google Earth launches but I cannot see any land mass. Only outlines of countries, states and territories borders are shown.... Look attached picture.

Also, when GE is open there is a sign on button in top right corner. I get this error message too.

Any idea how to correct these two issues or what maybe missing?

On a side note, isn't the launcher bar on the left side suppose to disappear? As you can see from the attached pic it's always in view.

And finally, I opened Firefox to be sure that "check spelling as I type" is "ticked" but when a word is mispelled nothing happens. what do I need to do to fix this?

Thanks for the help and happy Labour Day - May Day...

Suomalainen

---

### Post by alphacrucis2 on 2012-04-30
Not sure what is causing your googleearth problem as it is working ok here. As far as the launcher bar goes, they changed the default to always display. You can make it autohide through the settings. They removed the dodge behavior as it caused problems with interfering with browser back buttons.

---

### Post by suomalainen on 2012-04-30
@ All,

I uninstalled Google Earth and then downloaded the deb from Google's web site. I installed that package and still the same problem. E.G. I can see the outline of state and country borders but no land masses whatssoever.

Additionally, now the fonts appear not too appealing.

Anyone know what the deal is?

Thanks!

---

### Post by oregonbob on 2012-05-01
I haven't been able to get Google Earth running since Unity was release with 11.10. I just upgraded to 12.04 hoping it would work but it doesn't. That is such a mainstream killer app that Ubuntu should make sure it works on every release.

My latest error message was:

[I]Major Version 6
Minor Version 2
Build Number 0000
Build Date Jan 23 2012
Build Time 17:11:07
OS Type 3
OS Major Version 3
OS Minor Version 2
OS Build Version 0
OS Patch Version 0
Crash Signal 11
Crash Time 1335905760
Up Time 1.41974

Stacktrace from glibc:
./libgoogleearth_free.so(+0xc0af3)[0xf745aaf3]
./libgoogleearth_free.so(+0xc0c73)[0xf745ac73]
[0xf77ad400]
[/I]

I did get GE to run on a 12.04 Virtual machine on virtualbox. So that makes me think there is something wrong with my display driver (NVidia) on my main PC.

---

### Post by edeneen on 2012-05-01
I had a similar problem; during install with Linux version Google Earth gave me a message that my graphics hardware was inadequet, strange since GE works fine under Win7 on the same machine. I loaded it anyway, it worked okay, but the font looked bad.

---

### Post by Curtis6767 on 2012-05-01
I've been reluctant to download GE because I've read that it didn't work on Ubuntu. This discussion piqued my curiosity. 

I downloaded Gdebi from the software center to aid in downloading the deb file. Then I went to Google Earth and selected the amd64 deb file. I downloaded that. It went into the downloads folder of my Home file. I double clicked on that file and the software center opened with GE ready to be installed. 

Had I right clicked on the file, it would have opened in Gdebi which would have checked to make sure all dependencies were available. But double clicking and opening in the software center apparently did the same thing.

Other than the odd looking fonts, that was mentioned above, GE seems to be running fine. I hope it does prove to be equal to the version I have on my Win side.

---

### Post by pqwoerituytrueiwoq on 2012-05-01
i had no issue installing it the other day on xubuntu 12.04
that guide gets you the 32bit version yuo should use the 64bit if you installed the 64bit ubuntu
adds are google earth config files are messed up this will fix that
```
rm -rf ~/.googleearth
rm -rf ~/.config/Google
```

---

### Post by raysa on 2012-05-04
I can't get it to work on my 12.04 xubuntu.  I've tried downloading the package from the Googleearth website and installing with Software Centre, and I've tried building my own package with the GE package-builder and installing it with Gdebi. But the result is the same - GE starts to open then immediately crashes out.

What next to try?

Funnily enough it works on my hopelessly underpowered netbook running 12.04 lubuntu. Painfully slow because of the machine's limitations but perfectly stable.  But on the super-powered desktop it just crashes on opening (see above).

---

### Post by raysa on 2012-05-12
Any more news/views on this? 
Is it just a 12.04 64-bit problem? 
Is there a fix?

I've tried installing with gdebi, Software Centre and command line (completely unistalling and removing after each try) and the result is the same. GE starts to open, then as the world zooms in the programme freezes and completely locks up the computer, forcing a power-down reboot.

---

### Post by cmcanulty on 2012-05-12
If you can get to it disabling tool tips fixes it for some systems. There is a way I forget to do that from the file system. Also download qt4-qtconfig from synaptic then set fonts in qt4 to 14, by opening qt4 then set font to 14, then file-save, file-exit.. That helps it look a lot better

---

### Post by oregonbob on 2012-05-12
I couldn't get GE to work on my upgraded 12.04, so I did a fresh install of 12.04 and after that GE worked OK!

Then I installed Wine so I could use Picasa again and by installing Wine it REMOVED my Google Earth package without asking! What a buggy system Ubuntu has become.

Next you'll see someone reply and say, "Picasa is not linux, it is Windows", as if I haven't known that for years. Then they will say with great authority, "use DigiKam instead. Its native linux and much better". To that response I just shake my head and roll my eyes. Anyone who thinks DigiKam is even close to Picasa has obviously never used either one.

---

### Post by Curtis6767 on 2012-05-12
> **oregonbob said:**
> I couldn't get GE to work on my upgraded 12.04, so I did a fresh install of 12.04 and after that GE worked OK!

Then I installed Wine so I could use Picasa again and by installing Wine it REMOVED my Google Earth package without asking! What a buggy system Ubuntu has become. 

A week or so ago, when I commented in this thread, I had just downloaded and installed GE. I was a happy camper because I was concerned it wouldn't work. Aside from the odd fonts, it was fine.

Then a day or two later, I installed LMMS via a repository, rather than the Software Center. I had read that there was a LMMS/Wine connection and sure enough through the download process Wine was installed along with LMMS.

I immediately began having problems with my system and so I figured since LMMS was that last thing I installed then it could be the source of the problem, and so I deleted it. In that process, Wine was also deleted and much to my amazement so was GE.

I was not able to re-install GE afterward and my system got so bad that I had to do a fresh install of 1.204.  

I now have GE and LMMS, (this time I installed LMMS through the Software Center), on my system but I do not have Wine installed. Based on my own experience and those of oregonbob, I don't think I'll be messing with Wine anytime soon.

Just my $0.02's.

---

### Post by GDK2008UK on 2012-09-07
Dear All on this forum,
                                           I have had Google Earth running on Ubuntu 12.04LTS this morning but when I come back to my computer and try to fire up Google Earth it crashes out showing the prompt asking for a user password which is really weird as I didn't have this problem this morning maybe it was not a bright idea to install Google Earth on Ubuntu 12.04LTS at all so maybe if you want Google Earth then you should consider getting a windows laptop just for Google Earth.
Yours faithfully Gregory.

---

### Post by oregonbob on 2012-09-07
The last straw for me came with a bug in linux Google Chrome that slowed my entire PC to a crawl. It was so bad I thought my hard disk must be hitting bad sectors. Since 12.04 forked to Unity, Google has been distancing itself from it. Google Earth is unpredictable, Chrome has problems, etc.

I've been a Unix user for 25 years. I've been a linux-only user for around the past 6-8 years. Now I am sad to say I have gone back to running Windows 7 on my personal workstation. I still use Ubuntu on some servers. There are just too many hassles with Unity, besides the menu bar design totally sucks. It's rare to see a technology devolve as it has in Ubuntu.

---

### Post by jimfl on 2012-09-12
> **raysa said:**
> I can't get it to work on my 12.04 xubuntu.  I've tried downloading the package from the Googleearth website and installing with Software Centre, and I've tried building my own package with the GE package-builder and installing it with Gdebi. But the result is the same - GE starts to open then immediately crashes out.

What next to try?

I discovered a workaround elsewhere on the Net. As soon as you see the Startup Tips box appear, immediately!!! close it by clicking on its little x at the top right of that box. GE will then finish loading and work correctly.

---

