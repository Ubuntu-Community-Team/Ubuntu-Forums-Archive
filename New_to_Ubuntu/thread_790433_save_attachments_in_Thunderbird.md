---
title: "save attachments in Thunderbird?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by laytek on 2008-05-11
Hi Everyone,

How do I save an e-mail attachment to a samba share on another computer (rather than a local folder) when using Thunderbird?

Thanks,
LayTek

---

### Post by aysiu on 2008-05-11
Mount the samba share first?

---

### Post by laytek on 2008-05-11
aysiu,

Thanks for the reply. The samba share is mounted and seems to work perfectly. I use it all the time from nautilus and the other computers. I can't seem to navigate to it on Thunderbird's "Save All Attachments" window that pops when I select (right click on) an attachment.

LayTek

---

### Post by laytek on 2008-05-12
bump

---

### Post by gunnarvxo on 2009-10-08
Using Ubuntu 9.04, T.bird 2.0.0.23

When the share has been opened e.g. via Places/Network/ etc you cannot use a file there as attachment in a Thunderbird email. If you check such a file in Nautilus  (right-click-Properties) the file Location is shown as smb://<sambahost>/<share>/<path_on_share>

I never got those files to work as attachments by Thunderbird. This is a known T-bird problem:
[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/384760](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/384760)

The workaround is to mount these shares from the command prompt, e.g. via
 smbmount  "//<sambahost>/<share>/<path_on_share>t" /media/sambashare -o user="<domain>\<winusername>i"

This makes the files on the share to be reachable also via  /media/sambashare (any path you choose) and voilà, they can be used as attachments!

This is a bit of a hassle, but it may be a bigger hassle, having to copy files to a local directory before being able to attach them to emails.

---

### Post by dubbelodub on 2009-11-13
```
ln -s ./.gvfs network
```
Voila. Access all your samba shares but pointing thunderbird at your newly created network symlink.

---

