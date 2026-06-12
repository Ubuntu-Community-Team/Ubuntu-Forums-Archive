---
title: "HOWTO Install ClamAV Antivirus on Any Ubuntu Version"
date: 2006-12-13
forum: Outdated Tutorials &amp; Tips
---

### Post by SuperMike on 2006-12-13
How To Install and Configure ClamAV on All Ubuntu Versions

(Tested on Breezy and Dapper)

This tutorial will show you how to install and configure ClamAV and set it up so that it has the least occurrences of false-positives that might lead you to over-react when you think you might have a potential virus or rootkit.

1. Do you see your menus? Keep clicking on them until you find one that says something like Terminal.

2. A white or black window will usually open. That's your terminal. If you are old enough to remember the days of MSDOS command prompt, it's sort of like that. The terminal gives you access to the Linux shell, which is a command environment where you type short commands followed by strange characters and phrases like --this and --that so that you control or configure your operating system, or run something. In the following example, I'm sure there's the GUI way to do this, but I think it's faster for me to show you the command-line way to do this.

3. Type this, and when you are prompted for a password, use the one you used to login to your workstation.
Code:

sudo apt-get update sudo apt-get install clamav

If you get an error, then it's perhaps that I'm mistaken and you might need to enable the Universe option (only temporarily, of course) in something called the /etc/apt/sources.list file. These usually exist and are commented out with the # character as the first character of that line. You basically take an editor and edit this file. It's protected so that only a certain user, root, can access it, so you would edit it with something like:

```
sudo nano /etc/apt/sources.list
```

...and then you would save this file -- but only do that if you received an error on the apt-get commands I mentioned above.

Now, if you were in a situation where you had to edit the sources.list file, then go back and repeat this step # 3 all over again with the sudo apt-get statements.

4. Okay, at this point, the apt-get command may tell you it's going to install extra stuff like libclamav1 and freshclam. This is good news because libclamav is a driver to make the clamav package work, and freshclam is the tool that clamav needs so that it can update its virus signatures. So if it prompts you a Y/N, choose Y and press enter.

5. If you had to turn on the Universe option in order to install clamav, then it's probably not a good idea to leave that option turned on. Ubuntu knows this and that's why they turn it off by default. Universe is the option that's community-supported instead of being Ubuntu-tested. More than likely that means it's still going to work, but sometimes the Universe option, if you were to follow it with a risky command like...

```
apt-get upgrade
```

...might bring your whole computer into a kind of unstable nature. That's why I avoid leaving my computer in Universe mode and only use it temporarily to install stuff when I can't find it otherwise.

6. Now, when clamav is installed, I noticed that it doesn't run automatically. Sorry about that, but they wanted to make certain when you installed it that you told it exactly what you wanted it to do. Unlike other virus scanners that only have a few configurable options, clamav has a ton of different options you can choose from and it can't assume which one is going to suit you best.

7. Now, if you're like me, you realize that Linux is a sensitive instrument, unlike Windows. You can't just have your virus scanner catch what it thinks are bad files and start quarantining them. And why? Because it's risky to the operating system and could crash the whole thing. On Windows, however, they have a thing called Windows File Protection, and, as well, the virus scan authors work closely with Microsoft (and pay for that in cold hard cash) so that they don't quarantine files such that the computer would freeze up (usually). Therefore, I just have Clamav tell me if it finds a virus and I use forums like this one on the web (and some close Linux gurus I email occasionally) help me determine if the stuff is a false positive or a true virus. If it's a true virus, then I'm from the camp that would rather backup, test backup, format, reinstall, restore data files backup than to try to do "virus surgery" to remove the virus. This is because sometimes when a virus scanner finds the virus, if it's not a false positive, then it's often just found a symptom of the virus and not always the real virus itself. In other words, I don't believe in virus surgery being that affective in eradicating the virus.

8. Therefore, we now need to configure your scanner. But first, wouldn't you like your virus scanner to speak to you over your computer speakers and tell you it found a potential virus? I like that, so I use a program called 'festival'. You'll want to install it just like you did in step 3, and you may or may not need the universe option, but the command is:

```
sudo apt-get install festival
```

9. After you install festival, if you had to turn on the Universe option in your /etc/apt/sources.list file, please consider turning that back off again by commenting it out with # as the first character on that line and doing 'sudo apt-get update' once done.

10. Now test festival like so:

```
echo 'Hello, Computer User' | festival --tts
```

...Did you hear it say something to you? If not, then turn up your speakers or look at getting your sound working on your PC.

11. Now, let's configure ClamAV. There are two things you'll need. These are two files in the /usr/bin directory, which are:

```
/usr/bin/clamscan /usr/bin/freshclam
```

...you can use the 'ls' command, like:

```
ls /usr/bin/*clam*
```

...to see if those files are there.

12. Now, we need to edit a file called /etc/crontab. To edit it, we do:

```
sudo nano /etc/crontab
```

...and then add these lines at the bottom:

