---
title: "Problem Installing Sage Line 50 2013"
date: 2014-02-14
forum: New to Ubuntu
---

### Post by Amanda_Fields on 2014-02-14
I have installed Ubuntu 12.04 LTS and Wine 1.5 and am now trying to install Sage Line 50 Accounts 2013.  On first installation, I got several error messages (1628 failed to install, 1627 error data and finally 'command line syntax error'.  I clicked OK to each of these in turn and the installation continued until the finished dialogue box and then nothing happened.  As I could not locate an icon or identify any Sage files, I rebooted but still could not find anything.  I tried to install the program again from the CD.  Now the install shield dialog box comes up and when I click install it does start, however I am getting an error message after about 45 seconds from installshield stating: 1608: Unable to create InstallDriver instance, Return code: 2147467262. Any help in non-techy language would be very much appreciated, I have never used anything other than Microsoft before.

---

### Post by Vladlenin5000 on 2014-02-14
You're trying to install a Windows OS software into a Linux OS using a Windows "emulator" - WINE -, a situation that tends to not work more often than not. The only references I could find at WINEHQ were for much older versions, both the software and WINE itself. I couldn't find an instance where a user reported a successful (and usable) installation. The latest version, 2013, most certainly won't work at all (well, I guess you had the experience) and unfortunately for you not even using this commercial package based on WINE: [http://www.codeweavers.com/compatibility/search?name=sage;search=app;sort](http://www.codeweavers.com/compatibility/search?name=sage;search=app;sort)[medal_id]=DESC 
If you have a powerful enough computer, capable of running a virtual machine, you can have it running inside let's say a Windows 7. If not I'm afraid you'll need Windows really installed.

---

### Post by Amanda_Fields on 2014-02-17
Hi, thank you very much for your response, it confirms my belief, maybe we will have to look at a non windows based accounts package - it is proving very difficult to move away from Windows!  Thanks again.

---

### Post by Gordonbp531 on 2014-02-17
Some links you might want to have a look at:

[https://wiki.kubuntu.org/Accounting](https://wiki.kubuntu.org/Accounting)

[http://www.ubuntugeek.com/install-gnucash-financial-accounting-software-in-ubuntu.html](http://www.ubuntugeek.com/install-gnucash-financial-accounting-software-in-ubuntu.html)

[https://apps.ubuntu.com/cat/applications/manager-accounting/](https://apps.ubuntu.com/cat/applications/manager-accounting/)

---

