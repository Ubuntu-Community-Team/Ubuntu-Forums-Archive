---
title: "Maintaining a Linux Lab"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by KevJB on 2008-05-20
Hi All,

I have just been given a linux lab to take control of and look after. As per usual of course Linux servers are being taken care of by someone else and requests for additional resources are being frowned upon and progress very slowly. Well, naturally my first concern is users /home folders, I know I could NFS mount them so that the /home folder contents is the same between machines. Of course getting space on a linux server is proving difficult so if I follow this path users space will be very limited and of course all the storage will be outside my control.

The other thing is that I have been told to work on an intergration plan with the Windows and Mac guys so we can have all three OS's running in harmony and with as similar a setup as possible. So of course I'd like users linux files to be transferable to Windows or Mac as required. So I thought ok, great, I can do the samba stuff and store the linux /home folder as part of the windows home drives.

The windows guys have been more than helpful in getting stuff setup, providing access to logs and to administer the areas I need but we have hit one snag, the quota developed offered us 40MB of space. We might be able to increase that to 100MB or so but the problem is that some of our linux users are using programs like gimp and java (full development, not just the RTE) which seam to write a lot of "config" files to ~/.xyz (dotfiles) or ~/.xyz/abc/ (dotfolders?) and for some users this has gotten out of hand.

I don't need all this config stuff to come accross to the NTFS shares but I'm having trouble deciding which dotfiles (and folders) are important and which are not. I thought about doing some fancy stuff at logon and logoff to patch the /home/<username> directory with the important contents after creating the original from a base folder but this is starting to look too complex because if I put too little in the base folder I achieve nothing and putting too much in there results in a large patch file for users who don't use all the fancy stuff.

Could I just do a simple copy and exclude all the .xyz files and folders. Are there any files and folders that are important and need to be preserved or will Ubuntu just recreate whatever it needs on logon?

Finally where is the best practice location to do this? Obviously I'll need to copy or rsync or whatever at logon and logoff? Which files or scripts run at logon and logoff and are most suited to preforming these tasks.

Or does someone else have some ideas? I can't be the first person who thinks that the /home/<username> folder can become too large without actually storing too much user data in it?

Thanks,
KevJB

---

### Post by Xiong Chiamiov on 2008-05-21
I think there's an option in GIMP as to where it stores its swap files and such.

Though I have no experience in this area, the first thought that comes to my mind is to keep generic versions of those files locally and soft link to them from all the home directories.

---

