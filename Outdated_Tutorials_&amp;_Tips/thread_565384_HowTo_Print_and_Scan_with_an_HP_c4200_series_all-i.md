---
title: "HowTo: Print and Scan with an HP c4200 series all-in-one in Feisty"
date: 2007-10-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Capslock118 on 2007-10-02
Hello.

First off I would like to say you might want to try this link first:
[http://ubuntuisms.com/main/?p=31]("http://ubuntuisms.com/main/?p=31")
My how-to here is strongly based on the how-to you will find at the just mentioned link so real credit goes to Derrick from ubuntuisms.com.

Derrick, who created that how-to, had the right idea, it just didn't work for me; I was able to scan but printing was an issue.

Well I was able to fix it and if anything this thread is for my own future reference.

First, you need the hplip program. Do no use the hplip that is in the package management, it is out of date. At the same time I was not successful installing the 2.7.9 version; so use the 2.7.7.tar.gz located at source forge 
[here]("http://sourceforge.net/project/downloading.php?group_id=149981&use_mirror=superb-west&filename=hplip-2.7.7.tar.gz&15710402")

Now extract the files, I do not think it matters where but I put it in my home folder.

Now go to your terminal if you have not already.

```
cd hplip-2.7.7
```

Then you want to configure:
```
 .configure
```

Then make and install:
```
 make && make install 
```

now to run some install scripts. This following line will end up with asking you a few questions. I personally just went the default route so I would recommend you do the same unless you know what you are doing:

```
 ./hplip-install 
```

After the questions are over it will ask you to restart; I like saying no at this point and then close all of my applications and restart myself....

Now that your computer is rebooted you will need to run the hp setup software.

```
 sudo hp-setup 
```

As long as your printer is on all you essentially need to do is hit the next button until everything installs.

Print a test page to make sure it works then scan it with xSane image scanner.
All should be working properly

note that the only time I used sudo was for the very last step!

---

