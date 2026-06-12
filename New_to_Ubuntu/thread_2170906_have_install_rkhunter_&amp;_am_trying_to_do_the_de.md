---
title: "have install rkhunter &amp; am trying to do the debug"
date: 2013-08-28
forum: New to Ubuntu
---

### Post by Kojak Peg on 2013-08-28
Hi Everyone
I've installed rkhunter and have been reading the debug how to, on ubuntu.com ([https://help.ubuntu.com/community/RKhunter](https://help.ubuntu.com/community/RKhunter)), but being a novice I'm having trouble understanding even the most basic instructions on there. 

For example:
Underneath [COLOR=#333333][FONT=UbuntuMono]sudo apt-get install rkhunter[/FONT][/COLOR] it says, "[COLOR=#333333][FONT=Ubuntu]Do no forget to set rkhunter in sysconfig to run the --propupd every time new software is installed", but how do I do that?[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu] 
Then underneath  [/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono]sudo rkhunter --propupd[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]   in part 1) it goes on to says, "[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]add the line [/FONT][/COLOR]**APT_AUTOGEN="yes"**[COLOR=#333333][FONT=Ubuntu] to [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]/etc/default/rkhunter[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] (this gets read by [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]/etc/apt/apt.conf.d/90rkhunter[/FONT][/COLOR][FONT=Ubuntu, Ubuntu Beta, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][COLOR=#333333])", how do I do that.[/COLOR][/FONT]

[FONT=Ubuntu, Ubuntu Beta, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][COLOR=#333333]Now, I'm sure the linux user who wrote those instructions thought that they were all pretty straight forward, self explanatory notes that didn't require any further explanation.  And I'm sure you're all rolling your eye's and slapping your foreheads at newbie's ignorance, but I just don't understand the command line well enough to know how to carry out those instructions. So if someone could please explain it to me as if talking to a small infant., you know step by step, 1 2 3, that sort of thing.

Thanks     [/COLOR][/FONT]

---

### Post by 3rdalbum on 2013-08-28
It sounds like you are trying to make things more difficult for yourself.

If you stick to software from the Ubuntu repositories or reputable third party PPAs, you don't need to set up any automatic rkhunter scans, because they will not contain malicious software. If you aren't running any server software, you wont get rootkits anyway... and if you were running servers you would most probably understand those instructions. Not that you would need rkhunter to run every time you install software anyway, so you can periodically run rkhunter manually.

This isn't Windows XP where you can get a virus just by connecting to the internet, and every second program is a trojan. This is Ubuntu where the software is trustworthy and secure.

---

### Post by Kojak Peg on 2013-08-28
Yeah probably, but I like to make doubley sure there aren't and malicious programs on my system. So I've trying out all the different programs available. It also gives me an opportunity to try and learn the command line, because most of the time my computer is a glorified web browser. So even though I've been using linux exclusively now for the past few months and I'm comfortable navigating around the GUI I'm still completely lost when it comes to the terminal. Other than copying and pasting commands for webpages 

As for software I only use the Ubuntu repository, but I'm still weary about potential viruses and malware that may attach themselves to my system as I surf the web. I know the old line about linux being secure and it's probably a throw back to my windows days, but I do like to check every now and then just to be sure

---

