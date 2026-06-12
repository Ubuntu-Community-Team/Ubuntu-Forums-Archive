---
title: "User not in sudoers anymore."
date: 2012-12-03
forum: New to Ubuntu
---

### Post by hencelence on 2012-12-03
I was trying to give my user (lenz) root privileges for running commands.
So I edited the sudoers file in /etc using gedit, and I added lenz  ALL=(ALL:ALL) ALL to the sudoers.

But I made an error any mistyped "lenz" for lenzi... Now my user (lenz) is not in the sudoers file anymore. When I try to edit the sudoers file, it:
```

lenz@lenz-Studio-1537:~$ sudo visudo /etc/sudoers
[sudo] password for lenz: 
lenz is not in the sudoers file.  This incident will be reported.

```

lenz is the only user (other than root) on this system.

How could I solve this problem? I'd need to log in as root and edit the sudoers file again, right?

Help me please...

---

### Post by steeldriver on 2012-12-03
IMO adding individual users to the sudoers file only makes sense if you want to grant / deny permission for individual commands

If you want to give a user general administrative privileges you just need to add them to the 'sudo' user group (or 'admin' on older versions of Ubuntu)

```
gpasswd --adduser *lenz *sudo
```You will need to do this as root from the recovery console if you don't have another valid sudo login. Then edit /etc/sudoers back to how it was before.

---

### Post by CaptainMark on 2012-12-03
Boot into a live cd/usb and use sudo from there to edit the file /etc/sudoers and correct your mistake

---

### Post by hencelence on 2012-12-03
Thanks for quick & helpful response, Captain Mark & Steeldriver. :)

> You will need to do this as root from the recovery console if you don't  have another valid sudo login. Then edit /etc/sudoers back to how it was  before.     
Indeed I'll have to use a recovery disk, because: 
```
lenz@lenz-Studio-1537:~$ sudo gpasswd --add lenz sudo
[sudo] password for lenz: 
lenz is not in the sudoers file.  This incident will be reported.
  
```When logged in as root, what would be the commands I'd have to type to be able to edit/reset the sudoers file? Do I have to use vi to edit it?

---

### Post by steeldriver on 2012-12-03
You should use 'visudo' regardless of how you are logged in afaik - iirc it provides some basic checks to stop you screwing up the file. The actual editor it uses under the hood will depend on how your default editor is set.

You *could* do everything from a live cd / usb boot if you prefer - personally I think it's more work though (need to mount the original root partition etc.)

---

### Post by hencelence on 2012-12-03
> **steeldriver said:**
> You should use 'visudo' regardless of how you are logged in afaik - iirc it provides some basic checks to stop you screwing up the file. The actual editor it uses under the hood will depend on how your default editor is set.

You *could* do everything from a live cd / usb boot if you prefer - personally I think it's more work though (need to mount the original root partition etc.)

So how would I do it from the recovery console?

---

### Post by steeldriver on 2012-12-03
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by hencelence on 2012-12-03
Thanks a lot, steeldriver.

I'll be back in 20mins to tell you whether or not this is to be tagged [solved].

---

### Post by Impavidus on 2012-12-03
In which case you can tag it as [solved] yourself, see the thread tools near the top of this page.

---

### Post by hencelence on 2012-12-03
Worked fine, thanks for your help.

---

