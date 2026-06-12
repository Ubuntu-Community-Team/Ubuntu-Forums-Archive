---
title: "Creating shared directory"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by Konstabel on 2008-10-04
How can I share a directory within a home network so that it is accessible by a Windows machine?

---

### Post by Trevster on 2008-10-04
You can right click on a folder in nautilus and then select share options.

---

### Post by Konstabel on 2008-10-05
And how can I share the directory from a console?

---

### Post by xreaper on 2008-10-05
> **Konstabel said:**
> And how can I share the directory from a console?

first you're probably going to need to install samba.

sudo apt-get install samba

Its basically makes ur system 'windows friendly'. Give me 5 minutes and I'll post a link to the howto.

---

### Post by xreaper on 2008-10-05
Heres the simplest Howto that I could find. Hope it works for you ^^

[http://www.go2linux.org/how-to-install-samba-on-linux-with-swat](http://www.go2linux.org/how-to-install-samba-on-linux-with-swat)

---

### Post by Konstabel on 2008-10-05
Thanks reaper, I'll have a look

---

### Post by xreaper on 2008-10-05
Alternatively, If you are only dual-booting, then the answer is simple. create a FAT32 partion and store all of your files that you want to share in it.

---

### Post by hyper_ch on 2008-10-05
fat32 is outdated, windows can read/write ext2/3 with according drivers and linux can read/write ntfs

---

### Post by xreaper on 2008-10-05
Yeah, was just going for the simplest way to do it, but that works too !! =]

---

### Post by Konstabel on 2008-10-05
Reaper, thanks that worked. Got to share my folders, but without the ssl tunneling. Now I have another question.

The How-to explains it tunneling the connection through ssl. I already have a ssh connection setup. Could you please explain how to tunnel through this instead?

---

### Post by psypher on 2008-11-02
When using the "Share options" feature. How do I allow user only access and not guest access. When I try logging into the share i get the username promts, enter my user account details and get rejected. Why do I still have to run smbpasswd -a??

When is this stuff going to be simple? I know how to use samba using the smb.conf file. but you can no longer expect avg users to hack the smb.conf file, and now with this new feature those settingss aren't stored in smb.conf. When creating a new share there should be a pop-up asking to create the samba. Please could this added. One less command line thing normal users have to do, one step closer to being a true competitior to the other commercial OS's

---

