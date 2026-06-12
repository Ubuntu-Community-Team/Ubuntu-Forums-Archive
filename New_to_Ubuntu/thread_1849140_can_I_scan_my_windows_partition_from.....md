---
title: "can I scan my windows partition from...."
date: 2011-09-23
forum: New to Ubuntu
---

### Post by jacknet52 on 2011-09-23
the Ubuntu partition? Can you recommend a good virus scanner please? Thank you much.

---

### Post by wildmanne39 on 2011-09-23
Hi, welcome to the forum! As for as I know you have to do hat from windows.
Thank you

---

### Post by Rubi1200 on 2011-09-24
There are LiveCDs available from most of the better known antivirus companies:
[http://www.raymond.cc/blog/archives/2008/12/11/13-antivirus-rescue-cds-software-compared-in-search-for-the-best-rescue-disk/](http://www.raymond.cc/blog/archives/2008/12/11/13-antivirus-rescue-cds-software-compared-in-search-for-the-best-rescue-disk/)

---

### Post by jacknet52 on 2011-09-24
How do you feel about ClamTK running from inside ubuntu so I can scan the windows partition?

---

### Post by haqking on 2011-09-24
> **jacknet52 said:**
> How do you feel about ClamTK running from inside ubuntu so I can scan the windows partition?

Yeah thats fine.

There are lots of bootable AV disks you can use, but as long as your partition is available in Linux then ClamAV is as good as any other really.

However you are better off running an upto date AV scanner within your windows partition itself.

---

### Post by jacknet52 on 2011-09-24
@haqking: Forgive my newness. So you're saying burn an AV disk in Ubuntu then run it in the windows part ? Rubi1200 gave me a link to several bootable av disks and being so new to Linux could you pick one for me? Also, if you have time: I have Smuxi and was trying to join the "User Days" on irc.freenode.net but it won't let me join. How does one go about that ? Thanks for your time. Much Appreciated.

---

### Post by haqking on 2011-09-24
> **jacknet52 said:**
> @haqking: Forgive my newness. So you're saying burn an AV disk in Ubuntu then run it in the windows part ? Rubi1200 gave me a link to several bootable av disks and being so new to Linux could you pick one for me? Also, if you have time: I have Smuxi and was trying to join the "User Days" on irc.freenode.net but it won't let me join. How does one go about that ? Thanks for your time. Much Appreciated.

What i mean is, if you have a windows partition, i presume you dual boot into windows.  If that is the case then it is best to have some AV software running in Windows for your purpose of scanning for malware, such as Symantec, ClamAV, McAfeee etc.

However if you really want to scan it without booting into it you could use a number of AV bootable disks, of which there are many, choose any, they all pretty much do the same job. an example would be one from kaspersky [http://support.kaspersky.com/viruses/rescuedisk](http://support.kaspersky.com/viruses/rescuedisk)

Just downloaad it and put it onto a USB or CD and boot your machine to it.

Or yes from your Ubuntu installation you can use ClamAV to scan the location of your windows files.

As for smuxi i am not familiar with it, but like all IRC clients they are usually pretty straight forward.  What error are you getting ? you cant connect to irc.freenode.net or you are having other issues ?

Cheers

---

### Post by Mark Phelps on 2011-09-24
+1 for the Kaspersky AV disk.

I have used this numerous time and it works great!

Ironically, it boots into Linux to run the AV program.

---

