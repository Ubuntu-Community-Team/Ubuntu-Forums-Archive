---
title: "Installation of soundcard x-fi"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by will_s54 on 2008-06-21
My first post and my first day on Ubuntu 8.04. I am a novice used to the Windows o/s.
Have just installed Ubuntu 8.04 on my two computers as a dual boot ( Vista and XP ). On the Xp machine with onboard sound I have music and no problems but on this computer with the Soundblaster fatlity Gamer x-fi card I have no sound . Pretty sure that its a case of no drivers so have downloaded some beta drivers from Soundblaster but have no idea how to install them. The old click and install from Windows wont work.

Is there a link with detailed instructions on how to install that a complete novice can follow ? No idea about terminal windows etc and the readme posted below is double dutch to me. In the meantime I will keep googling and hoping .



 "You must have the fully configured source for the Linux kernel and 

   ALSA which you
 want to use for this device driver. Partial installed 

   kernels (e.g. From distribution makers) may be unusable for this 

   action.
2) Run one of the following commands as root in the terminal:
   ./installer
   
  OR
   ./installer --with-alsainc=<ALSA_include_directory>

  * ALSA Source Tree
 
   On 2.6 kernels, the location of the ALSA source include directory      is parsed automatically from the running kernel.     If it is not in the standard place, specify the path via--with-alsainc=<ALSA_include_directory>.

  
  On 2.4 kernels, the location of the ALSA source include directory     must be specified via --with-alsainc=<ALSA_include_directory>.
  * Note      If integrated ALSA is to be used to build, --with-alsainc option must not be specified.

---

### Post by Nepherte on 2008-06-21
I have to say I never got my X-Fi card working with the given beta drivers from Creative. I recommend using OSSv4 for your card: [http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961)
which should work. It worked for me anyways.

---

