---
title: "[SOLVED] reinstalling open office issues"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by scotcella on 2008-10-22
I recently installed openoffice.org v3.0 about two weeks ago recently and had a very smooth installation.

Anyway when I tried to install java so I can use the macros, for some wierd reason open office was wiped off my laptop. I can't imagine how or why it happened, but nonetheless it was very odd. Since this happened, I thought I would reinstall in again, but have run into a snag..

THis is what i've done so far...

So I put in the terminal

```
sudo apt-get remove openoffice*.*
```

I extracted my download```


tar -zxvf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz
```

Then followed the commands

```
cd OOO300_m9_native_packed-1_en-US.9358/DEBS/
```
```

sudo dpkg -i *.deb
```

Which then gives me an error which now said:

```
Errors were encountered while processing:
 openoffice.org3
 openoffice.org3-base
 openoffice.org3-calc
 openoffice.org3-dict-en
 openoffice.org3-dict-es
 openoffice.org3-math
 openoffice.org3-writer
ella@ella-laptop:~/OOO300_m9_native_packed-1_en-US.9358/DEBS$
``` 


I can't get any further than this because of this error.

Any help appreciated

---

### Post by scotcella on 2008-10-22
Is anyone able to help me with this?

I need to do some work and can't spend the day fighting with the laptop trying to make it work. :(

BTW I am using Hardy.

---

### Post by drakeman007 on 2008-10-22
> **scotcella said:**
> Is anyone able to help me with this?

I need to do some work and can't spend the day fighting with the laptop trying to make it work. :(

BTW I am using Hardy.

Hello, there is a topic about this problem!! 

[http://ubuntuforums.org/showthread.php?t=953487](http://ubuntuforums.org/showthread.php?t=953487)

---

### Post by scotcella on 2008-10-22
Hi Drakeman,

Thank you for your reply. 

In the terminal I ran

> sudo dpkg -l | grep openoffice

and the output of that was

> ella@ella-laptop:~$ sudo dpkg -l | grep openoffice
rc  openoffice.org-calc                        1:2.4.1-1ubuntu2                                     OpenOffice.org office suite - spreadsheet
rc  openoffice.org-common                      1:2.4.1-1ubuntu2                                     OpenOffice.org office suite architecture ind
rc  openoffice.org-core                        1:2.4.1-1ubuntu2                                     OpenOffice.org office suite architecture dep
rc  openoffice.org-debian-menus                3.0-9354                                             OpenOffice.org desktop integration
rc  openoffice.org-draw                        1:2.4.1-1ubuntu2                                     OpenOffice.org office suite - drawing
rc  openoffice.org-hyphenation                 0.3                                                  Hyphenation patterns for OpenOffice.org
rc  openoffice.org-hyphenation-en-us           2.3.1-2ubuntu1                                       US English hyphenation patterns for OpenOffi
rc  openoffice.org-impress                     1:2.4.1-1ubuntu2                                     OpenOffice.org office suite - presentation
rc  openoffice.org-thesaurus-en-au             2.1-3ubuntu1                                         Australian English Thesaurus for OpenOffice.
rc  openoffice.org-thesaurus-en-us             1:2.4.0~m240-1ubuntu1                                English Thesaurus for OpenOffice.org
rc  openoffice.org-writer                      1:2.4.1-1ubuntu2                                     OpenOffice.org office suite - word processor

So it looks like thre is a mixture of the old OO and the latest 3.0 version. 

How do I fix this from here on?

Thanks so much for your help!

---

### Post by thomas228 on 2008-10-22
> **scotcella said:**
> Hi Drakeman,

Thank you for your reply. 

In the terminal I ran



and the output of that was



So it looks like thre is a mixture of the old OO and the latest 3.0 version. 

How do I fix this from here on?

Thanks so much for your help!

Scotcella

You may need to remove 00o3 first Try
you may have to remove 00o3 using tombuntu.com's script: 
sudo apt-get remove ooobasis3.0-base ooobasis3.0-binfilter ooobasis3.0-calc ooobasis3.0-core01 ooobasis3.0-core02 ooobasis3.0-core03 ooobasis3.0-core04 ooobasis3.0-core05 ooobasis3.0-core06 ooobasis3.0-core07 ooobasis3.0-draw ooobasis3.0-en-us ooobasis3.0-en-us-base ooobasis3.0-en-us-binfilter ooobasis3.0-en-us-calc ooobasis3.0-en-us-draw ooobasis3.0-en-us-help ooobasis3.0-en-us-impress ooobasis3.0-en-us-math ooobasis3.0-en-us-res ooobasis3.0-en-us-writer ooobasis3.0-gnome-integration ooobasis3.0-graphicfilter ooobasis3.0-images ooobasis3.0-impress ooobasis3.0-javafilter ooobasis3.0-kde-integration ooobasis3.0-math ooobasis3.0-onlineupdate ooobasis3.0-ooofonts ooobasis3.0-ooolinguistic ooobasis3.0-pyuno ooobasis3.0-testtool ooobasis3.0-writer ooobasis3.0-xsltfilter openoffice.org3 openoffice.org3-base openoffice.org3-calc openoffice.org3-dict-en openoffice.org3-dict-es openoffice.org3-dict-fr openoffice.org3-draw openoffice.org3-en-us openoffice.org3-impress openoffice.org3-math openoffice.org3-writer openoffice.org-ure

From [http://ubuntuforums.org/showthread.php?p=5977796#post5977796](http://ubuntuforums.org/showthread.php?p=5977796#post5977796)

Try that before reinstalling

Tom
ps: It might be more involved than that but with people like drakeman007 and others I'm sure your problem can be quickly solved

if you need to uninstall 2.4 heres another script that may be usefull
from http://ubuntuforums.org/showthread.php?t=954780
 Uninstall the existing installation of Open Office 2.4 software (this is a really long command string - please make sure you get all of it):


Code:
sudo apt-get remove openoffice.org openoffice.org-base openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human openoffice.org-writer

---

### Post by scotcella on 2008-10-22
Hi Tom,

I have read all your previous posts..  it wasn't until i read one of the posts that you individually removed all the packages via the synaptic manager, i did the same and the installation worked like a charm. So for the last hour I've been making myself a very detailed how to on OO for myself. 

All your posts were indeed correct...if a little confusing if you're reading quickly. 

When I was younger, my teachers kept telling me to **_*READ*_** properly..  goes to show they're always right!

So my lesson learnt was...  always check that I don't have old packages lurking around! 

Oh and ALWAYS read with patience!

So I'm happy to say this issue is now solved!! Yay!

---

