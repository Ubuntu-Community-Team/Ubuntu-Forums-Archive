---
title: "chmod question: the &quot;+&quot;at the end of &quot;rwx&quot;"
date: 2012-06-10
forum: New to Ubuntu
---

### Post by bikefreakvinnie on 2012-06-10
I've almost got zoneminder working and i'm sure its just a case of changing video permissions!..

I've installed zoneminder on my laptop and also on a server (ubuntu 12.04)...

zoneminder is working fine on the laptop or local host with these video permissions:
crw-rw----+ 1 root video

but on the server which i can't get working yet, video has these permissions:
crw-rw---- 1 root video

I don't understand what the + is at the end of the owner, group, and everyone else permissions. There is one other thing which may or may not have anything to do with it, i added user www-data to  video during installation, but www-data is a member of video on the server (as far as i can see anyway)...

appreciate any help on this one...

---

### Post by matt_symes on 2012-06-10
Hi

The + at the end of the permissions highlights an access control list in the file.

You can use the command

```
getfacl <filename>
```

To view the ACL for that file.

You can use

```
setfacl
```

sets an ACL for a file.

This may explain it better than i can.

[http://www.ghacks.net/2010/01/28/further-control-of-linux-files-with-acl/](http://www.ghacks.net/2010/01/28/further-control-of-linux-files-with-acl/)

What issues are you currently having ?

Kind regards

---

### Post by bikefreakvinnie on 2012-06-14
Thanks for that matt,
sorry about the late reply its been a busy week!

I've had a good look at the ACL article and installed it...
On my laptop which has zoneminder successfully working the video permissions are:

# file: dev/video0
# owner: root
# group: video
user::rw-
user:bikefreakvinnie:rw-
group::rw-
mask::rw-
other::---

However on the server which i'm trying to get working the video permissions are:

# file: dev/video0
# owner: root
# group: video
user::rw-
group::rw-
other::---

I recon if I could have the same permissions on the server, then zoneminder would work, could anyone explain what the differences or how i should solve this one!

---

### Post by matt_symes on 2012-06-14
Hi

> **bikefreakvinnie said:**
> 
# file: dev/video0
# owner: root
# group: video
user::rw-
user:bikefreakvinnie:rw-
group::rw-
mask::rw-
other::---

However on the server which i'm trying to get working the video permissions are:

# file: dev/video0
# owner: root
# group: video
user::rw-
group::rw-
other::---


I have never installed zoneminder so i am not sure if changing the permissions will work, however i think it's a reasonable assumption.

What is your user name on the server ?

You can find this out from the console, if you are not sure by looking, at your command prompt or typing

```
whoami
```

When you have determined that you can use the setfacl command..

```
sudo setfacl -m u:<user_name>:rw- /dev/video0
```

Substitute <user_name> for, ahem, your user name :)

Assuming your user name on your server is the same as on your laptop and is bikefreakvinnie.

```
sudo setfacl -m u:bikefreakvinnie:rw- /dev/video
```

After you have run the command, check the permission with.

```
getfacl /dev/video0
```

Kind regards

---

### Post by bikefreakvinnie on 2012-06-16
Excellent! Thanks a mil for that Matt! Its finally working now! I've been chipping away on and off trying to get that goin for 3-4 wks now so happy days!..

There is one thing if I restart those permissions set are lost - perhaps there is a way of making these permanent...

again thanks a mil

---

### Post by matt_symes on 2012-06-16
Hi

> **bikefreakvinnie said:**
> Excellent! Thanks a mil for that Matt! Its finally working now! I've been chipping away on and off trying to get that goin for 3-4 wks now so happy days!..

Cool. You did the heavy lifting by identifying it was the permissions though. Have a gold star :KS

> There is one thing if I restart those permissions set are lost - perhaps there is a way of making these permanent...

Are you sure about this ? I though they should be persistent between reboots.

Kind regards

---

### Post by bikefreakvinnie on 2012-06-17
[QUOTE=matt_symes]Have a gold star [/QUOTE]

cheers for that - my first one on the forum!

> 
Quote:
There is one thing if I restart those permissions set are lost - perhaps there is a way of making these permanent...
Are you sure about this ? I though they should be persistent between reboots.

yeh just checked it again now - your right they do seem to be permanent!

thanks again!

---

### Post by matt_symes on 2012-06-18
Hi

> yeh just checked it again now - your right they do seem to be permanent!

Just to say, if you are still having trouble with the permissions you may have to add ```
acl
``` to the options of the partition in your /etc/fstab.

Is it working for you after a reboot ?

Kind regards

---

### Post by bikefreakvinnie on 2012-06-19
I did see that in the link about ACL alright...
But since the permission I'm changing is not for a partition but for a video I did not edit the /etc/fstab file. Not sure if I should still do this... However it all seems to be working fine now even after a reboot!
Cheers for that!

---

