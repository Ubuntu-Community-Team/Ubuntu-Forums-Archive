---
title: "Sharing public folders between Vista and Ubuntu 8.10"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by pablolie on 2008-11-09
Seems easy enough. I have set up networking and Samba and open folders and workgroup on both a Vista 64 and an Ubuntu 8.10 machine. But while I can access the Ubuntu folder from the Vista machine, I can not access the public folder on the Vista machine from the Ubuntu machine. Very odd. I see the Vista computer, but don't get visibility into its public files, even though they I know they're enabled...

Is there an in-depth tutorial somewhere? I am especially interested in the way that Ubuntu and Windows view sharing folders in home networks or workgroups.

---

### Post by kerpow on 2008-11-09
Sounds like you have the hard bit working, with only (what should be) the easy bit left.

Can you confirm that you can see the shares on the Vista machine from any other machines on the network?   

The Samba clinet is installed as part of the basic Ubuntu install you should be able ot navigate to shares via the file manager application by typing into the address bar:

smb://192.168.100.10/sharename

Where the above IP is the IP of the Vista share and the sharename is the one you have.  Not using the sharename will prompt Ubuntu to list the available shares.

If you are not able to see the Vista files from other machines (or don't have other machines to test with) it would be worth checking you Vista (and or 3rd party) firewall settings.

Hope that helps.

---

