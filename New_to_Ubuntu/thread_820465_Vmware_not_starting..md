---
title: "Vmware not starting."
date: 2008-06-06
forum: New to Ubuntu
---

### Post by rraj.be on 2008-06-06
When i create my new virtual machine in vmware its displaying the following error.

```
Unable to change virtual machine power state: The process exited with an error:
End of error message.
```

What can i do to solve this

---

### Post by rraj.be on 2008-06-06
I tried with both dynamic and Fixed disk allocation but both resulted the same.

---

### Post by kpkeerthi on 2008-06-06
Run the vmware config tool and try starting your VM.
```
sudo vmware-config.pl
```

---

### Post by rraj.be on 2008-06-06
The reult is

```
raj@raj-workstation:~$ sudo vmware-config.pl
[sudo] password for raj: 
sudo: vmware-config.pl: command not found
raj@raj-workstation:~$ 

```

---

### Post by kpkeerthi on 2008-06-06
> **rraj.be said:**
> The reult is

```
raj@raj-workstation:~$ sudo vmware-config.pl
[sudo] password for raj: 
sudo: vmware-config.pl: command not found
raj@raj-workstation:~$ 

```

Thats strange.

```
sudo updatedb
```

Now try to find the executable:
```
locate vmware-config.pl
```

---

### Post by rraj.be on 2008-06-06
Its just blinking

```
raj@raj-workstation:~$ sudo updatedb
raj@raj-workstation:~$ locate vmware-config.pl
raj@raj-workstation:~$ 


```

---

### Post by Duck2006 on 2008-06-06
The info in this link may help with getting VMWare going.

[http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html)

---

### Post by TalioGladius on 2008-06-06
vmware-config.pl is in /usr/bin. 

Hardy?  If so download the vmware-any-any-update116 (just google a download link for it).  Extract and run ./runme.pl.

---

### Post by rraj.be on 2008-06-06
I have just installed vm ware server today morning.

So i think there is no need to upgrade.

[in synaptic too its showing available and installed versions are same.]

---

### Post by TalioGladius on 2008-06-06
> **rraj.be said:**
> I have just installed vm ware server today morning.

So i think there is no need to upgrade.

[in synaptic too its showing available and installed versions are same.]Have you ever gotten a VM to start?  I really think you need to run the any any patch, unless you've already done so. I've yet to see VMWare work at all on linux without that patch.

---

### Post by rraj.be on 2008-06-06
Just a two days ago i reinstalled my ubuntu and after that just now i am trying to run my vmware.

If patches shud be applied then where can i get it.

---

### Post by TalioGladius on 2008-06-06
> **rraj.be said:**
> Just a two days ago i reinstalled my ubuntu and after that just now i am trying to run my vmware.

If patches shud be applied then where can i get it.[http://groups.google.com/group/vmkernelnewbies/files](http://groups.google.com/group/vmkernelnewbies/files)


You want vmware-any-any-update-116.tgz.  Just extract it, cd to that directory, and run 'sudo ./runme.pl'.  Follow the instructions, you can generally take all of the defaults.

---

### Post by rraj.be on 2008-06-06
The file is missing in that location.

---

### Post by diablo75 on 2008-06-06
Browse to /var/lib/VMware  (or "VMware Server", can't remember exactly) and in there should be a folder called Virtual Machines.

In side that, a folder for each machine.  Go into the folder for the machine you're trying to start.

If you see any files with the word "READLOCK" or "WRITELOCK" in the extension, delete them, and then try again.

Edit:  After doing some googling, the above suggestion probably isn't the cause of your problem, but it is a problem I've run into on a couple of occasions.  It occurs when VMware is killed abruptly sometimes during a full system shutdown...

TRY THIS:  Open your Home Folder, hit CTRL-H to reveal hidden folders, find the ".vmware" folder, Right-Click and hit Properties, and then change the owner to yourself and make sure you have read-write access to the folder and all subfolders (there's a checkbox to make the change recursive to all sub folders and files).

---

### Post by rraj.be on 2008-06-06
There is nothing like that

the two  files are with extensio of vmx and .vmdx

---

### Post by bcom on 2008-06-06
I found a very helpful sticky in the Ubuntu Virtualization forum.

The sticky is How to VMWare in Ubuntu 8.04.  

I followed the instructions posted here and was able to get vmware server working after upgrading from Ubuntu 7.10.

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

---

