---
title: "Unity is not working correctly after installing gnome on 13.10"
date: 2013-11-22
forum: New to Ubuntu
---

### Post by Val87 on 2013-11-22
Hello everyone,
This is my first post.
I crewed up! :) I switched to Linux completely about 2 months ago, a decision i am not regretting. I even managed to get my favourite game World of Tanks running properly. Last night i discovered GNOME and wanted to play around with it, so i installed it. Long story short, i did not like it. When trying to go back to Unity on Login screen, this i what i get now:
[ATTACH=CONFIG]248005[/ATTACH]
When browsing through solutions on removing GNOME, situation still has not changed, there is no wallpaper and top dash icons seem to be different. I tried everythin i can, resetting unity and purging Gnome. GNOME is no longer in selection on login windows but on startup image i still get the little "foot". How can i fix it to go back to Unity working properly.

it seems like i have both GNOME and Unity running at the same time. 

Thanks,
Val

---

### Post by grier-devon on 2013-11-22
> **Valeri_Tarassov said:**
> Hello everyone,
This is my first post.
I crewed up! :) I switched to Linux completely about 2 months ago, a decision i am not regretting. I even managed to get my favourite game World of Tanks running properly. Last night i discovered GNOME and wanted to play around with it, so i installed it. Long story short, i did not like it. When trying to go back to Unity on Login screen, this i what i get now:
[ATTACH=CONFIG]248005[/ATTACH]
When browsing through solutions on removing GNOME, situation still has not changed, there is no wallpaper and top dash icons seem to be different. I tried everythin i can, resetting unity and purging Gnome. GNOME is no longer in selection on login windows but on startup image i still get the little "foot". How can i fix it to go back to Unity working properly.

it seems like i have both GNOME and Unity running at the same time. 

Thanks,
Val

hello there,
Glad to hear no regrets, You might have done something similar to what I did once, back when using Ubuntu 8.04 I installed the KDE desktop and found I did not like it, so I removed KDE using the purge command which did far to much damage. I basically had to do a re-install which was not fun. If no one else post anything then I would recommend backing up your stuff and then try re-installing Unity.
```
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity
```

If this does not work then I would recommend a re-install of the operating system, but I would wait to see what other users may have to say before trying my steps.

On a side note if you are curious to trying new desktops and play on the cautious side then just use a VM and install a Ubuntu flavour already supporting that desktop but that is my two cents.

Free VM for Ubuntu
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by Val87 on 2013-11-22
Thank you for your reply.
I tried all that, nothing has changed.
I just wonder if i would reinstall, would there be a way where i wont have to reinstall my applications and files?

---

### Post by grier-devon on 2013-11-22
> **Valeri_Tarassov said:**
> Thank you for your reply.
I tried all that, nothing has changed.
I just wonder if i would reinstall, would there be a way where i wont have to reinstall my applications and files?

This depends on how many files you have and where they are in the system, I back all my stuff up but I spent quiet sometime setting up my backup tool to make sure all my files can be backed up and then restored as needed. As for application maybe someone with more knowledge on the subject will come and assist. I have never tried to backup application since 99.9% of my application are open source and available in the software center I enjoy downloading the latest packages offered with each release. Hopefully someone else can shine some light on application backup and recovery, best of luck.

---

### Post by Val87 on 2013-11-22
I decided to burn a live DVD of 13.10. And chose Reinstall option with keeping files and applications. Currently sitting on live cd while installation is running. Hopefully, everything will be ok.

---

### Post by grier-devon on 2013-11-22
Okay, let us know how that works for you.

---

### Post by Val87 on 2013-11-22
Well the installation completed, and GNOME is gone. But i have to reinstall such packages as skype and Chromium, same with Playonlinu and Wine. Hope the game works after install is done. Its best not to experiment with Gnome at all.

---

### Post by grier-devon on 2013-11-22
> **Valeri_Tarassov said:**
> Well the installation completed, and GNOME is gone. But i have to reinstall such packages as skype and Chromium, same with Playonlinu and Wine. Hope the game works after install is done. Its best not to experiment with Gnome at all.

