---
title: "Name of Machine"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by sniper8752 on 2012-05-08
How do I find the name of my Ubuntu machine?

---

### Post by PaulW2U on 2012-05-08
In a terminal window type ```
hostname
```

---

### Post by sniper8752 on 2012-05-08
alright; thanks!

i am trying to do [the last step]("http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/"), but it tells me, "command not found".  Am I doing something wrong?

---

### Post by Holy bible on 2012-05-08
try using command ```
lshw
```

---

### Post by papibe on 2012-05-08
> **sniper8752 said:**
> i am trying to do [the last step]("http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/"), but it tells me, "command not found".  Am I doing something wrong?

Do you refer to this?
```
\\ubuntumachine\username
```
That is what you use in a Windows machine to access your share. Is that it?

Regards.

---

### Post by sniper8752 on 2012-05-08
> **papibe said:**
> Do you refer to this?
```
\\ubuntumachine\username
```
That is what you use in a Windows machine to access your share. Is that it?

Regards.

I get this error:

```
The network path was not found.
```

*Was doing it in ubuntu before, but did it now in windows 7.

---

### Post by sniper8752 on 2012-05-08
> **Holy bible said:**
> try using command ```
lshw
```

how do I use this command?  still trying to learn the commands

---

### Post by papibe on 2012-05-08
Try this on Windows:

Open 'Network Places' or Network on your File Manager and refresh. Does your Ubuntu machine appears on the list?

Regards.

---

### Post by sniper8752 on 2012-05-08
I am in the Network panel, and it is not showing up there.  I have the Ubuntu OS installed on my windows machine, on oracle virtual box.  not sure if that makes a difference or not.

---

### Post by chamber on 2012-05-08
It depends if your ubuntu vm and windows machine are on the same LAN. 

Check the ip address subnet mask and default gateway of them both.

---

### Post by papibe on 2012-05-08
Yes, it does.

By default (at least in Ubuntu) VirtualBox set the VM guest on another network (called NAT). Try changing it to 'Bridge':

This is the steps for the VB's Ubuntu version, but they should be very similar for yours:
[LIST]
[*]Shutdown your virtual machine, so that you are back on VirtualBox without any guest running.
[*]Select your Linux machine and press 'Settings'.
[*]In the new window, select Network from the list on the left.
[*]Change the field 'Attached to' from NAT to 'Bridge Adapter'.
[*]Start your virtual machine again.
[/LIST]

I hope that helps, and tell us how it goes.
Regards.

---

### Post by sniper8752 on 2012-05-08
> **chamber said:**
> It depends if your ubuntu vm and windows machine are on the same LAN. 

Check the ip address subnet mask and default gateway of them both.

just use "ifconfig" in ubuntu?  this is like ipconfig?

---

### Post by sniper8752 on 2012-05-08
> **papibe said:**
> Yes, it does.

By default (at least in Ubuntu) VirtualBox set the VM guest on another network (called NAT). Try changing it to 'Bridge':

This is the steps for the VB's Ubuntu version, but they should be very similar for yours:
[LIST]
[*]Shutdown your virtual machine, so that you are back on VirtualBox without any guest running.
[*]Select your Linux machine and press 'Settings'.
[*]In the new window, select Network from the list on the left.
[*]Change the field 'Attached to' from NAT to 'Bridge Adapter'.
[*]Start your virtual machine again.
[/LIST]

I hope that helps, and tell us how it goes.
Regards.

I am able to access the virtual box.  now, nothing is showing when i log in with my credentials.  isn't there suppose to be something, like documents, videos, or at least files?

---

### Post by jerome1232 on 2012-05-08
only if you shared them from inside Ubuntu. Right click the folders you want shared and select 'sharing options'

---

### Post by forrestcupp on 2012-05-08
Why don't you just use the "Shared Folders" option in VirtualBox? You don't have to set up networking; you can just set up shared folders from within VirtualBox to use for sharing files between your guest and host OSs.

