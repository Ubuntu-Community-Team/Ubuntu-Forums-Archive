---
title: "[SOLVED] Removal of older versions after each update"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by parathuruthil on 2008-09-04
I have installed Ubuntu in my old Toshiba A50 Notebook, which had a pre-installed Windows-XP, updated almost continuously. The Ubuntu Version is 8.04 (I think so), and I was prompted to some ~250 available updates. I have accepted all updates.
Now upon each login, I am prompted to accept one of the two Ubuntu installations, one xxxx-16 and the other xxxx-19. Looks one is the previous version.
Is there a way to delete the previous version after the new installation is found to be working OK? 
Does Ubuntu automatically delete the older versions? If not how I can delete it manually to save space?
Is there a way to migrate completely to Ubuntu, after cleaning the Windows-XP partition?
Dr. P. Gopalakrishnan [email]parathuruthil@gmail.com[/email]

---

### Post by Oldsoldier2003 on 2008-09-04
to delete unneeded kernels, open synsptic and search for linux-image. Mark your older images for complete deletion. This will remove the extra files and also prurge the entry form the grub menu list.

I usually leave the kernel before the one I am currently running as a type of fallback position in case something goes wrong with the current kernel.

---

### Post by sameerds on 2008-09-04
> **parathuruthil said:**
> Is there a way to delete the previous version after the new installation is found to be working OK?


Yes. Someone else has answered that. I just want to point out one very important detail here. On a good well-managed operating system, you never "delete" any software. You uninstall it. This is important ... software usually configures the system in some way when it is installed. Uninstalling it gives the system a chance to take relevant action about this configuration.

On Ubuntu, the framework called "apt" manages the installation and uninstallation of software. The most commonly used tools for this purpose are apt-get, aptitude and dpkg on the command line, and synaptic for a graphical interface.

> **parathuruthil said:**
> Does Ubuntu automatically delete the older versions?

I think the system usually maintains two versions of the kernel ... the current one, and the previous one. When a third one comes along, the oldest is removed.

> **parathuruthil said:**
> Is there a way to migrate completely to Ubuntu, after cleaning the Windows-XP partition?

Well, that is a very complicated question. Its a matter of how much you depend on windows-specific applications to do your work. Some websites need IE, for example. Then some documents simply can't be opened in anything other than Microsoft Office, and so on. I suggest you should keep your XP around as a fallback, no matter how comfortable you get with Ubuntu. Mark Shuttleworth, the man behind Ubuntu, [seems have the same opinion]("http://www.theregister.co.uk/2008/09/03/shuttleworth_linux_desktop_fear/")!

---

### Post by egalvan on 2008-09-04
> **parathuruthil said:**
> parathuruthil@gmail.com[/email]

Once you clean out the Win partition, you can use a partition editor (I like, and recommend, PartED Magic LiveCD).
 Select the unwanted partition, delete it, then re-format it as ext3.
 You can then use it as spare storage, or what-not.

---

### Post by parathuruthil on 2008-11-22
For some reasons, I am not able to boot from my UBUNTU partition in my disk (Toshiba A-50 Notebook, with a pre-installed Windows-XP, in which I have installed Ubuntu 8.04 - I was updating it frequently, and it is the latest version installed)
Presently, at the boot, the system does not display the usual choice of OS (Various versions of Ubuntu, memory test, and Windows XP). I am allowed to edit the command line, where I tried usual commands like ls, and sudo, but always get the response, unrecognised command.
I am not able to access the Ubuntu Partition in my disk from Windows XP (normal), and also from a trial installation using WUBI in the XP area.
Can I re-install the system with a UBUNTU CD?
Does it re-write the Ubuntu Partition? Can my data be still safe?
Dr. P. Gopalakrishnan
[email]parathuruthil@gmail.com[/email]

---

