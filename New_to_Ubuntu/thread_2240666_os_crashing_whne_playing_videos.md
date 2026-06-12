---
title: "os crashing whne playing videos"
date: 2014-08-21
forum: New to Ubuntu
---

### Post by ollie3 on 2014-08-21
When i play a video the whole os crashes xubuntu 

this is my hardeware info 


I have installed the restricted drivers and it still happens, i would realy appricate some help here, as I have been turning the laptop on and off a lot and don#t want to damage my hardwar.

Peace ya'll

---

### Post by SeijiSensei on 2014-08-21
What player are you using?

I recommend installing mplayer from the repositories if you don't already have a copy, then playing the video from the command prompt like this:
```
$ mplayer /path/to/my/video/file
```
and see what it reports.  If you don't see any obvious answers, you can try "mplayer -v" instead for the "verbose" result.

---

### Post by deadflowr on 2014-08-21
You are currently using the open-source nouveau graphics driver and not the restricted nvidia drivers.

If you installed the nvidia driver, perhaps you need to configure it.
```
sudo nvidia-xconfig
```
I'm unclear on how well your card is supported or which nvidia driver you might have installed so,
If trouble arises please look over this
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
(Or perhaps look over this before you run the command for a quick overview of what to do if something goes wrong...)

Also, try re-running the lshw command again with sudo so we can see the full output.
```
sudo lshw
```

---

### Post by Jonathan Precise on 2014-08-21
@ollie3:

What type of crash is it? Does it say something like kernel panic? Or does it just reboot? Or does everything hang forcing a hard reset?

Please gice more details about the crash so we can attack the problem better.

Regards.

---

### Post by ollie3 on 2014-08-22
thanks for all your help, 

Jon, the whole os crashes and freezes and I have to restart by the power button.

Deadflower, I tried installing the drive via terminal and it didn't work and then i read the link you sent and then used settings and changed drivers to nvidia.  That seems to hve fixed the problem as i now have a nvidia file in settings.

I have done a sudo lshw just in case as I kept getting a xubuntu problem report coming up, so was hoping you might be able to see if I ahve any other problems.


Thanks for you help guys, Linux is cool :)

---

### Post by ollie3 on 2014-08-22
blimey, now terminal wont let me type in commands, I can cut and paste them but then i can put in my password. grr

---

### Post by ollie3 on 2014-08-22
the terminal prob;lem is directly related to whern i try and run ufw

---

### Post by yancek on 2014-08-22
I'm not sure what the problem is with entering commands in the terminal but, you do know that when you type in your password nothing will show, not even asterisks **.

---

### Post by ollie3 on 2014-08-22
yeah i do now, I think it was before, which is wierd, i don't know why i woiuld have thought it wasn't working otherwise, anyway np now.  I am still having a driver problem that is being reported to me as i log into xubuntu but it goes away to fast to read, is there anyway of pausing this or finding it in some other place?

video is working now though, thanks for the help with that :)

---

