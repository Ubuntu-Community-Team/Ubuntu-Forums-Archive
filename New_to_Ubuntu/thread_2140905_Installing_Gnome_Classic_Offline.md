---
title: "Installing Gnome Classic Offline"
date: 2013-05-01
forum: New to Ubuntu
---

### Post by betatesterz on 2013-05-01
Hi all,

I am new to ubuntu and to this forum. Posting this as [ubuntu] rather then [edubuntu] because I believe the real question lies in the integration.

I have 2 ISOs downloaded. 
1. UbuntuServer 12.10
2. Edubuntu 12.10

Edubuntu comes with option of installing GNOME classic, that means it must have the gnome-session-fallback somewhere in the DVD/ISO. 

Now, 
- I have installed UbuntuServer on a machine which does not have internet connection. 
- I want to add a Gnome fallback desktop without internet
- I have added Edubuntu DVD as a repository using apt-cdrom
- I have fired apt-get update

So far, I can only see some 21 packages  available for installation and it does not include gnome-session-fallback. Am I doing something wrong? Is it  possible? 

It seemed possible to me initially because logically the DVD which allows gnome classic to be installed should also allow it to be installed on top of already  installed ubuntu server from the same line (12.10). 
When I did vice-versa (i.e. first install Edubuntu and then add Ubuntu-Server DVD in apt repository) I was able to install available products in that DVD offline. il.e. openssh-server mysql-server etc.

Please help me out. 

Thanks.

---

### Post by betatesterz on 2013-05-01
Hi Folks, 

Did I post it to the right forum/section? I don't see anyone replying, where as I am seeing a lot of people replying to other threads.
Please let me know if I/Moderator needs to move this to some other section

---

### Post by claracc on 2013-05-01
> **betatesterz said:**
> Hi all,

I am new to ubuntu and to this forum. Posting this as [ubuntu] rather then [edubuntu] because I believe the real question lies in the integration.

I have 2 ISOs downloaded. 
1. UbuntuServer 12.10
2. Edubuntu 12.10

Edubuntu comes with option of installing GNOME classic, that means it must have the gnome-session-fallback somewhere in the DVD/ISO. 

Now, 
- I have installed UbuntuServer on a machine which does not have internet connection. 
- I want to add a Gnome fallback desktop without internet
- I have added Edubuntu DVD as a repository using apt-cdrom
- I have fired apt-get update

So far, I can only see some 21 packages  available for installation and it does not include gnome-session-fallback. Am I doing something wrong? Is it  possible? 

It seemed possible to me initially because logically the DVD which allows gnome classic to be installed should also allow it to be installed on top of already  installed ubuntu server from the same line (12.10). 
When I did vice-versa (i.e. first install Edubuntu and then add Ubuntu-Server DVD in apt repository) I was able to install available products in that DVD offline. il.e. openssh-server mysql-server etc.

Please help me out. 

Thanks.

I don't know why installing first ubuntu-server and adding edubuntu DVD as repository doesn't allow you to install gnome-panel, perhaps software dependencies?.

Only I can give you two links which perhaps can help you to fix the problem:

[http://ubuntuforums.org/showthread.php?t=1900550](http://ubuntuforums.org/showthread.php?t=1900550), about how to install software off line

[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_Ubuntu_Software_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_Ubuntu_Software_Repositories), in particular see CD-ROM/DVD part for checking you have followed the required steps.

---

### Post by betatesterz on 2013-05-01
@claracc: Many thanks for the links. 

Regarding the first link, it uses synaptic. I can try that workaround for now. However it means re downloading required packages and its dependencies. I was kind of hoping I don't have to, as I had already downloaded a huge edubuntu dvd containing a lot of software/applications :) 

I had actually successfully added the DVD as repository and I can install other packages from it. The thing is I can not even see gnome-session-fallback anywhere in the list. So if probably someone has any ubuntu dvd (edubuntu/previous LTS versions, anything) containing this package (gnome-session-fallback) can check it out for me on their VM, it would be really great.

Meanwhile, I will try the workaround.

Thanks

---

### Post by Cheesemill on 2013-05-01
What you're attempting isn't going to be possible, that's not how the DVD's are arranged.

A Live CD of any of the Ubuntu variants doesn't actually contain the .deb files needed to install all of the packages it contains.

Take the Lubuntu Live CD as an example, when you use it to install Lubuntu onto your computer it doesn't install all of the required packages one by one. Instead it copys an image of an already installed system onto your hard drive (this is the same image the Live CD runs from). If you want a system that installs by using the apt-get command to install all of the required packages from their .deb files then you need to use the Alternate CD to install with instead. If you take a look at the contents of the 2 CD's you will see that the Live CD is mainly a large .squashfs file, this is the compressed image that is used to install the system whereas if you look at the Alternate CD you'll find all of the individual .deb files needed that make up a Lubuntu system.

 You can look at this as being the same difference between installing Windows by restoring an image of your drive (the Live CD) or by installing Windows and then installing all of your applications from their .exe installers (the Alternate CD).

Unfortunately all of the alternate install CD's (except Lubuntu) were dropped several releases ago, there is no longer an Edubuntu Alternate install DVD available for download that contains the packages you require.

---

### Post by betatesterz on 2013-05-04
That's really unfortunate :( That seems to answer why I am not able to add it in repository. But, again, I am able to do so using UbuntuServer. i.e. If I install any ubuntu flavor and then add UbuntuServer iso in repository I am able to install all the important software I need like PHP MySQL Apache etc. So probably UbuntuServer DVD is not using Image, but actually using packages.

---

### Post by Cheesemill on 2013-05-04
> **betatesterz said:**
> But, again, I am able to do so using Ubuntu Server. i.e. If I install any ubuntu flavor and then add Ubuntu Server iso in repository I am able to install all the important software I need like PHP MySQL Apache etc. So probably Ubuntu Server DVD is not using Image, but actually using packages.

I forgot to mention that earlier, the Ubuntu Server CD is the only other exception. It isn't a Live CD, instead it uses the same text mode installer and lots of deb files approach as the Alternate CD's. Basically if you can run a live session from a CD then it won't contain all of the individual deb files needed to install it.

Is there any good reason that you need to run 12.10? For servers it's usually recommended to install LTS releases such as 12.04 instead as they tend to be more stable and are supported for much longer, 12.04 is supported until 2017 whereas if you use 12.10 you only have a year left before you would have to upgrade your server.

However, the main advantage in your situation to installing 12.04 instead of 12.10 is that the alternate installation CD's are still available. This means that you could install 12.04 Server and then use the Ubuntu 12.04 alternate CD to install any other packages from.

---

