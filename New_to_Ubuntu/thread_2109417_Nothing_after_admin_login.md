---
title: "Nothing after admin login"
date: 2013-01-27
forum: New to Ubuntu
---

### Post by DanaLG on 2013-01-27
I have a DELL Dimension 3000, Intel Celeron 2.4GHz, 1GB RAM, 70GB drive with over 55GB free. 

I have used the 'Windows Installer" to load ubuntu 12.10. The install goes okay. I get the choice to boot to either Windows XP Pro or Ubuntu when the machine starts. When I try and run Ubuntu I get "The application Compiz has closed unexpectedly" error. After that the login screen shows, but if I try and login all I get is the blank desktop. After a re-boot, the ubuntu login screen shows, I get a "System program problem detected" error message.

I have been prompted to instal a update to ubuntu, which is strange.

How can it be working enough to tell me an update is available but the desktop is not showing?

The PC doesn't have a DVD player so I can't try loading it from that, and until I know that it will run I do not want to delete the Windows XP Pro. Its a spare PC so there are no files on it. I've done a windows update, Java, and Flash, as well as a Defrag. The Windows side is running fine.

I am a Mac guy with a good amount of Windows experience but I am new to Ubuntu.

---

### Post by DanaLG on 2013-01-27
An update:
It indicated that an update was available, I downloaded and installed it. BUT I continue to have the same problem. The login screen seems fine, I can see the network connection, the time, date, I can restart or shut down, all looks normal. BUT, when I login as a Admin, or a guest, everything goes away and all I have is the mouse and the colorful screen. 

I have read that it might be a video driver? But how do I get to that?

---

### Post by sanderj on 2013-01-27
Login as Admin on Ubuntu? How do you do that?

Can you post a picture (taken with your phone or camera) of what you see?

---

### Post by frank604 on 2013-01-27
@sanderj: I think it is the windows mentality where a user has administrator rights.  He basically means when he logs in as himself not as root.  Just my guess and an off-topic comment.

Edit: Perhaps log into "unity 2D" instead of regular unity.  To the right of your username there is a circle (less than an inch away).  Click on it and a dropdown will appear.  Select Unity 2D.

---

### Post by DanaLG on 2013-01-27
Here is what I get:
I never get to a point that even shows a username. 
I have the login screen, or the totally blank screen.

---

### Post by sanderj on 2013-01-27
Ah: you *created* an account named 'Administrator'. Now I understand your older post.

The first screen looks good, the second doesn't.

Have you tried the 2D method described earlier?

---

### Post by DanaLG on 2013-01-27
I can't find that button?
I can get to the terminal, what is the code for changing it?

---

### Post by steeldriver on 2013-01-27
you might need to reset compiz?

[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

I'd try the dconf method first - not a fan of ppas unless absolutely necessary

---

### Post by HiImTye on 2013-01-27
what did you do before you were unable to login? I would try owning your home folder

before logging in, go to tty1 by hitting *ctrl+alt+f1*, login (as your 'Administrator' account), and type the following (exactly):
```
sudo chown -R $USER:$USER /home/$USER/
```when you're done, to return to tty7 hit *ctrl+alt+f7*

---

### Post by DanaLG on 2013-01-27
I was never able to login, this is a fresh new instal. All I get is a login screen.
I tried that, and there is no difference.

There is no icon next to the user names.

If I choose "Guest Session" I get the same blank-ness.

---

### Post by HiImTye on 2013-01-27
odd. I would try a reinstall if you haven't done anything on it anyway. in my experience, it's best to not do the updates when you're installing

---

### Post by DanaLG on 2013-01-27
I've done a fresh instal 3 times now. I run the Windows Installer, then download and install. That all seems to go fine. When I boot, I get a choice of Windows XP Pr or Ubuntu. When I choose Ubuntu I get a normal looking login screen, I'm guessing because I've never used Ubuntu before. I can login as the account I created at installation which I called "Administrator" and I enter my password. I am then presented with a blank screen.

If I wait awhile I will get a "System program problem detected" error message. But all I can do is either cancel or report the problem. I've click both, but no difference. If I try and report the problem I get "The application Compiz has closed unexpectedly" error.  If I click "relaunch" the Compiz error just keeps coming up.


When I tried to do the "sudo apt-get install dconf-tools" in the terminal I get a error saying the "sudo apt-get" is invalid.

---

### Post by DanaLG on 2013-01-28
I tried both the processes described in this link:

[http://www.webupd8.org/2012/10/how-t...in-ubuntu.html](http://www.webupd8.org/2012/10/how-t...in-ubuntu.html)

Neither one had any effect.

I have deleted ubuntu totally, re-downloaded the Windows installer. Run through the installation a total of 4 times, and I get the exact same result.

---

### Post by windscape on 2013-01-28
Hi,

The issue is probably that the integrated video is too old to support modern hardware OpenGL 3D acceleration which Unity requires. Ubuntu removed Unity 2D in 12.10 as far as I know. 

My suggestion is to try Ubuntu 12.04, or a more lightweight version such as Xubuntu or Lubuntu. 

If none of those pan out, then another distribution that is much more lightweight, such as Puppy Linux, may work better on relatively ancient hardware such as yours.

---

### Post by oldos2er on 2013-01-28
This may be a long shot, but I've read of people having various problems related to a user name with a capitalized first letter. If you're reinstalling, try *administrator* instead of *Administrator*.

---

### Post by DanaLG on 2013-01-28
Gave up on it last night and shut it all down. Today I booted it up, one last time before i delete it again and try a 5th instal and what do you know, I have a dashboard.

It is running incredibly slow, un-useably slow, but I do have a dashboard. 

I still got the Compiz failure error.

I guess I'll re-boot and see if that helps, but I am so excited about having it working, even if it is in slow-motion, that I am afraid to do anything that will stop it..

---

### Post by frank604 on 2013-01-28
Just realized you are doing a wubi installation?  I hear it is a bit finicky.  If you don't want to dualboot and are looking to test the waters, perhaps installing virtualbox in windows and then installing ubuntu inside virtualbox would suffice?  Most definitely less headache.

---

### Post by DanaLG on 2013-01-28
Agreed, I do not really want a duel boot machine. I ave no use for the "Windows" part.

I have come to the conclusion that the DELL Dimension 3000 is just too old and slow for ubuntu. So I installed lubuntu. Sure its not as fancy looking, and might not have all the "Bling" but I just wanted to make the old PC useful again without spending $199 for an operating system I don't like.

So far it installed well, and runs just fine.

Thanks to everyone who helped me with this. 
I have another old'ish DELL, maybe I'll try the full instal on that one . . . . ):P

---

### Post by DuckHook on 2013-01-29
> **DanaLG said:**
> I have come to the conclusion that the DELL Dimension 3000 is just too old and slow for ubuntu...
...I have another old'ish DELL, maybe I'll try the full instal on that one . . . . ):P

Please read my replies on the following thread:

[http://ubuntuforums.org/showthread.php?t=2108988&goto=newpost](http://ubuntuforums.org/showthread.php?t=2108988&goto=newpost)

---

