---
title: "Need help with Samba"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Heicron on 2008-08-09
Greetings,

I am a new user to Ubuntu and just installed the latest version. I am having a problem connecting to the two other Windows computers on my wired network. Internet connection is working. It seems that Samba is not installed. Is there some documentation that can guide me step by step on installing Samba? I was able to download a Samba tarball but now I am lost as what to do with it.

Thanks,

Joe

---

### Post by perlluver on 2008-08-09
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba), that link should explain it all to you.

---

### Post by aloshbennett on 2008-08-10
If all you need to do is access shared folders on a windows machine, run 'smb://<windiows-machine-name>' at the run prompt (ALT F2).
You can install smb by doing 'sudo apt-get install smb'


If you want to share files, you would need to set up Samba.

---

### Post by Heicron on 2008-08-10
Thank you for links. I can now now see the Ubuntu computer on the Windows computers. I'll have to get the rest of the configuration now and try to get the printers working. I found some differences with the graphical configuration about the Windows shares. I'll probably be back with more questions.

Thanks for the help.

---

### Post by Heicron on 2008-08-15
I need more help configuring Samba.
I have Samba installed but it seems the graphical configuration module is not installed or I don't know how to get to it.
In the network settings box, the general tab only has two boxes:
	Host Name:
	Domain Name:
Nothing for Windows Networking for entering the description and workgroup.
The Ubuntu computer has the default "workgroup" name for work group. The Windows computers are in a workgroup with a specific name.
I tried to edit the Samba config.file to change the "workgroup" name but it would not let me save the file after making the change.

I have two Windows computers, one WinXP and one Vista on a home network with a router. My printer is on the Vista and shared but Ubuntu can't connect to it.
I can access the shared files on the Win-XP from the Ubuntu using Konqueror, box but cannot access the shared folder "public" on the Ubuntu box which does appear on the Windows Network of both computers. Althought it is in the "workgroup" work group on both boxes. When I click on the shared Ubuntu folder I get a log-on: password: dialog box. I enter the Ubuntu log-on and password but get no access.
I don't quite have the hang of the proper syntax to do the manual configuration and was hoping to get things set up with the graphical configuration first and learn from there. But I was really stumped when I could not edit the Samba.config file.
As you can tell I am spoiled by Windows and am trying to work away from it.
Thanks for helping.

---

### Post by Iowan on 2008-08-15
> **Heicron said:**
> 
I tried to edit the Samba config.file to change the "workgroup" name but it would not let me save the file after making the change. Try it via **sudo** 
(eg.** sudo nano /etc/samba.smb.conf**)
 If you use **gedit** for an editor, use **gksu** or **gksudo** 
(eg **gksu gedit /etc/samba.smb.conf**)

BTW... I usually do a ```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
``` before I mess with the file - then I can put it back (or reference the original).

---

### Post by Heicron on 2008-08-15
I was able to do the file backup but none of the edit commands worked.
How else is one able to edit the smb.conf file?

---

### Post by Nepherte on 2008-08-16
```
gksudo gedit /etc/samba/smb.conf
```

This howto is pretty good: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
You can remove the [profiles], [netlogon] and [homes] section if you're only interested in file sharing. If you don't need printer sharing, you can remove [print$] and [printers] as well.

---

### Post by dentaku65 on 2008-08-16
See my HowTO :)
[http://ubuntuforums.org/showthread.php?t=890867&highlight=samba]("http://ubuntuforums.org/showthread.php?t=890867&highlight=samba")

---

### Post by Heicron on 2008-08-16
Thanks for the command line info and how to links.
I do want to share printers also. I was able to install one on Ubuntu and I was able to share it with the Vista box but not the XP box. I quess I have more homework to do.

Thanks all.

---

### Post by TJCIB on 2008-08-16
I like to use NFS for file sharing.
You can use Samba for printer sharing.

I know it is nice to have everything in one place, but I think NFS is *way* easier/faster/better than samba for file sharing.  

The printer setup on Samba is pretty straight forward and well documented.

You can setup NFS on Windows boxes with a (free) download from the microsoft website called SFU (service for unix administration).  I have 15 computers, a mixture of windows and linux all shared via NFS with no problems.

---

### Post by Heicron on 2008-08-16
After reading through some of the how-to I find that there are a few issues I still don't understand so I will ask a specific question one by one.
The first question mat resolve more than one issue.

How do I tell the Ubuntu computer that it is the wrong workgroup?
As I installed the system I entered the workgroup name, which is something other than "workgroup". But viewing the network from the Windows computers and even the Ubuntu computer, it shows that it is in the "workgroup" workgroup.
How do I resolve this?

---

### Post by john test on 2008-08-16
I think you need to edit the smbd.conf file and change the workgroup entry to match the one you need

---

### Post by Iowan on 2008-08-16
> **john test said:**
> I think you need to edit the smbd.conf file and change the workgroup entry to match the one you need**/etc/samba/smb.conf?**

---

### Post by Heicron on 2008-08-17
I was able to edit the smb.config file. The problem was that after I did the first edit I didn't restart Samba. So now I have the windows shares mounted and can access the Ubuntu shares from the Win boxes.
The problem now is that I can't see the shared printer that is on the Vista box. I tried the solution of entering the IP of the Vista box but I still get the not accessible error when trying to install a printer via Samba. 
I was able to install the printer on the Ubuntu box and print from Vista.

How do I print from Ubuntu to the Vista printer?

Thanks for the help.

---