```
00 1 * * * root /usr/bin/freshclam 
# 
30 3 * * * root /usr/bin/clamscan --quiet -r -i --no-mail --no-ole2 --no-pe --no-html --max-recursion=10 --log=/var/log/clamav/clamav.log --exclude-dir=/proc|/sys|/dev|/mnt|/media / 
# 
30 7 * * * root tail /var/log/clamav/clamav.log | grep -i infected | grep -iv ': 0' && echo 'Potential Virus Found' | festival --tts
```

First, it updates your virus scanner files at 1:00am.

This then kicks off the virus scanner at 3:30am in the morning (because it's likely going to need to run a long time), will exclude some common folders where false positives are likely, and will dump the results in a logfile called /var/log/clamav/clamav.log.

It then follows at 7:30am by checking this logfile, seeing if it contains the word "infected", and saying the phrase 'Potential Virus Found" to you if it finds it. I assume you're up by then, checking your email, and if not you can change the time to a more reliable time when you're sitting there. It's not that there is a virus that it found, but there might be one and it requires further investigation, communication with forums like this, etc.

So, anyway, save this crontab file and it's almost ready to go.

13. Now it's a good time to manually run these two tools. Start by typing:

```
sudo freshclam --verbose
```

...and when you get errors about needing to use the latest version of ClamAV, I usually ignore those because their not that critical to me (in my opinion). Besides, I uninstall and reinstall clamav every so many months to ensure I'm on the latest version.

14. Now run the next tool and be prepared to walk away for a few hours. It will slow your system down a good bit.

```
sudo clamscan --quiet -r -i --no-mail --no-ole2 --no-pe --no-html --max-recursion=10 --log=/var/log/clamav/clamav.log --exclude-dir=/proc|/sys|/dev|/mnt|/media /
```

...oh, and yes, there's a slash on the end that is preceded by spaces --> that's the directory where you want to start scanning from, and in this case that's the root directory.

15. Now when the clamscan command finishes, you need to check the output by doing:

```
sudo cat /var/log/clamav/clamav.log
```

Do you see something like "Infected" followed by a number? If so, then you may or may not have a potential virus and it requires further evaluation with technical people on the web like here, and with good technical friends who know Linux. It will likely happen so rarely for you that you won't need to do that very often.

16. Okay, you don't need to leave the Terminal window open anymore, but you can use it to 'cat' out the clamav.log file occasionally to see how things are going in the next few days.


Commentary:

* Sure, it would be nice to have a GUI front end for all this when you're a newbie, but realize that (a) ClamAV is free, and (b) Someone has to build it and they're taking volunteers, and (c) Linux with a stable GUI (like KDE or GNOME) is still a relatively new operating system on the computer operating system timeline when you compare it to the lifespan of Windows. It's going to take awhile before you see programmers having the time to build this. They probably already are.

* Since the community supports ClamAV, it's good and bad as far as being reliable. It's good in that you'll often find it updated most of the time with newer virus signatures more frequently than you would a commercial package. It's bad in that it has less bureaucracy, and less at stake (because it has no paying customers), and therefore you might end up with occasional false positives because it is not reviewed as meticulously as other commercial packages. It's a tossup -- some days it might beat something like a Kapersky Anti-Virus, and other days it may not. However, since most people like it as the de-facto virus scanner on Linux, I stick with it and trust it, and now will cautiously consider the false positive thing more closely. I've also changed my scan script such that it doesn't look in directories where false positives are more prone.

---

### Post by dmizer on 2007-01-12
thank you for this ... i at least learned a bit about chrontab

but i have several problems with this.  you give the command full of preset options, including disabling scanning of microsoft office documents, and portable executables.  my thinking is that this is of course a very bad idea if you're target is a dedicated samba server hosing shares to an office full of windows computers.

my first scan with your settings scanned a total of 110 files, on a share which contains 25 gig of office documents and portable executables, and the scan took less than 2 minutes.  were it not for the protracted difference in the time i expected this scan to take, i might never have known to look more deeply at the options.

you mentioned that you changed the script to disable scanning in directories where false positives are prone ... does that include some of the disabled functions you've set up?  or in other words, is there a valid reason for turning off ole and pe?

---

### Post by SuperMike on 2007-01-12
You make a good point. Yes, my doc does not reflect scanning in the case of Linux being used to host a Samba share. To enable that, remove these flags:

--no-ole2 --no-pe

...from the clamscan line.

---

### Post by Athanasius on 2007-01-12
Automatix has a GUI for Clamav

---

### Post by re2st on 2007-08-01
Hello,

Thanks for the great guide.

I have one problem though, when I do "sudo freshclam -v", aside from the message about the outdated installation, I also get this message: "LibClamAV Error: Database Directory: /var/lib/clamav/ not locked"

What is wrong here? How can i fix it?

Thanks!

---

### Post by mempman on 2009-01-25
Thanks Bud.  I wonder why they (forum moderators) took off the "Thank Post" option.

---

### Post by geezerone on 2009-01-25
> **mempman said:**
> ...  I wonder why they (forum moderators) took off the "Thank Post" option.

[http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714)

---

