---
title: "Logmein, Ubuntu 8.10, Firefox 3, Java 6"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by carusoswi on 2008-11-03
Ok, back in my 8.04 days, I had to drop back to Java 5 to get Logmein to work from Linux.  I had upgraded to 8.10 and Logmein continued to work.  Had to start from scratch over the weekend, installed 8.10 to a clean HD.  No joy with Logmein.  FF version is 3, Java is 6.

Would drop to java 5 if I knew how.

Ran into a similar problem with FF and XP this time around (XP is also a new installation), but could sign on to java's site and run a test that confirmed java 6 was installed and working - don't know what, if anything, was changed, but the XP side is working now.

Any suggested solutions welcome.  Happy to drop to java 5 if someone can point the way.  Can't seem to find previous instructions, and not certain they would work with 8.10 anyhow.

Thanks.

Caruso

---

### Post by taurus on 2008-11-03
Go into System -> Administration -> Synaptic Package Manager and enter java in the Search field.  Remove java 6 (and all the associated files) and then install java 5 from there.

---

### Post by carusoswi on 2008-11-04
> **taurus said:**
> Go into System -> Administration -> Synaptic Package Manager and enter java in the Search field.  Remove java 6 (and all the associated files) and then install java 5 from there.

Tried that . . . no joy.  Java 5 seems worse than Java 6.  After clicking remote control (which is supposed to bring up my remote desktop), Java 6 just returns a black screen.

Java 6 at least gave me messages that my desktop would apear shortly (although it never does).

Seems I go through this with every Ubuntu install.  The solution never seems quite the same.

thanks for your reply.

Caruso

---

### Post by Excedio on 2008-11-05
> **carusoswi said:**
> Ok, back in my 8.04 days, I had to drop back to Java 5 to get Logmein to work from Linux....

Could you explain to me how you got your LogMeIn to install please? I'm still very new to Linux and using the terminal. I've already downloaded the tarball and extracted the files in it.

I opened the README file for LogMeIn and it says what commands to use in the terminal, but I can't seem to type the commands correctly.

Help please...

Lorenzo

---

### Post by carusoswi on 2008-11-08
Perhaps my post is misleading.  I have Logmein installed on my office PC (running XP) and often need to access it from my home.  I use a browser from Linux to do that - no need for Logmein to be installed on my home (linux) machine.

Since I turn off my home machine when I leave the house, I have no need to remotely access the home machine from the office, hence, no logmein installed on the home (linux) machine.  

My problem is maintaining my ability to connect to the office machine from my home machine while in Linux.  With XP, there is never (almost never) a problem.  It seems that, with every install/reinstall or upgrade in Ubuntu, this problem crops up again.  In 8.04, the problem was narrowed down to Java 6.  When I first upgraded to the 8.10 beta, Java 6 worked fine with my browsers to access my office XP box.  Then, last weekend, I downloaded the 8.10 desktop CD and performed a clean install (I needed to do this due to unreleated hardware problems). Following the clean install, accessing my office PC from within Ubuntu was no longer possible.

I have never tried installing Logmein in Ubuntu.

Caruso

> **Excedio said:**
> Could you explain to me how you got your LogMeIn to install please? I'm still very new to Linux and using the terminal. I've already downloaded the tarball and extracted the files in it.

I opened the README file for LogMeIn and it says what commands to use in the terminal, but I can't seem to type the commands correctly.

Help please...

Lorenzo

---

### Post by Xsoldier2000 on 2008-11-19
You know, I'm having the EXACT same problem. If I switch to LinuxMint (defaults install) Logmein works right out of the box. But for the life of me, I can't get it working in Ubuntu.

Let me correct myself, I get it working, but I can only type in a box on top of the Remote Control screen and have to refresh constantly. But with Mint, it's like using a VirtualBox...just like I'm at the computer itself.


Anyone got it working yet?

---

### Post by carusoswi on 2008-11-19
I just consider it to be another one of those setbacks that one gets used to if you follow the Ubuntu upgrade path.  I'm not certain if it's fair to be critical, but with each new upgrade, it seems I have to wait for features upon which I rely to get fixed in the new version.  The problem with logmein is a common issue that crops up everytime I upgrade to a new version.  I'm not certain why that is, but, as you say, the solution is as simple as going with another distro or sticking to the previous Ubuntu version.

It's still not working for me - in fact, my Java 6 is broken, too.  I can't remove it completely, can't upgrade it completey - I get an error message every time my system updates having to do with some bit of Java 6 that isn't downloading correctly.

I'll just live with the logmein problem for now and use XP when I have to telecommute.

Let me know if you get yours to work.

Caruso

> **Xsoldier2000 said:**
> You know, I'm having the EXACT same problem. If I switch to LinuxMint (defaults install) Logmein works right out of the box. But for the life of me, I can't get it working in Ubuntu.

