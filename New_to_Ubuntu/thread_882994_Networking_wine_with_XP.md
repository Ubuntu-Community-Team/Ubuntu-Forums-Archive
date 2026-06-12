---
title: "Networking wine with XP"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by TJCIB on 2008-08-07
I have a school information system program running through wine, no problems at all.

I would like to network it with the XP machines that hold its data files.  Obviously, all of the instances of this program must be running from the same data files.

Not quite sure where to start, but here are my initial thoughts:
Set up the XP Box as an NFS server.
Then mount the directory on my Ubuntu Box.
Would I have to mount the NFS share in the /.wine/*program*/*datalocation* directory.  I am new to wine, but I'm assuming it doesn't read directories outside of its emulated c:/ drive.

Any help would be great.

---

