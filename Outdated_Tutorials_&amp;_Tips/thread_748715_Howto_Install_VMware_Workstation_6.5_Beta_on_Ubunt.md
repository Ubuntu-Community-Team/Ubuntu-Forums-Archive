---
title: "Howto: Install VMware Workstation 6.5 Beta on Ubuntu Hardy"
date: 2008-04-07
forum: Outdated Tutorials &amp; Tips
---

### Post by rmtatum on 2008-04-07
Download VMware Workstation 6.5 Beta at [http://communities.vmware.com/community/beta/workstation6.5](http://communities.vmware.com/community/beta/workstation6.5)

Download vmware-any-any-update116 at [http://groups.google.com/group/vmkernelnewbies/files](http://groups.google.com/group/vmkernelnewbies/files)

Open your favorite terminal and type:
```

tar -xvzf VMware-workstation-e.x.p-84113.x86_64.tar.gz
tar -xvzf vmware-any-any-update-116.tgz
cd vmware-any-any-update116
rm vmmon.tar 
cp ../vmware-distrib/lib/modules/source/vmmon.tar ./
sudo ../vmware-distrib/vmware-install.pl

```

Answer no when asked to run vmware-config.pl 

Then type:

```

sudo ./runme.pl

```

Answer yes when asked to run vmware-config.pl

View the following thread on the vmware forums to solve the missing vsock issue: [http://communities.vmware.com/thread/137323?tstart=0](http://communities.vmware.com/thread/137323?tstart=0)

VMware Workstation 6.5 Beta should run now.

---

### Post by lptr on 2008-06-16
Upgraded today from 7.10 to 8.04.

Opposed to your experience, vmware-any-any-update was here not necessary with Kubuntu 32 bit 8.04 Hardy Heron. vmware workstation 6.5 beta, Build 91182 worked out of the box.

\\:D/

---

### Post by cob4lt on 2008-09-22
what about crack for vmware? I entered serial and there is expiration date now?

Thanks

---

### Post by binbash on 2008-09-22
> **cob4lt said:**
> what about crack for vmware? I entered serial and there is expiration date now?

Thanks

That kind of stuff is not allowed here

---

### Post by cob4lt on 2008-09-22
Ok sorry, i didn't know

---

### Post by lptr on 2008-09-23
> **binbash said:**
> That kind of stuff is not allowed here

As a regular 6.0 key owner I finding this 'timeouts' strange, too. I do understand that they - VMware - want to force testers to upgrade regulary. Otherwise everybody would only step up from time to time.

In my opinion they should not do this enforcement. Especially for the normal customers owning the previous version and willing to test. I would prefer to be informed via mail if a new update is available (one line would be enough). The other way round is simply stupid.

BTW: From the organizational standpoint some things seem not fully ok at the company. AFAIK until today they did not mention when 6.5 is planned to official release. Over weeks they had heavy trouble with their online forum. Messages disappeared strangely and reappeared anyhow some later. Postings had not been possible. Strange error messages to be shown if posting anything. Reaction times were slow. Answers sometime crude (ok I did not see 'man man', yet).  For anybody like VMware potentially loosing ground/customers in an emerging market this should not be normality. 

Sorry if I do flame them here... but this time bombing is really boring.

rob*

---