Let me correct myself, I get it working, but I can only type in a box on top of the Remote Control screen and have to refresh constantly. But with Mint, it's like using a VirtualBox...just like I'm at the computer itself.


Anyone got it working yet?

---

### Post by Xsoldier2000 on 2008-11-20
Well, I did get mine to work....but not the correct way. I had heard about "Super Ubuntu 2008.10" (Just an amped up Ubuntu 8.10 with flash, java, media codecs, dvd....already installed by default. Check it out.) so I gave it a shot. Downloaded it and burned to DVD...checked the live environment and Logmein worked perfectly. I only had to accept the security thing and I was off using logmein.com without a problem.

I know it's not how to fix a problem, but installation and configuring took me only about an 1 1/2 hrs. Where as regular Ubuntu install was about 2 1/2 - 3 hrs. (Still WAY far less than that **_OTHER_** operating system ;-) (average about 4 - 5 hrs.))

This *IS* Ubuntu 8.10, just with everything else installed that I would have to take time to install later.

I just copied my entire home directory to a different hard drive, installed "Super" and about 6 additional programs, then recopied my home directory back. 

Hope this helps someone else.

---

### Post by carusoswi on 2008-11-21
SEA MONKEY SUITE was the solution to this problem.  I am also slowly coming to the conclusion that many of the crashing issues I have experienced with the 8.10 upgrade have to do with the current iteration of Firefox.

Anyhow, I installed Sea Monkey and was able to log onto my remote computer using Logmein - no problems.

I think I am going to uninstall Firefox.  Firefox used to be my strongest form of "civil disobedience".  Now, it seems to have accumulated bloat reminiscent of the 'e' browser.

I hope FF sort things out.  For now, it's the monkey for me.

Caruso

---

### Post by carusoswi on 2008-11-21
I was so giddy when Sea Monkey worked to get my Logmein going, I didn't see your post.  I'll have to check out this super Ubuntu . . . surprised I haven't already come across it.

I also looked up a brief history of Sea Monkey to see (as I suspected) that is shares its heritage with Firefox.  Browsing through the similarities and differences did not make apparent to me the reason why Sea Monkey should work while FF does not.  Perhaps someone can enlighten me.

Caruso

> **Xsoldier2000 said:**
> Well, I did get mine to work....but not the correct way. I had heard about "Super Ubuntu 2008.10" (Just an amped up Ubuntu 8.10 with flash, java, media codecs, dvd....already installed by default. Check it out.) so I gave it a shot. Downloaded it and burned to DVD...checked the live environment and Logmein worked perfectly. I only had to accept the security thing and I was off using logmein.com without a problem.

I know it's not how to fix a problem, but installation and configuring took me only about an 1 1/2 hrs. Where as regular Ubuntu install was about 2 1/2 - 3 hrs. (Still WAY far less than that **_OTHER_** operating system ;-) (average about 4 - 5 hrs.))

This *IS* Ubuntu 8.10, just with everything else installed that I would have to take time to install later.

I just copied my entire home directory to a different hard drive, installed "Super" and about 6 additional programs, then recopied my home directory back. 

Hope this helps someone else.

---

### Post by Xsoldier2000 on 2008-11-23
Hey, thanks for the tip. I will keep that in mind moving forward. 

How is the Layout with Sea Monkey compared with Firefox? (Have you had any issues with it now that you've had it a few days? Does it import all your firefox bookmarks and/or passwords?)

Or do you use it strictly for logmein?

I'm also confused as to why Monkey would work as opposed to FF? (on the same system/platform)

Thanks again.

---

### Post by NeroWolf on 2008-12-11
It seems to me that FireFox has a built-in Java parser that is buggering-up LogMeIn for a good majority of would-be users that are giving the one-finger salute to big-ticket corporations.

OR

Alternatively, the Synaptic management of the Java6 install is not auto-registering the plugin to FireFox, and thus is not resolving the issue.  Could also be that you have to manually register said plugin...

In any case, I'm downloading Super Ubuntu 2008.10 right now to try it out.

-- Nero:lolflag:

---

### Post by carusoswi on 2009-05-02
> **NeroWolf said:**
> It seems to me that FireFox has a built-in Java parser that is buggering-up LogMeIn for a good majority of would-be users that are giving the one-finger salute to big-ticket corporations.

OR

Alternatively, the Synaptic management of the Java6 install is not auto-registering the plugin to FireFox, and thus is not resolving the issue.  Could also be that you have to manually register said plugin...

In any case, I'm downloading Super Ubuntu 2008.10 right now to try it out.

-- Nero:lolflag:

I lost track of this thread and, having upgraded to 9.04 am curious if you ever got your logmein to work in Ubuntu 8.10 or if you have upgraded to 9.04 and whether you have been able to get it to work there.

Thanks.

Caruso

---

### Post by ftw on 2009-05-08
I didn't get firefox to work but opera worked...if that helps.

---

