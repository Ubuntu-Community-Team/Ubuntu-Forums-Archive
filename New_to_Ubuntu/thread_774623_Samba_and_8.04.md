---
title: "Samba and 8.04"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by GrahamCable on 2008-04-29
This is my first go with Linux.

Ubuntu installed OK
Upgraded to 8.04.  Easy to do & it seemed to work.
Added NTFS app so I can see my Windows volume. Easy & it worked
Added Samba. Easy to do & said all OK but .....
When I try to start it it crashes.  No indication of what the problem is.

Internet connects OK so I am assuming the Network adaptor is OK (100MHz, on board)

Can anyone help?  First, does it work OK in 8.04, then where do I look for possible causes.

Many thanks

---

### Post by screate on 2008-04-29
I am having the same issue.

---

### Post by mikeyphi on 2008-04-29
Could you give some info on what you are using Samba for?
How are you trying to 'start it'?

---

### Post by GrahamCable on 2008-04-30
> **mikeyphi said:**
> Could you give some info on what you are using Samba for?
How are you trying to 'start it'?
Thanks for responding.

I want to link this PC into a Windows Workgroup, possible to use it as a Web server, but really this is me trying to get to grips with Linux & its usability, so I just want to do it. 

I chose Ubuntu because I am not a technician, although I do have a pretty good understanding & expereince of Windows & the underlying technologies eg TCP/IP, firewalls, etc .  I don't want to have to rely upon command line based tools.

I am starting it via an item called Samba that has appeared on System-Administration menu.

Don't know if this is relevant, but the first time I installed Samba (and after it had crashed) I was able to see the PC from an XP macahine in a MSHome workgroup, but could not access it in anyway (I guess because I had not been able to specify any shares).  I have removed Samba since then & re-installed it, but now I don't even get that.

Regards

---

### Post by mikeyphi on 2008-04-30
OK!
Now I know where you're at!!
You need to enable sharing under your windows OS.
Then you need to enable sharing under your Ubuntu OS - you knew that already!
In Ubuntu right-click on the Folder you want to share, select Properties/Share tab - tick the first box and enter a share name. You will be prompted to install Samba if it's not installed. All should be good following a reboot. When accessing the shared folder you will be asked for username/password - I used my normal system details.
You might have to change the 'group' name - I believe it's WORKGROUP by default in Ubuntu, but the name must be the same for both OSs

Ask again if there are still issues.

---

### Post by bilal.17 on 2008-04-30
i have the same issue, samba crashes after i try to start it from system->administration->samba

---

### Post by bilal.17 on 2008-04-30
I forgot to mention, that it works perfectly on my desktop where on my laptop it crashes the same way as mentioned above.

---

### Post by hyper_ch on 2008-04-30
please post the output of:
```

sudo /etc/init.d/smb restart

```

---

### Post by GrahamCable on 2008-05-03
> **mikeyphi said:**
> OK!
Now I know where you're at!!
You need to enable sharing under your windows OS.
Then you need to enable sharing under your Ubuntu OS - you knew that already!
In Ubuntu right-click on the Folder you want to share, select Properties/Share tab - tick the first box and enter a share name. You will be prompted to install Samba if it's not installed. All should be good following a reboot. When accessing the shared folder you will be asked for username/password - I used my normal system details.
You might have to change the 'group' name - I believe it's WORKGROUP by default in Ubuntu, but the name must be the same for both OSs

Ask again if there are still issues.
seem to be going backwards.

on restarting, I could not access the volumes that were previously accessable.  Not aware I had done anything.
In the end I found a video that suggested using the Shared Folders approach (in 7.10 but not 8.04).  

So I re-installed, that seemed to work OK re Samba, & I then installed NTFS.  All OK, but then now I cannot mount the volumes (but at least I can see them).  I now get a not authorised to mount message.  But I do have Manage Systems privileges

I do appreciate your help, but should I just give up & go back to Windows?

---

