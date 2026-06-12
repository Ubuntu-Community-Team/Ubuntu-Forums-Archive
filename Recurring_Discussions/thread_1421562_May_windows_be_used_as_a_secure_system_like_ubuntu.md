---
title: "May windows be used as a secure system like ubuntu?"
date: 2010-03-04
forum: Recurring Discussions
---

### Post by Kike89 on 2010-03-04
Well I red in a post that one of the most important characteristics which makes Linux such a secure system is that always you need to do any change outside your desktop files you have to open a terminal window an do it as root using sudo. In windows, when you log in with your main account you have "administrator acces" so everything is exposed, so my question is, what if you DON'T use your administrator account in windows but a regular account and change to administrator JUST when you need to do any change without entering to the internet? will that lower the risk of being attacked in windows? is that better than login in as administrator all the time?

I need to know this because I have dual-boot in my notebook (vista and ubuntu), my first OS is Ubuntu, but I still need to use vista to play games and stuff and I don't have an anti-virus because I'm not willing to pay an expensive fee every year for something that won't cover me at all, therefore I need to know what are the better tips for using windows in a secure way.

thanx

---

### Post by blur xc on 2010-03-04
I'll be interested in hearing the replies on this one as well.  I don't have very much experience with Vista and Win 7, but I know for a fact running XP w/o full admin access seriously impedes many features.  At least w/ XP home- I don't know if XP Pro/Ultimate (whatever) has better access controls.

BM

---

### Post by Dougie187 on 2010-03-04
It won't decrease the risk of attack in windows, just like nothing will decrease the risk of attack in linux.

Though it would limit the software that could be installed, and make it so nothing could be installed to the whole system (without some admin password). This alone would not secure your system completely but it couldn't hurt. I'm not sure if there are other ways of getting around windows admin authentication or not, but if there are not, it should help a lot.

---

### Post by doas777 on 2010-03-04
> **Kike89 said:**
> Well I red in a post that one of the most important characteristics which makes Linux such a secure system is that always you need to do any change outside your desktop files you have to open a terminal window an do it as root using sudo. In windows, when you log in with your main account you have "administrator acces" so everything is exposed, so my question is, what if you DON'T use your administrator account in windows but a regular account and change to administrator JUST when you need to do any change without entering to the internet? will that lower the risk of being attacked in windows? is that better than login in as administrator all the time?

I need to know this because I have dual-boot in my notebook (vista and ubuntu), my first OS is Ubuntu, but I still need to use vista to play games and stuff and I don't have an anti-virus because I'm not willing to pay an expensive fee every year for something that won't cover me at all, therefore I need to know what are the better tips for using windows in a secure way.

thanx

my users manage to infect themselves regularly despite being only "users". most of the fake antivirus malwares in particular seem to require only minimal access, which is odd since most of them disable or alter the security center service. we've even locked down the installer service, but it still manages to get through.

I came to the conclusion a long time ago, that there is just no way to tell if a windows system is clean. once rootkits became the rage, theres just no telling.

---

### Post by Kike89 on 2010-03-04
If shuting down the administrator acces in windows won't make your system safer, then why is Linux supossed to be such a safe system? even safer than mac.

---

### Post by philinux on 2010-03-04
> **Kike89 said:**
> Well I red in a post that one of the most important characteristics which makes Linux such a secure system is that always you need to do any change outside your desktop files you have to open a terminal window an do it as root using sudo. In windows, when you log in with your main account you have "administrator acces" so everything is exposed, so my question is, what if you DON'T use your administrator account in windows but a regular account and change to administrator JUST when you need to do any change without entering to the internet? will that lower the risk of being attacked in windows? is that better than login in as administrator all the time?

I need to know this because I have dual-boot in my notebook (vista and ubuntu), my first OS is Ubuntu, but I still need to use vista to play games and stuff and I don't have an anti-virus because I'm not willing to pay an expensive fee every year for something that won't cover me at all, therefore I need to know what are the better tips for using windows in a secure way.

thanx

Get comodo avira or avg anti-virus. All free. Running as a limited user was always the recommended way.

---

### Post by Kike89 on 2010-03-04
> **philinux said:**
> Get comodo avira or avg anti-virus. All free. Running as a limited user was always the recommended way.

thx for the tip

---

### Post by doas777 on 2010-03-04
> **Kike89 said:**
> If shuting down the administrator acces in windows won't make your system safer, then why is Linux supossed to be such a safe system? even safer than mac.

well first off, the restriction on linux actually works for the most part, unlike windows. another big one, is that in the windows world, if you can read a file (the most basic access) you can execute it if it is an application. in unix, execute is a seperate right, and it granted very sparsely. in windows, the "everyone" group has significant access to most of the filesystem.

---

### Post by Ozymandias_117 on 2010-03-04
> **Kike89 said:**
> If shuting down the administrator acces in windows won't make your system safer, then why is Linux supossed to be such a safe system? even safer than mac.

This may answer some of your questions [http://freewebsoftwarereviews.blogspot.com/2007/12/why-linux-is-more-secure-than-windows.html]("http://freewebsoftwarereviews.blogspot.com/2007/12/why-linux-is-more-secure-than-windows.html")

---

### Post by Mark Phelps on 2010-03-04
Vista and Win7 changed the way default accounts are configured in MS Windows.  When you login, you are NOT an Administrator anymore; instead, you are a general user with SOME elevated rights.  The default Administrator account is actually hidden and you have to go to some trouble to unhide it to login using that account.

UAC is also different, not only for Vista, but also for Win7, and while some folks find it annoying, there's more tailoring you can do under Win7 to avoid getting all the popups you got under Vista without having to disable UAC entirely.

As to the relative security level, all I can say is that I used two Win7 test boxes, both connected to the Internet through a local router, for over six months WITHOUT any AV products installed (and with Windows Defender disabled), and neither one got any infections or viruses.

How do I know? I regularly booted from several different AV CDs and ran scans -- just to see if I was getting any infections.

However, I'm not saying Win7 can't be infected, I'm just saying that my experience with it has been a LOT better than with XP.

---

### Post by Lightstar on 2010-03-04
Windows is a mess when it comes to administrator stuff, that's what I think!

Shortly after installing Windows 7 I got a few old documents I could not open (including ubuntu's ISO file, odd coincidence huh?  haha and some game installers).  Apparently I did not have the permission to open them.  Everytime I changed the permissions and clicked 'apply' they would return the way they were.

I had to log in windows as administrator.  The administrator was not showing in the logon screen by default, so I had to 

1) run cmd as administrator, 
2) add administrator to the logon screen through the terminal (yay terminal) 
3) log out
4) log in as administrator
5) change file permissions
6) permissions did not stick, had to copy the files as admin, the copied files somehow had the right permissions (yay)
7) go to terminal, and remove admin from the logon screen
8) re-login as normal user.

All that to open a few files that got permissions messed up.

Yeah.. win 7 is more secure, and also more trouble for me.
I do like it ALOT more than vista.  I think the only ones I've like was Windows 98 and Windows 7.

---

### Post by bodhi.zazen on 2010-03-04
[http://en.wikipedia.org/wiki/Comparison_of_privilege_authorization_features](http://en.wikipedia.org/wiki/Comparison_of_privilege_authorization_features)

Linux vs Windows security = recurring discussion / debate

Nice overview here:

[http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/](http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/)

At lease if you read that you will be familiar with the issues and can make your own decision.

---

