---
title: "Frustrated by Ubuntu"
date: 2012-06-06
forum: Recurring Discussions
---

### Post by mulugeta on 2012-06-06
I wanted to use Ubuntu. I downloaded the Windows installer and installed dual-boot. After installation i tried to open some videos - none is working. i open the terminal to check if gcc is there - it wasn't. I tried to download both and install - i run into a dependency hell. 

Why is ubuntu distributed without sorting out the basics??? This is really shame!

---

### Post by 23dornot23d on 2012-06-06
Use Flash Aid for the videos ..... in a browser like Firefox
[COLOR=Blue][U][B][https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)
[/B][/U][/COLOR]
make sure that your repos are uptodate

[B]sudo apt-get update

[/B]Then add aptitude ( this helps if there are dependency issues .

**sudo apt-get install aptitude**

or VLC for videos and streaming ..... open a terminal window and type in ....

**sudo aptitude install vlc**

and how are you trying to load gcc ...... ?

[B]sudo aptitude install gcc

[/B]> 
Why is ubuntu distributed without sorting out the basics??? This is really shame!


In answer to this - it may be a codec issue ... 

Which you can install by checking a box during installation .....  
( if you did this they should have been installed )

Also one to add third party software and upgrade from the internet  
( as far as I can remember )

If you did not do either of these there still is not real problem as they can be done 
manually .... Linux is easy once you get it set up correctly ......

---

### Post by Megaptera on 2012-06-06
> **mulugeta said:**
> ...Why is ubuntu distributed without sorting out the basics??? This is really shame!

"Due to the legal status of the software included in ubuntu-restricted-extras, the package is not included by default on any Ubuntu CDs"

From: [http://en.wikipedia.org/wiki/Ubuntu-restricted-extras](http://en.wikipedia.org/wiki/Ubuntu-restricted-extras)

---

### Post by Drenriza on 2012-06-06
> **mulugeta said:**
> I wanted to use Ubuntu. I downloaded the Windows installer and installed dual-boot. After installation i tried to open some videos - none is working. i open the terminal to check if gcc is there - it wasn't. I tried to download both and install - i run into a dependency hell. 

Why is ubuntu distributed without sorting out the basics??? This is really shame!

Yea well i also thinks it's a shame that Ubuntu docent come with the basics.

VLC, Flash, newest version of Java, Option for multiple browser pick (Firefox, Chrome, Opera). With some other things here and their which would improve the general user experience (in my opinion) and raise the "professional feel" of the OS itself.

People don't wan't quantity, they wan't quality!

EDIT.
> "Due to the legal status of the software included in ubuntu-restricted-extras, the package is not included by default on any Ubuntu CDs"
Then fix the legal stuff. Why should it be the general users problem? And in my opinion it just shows that the firm behind Ubuntu (Canonical) is not doing their job.

If their is a problem, fix it. That is what users of Ubuntu does each and every day, so why can't Canonical?

---

### Post by sffvba[e0rt on 2012-06-06
> **Drenriza said:**
> Then fix the legal stuff. Why should it be the general users problem? And in my opinion it just shows that the firm behind Ubuntu (Canonical) is not doing their job.

If their is a problem, fix it. That is what users of Ubuntu does each and every day, so why can't Canonical?

> Ubuntu strives to make all software that meets the licensing terms in the Ubuntu License Policy available. However patent and copyright restrictions complicate free operating systems distributing software to support proprietary formats.

Ubuntu's commitment to only include completely free software by default means that proprietary media formats are not configured 'out of the box'.

Ubuntu can play the most popular non-free media formats, including DVD, MP3, Quicktime, Windows Media, and more by following the instructions below. If this seems like unnecessary work, remember that Ubuntu is a distribution of free software and these packages are (at least arguably) affected by patents and license restrictions in some countries. Avoid formats suppressed by DRM (Digital Rights Management, or Digital Restrictions Management), as they are often unplayable.

See Ubuntu's Free Software Philosophy and the Free Formats page for a more comprehensive discussion of these issues.

    Legal Notice Patent and copyright laws operate differently depending on which country you are in. Please obtain legal advice if you are unsure whether a particular patent or restriction applies to a media format you wish to use in your country. 



[Source]("https://help.ubuntu.com/community/RestrictedFormats")


404

edit - @OP - If you are running into dependency issues that you are doing something seriously wrong.

---

### Post by coffeecat on 2012-06-06
@mulugeta, as others have said, codecs for proprietary media formats cannot be installed by default because of the patent and copyright laws in some countries. Someone has already mentioned ubuntu-restricted-extras. My routine, and I install Ubuntu several times a year on different systems, is to install ubuntu-restricted-extras as a matter of course. That gives me most of the media codecs I need, flash, java and MS core fonts. For more, see here:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

And if you want to play encrypted commercial DVDs, you will also need libdvdcss2:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

As far as gcc is concerned, why do you need it? If you are a beginner to Ubuntu, you do not need to compile anything, so if you are trying to compile something, I suggest you stop now and instead get advice about the apps you are trying to install.

For the record, the reason that gcc is not included by default is that >95% (at a guess) of users do not need it. Only developers and experienced users need to compile anything. Developers know that they can simply install the package build-essential to get most of the packages they need.

---

### Post by mastablasta on 2012-06-06
> **Drenriza said:**
> Yea well i also thinks it's a shame that Ubuntu docent come with the basics.
 
VLC, Flash, newest version of Java, Option for multiple browser pick (Firefox, Chrome, Opera). With some other things here and their which would improve the general user experience (in my opinion) and raise the "professional feel" of the OS itself.
 
People don't wan't quantity, they wan't quality!
 
EDIT.
 
Then fix the legal stuff. Why should it be the general users problem? And in my opinion it just shows that the firm behind Ubuntu (Canonical) is not doing their job.
 
If their is a problem, fix it. That is what users of Ubuntu does each and every day, so why can't Canonical?
 
you are comparing ubutnu to what other FREE operating system that includes these? Mint (ubuntu based) has the codecs/flash and such and if someone sued them it would be hard for them to defend it. and as mentioned they might be allowed for free in some countries but not in others.
widnows comes with them preloaded but you need to pay for it (though i remember they were also missing codecs in xp). windows comes with only one browser (IE)  in Europe it should offer more to download & install.

---

### Post by mutap on 2012-06-06
> **mulugeta said:**
> I wanted to use Ubuntu. I downloaded the Windows installer and installed dual-boot. After installation i tried to open some videos - none is working. i open the terminal to check if gcc is there - it wasn't. I tried to download both and install - i run into a dependency hell. 

Why is ubuntu distributed without sorting out the basics??? This is really shame!
[http://www.howtoforge.com/the-perfect-desktop-ubuntu-12.04-lts-precise-pangolin](http://www.howtoforge.com/the-perfect-desktop-ubuntu-12.04-lts-precise-pangolin)

Check out this thread to setup your OS(additional programs, codecs and repositories) after installation.

---

### Post by Drenriza on 2012-06-06
> codecs for proprietary media formats cannot be installed by default because of the patent and copyright laws in some countries. 

Their is always a solution. The question is if you want to spend the time and money to make it happen. And the answer here is **no**.

---

### Post by snowpine on 2012-06-06
> **Drenriza said:**
> Their is always a solution. The question is if you want to spend the time and money to make it happen. And the answer here is **no**.

There is always a solution, and in the case of Ubuntu, it is the user executing a simple terminal command or a couple of mouse clicks in the Software Center.

Linux is not Windows; it has a completely different culture and set of expectations for the user. If you embrace it, then it will embrace you. :)

---

### Post by arpanaut on 2012-06-06
> **Drenriza said:**
> Their is always a solution. The question is if you want to spend the time and money to make it happen. And the answer here is **no**.
So, you want Ubuntu to pay for the use of these patents and codecs,
then give you an OS for FREE?   ...Right!

With a little time and effort the end user can accomplish the same thing at no cost to anyone.  

Problem Solved!

---

### Post by blackbird34 on 2012-06-06
If you want codecs out-of-the-box, you can get Mint instead, they can do that BECAUSE they are based in France, which have different patent laws. Ubuntu/ Canonical are based in the UK or the US or South Africa or something, in any case *they are not French* and must follow copyright law.

---

### Post by sffvba[e0rt on 2012-06-06
*Thread moved to **Recurring Discussions**.*

As soon as the OP has specific questions on specific issues he should star new threads in the appropriate sub-forum.


404

---

### Post by Viper1987 on 2012-06-06
simple solution - google medibuntu. it will give you all of your codecs and plug-ins..

Btw, i heard that the only way to get the newest OFFICIAL flash player in Ubuntu is going to be by using Chrome due to licensing issues. Has anyone heard the same thing?

---

### Post by jockyburns on 2012-06-06
I just wonder if the OP actually realises how restrictive Windows is , when it comes down to the nitty gritty? I used windows for years (right from 3.1 through to XP) and lost count of the times I tried to do something , only to find the right "something" wasn't installed. If the OP realised that Win XP installed off a disk, almost immediately started to download updates, he'd realise that Win XP didn't strictly, work "out of the box" either.

---

### Post by QIII on 2012-06-06
Java and Flash aren't installed by default in, um, Windows any more than they are in Ubuntu.  Install Windows fresh and go to YouTube.  You'll be asked to install it.  Same for Java -- nobody can have it installed by default because Oracle will not allow it.

Microsoft pays a great deal of money for the license to include various codecs in their OSes -- in bulk.

You don't get them "free" with Windows.  They are rolled into the cost for your license to use Windows.

There are a number of things, like VLC, that could be included by default.  But what if you want it but Joe Fubar doesn't?  What if he uses smplayer instead?  Things like that are included in the repos for you to install if you want to -- and Joe doesn't have to uninstall them.

It is not incumbent on Canonical to get the legalities of software licensing arranged in every country where Ubuntu is used.  If you care to, you can provision the vast army of international lawyers that would be needed for that world conquest.

---

### Post by bodhi.zazen on 2012-06-06
> **mulugeta said:**
> I wanted to use Ubuntu. I downloaded the Windows installer and installed dual-boot. After installation i tried to open some videos - none is working. i open the terminal to check if gcc is there - it wasn't. I tried to download both and install - i run into a dependency hell. 

Why is ubuntu distributed without sorting out the basics??? This is really shame!

Learning a new OS can be frustrating. You seem to be ranting without mentioning any specific problem.

Some problems are due to your lack of experience or knowledge, so ask for help.

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

Some issues are a matter of knowing what to install. The install CD is limited to 700 mb so there is no way to include everything every user might want or need.

Some issues are legal. In that case you change the law (there is no technical solution).

Some problems are bugs. There is no OS that is free of bugs. Feel free to file bug reports and / or submit patches.

[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

Either way , I agree with moving this to recurring discussions, it is more a rant then a support thread, and we are all tired of people ranting about this or that.

good luck to you.

---

### Post by nll on 2012-06-06
Start by trying to do a fresh install of Windows, then move on to compare *sudo apt-get install ubuntu-restricted-extras* [to things like this]("http://www.zdnet.com/blog/hardware/no-windows-8-dvd-playback-will-mean-increased-costs-and-consumer-confusion/20181"). After that, please come back and tell us if you still are feeling frustrated.

---

### Post by bodhi.zazen on 2012-06-06
> **nll said:**
> Start by trying to do a fresh install of Windows, then move on to compare *sudo apt-get install ubuntu-restricted-extras* [to things like this]("http://www.zdnet.com/blog/hardware/no-windows-8-dvd-playback-will-mean-increased-costs-and-consumer-confusion/20181"). After that, please come back and tell us if you still are feeling frustrated.

Better, with your next purchase got with Linux pre-installed.

Then try installing windows.

---

