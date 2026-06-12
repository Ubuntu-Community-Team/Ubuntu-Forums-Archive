---
title: "samba credential file problem"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by raccoonone on 2008-06-21
I'm trying to mount a Windows share, and I tried the following command which works fine: "sudo mount -t smbfs -o username=<my user name>,password=<my password> //NEW/family_files /home/christopher/Shares/family_files"

However when I tried creating a file /root/.credentials and filling it in with:
username=<my user name>
password=<my password>

and then using the command "sudo mount -t smbfs -o credentials=/root/.credentials //NEW/family_files /home/christopher/Shares/family_files"

I receive this error:
"mount error 20 = Not a directory
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)"

Can anyone tell me what I'm doing wrong?

---

### Post by raccoonone on 2008-06-22
I still haven't been able to get this to work. Anyone have a suggestion?

---

### Post by Dedoimedo on 2008-06-22
Hello,

1. Try cred= instead of credentials=

2. And try -t cifs cred= OR credentials=

Dedoimedo

---

### Post by raccoonone on 2008-06-22
I tried both of those and still no luck, anything else I can try?

---

### Post by brallan on 2009-01-06
does the output of ```
cat /proc/fs/cifs/LinuxExtensionsEnabled
```

read ```
1
```?

you could try ```
sudo echo 0 > /proc/fs/cifs/LinuxExtensionsEnabled
``` and give it another try. worked for me.

---

### Post by raccoonone on 2009-01-06
Thanks for the suggestion. I managed to fix this myself. The problem was that there needs to be a blank line at the end of the credentials file to signify the end.

---

### Post by Chainsaw76 on 2010-02-07
I was having the same issue. I could mount with -o username=jason,password=qwerty but when I tried to use a credential file it failed.

The fix for me was changing the format of my credential files from 
username = jason
password = qwerty

to 
username=jason
password=qwerty

The old format worked fine with preveious versions of ubuntu/Windows. but with 9.10 and Windows 7 I had to eleminate the spaces. (both updates were done around the same time, so I am not sure weather 9.10 (or a kernel update) or Windows 7 caused it to stop working.

I hope this helps someone.

-Jason

---

