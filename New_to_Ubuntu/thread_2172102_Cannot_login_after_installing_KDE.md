---
title: "Cannot login after installing KDE"
date: 2013-09-03
forum: New to Ubuntu
---

### Post by BlacklightHalo on 2013-09-03
I have just installed KDE last night, set up my preferred environment (with desktop cube effects color scheme, set the splash screen to "minimalist" and also installed ksnapshot.) Installation was done following [these]("http://www.youtube.com/watch?v=X6fdufuKjc4") steps. Everything seemed to be working fine (actually pretty stellar.) Then I did a reboot to make sure all my changes could settle-in properly. When I got back to the login screen, however, there seems to be no user account for me (or anyone else for that matter.) If I click "switch user," my only option is something that says,  "Unused (:0, vt8)" which is already selected. If I type in my previous username and password, it won't recognize it and acts as though I've typed in error.

My computer is an HP desktop, but at the login screen it says Dellp2-1310. It has a sticker on the bottom that says "Vision E2" but I'm not sure if that's the model number (I can't find that model with a google search.) However, I believe this computer should not have problems running KDE (it was fine with Unity,) and I bought it because a trusted family friend said it would run well with Linux OS such as Ubuntu. But then given the issues I'm seeing, it seems less to me like a KDE problem and more like the computer just doesn't remember me somehow.

While I cannot login, I do seem to have other options. The blue down-arrow gives me options of which desktop to use (options are "Defualt," ""KDE Plasma Workspace," "KDE Plasma Workspace (failsafe session)," "Ubuntu" and "Failsafe." The red "shutdown" button on the screen gives me the options, "Switch User," "Restart X Server," "remote Login," "Console Login," and "Shutdown." Since I seem to have a root shell prompt at my disposal, anything you might need me to type to diagnose the problem is a do-able thing.

Would someone please help me get it functioning again?

Update - It seems this has happened before.

[http://ubuntuforums.org/showthread.php?t=2003566&highlight=kdm+username+password](http://ubuntuforums.org/showthread.php?t=2003566&highlight=kdm+username+password)

This person closed their thread already so I wasn't able to post that I'm having the same issue. Also, the question was asked if I'm seeing the KDM login screen - yes, I am. I chose that one at installation, thinking it was just better to use that one with KDE. I'm unable to switch it to LightDM login because it won't recognize my U/N and P/W in the first place.

---

### Post by deadflowr on 2013-09-03
The layout you describes sounds like the kdm login screen versus the lightdm login screen Ubuntu uses.
Is there a login box in the middle of the screen with empty boxes for user and password?

Since you've tried logging in maybe try switching display managers.

Press ctrl + alt + F2 and then entewr your username and password.
then type
> sudo service kdm stop
then type
> sudo service lightdm start
This should bring up Ubuntu's display manager and login screen.
Then in the login box look for the Ubuntu logo and click on it and select the Kde logo then enter password for your user.

---

### Post by BlacklightHalo on 2013-09-03
Thank you for your reply. In order for that to work, it would have to be accepting my username and password in the first place, which as I stated, it does not. It doesn't seem to even recognize that they exist, so I can't get as far as sudo-anything in the first place. Typing in my username and password in the root shell prompt when I use ctrl+alt+f2 returns, "login incorrect." And yes I am sure that I'm typing in my username and password exactly as I made them while creating the login. But yes, this is the KDM login screen, which I chose during the installation of KDE.

---

### Post by deadflowr on 2013-09-03
Follow this
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

And pay close attention to the output of  the ls /home command.
Sometimes people end up having a letter off from what they think it is.
If it's okay, then follow the guide and do a password reset.

---

### Post by BlacklightHalo on 2013-09-03
The shift key thing doesn't work. It doesn't seem to notice that either, and still goes straight to the KDM login screen where nothing is changed. This computer was supposed to have Windows 8 pre-installed, which doesn't have a BIOS and is screwy in that way to prevent hacking or something like that, but the company who sold it to us bypassed that in order to install Ubuntu on it instead. On bootup, other than the purple screen, it says "KVM disabled by BIOS" and then proceeds to the KDM login screen. It may not be affectable by things one can do at the bootup of a normal Ubuntu computer.

---

### Post by BlacklightHalo on 2013-09-03
If it has absolutely "made up its mind" to not respond to anything we do, do you suppose that putting in a live cd would allow me to reinstall the OS and start from scratch? As lame an option as that would be, I'd do it if it were my last resort.

---

### Post by deadflowr on 2013-09-03
You can try to reset the password with a liveCD
[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

---

### Post by BlacklightHalo on 2013-09-03
I will try that. It also seems like there's a way to add a user "to a group" (I'm not sure if that's the same thing as crating a user, but I can only try) so I may be able to use the link you sent me to create a new version of my account if all else fails. Thank you, and I'll write back with how that goes. But the question then becomes, how do I prevent this from happening again? I swear, every time I've tried to make KDE work (especially with the desktop cube,) it's caused the computer to go haywire no matter what kind of computer it was, desktop or laptop, compatible with Linux OS or not. I don't know what keeps going wrong, but whereas plenty of people use Ubuntu and KDE without problems (or at least without this one) my usual assumption of "there must just be something inherently wrong or bad about the way it's designed" doesn't seem to hold up.

---

### Post by BlacklightHalo on 2013-09-03
It doesn't seem to register that I'm trying to boot from a Live CD either. It takes a little longer and spends some time chewing on the disc, but still just drops me at the KDM login screen.

---

### Post by BlacklightHalo on 2013-09-04
I have successfully logged back in. It seems this was my mistake. I assumed my username was the on I'm used to seeing at the top-right of a Unity session, but actually it was "user." I'm going to close this thread. Thank you for your help, anyone who lent a hand.

---

