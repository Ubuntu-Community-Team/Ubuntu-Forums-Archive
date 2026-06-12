---
title: "Help: gedit 2.14 Remote Save?"
date: 2006-03-28
forum: Programming Talk
---

### Post by poster333 on 2006-03-28
I read that gedit 2.14 features remote saving.  I'm running Dapper with gedit 2.14.1, but all the remote files I open are still read-only.  ](*,) 

Can someone please explain the procedure for opening and saving remote files in the new gedit?

---

### Post by psayre23 on 2007-09-09
I'm not sure if this is exactly how I fixed this, but it sounds right.

run "gconf-editor" and run through the tree app > gedit-2 > preferences > editor > save

There should be a key called "writable_vfs_schemes", just add the one you want. Mine reads "ssh,sftp,smb,dav,davs,ftp"

I believe I just added the ftp and it then let me save to ftp files.

---

### Post by Ken Iovino on 2007-09-16
Thanks psayre23, I was having the same issue and your suggestion fixed that!

---