I wouldn't on intern releases, I have installed GNOME on Ubuntu 12.04 LTS and all went well but removing the packages can be difficult if you type in the wrong thing. One thing to watch for is using the command "purge", this does things differently then "remove". I try to avoid the use of "purge" unless it is truly necessary since I believe purge also means to remove dependencies as well. If you used "purge" there is a chance if Unity relies on any GNOME dependencies it may have pulled those too and that may be what caused Unity to have problems. Enjoy the fresh install and if you have any problems with installing some of those things do a google search or just post on the forum.

---

### Post by Val87 on 2013-11-22
Thanks! Games installed back fine. Everything back to normal. Wondering will the 14.04 be much different, i mean design wise, it starts to get a bit boring. :) And for some reason i don't have permission to edit my own profile on this forum, wonder why is that? :)

---

### Post by grier-devon on 2013-11-22
> **Valeri_Tarassov said:**
> Thanks! Games installed back fine. Everything back to normal. Wondering will the 14.04 be much different, i mean design wise, it starts to get a bit boring. :) And for some reason i don't have permission to edit my own profile on this forum, wonder why is that? :)

Well you need to have at least 50 post to add an avatar and signature I know that. 14.04 will have some minor changes but the focus for 14.04 is for Ubuntu Touch for the tablet. I do believe though 14.04 should also have xmir. If your looking for information on Ubuntu then head over to.....

omg ubuntu
[http://www.omgubuntu.co.uk/](http://www.omgubuntu.co.uk/)

and we also have the mighty Ubuntu Onair
[http://www.youtube.com/channel/UCm7OifwnZoMCChidCJZQruQ](http://www.youtube.com/channel/UCm7OifwnZoMCChidCJZQruQ)

---

### Post by deadflowr on 2013-11-22
It would seem you have solved, or at least resolved your problem.

But out of curiosity, how'd you install gnome?
By how I mean which gnome?(gnome, gnome-shell, gnome-panel?)

The blank screen might be from the fact the unity has the file manager to handle the desktop, where as gnome(gnome-shell) does not.
The output from the screenie lends me to believe that the ability for the file manager to handle the desktop could have been turned off.
The program gnome tweak tool (also known as advanced settings in gnome) could help tell if it was.(as well as rest it.)
Moot point though now, I guess.

Also, what was wrong with the icons?
Those seem normal.

---

### Post by Val87 on 2013-11-24
> **deadflowr said:**
> It would seem you have solved, or at least resolved your problem.

But out of curiosity, how'd you install gnome?
By how I mean which gnome?(gnome, gnome-shell, gnome-panel?)

The blank screen might be from the fact the unity has the file manager to handle the desktop, where as gnome(gnome-shell) does not.
The output from the screenie lends me to believe that the ability for the file manager to handle the desktop could have been turned off.
The program gnome tweak tool (also known as advanced settings in gnome) could help tell if it was.(as well as rest it.)
Moot point though now, I guess.

Also, what was wrong with the icons?
Those seem normal.

This is the look i was going for:

[IMG]http://2.bp.blogspot.com/-I0g6Tq22gv8/UTN8mrSDhfI/AAAAAAAAOVE/vU79Ekd5_WM/s1600/gnome-3.8-beta-frequent.png[/IMG]

As far as i can tell, it was GNOME 3, the latest one. With icons, the thing was that after removal of GNOME via terminal, from unity was left the launch bar on the left but the rest was what i have seen after trying to run freshly installed GNOME after restart, which was buggy and did not work very well, that is why i decided to go back to UNITY, when i tried to switch at the log in page, i got a black no wallpaper screen plus leftovers of GNOME in the top right corner plus the windows. See the screenshot at the beginning of the thread. If you are interested in my machine specs, they might contain the answer, may be they are not supported. Anyway i decided not to mess around with something i am not confident about and stick with unity for now, its working great and i am loving it. Although it would be nice to try how GNOME is in action when working properly. I guess when a more stable release of 13.10 is out, i might try again. 

[ATTACH=CONFIG]248075[/ATTACH]

P.S Just realized you will see that i am watching "The Good Wife", this is my only machine  i use it for university and entertainment and yep im in law school! :D So no mocking for the choice of a TV show :D

---

