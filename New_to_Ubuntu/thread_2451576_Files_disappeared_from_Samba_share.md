---
title: "Files disappeared from Samba share"
date: 2020-10-07
forum: New to Ubuntu
---

### Post by gourmetsaint on 2020-10-07
I had to change a zfs parameter (ie turn on compression) for a fileset. The same fileset is shared in Samba. I copied the files off the server to an external drive and back again to utilise the compression on the copy back. All went well - until I looked at the share from a Windows machine - those folders disappeared. They are there in Nautilus but not there from Windows. Folders I did not copy out and back are visible. I ran "sudo chown +r mark: /mnt/tgs-fs-01" but no change. All are 777 in permissions.

Any ideas?

Thanks, Mark

---

