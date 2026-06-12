---
title: "Not Sure if BitDefender has been correctly installed [ubuntu-14-04-LTS]"
date: 2014-12-05
forum: New to Ubuntu
---

### Post by avishek2 on 2014-12-05
Hello,

I just switched from windows to Linux. I followed this link: [http://debianhelp.wordpress.com/2013/11/27/to-do-list-after-installing-ubuntu-14-04-trusty-tahr-os/](http://debianhelp.wordpress.com/2013/11/27/to-do-list-after-installing-ubuntu-14-04-trusty-tahr-os/)

and installed BitDefender, then during the first update it crashed so I proceed to apply the fix as per the link above:

```
sudo touch /opt/BitDefender-scanner/var/lib/scan/bdcore.so.linux-x86_64
sudo ln -fs /opt/BitDefender-scanner/var/lib/scan/bdcore.so.linux-x86_64 /opt/BitDefender-scanner/var/lib/scan/bdcore.so
sudo bdscan --update
```

Now no crashes occur during update but the in the GUI it shows "no engines loaded" and 0 in all the following categories.

Please advice

---

### Post by thiebaude on 2014-12-05
BitDefender is only for Windows and can't be installed on Ubuntu.

---

### Post by avishek2 on 2014-12-05
> **thiebaude said:**
> BitDefender is only for Windows and can't be installed on Ubuntu.

But there are many resources on the net about installing BitDefender on Ubuntu!!

---

### Post by howefield on 2014-12-05
Have you rebooted since applying the fix ?

---

### Post by buzzingrobot on 2014-12-05
Can't explain the error, but, using an anti-malware tool on Linux is certainly far less critical than on Windows.  Not because Linux can't be attacked, but because it remains a very small target. Most malware seems to propagate by tricking users into installing it, in any case, so a liitle caution about browsing and avoiding phishing attempts, plus keeping your machine updated, will go a long way. Many, many Linux users, including me, have used it for years without an AV without problems.

That said, running one is also fine, and BitDefender's Linux release should work if they're going to make it available. Have you tried contacting them directly?

---

### Post by buzzingrobot on 2014-12-05
> **thiebaude said:**
> BitDefender is only for Windows and can't be installed on Ubuntu.

They do offer a Unix/Linux version.

---

### Post by howefield on 2014-12-05
> **avishek2 said:**
> Now no crashes occur during update but the in the GUI it shows "no engines loaded" and 0 in all the following categories.

It'll most likely load the engine ect when you try to scan something...

---

### Post by thiebaude on 2014-12-05
I learn something new everyday, thanks

---

### Post by Penguin360 on 2014-12-05
I personally don't think it is worth the hassle to install BitDefender on Ubuntu. First of all, like buzzingrobot mentioned before, Windows viruses don't work on Ubuntu. Secondly, BitDefender on Ubuntu does not provide real-time protection and only provides on-demand scan, so what protection does it provide?

---

### Post by avishek2 on 2014-12-05
Yup, it loaded when I scanned some thing...thanks howefield! Is there like someway to mark this question as answered?

---

### Post by slickymaster on 2014-12-05
> **avishek2 said:**
> Yup, it loaded when I scanned some thing...thanks howefield! Is there like someway to mark this question as answered?

[How to mark your thread as SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by Penguin360 on 2014-12-05
Interestingly, according to Ubuntu Wiki, you should NOT install anti-virus, unless you share files with Windows.

Check the #2 point in this wiki article: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by nicknefarious on 2015-04-22
For those who are interested there is a later (newer) version of BitDefender for install in Ubuntu/Debian to download from here - [http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/]("http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/") It currently (22/04/2015) offers Version 7.7.1 and looks to have been last updated in Nov 2014. I installed it by:-

[LIST=1]
[*]Downloading it
[*]Opening a terminal an using the cd command to change directory to the folder where the downloaded install file is stored (The install file will be called something like - BitDefender-Antivirus-Scanner-7.7-1-linux-amd64.deb.run ) BE AWARE THERE IS A 32-bit OPTION AND A 64-bit FOR DOWNLOAD AND INSTALL. Make sure you get the right one for your Operating System!)
[*]While in the directory of the downloaded install file run the command - ```
sudo sh ./BitDefender-Antivirus-Scanner-7.7-1-linux-amd64.deb.run
``` This command will change if the install file you downloaded is different. The command should be - sudo sh ./*NAME OF THE INSTALL FILE YOU DOWNLOADED*
[/LIST]
I have it installed and have it working with no workarounds or fixes. (I know this was an issue with previous versions) It runs pretty heavy when scanning on my ageing laptop but does the job and seems to do it well. It's a trial 30 day version, but you can get a 365 day key here - [http://www.bitdefender.com/site/Products/ScannerLicense/]("http://www.bitdefender.com/site/Products/ScannerLicense/") with a working email address to receive the key. Here's a link to BitDefender's info page - [http://www.bitdefender.com/support/How-to-configure-Bitdefender-Scanner-for-UNICES-837.html]("http://www.bitdefender.com/support/How-to-configure-Bitdefender-Scanner-for-UNICES-837.html")
You can see in the post dated 15th April 2015 in this BitDefender Forum thread [http://unices.bitdefender.com/2011/11/01/bitdefender-antivirus-scanner-for-unices/#more-1073]("http://unices.bitdefender.com/2011/11/01/bitdefender-antivirus-scanner-for-unices/#more-1073") that someone else recently installed this using the .RPM packages provided in their relevant Operating System.

This is an on-demand anti-virus scanning tool, not a live, on-access protection system. I am using it to scan a wide range of drives I have for Windows viruses/malware so I don't accidentally share these with a poor unsuspecting Windows user, or my Windows machines...

Hope this helps someone,

NN

---

