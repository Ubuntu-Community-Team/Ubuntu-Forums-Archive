---
title: "Error when trying to reinstall Skype"
date: 2014-12-30
forum: New to Ubuntu
---

### Post by jan_jan_64 on 2014-12-30
Hi all. Im pretty newbie with linux so please bare with me. I  just upgraded to Ubuntu 14.10, and due to some issues I had been  having (long story) was cleaning up a few programs and removed Skype with the intention of simply just  reinstalling it, but now I am unable to do so. I downloaded the Ubuntu  12.04 multiarch version (I assume that this means its compatible with  various versions) and tried to open it via the software centre. I get an  error in the software centre that says 'Cannot install  'libpulse0:i386'.
 
I ran a few other commands that I found on other threads that seemed to have similar problems, so so far I have run:
 
sudo apt-get clean && sudo apt-get update
sudo apt-get upgrade --fix-missing
 
And  then tried the software centre again, but still the same problem.I  tried installing the package manually through the terminal (sudo apt-get  install libpulse0:i386) and got this result:
 
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libpulse0:i386 : Depends: libsndfile1:i386 (>= 1.0.20) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
 
Not really sure where to go from here :/ Any advice? Cheers!

---

### Post by jan_jan_64 on 2014-12-30
UPDATE
 
I ran the repair broken packages option from the  GRUB menu, and although it seemed to work for that package, I get the  same issue now with another. The error reads:
 
Cannot install 'libqtwebkit4:i386'
 
