---
title: "HOWTO: Share from Linux using sshfs on Windows with &quot;dokan&quot;"
date: 2009-01-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Jose Catre-Vandis on 2009-01-01
[COLOR="Red"]dokan[/COLOR], (meaning clay pipe) providing [COLOR="Red"]sshfs[/COLOR] access to linux file shares (server) from Windows systems (client)

I am always looking for good ways of accessing linux file system shares from windows boxes, as I have to help my less technical windows users on my LAN gain access to everything being served up from my linux servers. If samba doesn't float your boat, and getting nfs to work on Windows is just too hard, there is another way; [COLOR="Red"]dokan[/COLOR], which runs as an executable on Windows systems (W2K,XP, Vista) to provide mounted network style shares via [COLOR="Red"]ssh[/COLOR]. Here's how.

This howto is aimed at an internal LAN, so low security measures are followed. I am sure there are ways to lock things down as tight as you want (probably from the linux end), but this is beyond the scope of this howto, I just want to get you up and running! 



[B]1. Share with ssh on Linux
[/B]
On your linux/ubuntu (server) PC, install [COLOR="Red"]openssh-server[/COLOR] if not already there and up and running:
```
sudo apt-get install openssh-server
```
That's about it. Your linux PC will be open to ssh access, but you will need to have a login and password in order to access the linux PC.



**2. Probably now best to test your ssh-ability, either from another linux box on your LAN:**
```
ssh user@linuxbox
``` or by using [COLOR="Red"]putty[/COLOR] on a Windows box on your LAN. Download [COLOR="Red"]putty[/COLOR] from here:```
http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe
```



**3. Set up dakon on your Windows PC**

Boot up your windows PC and prepare for some downloading and installing:

***a) .Net Framework 2.0 Redistributable Package***

Can't give a direct link but go to this page and click on the download button
```
http://www.microsoft.com/downloads/details.aspx?familyid=0856eacb-4362-4b0d-8edd-aab15c5e04f5
```
It's about 22.5mb. Once downloaded you will have a file **dotnetfx.exe**. Double click on this and follow the installation prompts selecting all defaults.

***b)  Microsoft Visual C ++ 2005 SP1 redistributable Package***

Again no direct link but follow this link for a download
```
http://www.microsoft.com/downloads/details.aspx?familyid=200B2FD9-AE1A-4A14-984D-389C36F85647
```
Its about 2.6mb. Once down, double click on the file **vcredist_x86.exe** and let it install. If a rebot required then do so.

***c) The dokan stuff*** (current version at time of writing 0.4.2.1.1238)
Download the following:
```
wget http://dokan-dev.net/wp-content/uploads/dokan-0421238x86.zip
```
Which brings down the dokan libraries (32 bit). Unzip and double click on the **DokanInstall32.msi** to install it.
Next download:
```
wget http://dokan-dev.net/wp-content/uploads/dokan-sshfs-0201226.zip
```
Which is the sshfs program. Unzip and double click to install **DokanSSHFSInstall.msi**.

If asked to reboot please do so.



**4. Running dokan**

a) The installation will have placed [COLOR="Red"]dokan[/COLOR] in your start menu / programs. Navigate to the shortcut and run [COLOR="Red"]dokansshfs[/COLOR] (you will need the IP/FQDN of your linux PC sharing via ssh, and the user and password at this point)

b) Enter the required details in the dialog box, select a drive letter, click OK, click OK again in the little dialog that appears, and then open up Explorer and you should see your drive letter. Click on this and it should reveal you linux share. Depending on your security settings you should have read / write access (at least to the users home directory)

c) You can save your access settings to make things easier to recall next time, but you will always have to enter the password.

d) You can also enter a path from root, so that the share opens up at a specific point on your file tree (e.g. /media/myfiles)

e) You can add additional shares to other PCs serving up [COLOR="Red"]ssh[/COLOR] by running [COLOR="Red"]dokansshfs[/COLOR] again.

f) Connecting network drives using ssh is not an automatic affair, you will have to run [COLOR="Red"]dokan[/COLOR] each time you boot up windows. 

===============


**5. Addendums**

a) [COLOR="Red"]dokan[/COLOR] is under heavy development so expect the versions to change on a regular basis, if the direct links do not work go to this site:
```
http://dokan-dev.net/en/download/
```
and download the latest versions of [COLOR="Red"]dokan[/COLOR] library and [COLOR="Red"]dokansshfs[/COLOR]. there is a [COLOR="Red"]dokan[/COLOR] library for 64bit machines too.


b) Also, as it is under development, you can't expect it to be flawless or work as you expect, but it worked for me first time, and allowed file exchange and audio / video real time viewing (as opposed to download then watch/listen.)


c) You can also setup a ssh server on Windows, but again this is beyond the scope of this howto.


Let me know how you get on, and I'll do what I can to help you if you get stuck :)


=================


Some licensing info on dokan from the developer: **Hiroki Asakawa**

> Licensing

=========



- Dokan SSHFS is provided "AS IS", without warranty of any kind,

  expressed or implied. Use at your own risk.



- Dokan SSHFS is being licensed to you free of charge for your

  private persona use only. You may use Dokan SSHFS for

  non-commercial purposes only.



- Redistribution of Dokan SSHFS is prohibited.

===================

All credits to **Hiroki** for this great addition to Windows software that helps provide access to ssh shares, which are more likely found on linux PCs.

---

### Post by scohar70 on 2009-10-28
Awesome tutorial.  Worked great for me first try.

---

