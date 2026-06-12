---
title: "CentOS - para saan ito and advantages nito"
date: 2009-02-09
forum: Philippine Team
---

### Post by dodimar on 2009-02-09
Currently, I am experimenting (well, studying - on my own) Linux+Windows networking (which includes setting up server etc, using vmware)..

curious about CentOS, ano ano ang gamit nito and ano ang advantage nito on a server+client setup...

Thanks..

---

### Post by loell on 2009-02-09
its main use are for servers, based on RHEL,  it has proven super stable.

---

### Post by dodimar on 2009-02-10
> **loell said:**
> its main use are for servers, based on RHEL,  it has proven super stable.

Pwede ba ito sa "roaming profile" server (like in windows server).

---

### Post by jsgotangco on 2009-02-10
It's RHEL without the Red Hat branding, meaning they (CentOS) pulled the sources of RHEL and rebundled it as CentOS.

---

### Post by dodimar on 2009-02-10
Okies.. got it... download time... 

thanks po mga bossing..

---

### Post by loell on 2009-02-10
> **dodimar said:**
> Pwede ba ito sa "roaming profile" server (like in windows server).

you can setup samba as Primary Domain controller, then from there, you can setup mandatory profile.

---

### Post by business.geek on 2009-02-11
As with any linux. CENTOS provides a good base for a domain controller. But given i've been working with Centos lately, I'd suggest you try building on an Ubuntu server.

Just my two cents.

cheers!

---

### Post by dodimar on 2009-02-11
> **business.geek said:**
> As with any linux. CENTOS provides a good base for a domain controller. But given i've been working with Centos lately, I'd suggest you try building on an Ubuntu server.

Just my two cents.

cheers!

A. Why would I go for an Ubuntu server and not centOS?

B. Why would I go for a centOS server and not Ubuntu?

---

### Post by business.geek on 2009-02-11
> **dodimar said:**
> A. Why would I go for an Ubuntu server and not centOS?

B. Why would I go for a centOS server and not Ubuntu?

my opinion?

Use Ubuntu:

- Ubuntu Server uses more up to date packages (read security updates).
- Ubuntu Server supports XFS and ReiserFS on installation. This is good when you're serving large files using Samba
- More refernce material on the net.
- has preinstall profiles, like email server, file server, openssh server etc...

Use Centos
- When you need to use applications that require RPM's or Redhat Enterprise Linux since centos uses the same source code as redhat.
- when you love RPM's
- when you need rpms....
- Centos is supported by more hosting companies then ubuntu server

---

### Post by jsgotangco on 2009-02-12
RHEL has a proven track record for the enterprise, so releases tend to be more stable (read: not bleeding edge, but rock solid). If you want to have this kind of setting without the cost of RHEL support, then go for CentOS.

Do not use this kind of setting in Ubuntu unless you are going to use LTS.

---

### Post by dodimar on 2009-02-12
Ubuntu tend to break things from one version to another (even updates breaks things)... 

transitioning from one CentOS version to another, is it the same? (I have already read some feedback regarding this but I need more info).

---

