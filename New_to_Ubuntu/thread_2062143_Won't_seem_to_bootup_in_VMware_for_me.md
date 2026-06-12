---
title: "Won't seem to bootup in VMware for me?"
date: 2012-09-24
forum: New to Ubuntu
---

### Post by CraigAnderson89 on 2012-09-24
Hey all, I recently downloaded Ubuntu from here : [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)
I downloaded the image file "ubuntu-10.04.4-desktop-i386" and mounted it onto VMware. Whenever I boot up, I get this screen: [http://i.imgur.com/P5vNY.png](http://i.imgur.com/P5vNY.png)

For those who can't see the IMG I get a black screen upon starting the VM saying : > Linux ubuntu 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 G NU/Linux
Ubuntu 10.04.4 LTS

Welcome to Unbuntu!
* Documentation [https://help.ubuntu.com/](https://help.ubuntu.com/)

To run a command as administrator (user "root"), use "sudo <command>".

ubuntu@ubuntu:~$

Has anyone encountered this problem and if so what did they do to fix it?

---

### Post by einonm on 2012-09-24
I don't think there is anything wrong with this - looks like a server install to me. A server install doesn't have a graphical interface.

Which exact link did you download ubuntu from? I suggest revisiting the download page, and selecting a link from under the 'desktop CD' heading, not anything under the 'server install CD' heading.

edit...
Ok, just re-read the file you downloaded. Perhaps the file name is wrong? There is a newer version available, 12.04LTS ([http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)) Why not try that?

---

### Post by cwsnyder on 2012-09-24
1) Did you check the MD5SUM or SHA1SUM, etc. for the file after you downloaded it to make sure that the download was valid?

2) Did you attempt to type **gdm** or **startx** at the command prompt (**$**)?

---

### Post by CraigAnderson89 on 2012-09-24
> **cwsnyder said:**
> 1) Did you check the MD5SUM or SHA1SUM, etc. for the file after you downloaded it to make sure that the download was valid?

2) Did you attempt to type **gdm** or **startx** at the command prompt (**$**)?

Yeah when I do startx I get this : [http://imgur.com/UZWpW](http://imgur.com/UZWpW)

Also I've tried deleting, then re-intsalling XORG, and reconfiguring, but that hasn't worked at all for me.

---

### Post by drmrgd on 2012-09-24
Are you sure that you didn't install the server version of Ubuntu?  That might be why you can't get an X session started.  Verify that you got the Desktop version and not the Server version.

---

### Post by CraigAnderson89 on 2012-09-24
> **drmrgd said:**
> Are you sure that you didn't install the server version of Ubuntu?  That might be why you can't get an X session started.  Verify that you got the Desktop version and not the Server version.

I'm absolutely positive I downloaded "
[ubuntu-10.04.4-desktop-i386.iso]("http://releases.ubuntu.com/lucid/ubuntu-10.04.4-desktop-i386.iso")  14-Feb-2012 11:51  694M  Desktop CD for PC (Intel x86) computers (standard download)"

Which specifies that it's a desktop, I suppose I'll try downloading the latest version posted.

---

### Post by cwsnyder on 2012-09-30
Did you consider a pre-made virtual appliance under VMWare?  [https://solutionexchange.vmware.com/store/category_groups/19](https://solutionexchange.vmware.com/store/category_groups/19) is a link to the virtual appliance store.  They do have 10.04 desktop appliances, I don't know if they are already updated to 10.04.4.

---

