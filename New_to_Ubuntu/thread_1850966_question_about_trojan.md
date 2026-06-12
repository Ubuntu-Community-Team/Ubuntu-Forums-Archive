---
title: "question about trojan"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by aam-aadmi on 2011-09-27
Hi All,

I have two partitions on my system. One of them runs Ubuntu 10.04 and the other has Windows 7. Yesterday, a trojan was detected in the windows partition (what else do you expect?!). Is it still safe to copy files from the windows partition into my Ubuntu partition?

Thanks.
Aam-aadmi

---

### Post by westie457 on 2011-09-27
> **aam-aadmi said:**
> Hi All,

I have two partitions on my system. One of them runs Ubuntu 10.04 and the other has Windows 7. Yesterday, a trojan was detected in the windows partition (what else do you expect?!). Is it still safe to copy files from the windows partition into my Ubuntu partition?

Thanks.
Aam-aadmi

Yes it is safe to copy the files. The chances of the trojan working on your Ubuntu partition are very slim.
Just a n idea to be safe install Clamav via the Software Centre and clean your Windows partition of the trojan and anything else that should not be there.

---

### Post by Dangertux on 2011-09-27
It's likely RELATIVELY safe. That being said, it is still possible via Wine for trojans to execute under Linux.  If you want to see that work, or understand more about it [URL="http://dangertux.wordpress.com/2011/09/17/the-truth-about-windows-malware-wine-and-ubuntu/"]read this.
[/URL]
That being said if you don't run the file under wine there is not much chance whatsoever it's going to do anything malicious. Personally, I'm not a huge fan of ClamAV it's pretty much garbage when it comes to detecting things. 

So if you're copying executables and running them under Wine in Ubuntu, I would be cautious about that. Otherwise it should be good.

---

### Post by haqking on 2011-09-27
> **Dangertux said:**
> It's likely RELATIVELY safe. That being said, it is still possible via Wine for trojans to execute under Linux.  If you want to see that work, or understand more about it [URL="http://dangertux.wordpress.com/2011/09/17/the-truth-about-windows-malware-wine-and-ubuntu/"]read this.
[/URL]
That being said if you don't run the file under wine there is not much chance whatsoever it's going to do anything malicious. Personally, I'm not a huge fan of ClamAV it's pretty much garbage when it comes to detecting things. 

So if you're copying executables and running them under Wine in Ubuntu, I would be cautious about that. Otherwise it should be good.

+1

Best to boot to something such as Kaspersky rescue disk (there are many others) [http://support.kaspersky.com/viruses/rescuedisk](http://support.kaspersky.com/viruses/rescuedisk)

Or have decent malware detection and cleansing within the Windows partition itself.

---

### Post by aam-aadmi on 2011-09-27
Thanks for the replies. I am not copying any executable files, just spreadsheets, word docs, etc. Thus, it is good to know that the files will not create problems in the linux partition.

Probably now I should just delete the windows partition!

Aam-aadmi

---

### Post by haqking on 2011-09-27
> **aam-aadmi said:**
> Thanks for the replies. I am not copying any executable files, just spreadsheets, word docs, etc. Thus, it is good to know that the files will not create problems in the linux partition.

Probably now I should just delete the windows partition!

Aam-aadmi

A file does not need to be a .exe to contain malware, alot of malware is spread through office docs, macro viruses etc.

Anyways as said before highly unlikely, even if they are infected the infection needs to be targeted at linux for it to effect you.

---

### Post by The Cog on 2011-09-27
Bear in mind that you might be copying a trojaned file. Be careful not to give copies of those files back out to windows users.

---

