---
title: "Remote Desktop  Win XP Home --&gt; Vista HP"
date: 2007-05-11
forum: Other OS Talk
---

### Post by RealG187 on 2007-05-11
I have my Vista machine and I cannot use remote desktop to control it from upstairs like I used to with my old P3, I can browse files but that's it. I cant go either way, but before I couldn't go from downstairs to up, but now I cannot go either way, I notice the tab in system setting looks different, but under advanced remote desktop is checked of!

System Properites-->  Remote Tab--> Allow Remote Assistance Invitations to be sent from this computer is checked off [this isnt remote desktop and shouldnt affect it, but I thought I would bring it up.

Below Remote Assistance is an advance tab "Allow this computer to be controlled remotely" is checked and set to 30 days.


Whats wierd is my Vista machine and the upstairs [xp]look diffferent in remote tabs than my P3, but the thing is I never ran Windows Update on P3 since its old and cannot handle XP as it is, and the upstairs one and Vista machine all updated all the time!

---

### Post by RealG187 on 2007-05-11
Please help! Please I dunno what to do, did I enable it wrong?

---

### Post by feravolo on 2007-05-14
You may want to try a windows version of VNC (vino), i downloaded a free version to access ubuntu from a windows 2000 machine and it also included both a client and  a server so I could also access the Windows system using VNC instead of Remote Desktop Protocol (RDP).

I believe the one that I downloaded is called "real vnc", there is also one called "tight VNC". All you should need to do is google "free VNC for windows".

---

### Post by RealG187 on 2007-05-15
So install server on laptop and client upstairs?

Whats wierd is dat in the Thign for Anytime upgrade it outlines features of Vista home premium and is doesnt say it has remote desktop but in the start menu it is there! Unless if thats only to run as a client and not to allow to be controled!


Here is what the screeshot in XP Pro looks like, I will post the XP Home and Vista ones when I get on thise machines [Laptop is burning DVD]..

[IMG]http://img525.imageshack.us/img525/5786/xpprods1.jpg[/IMG]

---

### Post by RealG187 on 2007-05-16
[img]http://img219.imageshack.us/img219/9382/vistahpnordcly1.jpg[/img]

Here is what it looks like on the Vista Machine I wanna use as the host!

---

### Post by Prometheus.172214 on 2007-05-17
Due to the security restrictions of Windows Vista, which uses a UAC based user profile, Windows XP Home Eidtion cannot by default connect to a Vista system. There is however a tweak to get this working, but unfodtunately (I know that ugly look you are giving me) I don't remember the hack. If you have a system made a PC Maker and not assembled, you can call the tech support guys there to check for the hack. Off course the simple solution is use the Windows version of VNC.
Also, edit your firewall rules, based on IP address. I am suspecting you have a router so set static IPs on your systems and use the right firewall settings. In the Manage Network Connections option in Vista, make sure that your Netwrok Type is set to Private and all other features are enabled.

---

### Post by RealG187 on 2007-05-17
I just went from my Vista to my old XP Pro machine, I dont think home Premium lets you host.

Are there any ohter apps VNC doesnt work either...

---

### Post by RealG187 on 2007-11-04
Upgraded to Vista ultimate and it works from XP and Ubutnu ([Despite screen res problem]("http://ubuntuforums.org/showthread.php?p=3704850#post3704850")) And no Aero or 3D Window flip.

But [I cant control Ubuntu from Vista (probably not XP either, havent tried!)]("http://ubuntuforums.org/showthread.php?p=3704850#post3704850")

---

