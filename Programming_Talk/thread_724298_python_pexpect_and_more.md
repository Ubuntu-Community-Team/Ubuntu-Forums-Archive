---
title: "python pexpect and more"
date: 2008-03-14
forum: Programming Talk
---

### Post by iostat on 2008-03-14
Greetings,

I'm trying to write a script to interact with the VMware Server installation process.  I'll put a disclaimer out front, I'm not a coder, but I can usually scrap together what I need to get the job done.  I know that I could install it through apt-get but that's not what I want to do.

I get held up when trying to interact with the vmware-config.pl.  The first thing it does is have you accept the EULA.  The seems to spawn more to display the EULA.  I'm having trouble using pexpect in python to interact with the perl script when it kicks to more to display the agreement text.  

Anyone had any experience with using pexpect to interact with more?  I would appreciate any help!  Thanks!

---

### Post by iostat on 2008-03-14
Ok, found an easier way to to this.  If you append > answer EULA_AGREED yes in /etc/vmware/locations after the vmware-install.pl script runs but before you run the vmware-config.pl, the EULA isn't displayed.  

If anyone wants to post about using pexpect and more, I'd be happy to learn from your experience.  Thanks!

---

