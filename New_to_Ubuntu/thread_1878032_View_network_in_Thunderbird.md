---
title: "View network in Thunderbird"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by StrangerSa on 2011-11-09
Hi Guys, I am an Ubuntu noob and not ashamed to admit it :lolflag:

Am loving Ubuntu but have one frustrating glitch. Please can you assist. How do I get Thunderbird to read my network so that I can attach files from my server or other computer.

Thanks in advance.

---

### Post by mastablasta on 2011-11-09
> **StrangerSa said:**
> Hi Guys, I am an Ubuntu noob and not ashamed to admit it :lolflag:
 
Am loving Ubuntu but have one frustrating glitch. Please can you assist. How do I get Thunderbird to read my network so that I can attach files from my server or other computer.
 
Thanks in advance.
 
 
how does the network setup look like? are you trying to connect to another linux computer or maybe a computer running windows?
 
more informaiton will have to be provided, but i am guessing this has to do with file sharing...

---

### Post by nothingspecial on 2011-11-09
Title edited to reflect the problem.

---

### Post by davdo2004 on 2011-11-09
I have always just made a temp copy of the file to a local folder from my network if I want to attach it to a email. There is probably a way to do what you want but I have never been bothered to find out how.

---

### Post by alphacrucis2 on 2011-11-09
> **StrangerSa said:**
> Hi Guys, I am an Ubuntu noob and not ashamed to admit it :lolflag:

Am loving Ubuntu but have one frustrating glitch. Please can you assist. How do I get Thunderbird to read my network so that I can attach files from my server or other computer.

Thanks in advance.

Interesting. I would say that this is a bug in Mozilla apps. I tried it myself by connecting to a windows share using nautilus. The share then appears in nautilus and I also see it in the open file dialog for Libreoffice apps, gimp and several other apps but it isn't visible to either thunderbird or firefox. Should be reported on launchpad.

---

### Post by SeijiSensei on 2011-11-09
I'm guessing you're talking about files shared with Windows networking technologies?  Some Linux applications support smb:// style URLs to point to files on Windows systems, but Thunderbird doesn't appear to be one.

The simplest solution to your question is to mount the share directly into the filesystem tree with smbmount or "mount -t cifs". See [https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently) for details.

---

### Post by StrangerSa on 2011-11-10
> **davdo2004 said:**
> I have always just made a temp copy of the file to a local folder from my network if I want to attach it to a email. There is probably a way to do what you want but I have never been bothered to find out how.

This is what I do now, but I have thousands of clients and it is a schlep

---

### Post by StrangerSa on 2011-11-10
> **SeijiSensei said:**
> I'm guessing you're talking about files shared with Windows networking technologies?  Some Linux applications support smb:// style URLs to point to files on Windows systems, but Thunderbird doesn't appear to be one.

The simplest solution to your question is to mount the share directly into the filesystem tree with smbmount or "mount -t cifs". See [https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently) for details.

Thanks, I can see the network and even have a link via the launcher and the home folders, but Thunderbird just refuses to see it. I am not smart enough to work via the terminal

---

### Post by StrangerSa on 2011-11-10
> **davdo2004 said:**
> I have always just made a temp copy of the file to a local folder from my network if I want to attach it to a email. There is probably a way to do what you want but I have never been bothered to find out how.

Please be bothered :():P

---

### Post by davdo2004 on 2011-11-10
Sorry strangerSa but I am out of my depth with this one. I don't send a lot of attachments from my network so the inconvenience is only a minor issue for me.
There is a bug filed on launchpad started in 2007. The last post on that bug was from October 2011 and is still not fixed.  [https://bugs.launchpad.net/ubuntu/+source/mozilla-thunderbird/+bug/105088](https://bugs.launchpad.net/ubuntu/+source/mozilla-thunderbird/+bug/105088).
Maybe there will be some progress now Thunderbird is the default mail client, from what I have been reading, Evolution did not have this problem.

---

### Post by StrangerSa on 2011-11-11
Thanks anyway, I am sure that a fix will come soon, seems a lot of peeps out there want it, same as they wanted THB for Ubuntu

---

