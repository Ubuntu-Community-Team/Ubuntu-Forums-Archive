---
title: "Sharing files between Ubuntu and Windows XP in a workgroup"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by C!pheR on 2008-10-12
Hi,

I'm trying to share files over my LAN. I've followed this [excellent article]("http://ubuntuforums.org/showthread.php?t=202605")

In Windows, I can now see the computer running Ubuntu when browsing workgrouped computers, however when I try to connect to that I get the following error message:

> \\Stephen-desktop is not available. You might not have permission to access this network resource. Contact the administrator of this server to find out if you have access permissions.

The network path was not found.When trying to view the workgroup from Ubuntu, I can only see Stephen-desktop in the workgroup and not my Windows PC or laptop (both of which are displayed in the Windows workgroup alongside stephen-desktop).

Any thoughts?

Edit: bodhi.zazen : Link fixed.

---

### Post by CaptainHowdy000 on 2008-10-12
Sorry I was looking for help and stumbled here but I thought I should let you know that your link is not correct in the post.

---

### Post by porchrat on 2008-10-12
> **C!pheR said:**
> Hi,

I'm trying to share files over my LAN. I've followed this [URL="http://http://ubuntuforums.org/showthread.php?t=202605&highlight=setup+samba+windows+network&page=66"][COLOR="Navy"]_excellent article_[/COLOR]
[/URL]

In Windows, I can now see the computer running Ubuntu when browsing workgrouped computers, however when I try to connect to that I get the following error message:



When trying to view the workgroup from Ubuntu, I can only see Stephen-desktop in the workgroup and not my Windows PC or laptop (both of which are displayed in the Windows workgroup alongside stephen-desktop).

Any thoughts?

Is your firewall on the ubuntu machine down?...and is the user on the Windows XP machine the user that you allowed access to the samba share?

Also try making sure that that user exists on the ubuntu machine as well and that the user has the same password on both the XP and ubuntu machines.

---

### Post by Orange_and_Green on 2008-10-12
Just a few easy checks first...

Are you running a personal firewall on the windows PCs? If you are, don't forget to add the appropriate exceptions for Stephen-desktop.

Also, do you have iptables or a "firewall" (rather, an iptables config utility like firestarter/gufw/shorewall) set up on the Ubuntu PC? If you do, don't forget to add the appropriate exceptions for the windows PCs.

Captain Howdy's right, the link to the samba guide is broken, try posting it again. At any rate, make sure that the samba daemon is running on Stephen-desktop.

Good luck:KS

---

### Post by bodhi.zazen on 2008-10-12
> **CaptainHowdy000 said:**
> Sorry I was looking for help and stumbled here but I thought I should let you know that your link is not correct in the post.

Yes, but if you look at the URL you will see it is a small typo.

Here is the link :

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

I will fix the OP.

---