Running that in a 'sudo apt-get install' command returns:
 
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libqtwebkit4:i386 : Depends: libgl1-mesa-glx:i386 but it is not going to be installed or
                              libgl1:i386
                     Depends: libqt4-opengl:i386 (>= 4:4.5.3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
 
The end says there are broken packages. but I have already tried to use the repair option from the GRUB menu twice. Help?

---

### Post by plucky on 2014-12-30
> I downloaded the Ubuntu 12.04 multiarch version (I assume that this means its compatible with various versions) and tried to open it via the software centre. I get an error in the software centre that says 'Cannot install 'libpulse0:i386'.

Enable the "partner" repository in Software Sources and use that to install skype.

Good Luck

---

### Post by jan_jan_64 on 2014-12-30
I enabled the "partner"s in the sources but it didnt help. After doing so I ran an update and tried to install skype again, but i got an error saying package dependencies cannot be resolved. Specifically, 'skype: Depends: skype-bin but it is a virtual package'

I tried to use the terminal to get skype-bin, and it returned:

"Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype-bin:i386 : Depends: libqtwebkit4:i386 (>= 2.2~2011week36) but it is not going to be installed
                  Depends: libgl1-mesa-glx:i386 but it is not going to be installed
                  Recommends: libasound2-plugins:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages."

I have also just discovered that my VLC has disappeared and I get a similar error message when trying to download it again.

---

### Post by mc4man on 2014-12-30
run & post - 
```
apt-cache policy libgl1-mesa-glx libgl1-mesa-dri
```

---

### Post by jan_jan_64 on 2014-12-30
OK:

libgl1-mesa-glx:
  Installed: 10.5.0~git20141210.47aaabda-0ubuntu0ricotz~trusty
  Candidate: 10.5.0~git20141210.47aaabda-0ubuntu0ricotz~trusty
  Version table:
 *** 10.5.0~git20141210.47aaabda-0ubuntu0ricotz~trusty 0
        100 /var/lib/dpkg/status
     10.3.0-0ubuntu3 0
        500 [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) utopic/main amd64 Packages
libgl1-mesa-dri:
  Installed: 10.5.0~git20141210.47aaabda-0ubuntu0ricotz~trusty
  Candidate: 10.5.0~git20141210.47aaabda-0ubuntu0ricotz~trusty
  Version table:
 *** 10.5.0~git20141210.47aaabda-0ubuntu0ricotz~trusty 0
        100 /var/lib/dpkg/status
     10.3.0-0ubuntu3 0
        500 [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) utopic/main amd64 Packages

Thanks!

---

### Post by Bucky Ball on 2014-12-30
```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Report errors, but issue all those commands regardless of if you get any. Might tell us what's being held back and why. How did you install Skype in the first instance? Manually using a PPA? Remove or disable it, if so, and install Skype from Software Centre. There could be some sort of release conflict happening.

---

### Post by mc4man on 2014-12-30
> **jan_jan_64 said:**
> OK:

libgl1-mesa-glx:
  Installed: 10.5.0~git20141210.47aaabda-0ubuntu0ricotz~trusty
  Candidate: 10.5.0~git20141210.47aaabda-0ubuntu0ricotz~trusty
  Version table:
 *** 10.5.0~git20141210.47aaabda-0ubuntu0ricotz~trusty 0
        100 /var/lib/dpkg/status
     10.3.0-0ubuntu3 0
        500 [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) utopic/main amd64 Packages
libgl1-mesa-dri:
  Installed: 10.5.0~git20141210.47aaabda-0ubuntu0ricotz~trusty
  Candidate: 10.5.0~git20141210.47aaabda-0ubuntu0ricotz~trusty
  Version table:
 *** 10.5.0~git20141210.47aaabda-0ubuntu0ricotz~trusty 0
        100 /var/lib/dpkg/status
     10.3.0-0ubuntu3 0
        500 [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) utopic/main amd64 Packages

Thanks!
You are yet another user that has upgraded an install that was using xorg-edgers ppa without **first **using ppa-purge **before **the upgrade to a new Ubuntu release.
What you need to do is add back the ppa, update your sources, then do a dist-upgrade
At that point you can continue using the ppa or install ppa-purge & purge the ppa back to the current 14.10 packages

---

### Post by jan_jan_64 on 2014-12-31
@Bucky Ball: 

OK, I ran the commands. The first time I ran them  it said that some packages were being held, but the rest of the commands  ran no problem. I restarted, but still the same error in the software  centre. So I ran the commands again, and it returned just one error:

sudo apt-get update
W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/utopic-backports/universe/source/Sources](http://de.archive.ubuntu.com/ubuntu/dists/utopic-backports/universe/source/Sources)  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

I  restarted before getting a copy of the files that were held, my  apologies, but I know that they were all from a ppa. I was advised to  install the ppa when I was having problem getting my new graphics  drivers a week or so ago, but I thought i had removed, I have since upgraded and, as use**r mc4man **has said, this may be the main issue.

@mc4man I will try your suggestion now.[**[COLOR=#DD4814][B]**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=320715")
[**[COLOR=#C61919][B]**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=504316")

---

### Post by jan_jan_64 on 2014-12-31
So, I set up the ppa again and updated it. Good news is, attempts to download VLC no longer gave an error and now works - yay! Bad news - Skype still wont download.

Currently getting this error in the Software Centre:

Cannot install 'libpulse0:i386'

which is the error I was getting when I made the first post.

---

### Post by Mike_Walsh on 2014-12-31
Hello, jan_jan_64.

Mmm. I hate to say it, but you might be just as well off (if you can spare the time, that is!), to wipe your hard drive clean & do a completely fresh install from the ground up.

I'm not an expert by any means, but having been lurking around the forums for 6 months, before joining back in May, I've read any number of posts from folk who have found out that in-place upgrades (whether Linux, OR Windows) just don't seem to work as well as a re-install. Of course, a Linux re-install is a whole heap easier than an MS one (all those restarts, jeez..!); I can get a Linux install up-and-running, WITH all my favourite software, in about 3 hours, I've done it that many times...

As with anything like this, safeguard your data at ALL costs....whatever it takes. I've got stuff I've moved through successive systems for the past 25 years.

PPAs are a bit of a minefield when you're doing upgrades, from what I can see of it.....a real PITA. You MUST make sure that you disable them before you do anything, and then remember to re-enable them when you're good to go again. I ALWAYS do fresh installs; I haven't done a single in-place upgrade for over 30 years, regardless of what OS I've been running at the time. And with the in-between releases only receiving 9 months of support, as opposed to 5 years, well.....that's why I have every intention of sticking with the LTS releases.

Stabilty means a lot more to me than cutting-edge features, and the newest of everything.

Just sorry this isn't helping with your problem...!

Regards,

Mike. ;)

---

### Post by mc4man on 2014-12-31
run this & let's see what is avail., ect.
 ```
apt-cache policy libpulse0:i386 libpulse0
```

---

