---
title: "Help Removing MailWasher"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Greg Mueller on 2008-04-30
I installed MailWasher 25 days ago and have decided to not buy it since it's so unfinished, buggy and unsupported. I went to remove it with the "add/remove applications" program and can't find it listed there.

How do I get rid of it?

---

### Post by Monicker on 2008-04-30
> **Greg Mueller said:**
> I installed MailWasher 25 days ago and have decided to not buy it since it's so unfinished, buggy and unsupported. I went to remove it with the "add/remove applications" program and can't find it listed there.

How do I get rid of it?

Is it listed in Synaptic? If its listed there you should be able to remove it  by right clicking and selecting "Mark for Complete Removal", then clicking on Apply.

You can also check by running "dpkg -l|grep mailwasher" from a terminal.  To remove from a terminal: sudo apt-get remove packagename

---

### Post by forestpixie on 2008-04-30
If it's mailwasher server it's a bit more complicated than that according to the website. [http://www.firetrust.org/docs/linux-install.html#uninstall](http://www.firetrust.org/docs/linux-install.html#uninstall)

It will only be in synaptic if it was installed with a .deb, if you needed to compile it you will have to do it in the folder you installed form I think.

---

### Post by Greg Mueller on 2008-04-30
I downloaded and installed it from here, if that helps

[http://www.firetrust.com/download/beta/mailwasher_2.0.0_ubuntu6.10_7.04.deb](http://www.firetrust.com/download/beta/mailwasher_2.0.0_ubuntu6.10_7.04.deb)

---

### Post by Monicker on 2008-04-30
> **Greg Mueller said:**
> I downloaded and installed it from here, if that helps

[http://www.firetrust.com/download/beta/mailwasher_2.0.0_ubuntu6.10_7.04.deb](http://www.firetrust.com/download/beta/mailwasher_2.0.0_ubuntu6.10_7.04.deb)

It should up in "dpkg -l" then.  I do not see why it would not.

---

### Post by Greg Mueller on 2008-04-30
sudo apt-get remove mailwasher worked great
thank you

---

### Post by ajgreeny on 2008-04-30
If you simply installed it using a double click on the .deb file you can uninstall it by following this info from the **man dpkg** output

dpkg -r | --remove | -P | --purge package ... | -a | --pending
              Remove an installed package. -r or --remove remove everything except con&#8208;
              figuration  files. This may avoid having to reconfigure the package if it
              is reinstalled later. (Configuration files are the files  listed  in  the
              debian/conffiles control file). -P or --purge removes everything, includ&#8208;
              ing configuration files. If -a or --pending is given instead of a package
              name,  then  all packages unpacked, but marked to be removed or purged in
              file /var/lib/dpkg/status, are removed or purged, respectively.

So it would be removed by ```
sudo dpkg -r mailwasher
```

---

