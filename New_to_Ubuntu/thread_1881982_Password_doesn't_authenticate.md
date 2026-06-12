---
title: "Password doesn't authenticate"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by artms on 2011-11-16
I have reset passwrd in recovery console,  says it resets then it doesn't work to authenticate. Tried to add user to sudo , says it doesn't exist, which it does.I can't do anything. I can log on but can't change anything. Help!
I recently upgraded to 11.10. BTW it always asks for wifi password even though I set that to auto log on....drives me crazy

---

### Post by ubudog on 2011-11-16
Hi there, open a terminal and type the following while logged in, in your user account:

```
passwd
```

Follow the instructions to see if you are able to change the password like normal.  Please let us know if it is successful.  :)

---

### Post by rob22941 on 2011-11-16
I'm actually having this issue in Kubuntu. I know exactly what the password is and tried using 'passwd' in terminal with no success.

Only options looks like reinstalling?

---

### Post by artms on 2011-11-16
it reset successfully....now what....

---

### Post by ubudog on 2011-11-16
> **artms said:**
> it reset successfully....now what....

Well, now you can try to sudo.

```
sudo -s
```

> **rob22941 said:**
> I'm actually having this issue in Kubuntu. I know exactly what the password is and tried using 'passwd' in terminal with no success.

Only options looks like reinstalling?

Strange.  You sure you entered the old password and everything correct?

---

### Post by artms on 2011-11-16
ok...I am a real beginner and very comfortable with windows...that said..i am very frustrated but truly appreciate any help after spendings days fumbling around in a tight little circle. 
password changed, tried to unlock user..the one I am...the only one which is set at standard...and the pasword will not authenticate has to be superuser but can't make superuser because pass won't authenticate

---

### Post by artms on 2011-11-16
I also tried this
dee@dee-Inspiron-1011:~$ sudo -s adduser dee
[sudo] password for dee: 
dee is not in the sudoers file.  This incident will be reported.
dee@dee-Inspiron-1011:~$ 

can't add cause it doesnt authenticate

---

### Post by ubudog on 2011-11-16
Ah, I see now.

Try this:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

It's a great article and will take you step by step through the process.

---

### Post by artms on 2011-11-16
I did that before but now that I have your help I'll try again so stand by

---

### Post by artms on 2011-11-16
k using other lappy 2 talk 2 u...
adding user 'dee' to group admin
gpasswd: cannot lock /etc/group; try again later.
adduser: '/usr/bin/gpasswd -a dee admin'returnes error code 1. Exiting.

tried sudo cp /etc/sudoers /etc/sudoers.backup.
 got
  Read-only file system

I then tried sudo nano command and edited the file to match   control x  yes to save and got
[Error writing /etc/sudoers : Read-only file ]

---

### Post by artms on 2011-11-16
as u can see these were not successful

---

### Post by ubudog on 2011-11-16
Hmm, this might be an upgrade problem.  I suggest reinstalling from scratch, backing up your stuff (documents, music, downloads, etc.) first. 

This should take about 30 minutes in total and get you back to mint condition... not sure what else to do.

---

### Post by Cyclane on 2011-11-16
Just to be sure, you've reset your password like this: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

And your FS is mounted read-only in recovery mode, to mount in read-write you have to remount it. I'm not sure if this will work but you can safely try it:
```
mount -o remount,rw /
```
If that doesn't work please post the output of:
```
mount
```

---

### Post by artms on 2011-11-16
I did not install this originally but upgraded to 11.10 last week. Been a problem ever since. I have a mini with no disc drive and have no idea what to do from here unless there is a recovery as part of the install. And even then i have no privileges to do squat on my own lappy paperweight. Sad

---

### Post by ubudog on 2011-11-16
> **ubudog said:**
> Hmm, this might be an upgrade problem.  I suggest reinstalling from scratch, backing up your stuff (documents, music, downloads, etc.) first. 

This should take about 30 minutes in total and get you back to mint condition... not sure what else to do.

If push comes to shove this should fix it.

---

### Post by artms on 2011-11-16
first on entered code mount -o remount,rw
got
[ 380744241] EXT4-fs (sdal): re-mounted. Opts: errors=remount-ro

