---
title: "Upgrade manager: Looking for history of upgrades"
date: 2012-03-06
forum: New to Ubuntu
---

### Post by 2muchcoffeeman on 2012-03-06
Ubuntu 11.10
Wubi installed within Win XP Pro
Dell Latitude D630

The Upgrade Manager found a few updates and I instructed it to install them. I don't usually spend any time studying all the updates before hitting the "install" button, mostly because I'm not enough of a Ubuntu expert to understand them anyway. So I usually just wave them all in.

During this particular update, I noticed the manager was installing a package containing a few words that caught my eye: "Chrome . . . ubuntu . . . stability . . ." or somesuch.

Before I could blink, the entire update was over and all the details about it vanished from the manager window.

What I want to do is find a log somewhere that contains the "description of update" details that usually are displayed in the Update Manager *before* installation begins. Once an update is complete, however, the manager no longer displays those details. I'm hoping those details, along with details of all previous updates since the 11.10 release, are stored somewhere for later reference. Where does one find them?

Reason: I had been having troubles with Chrome. After extended periods of use, the entire system would freeze, becoming unresponsive to any keyboard or mouse commands. Flash would continually crash, too. So, I abandoned Chrome for Firefox, where stability has been better. But, if this most recent update has fixed the stability/Flash problems with Chrome, I would like to resume the use of Chrome. I'd like to find the update details to see if the update did, indeed, address the Chrome problems, and how.

Thank you.

---

### Post by Script Warlock on 2012-03-06
have you tried to peek inside the ubuntu software center > history
in the terminal type "apt-get changelog apps-name"

---

### Post by 2muchcoffeeman on 2012-03-06
> **Script Warlock said:**
> have you tried to peek inside the ubuntu software center > history

Actually, no, I hadn't tried that, because it didn't occur to me to do so. I didn't make the connection that once the update manager is done making the update, the content of that update passes over to the realm of *installed software*, which is cataloged by the Software Center. Makes sense, but the connection didn't come naturally to me. Thanks for the insight.

And, yes, the update is logged in the Software Center. This is the one I wanted to find:

[INDENT]google-chrome-stable (17.0.963.56-r121963, 17.0.963.65-r124586)[/INDENT] 

That's cool, and I'm glad I found it. But what I really need are the *details* about the update. What does it do? What bug is it meant to fix? Does it address the problems I was having with Chrome? The Software Center does not provide any of that information.

And, now that I look at the log in the Software Center, I also want to learn about this update, which was part of the package of updates I just installed:

[INDENT]adobe-flashplugin (11.1.102.62.0oneiric1, 11.1.102.630oneiric1)[/INDENT]

So, I'm still on the hunt, but I'm a step closer thanks to your response. Thank you.


> in the terminal type "apt-get changelog apps-name"

I tried this in the terminal, and this was the result:

[INDENT]E: unable to locate package apps-name[/indent]

---

### Post by oldfred on 2012-03-06
Did not work for me, but apps-name should be the name of the app you are interested in.

This did work for me for python3.

aptitude changelog python3

[http://lglinux.blogspot.com/2008/02/apt-get-changelog.html](http://lglinux.blogspot.com/2008/02/apt-get-changelog.html)

---

### Post by 2muchcoffeeman on 2012-03-06
:redface: okay, I took the command too literally. Instead of typing[INDENT]apt-get changelog apps-name
[/INDENT]I should have entered[INDENT]apt-get changelog google-chrome-stable
[/INDENT]See how basic we newbies are?

Anyway, when I entered the command correctly, this is the result:[INDENT]Err Changelog for google-chrome-stable ([http://changelogs.ubuntu.com/changelogs/pool/main/g/google-chrome-stable/google-chrome-stable_17.0.963.65-r124586/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/g/google-chrome-stable/google-chrome-stable_17.0.963.65-r124586/changelog))
  404  Not Found
Err Changelog for google-chrome-stable ([http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_17.0.963.65-r124586.changelog](http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_17.0.963.65-r124586.changelog))
  404  Not Found [IP: 74.125.224.97 80]
E: changelog for this version is not (yet) available; try [https://launchpad.net/ubuntu/+source/google-chrome-stable/+changelog](https://launchpad.net/ubuntu/+source/google-chrome-stable/+changelog)
[/INDENT]Hm. Looks like there's no documentation anywhere about this update. Yet I know it must exist somewhere. . . unless Ubuntu allows undocumented updates to be released, which I doubt.

---

### Post by oldfred on 2012-03-06
I am not sure but I think it is looking for the next update not the history of the updates. You may just have to look for the history in Ubuntu on line.

[http://www.ubuntuupdates.org/package/google_chrome/stable/main/base/google-chrome-unstable](http://www.ubuntuupdates.org/package/google_chrome/stable/main/base/google-chrome-unstable)

---

### Post by 2muchcoffeeman on 2012-03-06
Yes, thank you, I believe that, actually, the appropriate URL would be 

[http://www.ubuntuupdates.org/google-chrome-stable](http://www.ubuntuupdates.org/google-chrome-stable)

. . . but in any case, there's not much information to be found at that page. Nothing to explain what the update does.

FWIW: After installing the updates, I fired up Chrome to see if performance would be improved and, not too long into my session, ran into the same old problems: The Flash plug-in would crash, and the entire system (not Chrome exclusively) would freeze up -- meaning that the hard drive would enter a near-continuously active state (as indicated by the constantly illuminated small light on the computer that signifies the hard drive). System responsiveness would drop to near zero. Now that I've closed Chrome and have resumed using FF, the issue has stopped. I guess I'm still searching for a solution.

---

### Post by Script Warlock on 2012-03-06
if chrome is the problem have you tried uninstall and reinstalling chrome?

---

