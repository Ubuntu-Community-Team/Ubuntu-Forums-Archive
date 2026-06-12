---
title: "clamav / false positives ?"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by smooth3006 on 2008-10-16
i installed clamav and clamtk today. i was running a scan and it said i had 4 viruses ? does this pick up alot of false / non viruses like avast does ? im only running a scan because i use xp in vmware in ubuntu. although i do have kaspersky internet security on xp as well.

---

### Post by toasty_ghosty on 2008-10-16
I do know that you can have a virus on Linux. BUT as it is made to run on a Windows computer it cannot do anything. I once downloaded a file from and e-mail and about a week later the person who sent it said it contained a virus and it tore apart his laptop. No issues here even though it scanned positive for one.

---

### Post by smooth3006 on 2008-10-16
the question is how can you tell if it's a real virus or not ?

---

### Post by cariboo on 2008-10-16
I was playing with clamav yesterday, did a completes scan of my /, /home and Vista partitions, it took about 6 hours and all it found was the two viruses that I have stored in a folder in my home partition. So if it did find something, it might be an idea to check them out.

Jim

---

### Post by GuitarRocker2562 on 2008-10-16
They are probably windows viruses. So they won't attack you, unless you boot into Windows and have access to them in windows.

---

### Post by hyper_ch on 2008-10-17
you should not scan your linux file system with antivirus software created for detecting windows viruses. If you run a fileserver or mail server then you would limit the scanner only to files contained in there but not the whole linux filesystem - or you would limit it to an windows partition.

---

### Post by Keen101 on 2008-10-17
> does this pick up alot of false / non viruses like avast does ?

In my experience, no.

If clamav Say's it found a virus, then it probably did. Sometimes clamav doesn't even find the nasty ones, but works good for most.


In the past i had an xp machine, and clamav said it had 14 viruses. got rid of them, but we were pretty sure there might be more. we were right, and the xp machine got hit by something that activated windows updates. the updates downloaded more virus code, and the system crashed. had to re-install the whole thing.

this is one reason i use Linux now. I don't even have to worry about viruses. But, i occasionally scan my system, so i don't become a carrier.

---

