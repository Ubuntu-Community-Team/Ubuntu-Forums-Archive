---
title: "Ubuntu on Toshiba NB550D Please Help"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by Elza on 2011-09-30
I'm sorry for my english.

I'm completely new to Ubuntu software, so please be kind with me and understand my mistakes in description of my problem.
I purchased Toshiba NB550D with Win 7 starter, because it wasn't working fast enough, I decided to switch to Ubuntu 11.04, as my boyfriend recommended it to me.

But unfortunatelly some things don't work properly now:
-Most of the Fn Keys don't work,
-Bleutooth doesn't work,
-I can't switch off wifi and just enable it when is needed. It's all the time on. (the light of wifi is on, even if I don't want to use it) which I think, uses a lot of extra battery. When I was working on Win7 - battery last even for 8 hours, with Ubuntu maximum 4 hours, how can I change (improve) that?
- fan is working loud and all the time, on Win7 was very quiet. Can I somehow change it? Maybe, this uses a lot of battery as well?
- using skype, speakers are not working properly, not clear sound

I spent already 2 days, trying to fix it, but no success :( Long hours on forums. Please Help me.

---

### Post by StarZtorm on 2011-09-30
Hi, from what i can see other people have had some or no problems installing Ubuntu on this computer. have you installed it alongside windows? did you install the 32 bit version of the system? Have you tried formatting and installing Ubuntu again?

---

### Post by technosysind on 2011-09-30
I hope you installed as dual boot with windows. 
Concerning the Bluetooth - I think the NB550D uses an Atheros combo-card with both WLAN and Bluetooth. Am I right?
If so, there seems to be general problem getting the BT to work properly, wireless works well though.
I have filed a bug to Fedora Bugzilla concerning this issue on an R830 - uses the same module I think.
Link: [https://bugzilla.redhat.com/show_bug.cgi?id=734369](https://bugzilla.redhat.com/show_bug.cgi?id=734369)

Concerning the mic -  basics first:


[LIST]
[*]did you check the sound input settings and turn up the recording level?
[*]did you try an external mic? You can for testing purposes use a  headset / earphones as a MIC since they work exactly the same. You may  have to shout to get any input however [IMG]http://forums.computers.toshiba-europe.com/forums/images/emoticons/happy.gif[/IMG]
[/LIST]
 
If the external MIC works you may want to try booting the unit on 11.04 or maybe even any pre-release of 11.10.
This to see if the MIC-issue is resolved.
If so, I believe some googling will supply you with a solution!

---

