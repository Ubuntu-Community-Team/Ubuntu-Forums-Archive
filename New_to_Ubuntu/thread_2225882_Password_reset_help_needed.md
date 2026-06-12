---
title: "Password reset help needed"
date: 2014-05-23
forum: New to Ubuntu
---

### Post by kryznic on 2014-05-23
Hello,

i setup a ubuntu desktop about 3 years ago or so and used it for a while then it died or so I thought. I recently turned it back on and I can get to the login screen but cannot remember my password.  I have tried booting into recovery mode and dropping out to a root prompt but it prompts me for the root password which I also do not know.  Can someone please guide me on how to reset either or both passwords?  

There are photos on the drive I want to retrieve but cannot login. :0(

thanks.

chris

---

### Post by papibe on 2014-05-23
Hi kryznic.

Here's a tutorial on how to do it: [Reset Password]("http://psychocats.net/ubuntu/resetpassword").

BTW, unless your hard drive is encrypted, you should be able to get your pics and files using the Ubuntu installation media as a Live CD/USB.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by deadflowr on 2014-05-23
Do what you did and boot into the recovery mode, then enter the root shell again, and run this line first
```
mount -o rw,remount /
```
Recovery mode mounts as read-only, so you need to run this line to remount it as read/write.
then run this
```
ls /home
```
look for your user's name
then use the name in the passwd
```
passwd <usernamehere>
```
(change <usernamehere> to your username , no need for the <,> symbols.
then exit, you should now have a new password for your user.

No need to do anything about the root password, as Ubuntu's root password is locked by default, anyway.

---

### Post by kryznic on 2014-05-23
Thanks for the quick replies!

i tried that tutorial prior to this post but as I stated when I choose 'drop to root shell prompt' it is asking me for the root password or to hit Control D which just brings me back to the recovery mode menu. I don't get the root@ prompt shown in the tutorial pic.

i have also tried to take the drive out and hook it up to a windows machine as a USB drive but I get nothing, I'm assuming if I did that to another Ubuntu machine I would be able to browse the drive contents? I don't believe the drive is encrypted it's just a old Dell Optiplex my work gave me. 

Thanks!

---

### Post by papibe on 2014-05-24
I've never seen a password being asked on recovery mode. That's unusual. I can't think of a reason why that's happening. May be the root account was enabled and set with a passwords?
> **kryznic said:**
> I'm assuming if I did that to another Ubuntu machine I would be able to browse the drive contents?
Yes. Any recent Linux distro would work to access your files.

Also, you can access them in the same machine using the Ubuntu Installation CD/USB as a Live media. Instead of chose 'Install Ubuntu' you select 'Try Ubuntu', and you'll get to the a GUI desktop. In this case you would need to copy your files to another external media, or to a server using the network.

Let us know how it goes.
Regards.

---

### Post by kryznic on 2014-05-24
Yea I think I may have changed the root password because it was a logging machine initially at my old job. 

I will throw Ubuntu on a flash drive and boot it up and copy my files to another flash drive. Thanks!  I will let you know how I make out :0)

---

### Post by deadflowr on 2014-05-24
I've never seen the root shell in recovery mode need a password either, ever.
Regardless if I set a root password or not.
But another benefit of the livecd is you can also reset the password with that as well.
[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

---

### Post by squakie on 2014-05-24
And......no, it won't work on a Windows system - the file system is unknown to Windows.

---

### Post by kryznic on 2014-05-24
Ok, so I got Ubuntu on my USB to boot up and i can see the files on my drive,  I search for the username in question and I see the folders I want to get into under that user but it says I don't have permissions.  Grrrrrrrrrr,  so I guess I will give deadflowr's suggestion a shot and see if I can reset the password.  This is so weird.

---

### Post by kryznic on 2014-05-24
Well I tried deadflowr's suggestion, tho I am not using LiveCD but a USB drive and I still can't get in.  Recovery mode says to enter root password for maintenance.  I guess I just lose out on this one unless the password comes to me somehow.  =o/

---

### Post by papibe on 2014-05-24
> **kryznic said:**
> I want to get into under that user but it says I don't have permissions.  Grrrrrrr...
Try browsing as the super user, i.e.. open nautilus as root:
```
gksudo nautilus
```
or
```
sudo nautilus
```
and then navigate to your files.

Let us know how that worked.
Regards.

---

### Post by kryznic on 2014-05-24
Actually I took a beginners Linux class a couple years ago and we used Cent OS and I remember part of the final exam was resetting the root password by modifying the boot loader? I gotta dig up my notes maybe that can do it? Something about single user mode or something.

---

### Post by kryznic on 2014-05-24
Thanks Paine I will give that a try!

---

### Post by deadflowr on 2014-05-24
> **kryznic said:**
> Well I tried deadflowr's suggestion, tho I am not using LiveCD but a USB drive and I still can't get in.  Recovery mode says to enter root password for maintenance.  I guess I just lose out on this one unless the password comes to me somehow.  =o/

From a liveCd/USB you would simply choose "Try Ubuntu"
(Ignore the advice to ctrl+alt+F1 and simply let it boot a desktop session, as it does when doing the Try Ubuntu option.)
Then open a terminal from there.
It won't prompt for a root password.
If it does, you're doing something wrong.

---

### Post by sisco311 on 2014-05-24
You can boot into a root shell without knowing the root password. 

At the grub menu highlight the recovery mode option and press e for edit. This will get you to an emacs like editor from where you can change the kernel parameters. 

Replace the *ro single quite *parameters from the *kernel *line with *rw init=/bin/bash *and press Ctrl+x to boot.

 Wait for all the boot-up processes to finish. Remount  / as rw:
```
mount -o rw,remount /
```

Lock the root account password:
```
passwd -dl root
```

Set up a new password for your user:
```
passwd *username*
```

and reboot the system:```
reboot
```

---