---

### Post by sniper8752 on 2012-05-08
> **forrestcupp said:**
> Why don't you just use the "Shared Folders" option in VirtualBox? You don't have to set up networking; you can just set up shared folders from within VirtualBox to use for sharing files between your guest and host OSs.

how do I do that?

---

### Post by jerome1232 on 2012-05-08
> **forrestcupp said:**
> Why don't you just use the "Shared Folders" option in VirtualBox? You don't have to set up networking; you can just set up shared folders from within VirtualBox to use for sharing files between your guest and host OSs.

That works for Guest to host sharing, but not Host to guest. I was under the impression the OP was trying to setup sharing from Host to Guest.

---

### Post by papibe on 2012-05-08
> **sniper8752 said:**
> I am able to access the virtual box.  now, nothing is showing when i log in with my credentials.  isn't there suppose to be something, like documents, videos, or at least files?

Now that you can 'see' the server, you should test your home share by running the other command on Windows:
```
\\ubuntumachine\username
```
(be sure to use the correct machine and user name).

Regards.

---

### Post by sniper8752 on 2012-05-08
> **jerome1232 said:**
> I was under the impression the OP was trying to setup sharing from Host to Guest.

Both ways would be nice.

---

### Post by sniper8752 on 2012-05-08
> **papibe said:**
> Now that you can 'see' the server, you should test your home share by running the other command on Windows:
```
\\ubuntumachine\username
```
(be sure to use the correct machine and user name).

Regards.

It still doesn't seem to work.  I am still able to see it on the Network screen though in windows 7.

---

### Post by forrestcupp on 2012-05-09
> **jerome1232 said:**
> That works for Guest to host sharing, but not Host to guest. I was under the impression the OP was trying to setup sharing from Host to Guest.

What? I have Windows 7 as a guest for my Ubuntu 12.04 host in VirtualBox. I've set up my Ubuntu host's /home folder to be my shared folder in VirtualBox, and I can access and modify files in those folders from both the host and guest. The host's /home folder shows up as a second drive in my Windows 7 guest. If you're just trying to share files between the host and guest, there's no reason at all that you need to go through the trouble of trying to set up networking. Why would you send files through the LAN when you can just share them on the same hard drive on the same PC?

---

### Post by sniper8752 on 2012-05-09
when I try to share my home folder, i get the error,

```
'net usershare' returned error 255: Ignoring unknown parameter""security"
net usershare add: share name username is already valid system user name
```

---

### Post by jerome1232 on 2012-05-09
> **forrestcupp said:**
> What? I have Windows 7 as a guest for my Ubuntu 12.04 host in VirtualBox. I've set up my Ubuntu host's /home folder to be my shared folder in VirtualBox, and I can access and modify files in those folders from both the host and guest. The host's /home folder shows up as a second drive in my Windows 7 guest. If you're just trying to share files between the host and guest, there's no reason at all that you need to go through the trouble of trying to set up networking. Why would you send files through the LAN when you can just share them on the same hard drive on the same PC?

You actually sort of said it in your post.

What I mean is, you can't access a file on the guest, unless you go to the guest and copy it to the machine folder on the host, if you setup networking, in addition, then you can 'pull' files from the guest at your whim as well. Hopefully you understand what I am saying.

---

### Post by forrestcupp on 2012-05-09
> **jerome1232 said:**
> You actually sort of said it in your post.

What I mean is, you can't access a file on the guest, unless you go to the guest and copy it to the machine folder on the host, if you setup networking, in addition, then you can 'pull' files from the guest at your whim as well. Hopefully you understand what I am saying.

I understand. I just think it's a lot easier to use VirtualBox's shared folders and be mindful of that while you're in your guest. In my guest OS, I actually use the shared /home folders to store all of my files so I never have to worry about it. If for some crazy reason I need some obscure program file, it doesn't take that long to restore a snapshot state and copy it over to the shared folder.

---

