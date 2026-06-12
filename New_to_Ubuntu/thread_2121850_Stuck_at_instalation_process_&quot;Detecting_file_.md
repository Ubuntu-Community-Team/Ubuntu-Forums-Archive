---
title: "Stuck at instalation process &quot;Detecting file systems&quot;."
date: 2013-03-03
forum: New to Ubuntu
---

### Post by mcmacker4 on 2013-03-03
I'm having LOTS of problems trying to install Ubuntu on an external USB hard drive.
My problem now is that, while installing (just after entering my login info) the Installation got stuck saying "Detecting file systems" and the console says:

```
** (firefox:17720): WARNING **: Failed to open webapp application path dir /usr/local/share/unity-webapps/userscripts: Error opening directory ' /usr/local/share/unity-webapps/userscripts' : No such file or directory
```

And said the same like 6 times but with different directories.

I don't know what to do, I thought it was doing fine (after 2 days of hard work trying to install this...)

---

### Post by Bashing-om on 2013-03-03
mcmacker4; Hi !
Is your main operating system Windows 7 or 8 ?? Perhaps UEFI is preventing the install .
Can you boot the install medium into the "try ubuntu" mode ?
[INDENT=2]
try'n to help

[/INDENT]

---

### Post by mcmacker4 on 2013-03-04
My main OS is Mac OS X 10.5.8, and, yes, I can boot in Try Ubuntu mode, in fact, I used gparted to manage the partitions I made in my External Hard Disk Drive.

---

### Post by Bashing-om on 2013-03-04
mcmacker4; From the error that you posted one may surmise that the browser can not connect. Are you attempting th use wireless as the interface ?
If so, perhaps the wireless drivers are not loaded, easiest solution in this event is to hook up wired first and after updates have completed, in the "Additional Drivers" utility choose a driver to install.
[INDENT=3]
hope this helps

[/INDENT]

---

### Post by mcmacker4 on 2013-03-04
I'm using an Ethernet to connect to the internet and it works perfectly with mac... Any other suggestions?

---

### Post by Bashing-om on 2013-03-04
mcmacker4; 
 The short response is no;
I will keep on this, see what I can come up with. 
Presently not making much sense to me that the installer is even aware of firefox at that time// The installer should be using means within the kernel for all 'net activity// Configuring DHCP for networking is one of the last steps the installer does.

Anyone else with ideas ???????

Don't know --research and ruminate time for me

---

### Post by mcmacker4 on 2013-03-04
Oh Sh*t!!! Sorry for bad language but I just realised I checked the checkbox that allowed to Update while installing.
May the problem be here??

---

### Post by Bashing-om on 2013-03-04
mcmacker4;
Nah, The standard is to do the 3rd party updates during install // That said I have seen post where it did cause problems. As this is a fresh install, all that will be lost is a bit of time to try and (re)install and not check that option; then do the updates/upgrade when install completes.

Maybe get a different error or more to work with if you do (re)install.[INDENT=2]
my opinion

[/INDENT]

---

### Post by mcmacker4 on 2013-03-05
Ok, I'll try. But for the moment (this goes for moderators) please do not close this thread as I will be posting here news about the installation. Some errors may occur and, if any show up, I will be posting them here.

---

### Post by mcmacker4 on 2013-03-05
I just tried to install it without downloading updates. Now, instead of giving me a firefox error it happens the same as all the other times I tried to install Ubuntu. It gets stuck just after saying:
```
Mar 5 20:02:36 ubuntu ubuquity[5942]: Step_before = stepUserInfo
```
And then it says: 
```
Mar 5 20:17:01 ubuntu CRON[15426]: (root) CMD ( cd / && run-parts --report /etc/cron.hourly)
```
And this will keep on appearing every hour. I know because it happened before...

---

### Post by Bashing-om on 2013-03-08
mcmacker4; Sorry to have left you high and dry, Things came up I had to attend to.

I admitt I am totally mistified as to what is happening, A cron job should not even be running at this point in the installation (same situation as firefox starting prior to this install attempt)

I am not familar with macs, so I may be out in left field with this: A bios setting for something like "secure Boot" (??) preventing installation of another operating system ?

Let's see what the drives look like;
boot up ubuntu's install disk -> try ubuntu and post the output of terminal code :
```
 sudo fdisk -l 
``` and maybe get some idea of what we are working with.
[INDENT=2]
not much help, but try'n

[/INDENT]

---

### Post by robjf on 2013-06-03
I am having the exact same problem on a MacBook Air (2012) purchased today especially to run Ubuntu 13.04. Did you get anywhere with this? I followed this thread to install: [http://www.thatsthewayyoudoit.me/2013/04/how-to-install-ubuntu-1304-on-macbook.html](http://www.thatsthewayyoudoit.me/2013/04/how-to-install-ubuntu-1304-on-macbook.html)

Kind regards, 

Rob

---

### Post by robjf on 2013-06-03
formatting ubuntu partition as ext3, swap as fat 32, and choosing not to install 3rd party or updates allowed me to continue with the install. not exactly sure which of these steps resolved the problem but apparently successful install of 13.04 :)

---

