---
title: "Amarok + iPod"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Crope on 2008-04-25
Using the form on:
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

I've been trying to mount my iPod. When I try to connect, it says:

```
ssh: connect to host 192.168.1.103 port 22: Connection refused
read: Connection reset by peer

```

Up to the mounting point, I've followed the instructions exactly as listed. And yes, I have a properly jailbroken iPod touch.

Any ideas or help at all would be amazing, thanks guys.

---

### Post by Crope on 2008-04-25
Bump

---

### Post by Joeb454 on 2008-04-25
Hi there,

Somebody will be looking for a solution. What iPod are you using (5th Gen, 6th Gen, Touch etc.) This is actually quite important.

And it is considered bad forum practice to bump more than once every 24 _hours_ :) Just letting you know

---

### Post by Crope on 2008-04-25
I just said I had an iPod touch.

---

### Post by Joeb454 on 2008-04-25
My mistake sorry. I didn't see that part :oops:

I'm not sure if the latest iPod's are supported in Linux yet, I know there was initial issues with the way Apple had designed the software used to sync them

---

### Post by Crope on 2008-04-25
No problem.

According to google and videos, it seems quite possible. It just wont mount my iPod for some reason.

---

### Post by lunarcloud on 2008-04-25
It should work like all others, are you using gnome or kde3/kde4?
I know the libgpod and such has support for the touch. should be able to just pop up like an external hard drive.

if not, then maybe messing with [https://launchpad.net/~ipod-touch/+archive](https://launchpad.net/~ipod-touch/+archive) might help, but i doubt.

---

### Post by Crope on 2008-04-25
I'm using Gnome. When I plug it in, it pops up as a "Camera device". I cant find a way to access the files, though.

---

### Post by Crope on 2008-04-26
I've been messing around with it. I finally got the password prompt I've been looking for (I have 1.11 firmware), so I know the password is "alpine", but it's still not connecting! @_@

Here's the output:
'```
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added '192.168.1.102' (RSA) to the list of known hosts.
Connection closed by 192.168.1.102
root@192.168.1.102's password: 
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option
root@james-desktop:~# ipod-touch-mount
root@192.168.1.102's password: 

```

---

### Post by Crope on 2008-04-26
Bump ;)

---

### Post by Joeb454 on 2008-04-26
You're definitely sure the password is correct? And you know that Ubuntu will not show anything being typed in the terminal for your password?

---

### Post by Crope on 2008-04-26
Correct, and yes I realize that.

---

