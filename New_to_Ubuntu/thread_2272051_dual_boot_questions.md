---
title: "dual boot questions"
date: 2015-04-03
forum: New to Ubuntu
---

### Post by E_Coloney on 2015-04-03
I'm absolutely new to Ubuntu.  It appears fascinating.

I am trying to understand security and protect myself when looking at my bank/stock accounts.
If I set up a dual boot system with Windows 7 (I think probably only boot from a usb stick), if I have an (unknown) trojan/virus/spyware/malware in Windows and boot into Ubuntu, does it effectively render the malware non-effective/inoperative?
Then, can I tell Ubuntu to not write ANYTHING to my hard drive or usb stick to protect me from any Linux-based threats?

Many thanks,

---

### Post by Frogs Hair on 2015-04-03
Hello and Welcome E_Coloney

When you access a site from a web browser keep in mind that browser exploits which are not viruses use java script and for that reason cross platform. Windows viruses won't run in Linux but could be passed to a Windows computer via a file or email attachment. See the security link in my signature.           [**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1977341")

---

### Post by Mark Phelps on 2015-04-03
> If I set up a dual boot system with Windows 7 (I think probably only boot from a usb stick),
If you are intending to boot Win7 from a USb stick -- forget it.  MS doesn't support booting windows prior to Win8 from external drives.

>  if I have an (unknown) trojan/virus/spyware/malware in Windows and boot into Ubuntu, does it effectively render the malware non-effective/inoperative?Windows infections don't apply to Linux; so, it's not that it renders it ineffective, it simply doesn't infect Linux.

> Then, can I tell Ubuntu to not write ANYTHING to my hard drive or usb stick to protect me from any Linux-based threats?
If you boot Ubuntu from a USB stick, that is not persistent, that is, everything is written only to memory and when you reboot, the contents of the USB stick are the same as before.

---

### Post by TheFu on 2015-04-03
If you don't mount the storage, then nothing will be written.

If all you need is an online banking live-boot, then I wouldn't install anything. Just use yumi to make a boot flash drive with some minimal Linux distro - TinyCore is small and has a browser. Run that for your financial stuff.  [http://krebsonsecurity.com/2012/07/banking-on-a-live-cd/](http://krebsonsecurity.com/2012/07/banking-on-a-live-cd/) agrees.

Windows viruses can run under Linux through WINE. If you don't install WINE, then a virus written for Windows will not have any impact. It may be passed on in the normal ways - ftp, sftp, email, normal file transfer methods.

Linux has malware.
Linux has viri, botnets, and 50 other "bad things."  Most of these things only become a concern if you run servers/services.  TinyCore won't do that by default.

There isn't any replacement for a user who makes smart security choices, regardless of the OS used.

If you really, really don't want anything written - burn a CD and boot off that. It will be slower, but TinyCore will still be nearly instantaneous. Large distros like Ubuntu will be slower.

---

### Post by PondPuppy on 2015-04-03
A couple of other thumb-drive-optimized Linux distros are Porteus and Puppy. A Porteus installation can be set to persistent or non-persistent ("always fresh") mode at boot-up.

If you wish, you can install Firejail on Ubuntu, and use it to run Firefox (or Chromium) in a sandbox. Doing that, plus using add-ons like NoScript and Ghostery or Disconnect, will probably make browsing as safe as you need. 

However, for online banking you may need to tell NoScript to whitelist your banking site. Same for some shopping, ticket-buying, hotels, etc. It depends on what the designer used to make the website interactive.

---

### Post by newb85 on 2015-04-04
> **TheFu said:**
> Most of these things only become a concern if you run servers/services.  TinyCore won't do that by default.

Ubuntu won't do that by default, either.  (Server packages are available in the repos, but have to be installed before you can turn them on.)  And Ubuntu has a dedicated security team.

If you're going to run from a non-persistent live media, something lightweight definitely has it's advantage (speed).  However, in general, the *best* security measure in Linux is keeping your system up-to-date, which isn't possible in non-persistent live media.  Some security threats are nullified by using live media, but not all.  Heartbleed would be one example.

---

