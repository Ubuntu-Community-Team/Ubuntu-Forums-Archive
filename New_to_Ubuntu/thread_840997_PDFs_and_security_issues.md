---
title: "PDFs and security issues"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by JimmyJim on 2008-06-25
I got a few ebooks online that are all PDFs. Back in my Windows days, I remember reading that PDFs could be used to contain embedded viruses. So I ask:

How can I make sure these PDFs don't contain any malicious code (rootkits) that can infect my Linux system?

Thanks in advance; I know its best to stay away from possible risks, but I would like to read these.

---

### Post by RomeReactor on 2008-06-26
Hi. The rootkit would have to be tailor-made to the Linux file system, and you would need to open the file as root (meaning, with administrator privileges). As long regularly update the system, you should be OK.

In case you want some extra protection, you can install **rkhunter**, **chkrootkit**, and/or **unhide**. Look for them in Synaptic (System->Administration->Synaptic).

[This page]("http://www.melbpc.org.au/pcupdate/2507/2507article6.htm") gives more information regarding this.

---

### Post by JimmyJim on 2008-06-26
> **RomeReactor said:**
> Hi. The rootkit would have to be tailor-made to the Linux file system, and you would need to open the file as root (meaning, with administrator privileges). As long regularly update the system, you should be OK.

In case you want some extra protection, you can install **rkhunter**, **chkrootkit**, and/or **unhide**. Look for them in Synaptic (System->Administration->Synaptic).

[This page]("http://www.melbpc.org.au/pcupdate/2507/2507article6.htm") gives more information regarding this.

Thanks a lot! :)

---

