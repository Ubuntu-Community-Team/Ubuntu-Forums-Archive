---
title: "Need help please, ClamAV shows 3 infected files"
date: 2015-08-09
forum: New to Ubuntu
---

### Post by Kabir_Gandhiok on 2015-08-09
Hi

Could anyone please help me with the 3 infected files that clamav shows me. I ran clamscan -r / which showed infected files - 3
Next I ran clamscan -v / which showed these files /initrd.img: Symbolic link, /initrd.img.old: Symbolic link, /vmlinuz: Symbolic link
I have no clue what these 3 files are and if they're even viruses or not. I did some searching on google, but only found out that these files have something to do with networking and (or) kernel updates. Also, I read that these files regenerate in the system. Grateful if anyone can help me clean these files.

During scan I did not have any mounted external drives. My system dual booted with windows 8.1 with Ubuntu as the primary boot partition, so unless I don't select Windows in the grub, the system automatically takes me to Ubuntu.

I hope this is nothing to panic.

Thanks!

---

### Post by NathanRodriguez on 2015-08-09
These are system files, hard to believe that they got some kind of infection. Just to be sure test with other anti virus software.

---

### Post by Kabir_Gandhiok on 2015-08-09
Is there any way to check without installing another anti virus software? Also, if these files were infected wouldn't something have gone wrong with my system? I tried rebooting and it went fine. Just want to know if I need to clean these files or ignore them as false positives.

---

### Post by Geoffrey_Arndt on 2015-08-09
Check this out first . . . most likely false positives as those are all normal Linux files (vmlinuz) is a link to the actual kernel.

[http://www.clamav.net/report/report-fp.html](http://www.clamav.net/report/report-fp.html)

---

### Post by monkeybrain20122 on 2015-08-09
ClamAV is famous for giving false positives, according to one thread it even flagged itself as a virus once. It is junk and you don't need AV on Linux 

ClamAV scans for Windows virus btw, in case you don't know. Some people install it in an attempt to protect Win users they communicate with but AV is supposed to be running on their ends, it is not our job to babysit Win users.

---

### Post by Kabir_Gandhiok on 2015-08-09
That's funny and honestly, I do not want any AV on my Linux, it's only because sometimes I have to boot into windows, plus I'm also slightly concerned about getting a virus or malicious software on Linux through Bit-torrent downloads. Those places are full of it, aren't they?

---

### Post by Geoffrey_Arndt on 2015-08-10
Just be careful what sites you download from . . form your own circle of trust.   Use encryption, especially using the right algorithms with diverse and strong passwords.   It's not needed to use full-disk encryption, but your low and mediium priority files should use AES/256, and your topmost or mission-critical files should use 64 character password with passkey device, with preferred algorithm being Twofish.

---

### Post by pthfdr on 2015-08-10
Reply:Encryption is for those "Popular Paranoia™ subscribers".
I don't think your documents is THAT important to use encryption.
And encryption makes file access slower.

---

### Post by QIII on 2015-08-10
> it is not our job to babysit Win users.

Which is exactly why I don't cover my mouth and nose when I sneeze in a crowd.  Not my job to avoid infecting others.

---

### Post by sandyd on 2015-08-10
If you still want antivirus, but don't want all of the clamav false positives, try [http://www.bitdefender.com/business/antivirus-for-unices.html](http://www.bitdefender.com/business/antivirus-for-unices.html).

It says business, but you can just click on "Request a free liscence".

The virus definitions seem to be updated regularly and without false positives.

---

### Post by sammiev on 2015-08-10
> **sandyd said:**
> If you still want antivirus, but don't want all of the clamav false positives, try [http://www.bitdefender.com/business/antivirus-for-unices.html](http://www.bitdefender.com/business/antivirus-for-unices.html).

It says business, but you can just click on "Request a free liscence".

The virus definitions seem to be updated regularly and without false positives.

+1

Been using it for years now.

---

### Post by monkeybrain20122 on 2015-08-10
> **QIII said:**
> Which is exactly why I don't cover my mouth and nose when I sneeze in a crowd.  Not my job to avoid infecting others.

Not a good analogy. If they don't take measure on their end they will get virus from somewhere whether you run a AV on your end or not. Last I check it is not socially require to run AV for OTHER people.

---

### Post by Kabir_Gandhiok on 2015-08-11
Well as it turns out I had 3 phishing emails in the Thunderbird .cache, specifically from my gmail account, which is what clamav was flagging as infected files. Figured it out after running clamscan -r --bell -i / anyway, I just removed those files, but I still don't know if they were false positives or actually phishing. I do agree on some level that one of the reasons I switched over to Linux is because it isn't the virus magnet windows is but there are many... many more reasons why I prefer and like Linux over windows. Windows is a major pain in the butt and 10 is no better. Thanks all for your inputs :-) but I don't think I'm going to install bit-defender, I guess I don't want one of those major AVs running on my Linux.

---

### Post by buzzingrobot on 2015-08-11
> **Kabir_Gandhiok said:**
> ...I had 3 phishing emails in the Thunderbird .cache...

Email is independent of the OS in use. Clicking on a link works the same in Linux as in Windows.  The difference depends on what the malware was packaged as. Flash or Javascript?  Then a browser in Linux might be as vulnerable as the same browser in Windows.  A Windows executable (.exe)?  That only runs in Windows.

---

### Post by Kabir_Gandhiok on 2015-08-11
> **buzzingrobot said:**
> Email is independent of the OS in use. Clicking on a link works the same in Linux as in Windows.  The difference depends on what the malware was packaged as. Flash or Javascript?  Then a browser in Linux might be as vulnerable as the same browser in Windows.  A Windows executable (.exe)?  That only runs in Windows.

I'm not sure if the file was packaged as Flash or javascript or if it was an exe, I didn't check before removing it. All I remember is clamav listed the path of these files and that they were phishing, gmail, spoofed domain. I thought it was safe to remove these files since they had nothing to do with the system.

---

