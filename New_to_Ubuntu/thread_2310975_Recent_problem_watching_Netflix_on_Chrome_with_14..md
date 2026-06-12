---
title: "Recent problem watching Netflix on Chrome with 14.04"
date: 2016-01-23
forum: New to Ubuntu
---

### Post by mtds on 2016-01-23
For the last few months I've been streaming Netflix onto my laptop.  I'm running Ubuntu 14.04 LTS.  Firefox is my go-to browser, but I found I could only watch Netflix and Amazon movies if I installed Chrome, which I did, using Ubuntu's Software Center.  

Everything was fine until yesterday, January 22, when the automatic update feature of Ubuntu installed a new version of Chrome.  Now I can't watch movies from either Netflix or Amazon.  I get this error message: 

[I]We cannot find all the required components to play Netflix on this device.  Please visit chrome://components, locate the WidevineCdm component, and click the "Check for update" button.
  Error Code M7702-1003[/I]

There is no "Check for update" button at chrome://components.

I get a similar message from Amazon, except that it sends me to chrome://plugins.

My ideal solution would be to watch movies in Firefox, but I'll use Chrome if necessary.

Any help?  Thank you in advance for your efforts.

---

### Post by Vladlenin5000 on 2016-01-23
I have Chrome version [COLOR=#303942][FONT=Ubuntu]48.0.2564.82 and it works fine at least for Amazon. Are you sure you have Google Chrome and not Chromium? [/FONT][/COLOR]

---

### Post by mtds on 2016-01-23
> **Vladlenin5000 said:**
> I have Chrome version [COLOR=#303942][FONT=Ubuntu]48.0.2564.82 and it works fine at least for Amazon. Are you sure you have Google Chrome and not Chromium? [/FONT][/COLOR]

Thank you for your reply.  I just checked and I do have Google Chrome.  It is V[COLOR=#303942][FONT=Ubuntu]ersion 48.0.2564.82 as well.[/FONT][/COLOR]

---

### Post by monkeybrain20122 on 2016-01-24
[COLOR=#303942][FONT=Ubuntu]I have Chrome 48.0.2564.82 (64-bit), netflix works with no problem. Maybe your profile is somehow corrupt. To check, close Chrome, open the file browser to your home, press ctrl+h or choose [/FONT][/COLOR]show hidden file from menu, then open .config and look for the sub-folder google-chrome. Right click to rename it to something like google-chrome-bk. Now start Chrome and see if you still have any problem. To revert back to old profile, close chrome, delete the folder google-chrome in .config and rename goole-chrome-bk back to google-chrome.

---

### Post by mtds on 2016-01-24
> **monkeybrain20122 said:**
> [COLOR=#303942][FONT=Ubuntu]I have Chrome 48.0.2564.82 (64-bit), netflix works with no problem. Maybe your profile is somehow corrupt. To check, close Chrome, open the file browser to your home, press ctrl+h or choose [/FONT][/COLOR]show hidden file from menu, then open .config and look for the sub-folder google-chrome. Right click to rename it to something like google-chrome-bk. Now start Chrome and see if you still have any problem. To revert back to old profile, close chrome, delete the folder google-chrome in .config and rename goole-chrome-bk back to google-chrome.

First of all, thank you for your reply and you *very *clear directions.  I think that I learned a little just following them.  I tried it three times and everything went as you said. (When Chrome asked me to set up a profile I declined.)   However, I received the same error message each time.  Thanks again for trying to help me!

---

### Post by Ddamia on 2016-01-24
You are not the only one having this problem. I experienced the same today. Purging Chrome completely and re-installing meant Netflix worked. ONCE. When I closed the browser and re-opened it, I got the same error message again. I tried the same twice. I also tried creating a new browser profile. Nothing doing. 

Apparently, the only solution is reverting to the older version (47) of Chrome. This appears to work. They must have broken something with the update. Instructions on how to revert to the previous version can be found here: [http://askubuntu.com/questions/724879/chrome-on-ubuntu-no-longer-supports-netflix-latest-update-removed-widevine-comp?answertab=active#tab-top](http://askubuntu.com/questions/724879/chrome-on-ubuntu-no-longer-supports-netflix-latest-update-removed-widevine-comp?answertab=active#tab-top)

---

### Post by mtds on 2016-01-24
> **Ddamia said:**
> You are not the only one having this problem. I experienced the same today. Purging Chrome completely and re-installing meant Netflix worked. ONCE. When I closed the browser and re-opened it, I got the same error message again. I tried the same twice. I also tried creating a new browser profile. Nothing doing. 

Apparently, the only solution is reverting to the older version (47) of Chrome. This appears to work. They must have broken something with the update. Instructions on how to revert to the previous version can be found here: [http://askubuntu.com/questions/724879/chrome-on-ubuntu-no-longer-supports-netflix-latest-update-removed-widevine-comp?answertab=active#tab-top](http://askubuntu.com/questions/724879/chrome-on-ubuntu-no-longer-supports-netflix-latest-update-removed-widevine-comp?answertab=active#tab-top)

ALL RIGHT!!  That fixed the problem.  Thank you Ddamia and the Ubuntu community!

---

### Post by Ddamia on 2016-01-24
You're welcome. It's been driving me crazy all evening, so I can only imagine it was doing the same for you!

I just hope Chrome will fix the problem, because not being able to install updates will probably create security issues.

---

### Post by mörgæs on 2016-01-24
@mtds: Good, please mark the thread 'solved'.

---

### Post by mtds on 2016-01-24
Whoops, not quite solved yet.  In the link Ddamia provided, which detailed the successful fix for my problem with Chrome, there was also a command to "force apt to ignore Chrome in the future so it doesn't keep getting updated".  The command was "sudo apt-mark hold goggle-chrome-stable".  I've run that twice in terminal and twice Ubuntu's updating software has come back and changed Chrome back to the latest, not-working-for-me version.  Is there a way to shield the older, works-for-me version of Chrome from these automatic updates?

Again, thanks to all who have helped me so far and to anyone who can help me over this last obstacle.

Maybe this will be useful:

```
john@john-Satellite-C55-A:~$ sudo dpkg -i /var/cache/apt/archives/google-chrome-stable_47.0.2526.111-1_amd64.debdpkg: warning: downgrading google-chrome-stable from 48.0.2564.82-1 to 47.0.2526.111-1
(Reading database ... 997022 files and directories currently installed.)
Preparing to unpack .../google-chrome-stable_47.0.2526.111-1_amd64.deb ...
Unpacking google-chrome-stable (47.0.2526.111-1) over (48.0.2564.82-1) ...
Setting up google-chrome-stable (47.0.2526.111-1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
john@john-Satellite-C55-A:~$ sudo apt-mark hold goggle-chrome-stable
E: Unable to locate package goggle-chrome-stable
E: No packages found
john@john-Satellite-C55-A:~$ 
```

---

### Post by deadflowr on 2016-01-24
First off, I'm wondering if a VPN-setup is in play?
I ask because Netflix recently accounced plans to block VPN connections.
How they plan to do that is not open, so using widevine, somehow, is something to think about.


Second, and what I really wanted to post about was,
There is no need to apt-mark hold chrome.
You can simply disable the google repo.
Open Software and Updates go to other software and uncheck the google entries, then close and reload.

---

### Post by mtds on 2016-01-24
> **deadflowr said:**
> 
There is no need to apt-mark hold chrome.
You can simply disable the google repo.
Open Software and Updates go to other software and uncheck the google entries, then close and reload.

Thanks for the reply, deadflowr.  

I followed the instructions Ddamia provided and then did what you suggested.  At the moment Netflix and Amazon are both working, so I'm a happy guy.  I'm guessing that the acid test will be the next auto update alert.  Thanks for taking the time to help!

---

### Post by monkeybrain20122 on 2016-01-25
If you disable google's repo it won't upgrade, but it is not safe to use an outdated browser and a few months down the road Netflix may block you because your browser is outdated, so make sure you re-enable the google repo later may be in a month or so. I still cannot reproduce your problem. I am mainly running 15.04 and 15.10 but I have a 14.04 backup installation in my external drive, I will check when I have a chance. Maybe something peculiar to 14.04.

---

### Post by mtds on 2016-01-25
> **monkeybrain20122 said:**
> If you disable google's repo it won't upgrade, but it is not safe to use an outdated browser and a few months down the road Netflix may block you because your browser is outdated, so make sure you re-enable the google repo later may be in a month or so. I still cannot reproduce your problem. I am mainly running 15.04 and 15.10 but I have a 14.04 backup installation in my external drive, I will check when I have a chance. Maybe something peculiar to 14.04.

Thanks for looking into this problem and for the advice.  I'll do as you suggest and re-enable google repo in a month.  It is great to have a place to get some help and guidance.

---

### Post by Ddamia on 2016-01-25
> **monkeybrain20122 said:**
> If you disable google's repo it won't upgrade, but it is not safe to use an outdated browser and a few months down the road Netflix may block you because your browser is outdated, so make sure you re-enable the google repo later may be in a month or so. I still cannot reproduce your problem. I am mainly running 15.04 and 15.10 but I have a 14.04 backup installation in my external drive, I will check when I have a chance. Maybe something peculiar to 14.04.

I'm on 14.04 too. Just thought I'd specify. 
I hope someone -- or preferably Google -- sorts this problem out, because of course you can't stay on an older version of Chrome forever!

---

### Post by deadflowr on 2016-01-25
Note that an alternative thing to try would be to keep the repo enabled and install google-chrome-unstable.
To see if a newer version has a fix.
I somehow doubt it will.
But it is an option.

---

### Post by Ddamia on 2016-01-25
> **deadflowr said:**
> Note that an alternative thing to try would be to keep the repo enabled and install google-chrome-unstable.
To see if a newer version has a fix.
I somehow doubt it will.
But it is an option.

I suspect it might be too soon, no?

---

### Post by deadflowr on 2016-01-25
> **Ddamia said:**
> I suspect it might be too soon, no?
Never too soon if running unstable.;)

But in that scenario, you would want to set the apt-mark hold function for the stable version.
Basically put the hold on chrome-stable, first, then install unstable.
Do this so that the unstable version keeps updating.
But the stable version will stay as is.

Unstable gets updates a lot more frequently.

There is also this:
[https://productforums.google.com/forum/#!topic/chrome/CvRAbQgZOtw](https://productforums.google.com/forum/#!topic/chrome/CvRAbQgZOtw)

---

### Post by Ddamia on 2016-01-26
I've disabled the chome-stable repo in the update manager, as you suggested earlier. So, presumably, that will hold the stable version.

Looking at that link... This command is to run chrome-unstable from terminal? ***killall -s 15 chrome; killall -s 15 chrome; google-chrome-unstable***
What do the killall commands do, and why are they needed? 
(excuse ignorance! :-) )

---

### Post by deadflowr on 2016-01-26
Chrome's been known to have process or two(or ten) running even when closed.

---

### Post by Ddamia on 2016-01-29
Ah. I am enlightened. Thank you.

---

### Post by 71-shane on 2016-02-09
I came here looking for ALMOST the same thing. I can't watch Netflix on Chrome 48, IF I launch it from the launcher. I wanted to know what the difference was between launching from the launcher and launching Chrome from the command line, because if I launch from terminal, I can watch Netflix no problem. But if I launch from dash, it gives me an error saying WidevineCdm is not working. 

So, maybe its a workaround for you to launch chrome from the Terminal? It works for me. 

I'd like to know though, how can I make it so that launching from the launcher works also? 

Thanks.

---

### Post by mtds on 2016-03-01
I'm the OP, and an unskilled Ubuntu fan/user.  I'm still using the oldest version of Chrome that allowed me to view Netflix, but I'm concerned about continuing with an un-updated browser.  Does anyone know whether or not Chrome has been fixed?  If so, how do I get back to the state where Chrome will be part of my automatic updates?  Thank you!

---

### Post by deadflowr on 2016-03-01
> **mtds said:**
> I'm the OP, and an unskilled Ubuntu fan/user.  I'm still using the oldest version of Chrome that allowed me to view Netflix, but I'm concerned about continuing with an un-updated browser.  Does anyone know whether or not Chrome has been fixed?  If so, how do I get back to the state where Chrome will be part of my automatic updates?  Thank you!
To get chrome back into the updates depends upon what method of disabling those updates you used.

Did you apt-mark hold the chrome package or disable the google repositories?
(or did you uninstall google-chrome-stable entirely?)

---

### Post by mtds on 2016-03-02
> **deadflowr said:**
> To get chrome back into the updates depends upon what method of disabling those updates you used.

Did you apt-mark hold the chrome package or disable the google repositories?
(or did you uninstall google-chrome-stable entirely?)

Originally I disabled the updates by going to "Software & Updates", then "Other Software", and then un-selected "http://dl.google.com etc".

Just now I allowed updates.  Clicked/selected "http://dl.google.com etc", pressed "Reload", waited, allowed the updates, and checked to see if Netflix would work.  It didn't work and it gave me the error message of several weeks ago.  Soooo, I have answered my own question; Google has not fixed this Chrome/Ubuntu/Netflix problem.

Now (can you hear me gnashing my teeth?) when I run the original commands at the link ([http://askubuntu.com/questions/72487...active#tab-top]("http://askubuntu.com/questions/724879/chrome-on-ubuntu-no-longer-supports-netflix-latest-update-removed-widevine-comp?answertab=active#tab-top")) graciously provided by Ddamia on January 24 and which worked so well for me at that time, it no longer works.  Woe is me, woe is me.  Should I have stayed with Windows Vista?  Am I just too stupid to be trusted with a computer?  (Be kind...)

Any help would be appreciated!

---

### Post by mtds on 2016-03-03
> **mtds said:**
> Any help would be appreciated!

Eventually I went to Google and downloaded and installed Chrome version 49.  It appears to be working fine with Netflix.  So version 47 worked, version 48 did not, and 49 does.  I'm sure happy that I don't have to go back to Windows Vista!

---

### Post by mörgæs on 2016-03-03
Good, please use Thread Tools for marking a thread solved.

---

