---
title: "How to get rid of/permanently block a neighbor who is a cracker/&quot;hacker?&quot;"
date: 2022-05-09
forum: New to Ubuntu
---

### Post by 1971rudrani on 2022-05-09
Namaste' everyone,

I hope you all had a most excellent Mother's Day with really nice weather and cute critters running around outside.

I have an HP Stream which I just installed Ubuntu Budgie on yesterday.  I have a parasite permanently residing and lurking on it who happens to be a guy who lives in the same building as I do.  He apparently has some killer cracking/"hacking" skills and won't let up no matter how I have tried to block the usernames he's used.  I have a suspicion he has some sort of backdoor app or something that lets him sneak in when I'm asleep or afk eating in the dining room or something.

I have tried installing different flavours of Linux to see if that wouldn't help; it didn't.  I originally had Linux Mint, but also tried Zorin OS, and then this one that I'm using now.

I tried using the following command to see what he was up to (it worked but it still didn't get rid of him obviously):
  	 	 	 	  sudo less /var/log/auth.log  The most recent output of this command:

)
May  9 13:46:35 HP-Stream-Laptop-14-cb1xxx systemd-logind[577]: New session c2 of user rudrani1971.
May  9 13:46:35 HP-Stream-Laptop-14-cb1xxx systemd: pam_unix(systemd-user:session): session opened for user rudrani1971(uid=1000) by (uid=0)
May  9 13:46:35 HP-Stream-Laptop-14-cb1xxx lightdm: gkr-pam: gnome-keyring-daemon started properly and unlocked keyring
May  9 13:46:41 HP-Stream-Laptop-14-cb1xxx polkitd(authority=local): Registered Authentication Agent for unix-session:c2 (system bus name :1.79 [budgie-polkit-dialog], object path /org/freedesktop/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
May  9 14:01:29 HP-Stream-Laptop-14-cb1xxx lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm(uid=115) by (uid=0)
May  9 14:01:29 HP-Stream-Laptop-14-cb1xxx systemd-logind[577]: New session c3 of user lightdm.
May  9 14:01:29 HP-Stream-Laptop-14-cb1xxx systemd: pam_unix(systemd-user:session): session opened for user lightdm(uid=115) by (uid=0)
May  9 14:01:29 HP-Stream-Laptop-14-cb1xxx lightdm: gkr-pam: gnome-keyring-daemon started properly
May  9 14:01:30 HP-Stream-Laptop-14-cb1xxx lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "rudrani1971"
May  9 14:08:58 HP-Stream-Laptop-14-cb1xxx lightdm: gkr-pam: unable to locate daemon control file
May  9 14:08:58 HP-Stream-Laptop-14-cb1xxx lightdm: gkr-pam: stashed password to try later in open session
May  9 14:08:58 HP-Stream-Laptop-14-cb1xxx lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
May  9 14:08:58 HP-Stream-Laptop-14-cb1xxx systemd-logind[577]: Removed session c3.
May  9 14:10:58 HP-Stream-Laptop-14-cb1xxx PackageKit: uid 1000 is trying to obtain org.freedesktop.packagekit.package-install auth (only_trusted:1)
May  9 14:11:07 HP-Stream-Laptop-14-cb1xxx polkitd(authority=local): Operator of unix-session:c2 successfully authenticated as unix-user:rudrani1971 to gain TEMPORARY authorization for action org.freedesktop.packagekit.package-install for system-bus-name::1.121 [/usr/bin/gnome-software --gapplication-service] (owned by unix-user:rudrani1971)
May  9 14:11:07 HP-Stream-Laptop-14-cb1xxx PackageKit: uid 1000 obtained auth for org.freedesktop.packagekit.package-install
May  9 14:13:20 HP-Stream-Laptop-14-cb1xxx sudo: rudrani1971 : TTY=pts/0 ; PWD=/home/rudrani1971 ; USER=root ; COMMAND=/usr/bin/less /var/log/auth.log
May  9 14:13:20 HP-Stream-Laptop-14-cb1xxx sudo: pam_unix(sudo:session): session opened for user root(uid=0) by (uid=1000)
~
(END)

He (the cracker/"hacker") is the username lightdm.  I'm rudrani1971.  I'm running Ubuntu Budgie 22.04.

He keeps using something called "pam" which I'm working on figuring out, to break into my computer and rummage around; Gods only know what the hell he's doing.

Anything you folks can do to help me would be greatly appreciated.  If there is something I have neglected to include in my information, please let me know and I'll see what I can do to supply it.

Thank you all for taking the time to read all this, and I look forward to your advice.

---

### Post by GhX6GZMB on 2022-05-09
No one is sniffing on your machine."Lightdm" is the display manager used when logging in. "Pam" is the password manager.
Please throw your tin-foil hat away.

---

### Post by grahammechanical on 2022-05-10
If you need proof.

[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

[https://en.wikipedia.org/wiki/Linux_PAM](https://en.wikipedia.org/wiki/Linux_PAM)

There are three areas that offer opportunities to someone to hack our machine.

 1) Physical access. How many people have physical access to your machine? Is your password so obvious that it can be easily guessed? 

2) Through an internet connection. We can change the passphrase that an OS needs to use to connect to the router/modem from the default passphrase and we can confirm 
that communication between the computer and the router/modem is done through strong encrypted communications. We can switch off the router/modem.

3) Through Wireless (WiFi) connection from the hacker's computer to our computer. If practical we can use Ethernet cable to connect to the router/modem and switch off Wifi for our machine. We can keep WiFi switched off until we need to use it.

Regards

---

