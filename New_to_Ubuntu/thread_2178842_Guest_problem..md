---
title: "Guest problem."
date: 2013-10-05
forum: New to Ubuntu
---

### Post by ex-para on 2013-10-05
I booted my laptop up that has 12.4 and it came up with quest. Guest has none of my documents, bookmarks in fact nothing. I am busy with a project on another computer and all the info I need for it is on the computer with the guest problem. I first had 8.04 and advanced from one upgrade to another all seemed OK but I have never really liked 12.4 as it has had other problems but back to the reason I am asking for help. Can any one please tell how I can get my documents etc.. back and get rid of the guest  as I have tried a few things with no success.

---

### Post by whitesmith on 2013-10-05
I think this thread answers your question: [http://ubuntuforums.org/showthread.php?t=1024371](http://ubuntuforums.org/showthread.php?t=1024371)

---

### Post by slickymaster on 2013-10-05
Ubuntu's Guest account is a special type of account, which has its home directory set to the mount point of a **tmpfs** filesystem, which is used to store data which does not need to be persisted after a reboot. The data in tmpfs is stored in RAM backed up by the swap space, so the data is never written to disk in the first place, so there's basically nothing to recover.

To disable this account do the following in a terminal window:```
gksudo gedit /etc/lightdm/lightdm.conf
```Once the file is opened, add the following line to it:```
allow-guest=false
```Save and exit the file and restart lightdm```
sudo restart lightdm
```

---

### Post by newb85 on 2013-10-05
It's doubtful that removing gdm-guest-session will disable guest login, since Ubuntu doesn't use GDM by default anymore.  It was replaced by LightDM a couple years ago.  (Of course, you can easily install gdm, and you should be prompted during configuration about which display manager you want to use.)

---

### Post by ex-para on 2013-10-06
Thanks for the replies but I could not use any of the commands as I have no sudo password in guest. To get it working I clicked on the computer name just above the login space and got rid of the guest screen and back to the normal one, this was of course pure luck.

---

### Post by newb85 on 2013-10-06
Of course the guest account doesn't have sudo privileges.  It's the guest account.  You should be performing administrative tasks from an account that has administrative privileges.  If you're working with your own machine, normal use shouldn't be in a guest account, either.

---

### Post by ex-para on 2013-10-07
I am not sure what you mean, I was given some commands to get me out of guest but I was unable to use them nor was I able to use the computer as it was in guest.

---

### Post by stinkeye on 2013-10-07
**@ex-para**,
Are you not able to log out of the guest account and into your user session?
**[COLOR="#FF0000"]EDIT:[/COLOR]** OK it appears that's what you eventually did.

---

