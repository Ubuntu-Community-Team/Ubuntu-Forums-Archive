---
title: "[SOLVED] Need serious help!"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by JimmyJim on 2008-06-20
Agh, I'm going insane :shock:! Being the idiot I am, I did a chown command on something I shouldn't have since I was having issues with permissions. I didn't know this would mess everything up! 

Now the following doesn't work:
[LIST]
[*]sudo commands
[*]my internet connection
[*]reading a USB stick
[/LIST]
and probably a lot more!

I'm using Ubuntu 8.04 -- If you need any specific information, let me know.

Can anyone here help me please? The only thing preventing me from going back to Windows at this point is Linux's security (my parent's computer, which I share networks with, probably has malware) and the fact that I can't back anything up on USB because Linux is currently preventing it! ](*,)

---

### Post by JimmyJim on 2008-06-20
Honestly, I'm at a point where I feel like going back to Windows. I know you guys are loyal to Linux, but you've gotta understand that although I like the open source environment and nice features, its been a big hassle for me. If you answer the following questions I will return to XP:

[LIST=1]
[*]How can I get my USB stick to read again so I can backup my files? (I found a tutorial online but it didn't work out)

[*]Although not related to Linux, how can I prevent any malicious transfer over an Windows XP network to my desktop? I think my parents' computer might have malware, and if I can guarantee my computer's security won't be compromised because of it, I'll happily return to XP.
[/LIST]

Thank you very much in advance -- you might save my sanity!

---

### Post by ruffEdgz on 2008-06-20
If you go into your terminal and type 

```

history | less 

```

can you see which file you did chmod so we can better understand the situation.

I'm sorry that you are frustrated and I will try my best to help out so we can get things back to normal.

---

### Post by JimmyJim on 2008-06-20
> **ruffEdgz said:**
> If you go into your terminal and type 

```

history | less 

```

can you see which file you did chmod so we can better understand the situation.

I'm sorry that you are frustrated and I will try my best to help out so we can get things back to normal.

Heh, thanks for helping. I'll quickly go back to my computer now and do this. I'll edit this post with the answer in about 2 minutes.

EDIT:

I think this is where it went bad:

"sudo chown -R user/tmp"

I was trying to permit access to a file, that was probably the bad mistake. If you don't think thats it, let me know!

NOTE: I'm having to write this information out by hand since my printing network stopped working after an update a week ago and my internet connection just stopped working on my Linux machine, and the USB drive doesn't work. So if any responses are delayed, thats why.

---

### Post by JimmyJim on 2008-06-20
Ah, wait a sec, you said chmod? I don't remember doing that before the problems occurred, but I can check again if you like.

EDIT:

Here is the chmod that I did, note that I did this AFTER the problems occured in attempt to fix it (I saw it in another post):

"chmod 4755 /usr/bin/sudo"

This was an attempt to get sudo working after problems occurred.

---

### Post by ruffEdgz on 2008-06-20
Do you remember doing any kind of command or activity before all these 'things' happened with the sudoers and usb not mounting?

Any and everything you can remember would be helpful

::EDIT::

Just a question but have you checked your /etc/passwd or /etc/group and just to check your account. Also, try adding yourself to the 'admin' group which should be like #110

Just a thought...

Also, tell me the chown that you did as well which is probably what I meant to say in the first post I made but was an idiot and place chmod :P

---

### Post by JimmyJim on 2008-06-20
> **ruffEdgz said:**
> Do you remember doing any kind of command or activity before all these 'things' happened with the sudoers and usb not mounting?

Yes, I think I used chown to try to permit certain folders; the one I showed you is all thats in the log.

> **ruffEdgz said:**
> Just a question but have you checked your /etc/passwd or /etc/group and just to check your account.

No, what should I be looking for?

> **ruffEdgz said:**
> Also, try adding yourself to the 'admin' group which should be like #110

I'm not sure how to do that.

> **ruffEdgz said:**
> Also, tell me the chown that you did as well which is probably what I meant to say in the first post I made but was an idiot and place chmod :P

Yes, that chown that I showed was probably what messed everything up.

---

### Post by JimmyJim on 2008-06-20
Here's what I did chronologically, although my memory is fuzzy:

[LIST=1]
[*]I tried "sudo chown -R user/tmp" to permit access to a folder, where 'user' is my account name.

[*]I THINK things went wrong after this; it seems that way from my terminal log anyway. I noticed sudo stopped working. I rebooted and tried this in recovery console:
```
chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo
```

(This came from here: [http://ubuntuforums.org/showthread.php?t=219767](http://ubuntuforums.org/showthread.php?t=219767))


[*]I rebooted again, but there were still problems. I tried sudo and instead of the original error (same as the one in this link: [http://ubuntuforums.org/showthread.php?t=219767](http://ubuntuforums.org/showthread.php?t=219767)), I got one saying "/etc/sudoers is owned by uid 1000, should be 0". 

[*]Whenever I use sudo now I get that error previously mentioned error "/etc/sudoers is owned by uid 1000, should be 0". I also noticed that my internet connection and USB device no longer worked. I'm not sure if that stopped working before or after the original chown.
[/LIST]

---

### Post by ruffEdgz on 2008-06-20
To check the /etc/passwd and /etc/groups you just need to do the command below:

```

less /etc/passwd 

less /etc/groups

```

PS: do you know your root password if not, I can show you how you can change it and login as root which could help you get any and all files out so you can delete the OS or what not :P

::edit::
Try and look at the permissions of /usr/bin/sudo by doing this command:
```

ls -al /usr/bin | grep sudo

```

tell me what you see from that in terms of 'wrx' and owner

---

### Post by Xerp on 2008-06-20
Sounds to me like a load of permissions got hosed. I'd try rebooting in rescue mode or from a live cd and then reinstall all packages.

---

### Post by JimmyJim on 2008-06-20
> **ruffEdgz said:**
> To check the /etc/passwd and /etc/groups you just need to do the command below:

```

less /etc/passwd 

less /etc/groups

```

I tried less /etc/passwd and I got a lengthy list. 
I tried less /etc/groups and it said it doesn't exist. (I'm not sure if thats the problem)

If you need anything specific, let me know. I don't know what I'm looking for here, and it would take me a long time to write out by hand!

> **ruffEdgz said:**
> PS: do you know your root password if not, I can show you how you can change it and login as root which could help you get any and all files out so you can delete the OS or what not :P

I know my root password. I can get my files that I want to backup, but I can't transfer them to my USB drive because Ubuntu gets an error when I plug it in!

> **ruffEdgz said:**
> Try and look at the permissions of /usr/bin/sudo by doing this command:
```

ls -al /usr/bin | grep sudo

```

I did that and here is what I got:
```

lrwxrwxrwx    1   user      root 4 2008-05-27 19:00 gksub -> gksa
- rwsr -xr -x 2   root      root 107872 2008-05-14 20:41 sudo
- rwsr -xr -x 2   root      root 107872 2008-05-14 20:41 sudoedit
```

---

### Post by JimmyJim on 2008-06-20
> **Xerp said:**
> Sounds to me like a load of permissions got hosed. I'd try rebooting in rescue mode or from a live cd and then reinstall all packages.

How do I reinstall all packages? If this'll make me lose data, I have to find a way to get the USB drive to read so I can backup some stuff.

---

### Post by Bigtime_Scrub on 2008-06-20
> **JimmyJim said:**
> How do I reinstall all packages? If this'll make me lose data, I have to find a way to get the USB drive to read so I can backup some stuff.



I think we should take this step by step from the start. 

So first of all is the USB mounted correctly? Does on icon of it show up on your desktop and if it does, can you look in it?

---

### Post by Nameless_one on 2008-06-20
I suggest you backup your data to a DVD or something like that and reinstall ubuntu. It will work fine as before, and then you might consider not fiddling with permissions and the like in the future ;) this will probably restore all functionality to your machine.

---

### Post by JimmyJim on 2008-06-20
> **Bigtime_Scrub said:**
> I think we should take this step by step from the start. 

So first of all is the USB mounted correctly? Does on icon of it show up on your desktop and if it does, can you look in it?

If by mounted correctly, you mean plugged in correctly, then yes. It worked before everything else stopped working.  The icon doesn't appear on my desktop, but it appears in my "Places" tab. I cannot look in it. If I click on it, I get the following warning: "Cannot mount volume: Error org.freedesktop.DBus.Error.AccessDenied"

---

### Post by JimmyJim on 2008-06-20
> **Nameless_one said:**
> I suggest you backup your data to a DVD or something like that and reinstall ubuntu. It will work fine as before, and then you might consider not fiddling with permissions and the like in the future ;) this will probably restore all functionality to your machine.

Hmm, yeah I think I'll do that instead. This will suck though, it took me awhile to get everything working and now my setup will be lost :(.

---

### Post by Nameless_one on 2008-06-20
You should consider trying this: [Making a seperate /home partition](http://www.psychocats.net/ubuntu/separatehome). That way, if something goes wrong, you get to keep all your settings, and after reinstalling ubuntu, simply reinstalling your favourite programs will bring everything back to normal very quickly. 

Also, [everything on that site](http://www.psychocats.net/ubuntu/separatehome) is useful to start you off on ubuntu. It's not a lot of reading material, and it' straight to the point. Most of the info you will need, in the beginning, is there. Afterwards you might want to check the link in my sig. That should keep you problem-free for a while!

---

### Post by JimmyJim on 2008-06-20
> **Nameless_one said:**
> You should consider trying this: [Making a seperate /home partition](http://www.psychocats.net/ubuntu/separatehome). That way, if something goes wrong, you get to keep all your settings, and after reinstalling ubuntu, simply reinstalling your favourite programs will bring everything back to normal very quickly. 

Also, [everything on that site](http://www.psychocats.net/ubuntu/separatehome) is useful to start you off on ubuntu. It's not a lot of reading material, and it' straight to the point. Most of the info you will need, in the beginning, is there. Afterwards you might want to check the link in my sig. That should keep you problem-free for a while!

OK, thanks. I'm burning a backup DVD right now as I type this, and I'll reformat soon. Thanks for the help everyone.

---