mount
really long thing
/dev/sda1 on / type ext4 (rw.errors=remount-ro,commit=0)
proc on /proc type proc (rw.noexec, nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusect l on /sys/fs/fuse/connections type fusect l (rw)
none on /sys/kernel/debug type debugfs (rw)
none on sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw, mode=0755)
devpts on /dev/pts type devpts (rw,moexec,nosuid,gid=5,mode=0620
none on /run/lock type tmpfs (rw,moexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


Phew...lots a typing.

---

### Post by artms on 2011-11-16
> **ubudog said:**
> If push comes to shove this should fix it.
I would love to set this back to original but I don't have the program on a disk and I don't have a disk drive..this is a Dell Mini 10 any suggestions?

---

### Post by ubudog on 2011-11-16
> **artms said:**
> I would love to set this back to original but I don't have the program on a disk and I don't have a disk drive..this is a Dell Mini 10 any suggestions?

You could use a friend's PC, go to a local library, or whatever.

---

### Post by artms on 2011-11-16
and do what? I have another laptop ...how does having another pc at the library help me fix the problem on my mini? all suggestions are welcome

---

### Post by ubudog on 2011-11-16
> **artms said:**
> and do what? I have another laptop ...how does having another pc at the library help me fix the problem on my mini? all suggestions are welcome

To get the disk, I mean.

---

### Post by artms on 2011-11-16
if i had a disk how could i install it on a lappy that doesn't have a disk drive? I downloaded linux mint but it's an iso and i don't know what to do with that either. if i could get something on an exterior hard drive maybe i could wipe the hard drive and do a clean install...but i have never done that with an exterior hard drive. You know I changed completely from windows to this and was fairly happy till this happened and now I feel it's beyond me. I have the windows recovery disks for the mini but no disk drive. I thought maybe I could connect the mini to my other laptop to use its disk drive but so far it seems I cannot. What do people with these netbooks do?I can't do anything with Ubuntu from now on with no privelege. Could I try to upgrade again and see if it'll fix it? what if I go back to an earlier version? I have no  idea at this point...but I'm willing.

---

### Post by ubudog on 2011-11-17
> **artms said:**
> if i had a disk how could i install it on a lappy that doesn't have a disk drive? I downloaded linux mint but it's an iso and i don't know what to do with that either. if i could get something on an exterior hard drive maybe i could wipe the hard drive and do a clean install...but i have never done that with an exterior hard drive. You know I changed completely from windows to this and was fairly happy till this happened and now I feel it's beyond me. I have the windows recovery disks for the mini but no disk drive. I thought maybe I could connect the mini to my other laptop to use its disk drive but so far it seems I cannot. What do people with these netbooks do?I can't do anything with Ubuntu from now on with no privelege. Could I try to upgrade again and see if it'll fix it? what if I go back to an earlier version? I have no  idea at this point...but I'm willing.

Does the lappy have a USB port?  If so, you can put the .iso on the disk (not just copying), described [here]("http://www.ubuntu.com/download/ubuntu/download"), in step two.  Just select USB, and Ubuntu.

---

### Post by artms on 2011-11-17
Thanks.I have usb and exterior hard drives. BTW I copied all that code after I entered mount on a previous post. I have no idea what it meant so could anyone tell me?

---

### Post by Paddy Landau on 2011-11-17
To answer your question about how to reinstall Ubuntu:


[LIST]
[*]Go to the [Ubuntu download page]("http://www.ubuntu.com/download/ubuntu/download") (on your other laptop).
[*]Step 1: Download Ubuntu.
[*]Step 2: Follow the instructions to create a bootable USB stick.
[*]Step 3: Follow the instructions to "Try it!" on your failed computer.
[/LIST]

While you are "trying it", you can back up your data, e.g. onto another USB stick or an external hard drive.

Once you are finished with "Try it!":

[LIST]
[*]Reboot.
[*]Step 4: Follow the instructions to "Install it!".
[/LIST]
 
(If you had initially installed with your data on a separate partition, you should be able to reinstall without overwriting your data, but don't rely on that -- please back up first.)

Finally you can restore your data.

---

### Post by artms on 2011-11-17
Is it possible to use an sd card in a usb card reader as well?

---

### Post by artms on 2011-11-17
So far so good. Reinstalled and now I don't have firmware for my wireless on my Dell Mini 10. It seems that it was downloading something in the beginning that was broadcom something then the connection stopped. So I closed that window and it finished installing. Is there some driver or something I need and can I do this without going into terminal? The little lappy is connected with an ethernet. Do I downlad some packages? What do I do now? i need something but don't know what.

---

### Post by artms on 2011-11-17
I'm very happy to report that for me as a beginner, I have with your help successfully installed Ubuntu. My pass authenticates, the internet connects automatically and i know I can do it again if I have to.  One thing I liked before was that I could choose different shells I guess you call em. I liked gnome but only see ubuntu and ubuntu 2d and one other. Can I get the gnome ones too?  Thanks again!!!

---

### Post by Paddy Landau on 2011-11-18
> **artms said:**
> Is it possible to use an sd card in a usb card reader as well?
Sorry, I don't know.

> **artms said:**
> Is there some driver or something I need...
While connected to the Internet, open *Additional Drivers*. It will automatically search for new drivers. If any are listed, you may -- or may not -- need to enable them.

> **artms said:**
> ... I have with your help successfully installed Ubuntu.
Fantastic!

Please [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") if your original question has been answered.

> **artms said:**
> I liked gnome but only see ubuntu and ubuntu 2d and one other. Can I get the gnome ones too?  Thanks again!!!
Bearing in mind how everything is changing for touch screens (including Windows 8, may I suggest that you give Unity a try first? You may find you enjoy it.

At the login screen, after you click your name but before you enter your password, you will see some options at the bottom of the screen. On my system (11.04), one of them is *Ubuntu Classic*, but I think that 11.10 no longer has it, as the new Gnome 3 is not all that much different from Unity.

If you really hate Unity, you may want to install a different derivative of Ubuntu; you can try [Xubuntu]("http://www.xubuntu.org/"), which uses XFCE, or [Lubuntu]("https://wiki.ubuntu.com/Lubuntu"), which uses LXDE (Lubuntu is also lightning fast, suitable for older and slower systems, but the trade-off is that it lacks a degree of flexibility).

---

### Post by ubudog on 2011-11-18
Awesome post Paddy Landau.

Glad you got it working finally artms.

---

### Post by artms on 2011-11-18
Thanks so much. Perhaps there's a way with unity to get what I want which is to have a text based menu that clicks open other menus with lists. For me it's faster and clearer. Does Unity have that? I don't like having space taken up with icons on my little lappy

---

### Post by Paddy Landau on 2011-11-19
> **artms said:**
> Perhaps there's a way with unity to get what I want which is to have a text based menu that clicks open other menus with lists.
If you get used to Unity, you'll discover that Unity is not actually slower, but faster.

However, on 11.04 (I don't know what 11.10 is like), you can do this:
Dash > More Apps > All Applications (at the top right).
It's not quite the same thing, though.

As I say, if you wish to retain the old menu structure, try Xubuntu or Lubuntu instead. Being part of the Ubuntu family, you will still get support on these forums.

---

