---
title: "password not working, can't get to grub to reset"
date: 2022-06-26
forum: New to Ubuntu
---

### Post by jediviking on 2022-06-26
My daughter is very frustrated right now. Her HP Envy laptop has Lubuntu 20.04 on it (newly installed about three months ago). Last month, she noticed that her password stopped working. She has tried looking for a way to change it, but hasn't made any progress. I took a look at it a bit ago and definitely can't find a grub menu with which to reset her password. I tried Esc and Shift (separately on different boots) according to some advice I read, but no luck getting to grub.

Help would be appreciated. I have too many inoperative computers right now - need to get a few of them running correctly.

(I've had a love/hate relationship with Ubuntu for a long, long time... so, not a newbie, but still a beginner in many ways.)

---

### Post by guiverc on 2022-06-26
Firstly I'd switch to a text terminal, and try logging in there.

If insufficient space exists in $HOME (*your home user directory*), but text logins will still work allowing you to remove some files & create space, so you can login via the GUI again. It'll also confirm the password is correct.

I'm aware of some users having issues when encryption is involved & they use non-ASCII keyboards (ie. non-english) as the language specified in a login session isn't yet available when you try and unlock an encrypted device & all US based/designed machines (inc. all made in Asia/China etc) assume ASCII keyboards; only a few upmarket european  devices cater with non-ASCII in firmware - but you didn't mention encryption so this is likely unrelated.

There is no grub option to change a password; GRUB is a boot loader and doesn't have access to your files, only files using in basic boot processes (esp. *where encryption is involved*).  If you want to make changes; it easiest using *live* media, mount your disk partition (*dealing with any encryption being used*) and change from there. In this manner Lubuntu, Ubuntu and windows (*or in fact any OS*) is pretty much the same; it's security is really only active when it's running (*why people use encryption!*).  Lubuntu uses Ubuntu's grub, with a theme file that will run on some older hardware so there is larger/easier to read text, blue background, logo etc.

---

### Post by jediviking on 2022-06-27
I did try logging in via the terminal window, but it did not work. She had tried as well. I'm fairly certain that we have the correct password, but something has clearly gone wrong with it.
The advice we'd been trying to follow involved using Grub to get to recovery mode, but that failed too.
I'm not sure how to do the change from the live media as I only saw the option to reinstall, which isn't what I was trying to do.

---

### Post by guiverc on 2022-06-27
You can also get to runlevel 1 by editing the *boot* line at `grub`, ie. using E to edit it, and adding " 1 " or " single " to the "*linux*" kernel line; though usually I'd also remove `quiet splash` at the same time so I got to see all messages during boot.

Given a text login doesn't work; the cause is likely something your daughter did in the last session before the problem occurred. I have no idea what that would be; I'd likely use a *live* system (eg. boot Lubuntu install media & use it without installing) to explore; looking at the .bash_history file for clues of commands, maybe the apt logs (`/var/log/apt/history.log`) to see if packages were installed that caused changes etc. 

You didn't mention encryption or non-english devices (esp. a non-english machine that maybe recently had a *firmware upgrade* recently applied; I talked about these issues in my prior reply; it's mainly an issue for devices sold in UK/Europe) but those are possible causes. As I'm an aussie, where I only see US/Chinese made devices with US keyboards, I have no experience with them, but am aware of difficulties on that can occur on devices sold in EU).

I'll provide a link to a question dealing with changing a lost administration password; it'll work too with Lubuntu (*which is just a Ubuntu system with some packages changed so as to use a different desktop*) - [https://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](https://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password).  With askubuntu, you generally look for the most-upvoted answer, but as I don't know your issue, I'm not sure if just changing your password will help, or it's just a temporary *work-around* given the real problem is unknown.

---

### Post by Impavidus on 2022-06-28
Just before entering some sudo command that requires the password, type the password in the terminal. Does it look right? If there's some keyboard layout mix-up, it could be wrong. But there's also the possibility that there was a keyboard layout mix-up originally and the issue only appeared when the mix-up was fixed, but the wrong password is still in the database.

If I remember correctly, [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)'s default repair un-hides the grub menu. That may help to find recovery mode.

---

