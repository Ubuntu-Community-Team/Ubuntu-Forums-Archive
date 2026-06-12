---
title: "Windows failed to start"
date: 2014-08-08
forum: New to Ubuntu
---

### Post by alex236 on 2014-08-08
I burned Ubuntu onto my USB using Unetbootin. I then inserted my USB into my other laptop. I pushed F12 to bring up the boot menu and selected my USB. And then I get the error message linked below. ([http://tinypic.com/r/hsrryf/8](http://tinypic.com/r/hsrryf/8))


I have no CD drive.

Windows XP

I'm trying to install Ubuntu 14.04.1 LTS 32 bit.


I have a Dell Inspiron Mini (10?) 


Please help me because I would love to get Ubuntu installed before school starts!!! Thank you.

---

### Post by mooreted on 2014-08-08
I don't see an error message. Remember that your netbook uses an Atom processor so you need to download the Ubuntu Netbook Edition.

Could you please post the error message you are receiving?

---

### Post by Jonathan Precise on 2014-08-08
I have had problems with unetbooting. Use [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) instead.

---

### Post by alex236 on 2014-08-10
> **mooreted said:**
> I don't see an error message. Remember that your netbook uses an Atom processor so you need to download the Ubuntu Netbook Edition.

Could you please post the error message you are receiving?

Could you please give me the link to download this version? I didn't download the correct one... (I downloaded from here: [http://www.ubuntu.com/download/desktop/](http://www.ubuntu.com/download/desktop/) 32 bit)

Here is the error message: [http://tinypic.com/r/hsrryf/8](http://tinypic.com/r/hsrryf/8)

---

### Post by alex236 on 2014-08-10
> **Jonathan Precise said:**
> I have had problems with unetbooting. Use [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) instead.

I'll do so! The error message is the only problem.....

---

### Post by mooreted on 2014-08-10
Sorry, I was wrong. They changed it:

"Ubuntu Netbook Edition
since the release of ubuntu natty (11.04) the netbook version has been unified and is now part of the ubuntu-desktop edition, this has been done via the unity desktop software.

you may now use the standard ubuntu desktop CD image to install on net-books with specifications such as:

Intel Atom processor @ 1.6 GHz
386 MiB of system memory (RAM)
4 GB of disk space
Screen of 1024x600 resolution
Graphics chipset with support for visual effects"

Try the other suggestion. Maybe Unetbooin messed up.

---

### Post by Jonathan Precise on 2014-08-10
Seeing from the error, looks like windows is messed up and can't be used anymore.

Do you have another PC, or any friend that is willing to lend you a laptop to use the LinuxLive software to write ubuntu to USB?

---

### Post by alex236 on 2014-08-10
> **Jonathan Precise said:**
> Seeing from the error, looks like windows is messed up and can't be used anymore.

Do you have another PC, or any friend that is willing to lend you a laptop to use the LinuxLive software to write ubuntu to USB?

Yes, I have another PC. BUT, if I go into the BIOS on this computer, and reset all BIOS settings, the computer boots normally. So, Windows is fine. My computer just doesn't want to boot from the USB.

Any suggestions?

---

### Post by mastablasta on 2014-08-11
suggestions:
- check the md5 sum of the downloaded image - [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
- use another USB image burner (linuxliveUSB, Yumi...)
- use another USB stick (some sticks can't boot)
- make sure USB is set as first device to boot from

edit: Also default Ubutnu might be too heavy for your netbook. try using Xubutnu or Lubutnu instead. or use Kubuntu with netbook plasma. some newer Netbooks work fine with Ubutnu but some older ones might have issues due to low ram, or poor GPU chip support.

---

### Post by alex236 on 2014-08-11
I used linuxliveusb this time. I then booted from my USB. NOW, I have this screen. ([http://tinypic.com/r/opqwys/8](http://tinypic.com/r/opqwys/8))

I assume the installation is starting. I will update this post....

edit: I now have the install screen. The Ubuntu OS is stunning!

edit: Ubuntu was amazing but it wasn't fast enough on my laptop. I will install a lighter linux. Any recommendations? Thanks for all the help!

edit: I'm installing Lubuntu.

---

### Post by Jonathan Precise on 2014-08-11
Glad it's working!

---

### Post by Andy_Crowd on 2014-08-11
You can try install with ubuntu mini.iso and then install a lightweight desktop environment, very lightweight: openbox, windowmaker, pekwm, but you will need to add more features by yourself as volume/panel/mount/network managers and more many are using plugins or applications designed for LXDE and XFCE. Or you can install LXDE with all functions or XFCE, they has most complete functionality.
[http://en.wikipedia.org/wiki/Desktop_environment](http://en.wikipedia.org/wiki/Desktop_environment)
[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)

Here you can search for specialized distros with already preconfigured lightweight desktop enviroments: [http://distrowatch.com/](http://distrowatch.com/)

---

### Post by Jonathan Precise on 2014-08-12
@Andy_Crowd: Thanks for the advice, but the OP had already solved the problem.

---

