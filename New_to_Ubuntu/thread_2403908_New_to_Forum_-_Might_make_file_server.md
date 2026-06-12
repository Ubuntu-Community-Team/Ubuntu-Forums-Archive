---
title: "New to Forum - Might make file server"
date: 2018-10-17
forum: New to Ubuntu
---

### Post by donmurraym on 2018-10-17
I wish to make a server out of this computer:
[https://downloads.dell.com/manuals/all-products/esuprt_desktop/esuprt_optiplex_desktop/optiplex-7010_owner%27s%20manual2_en-us.pdf](https://downloads.dell.com/manuals/all-products/esuprt_desktop/esuprt_optiplex_desktop/optiplex-7010_owner%27s%20manual2_en-us.pdf)

a Dell 7010  
I have a 64 gig ssd for the os
then I have a 4T ssd for the storage drive. who needs raid right ! ! ?

It uses a I5 Intel core 15-3470 CPU 3.20 GHz
and a 82579LM Gigabit Network Connection

I just want to share files to 5  computers that use win7 and win 10.   I don't need nas or webserver or print server I just want a place in the my home office to put all the files together in one place that has fast access.   I have no idea what I am getting into here.  Maybe this is a HUGE undertaking and I might be better off with windows peer to peer to network.   

I study hard drive imaging and hard drive cloning this is my area of interest.  I did once restore a Ubantu HD with a acronis 13 image.   I have been with dos and windows from their beginning but dont know much about linux.      

I am thinking I can use norton internet security to scan all the files on the linux server.   ?

I need advice and help here.

---

### Post by sp40140 on 2018-10-17
Two simple options are : 1] samba 2] sftp.
Both are quite simple to set up. And have excellent tutorials available in this forum and also many places online.
Pick the one which you think will work better for you.

As to scanning the file on linux server from norton in windows and antivirus in general: 
I am not sure.
You will find various opinions on antivirus here.

---

### Post by SeijiSensei on 2018-10-17
You can run the free ClamAV virus scanner on the server itself.  It finds most Windows malware.  Some commercial virus providers have versions that run on Linux as well.  I can't evaluate these as I have only used ClamAV for this purpose.  All the machines on my home network run Linux, so viruses aren't much of an issue.  At one client site we used ClamAV to scan mail and objects downloaded from the web.  I don't believe any of the 200+ users became infected by either of these vectors.  (USB thumb drives brought from home are a different matter, and the most common source for infections my client saw on his Windows network.)

Scanning network resources from a Windows desktop client will be very slow.  It's much better to have the server scan itself.

Are you comfortable typing commands, or do you need a GUI interface to manage the server?  The Ubuntu Server distribution is all you need if you're okay at the command prompt.  Otherwise you might install a "light-weight" Ubuntu flavor like Lubuntu or Xubuntu.  Desktop versions can run all the server packages as well.  

In either case, you'll need to install the Samba server package to share files with Windows machines.  Usually the easiest thing is to let users map their home directories on the server, typically as drive H:.  You can also have shared folders that some or all users can access.  

Documentation for Samba is extensive.  You might start here:  [https://help.ubuntu.com/lts/serverguide/samba.html.en](https://help.ubuntu.com/lts/serverguide/samba.html.en)

---

### Post by mastablasta on 2018-10-19
i would say look into Zentyal (small business server based on Ubuntu). it comes with desktop and webUI (so you connect to server via browser).
There is also Openmediavault (debian based) and Nethserver. both are aimed at "home" users and are easy to setup and administer. you basically add "plugins" and configure stuff with user interface.

aside from Samba and sFTP you might also explore "clowds" such as for example Owncloud, Nextcloud and Seafile. all are relatively easy to install even in command line and after they are setup, you mostly run everything via WebGUIs, clients or do auto sync via selected folders. one benefit of such setup could be file versions. so you can restore an older version. alternately the snapshots of files are also available on BTRFS file system or ZFS4linux filesystem. so you can easily restore files from the past which comes in handy when sharing files.

the commercial antivirus tools work much better than clamav on linux. they are mostly command line only. they scan for windows viruses. i would suggest you use these rather than clamav as they have a better detection rate.

this is a 3 years old test: [https://www.csoonline.com/article/2989137/linux/av-test-lab-tests-16-linux-antivirus-products-against-windows-and-linux-malware.html](https://www.csoonline.com/article/2989137/linux/av-test-lab-tests-16-linux-antivirus-products-against-windows-and-linux-malware.html)

i've been following similar stuff for a while and Bitdefender and Avast seem to have consistently good detection rates in the past couple of years, though they are not be free. the best free (commercial) options are Sophos and Comodo.

however instead of doing this server scanning thing, you could just simply have antivirus on client PC (on windows) where a range of free and good antivirus software is available (including those made by Microsoft). and then just use clamav to catch any leftovers. since you won't open it to the internet and with antivirus protection on clients you would probably get away without any antivirus on the linux box.

---

