---
title: "Location of RSA key file"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by pmohankumar on 2012-01-17
Hi friends,
i installed SFTP service and i connected my server through SFTP.
While connecting it asked, a RSA key to be saved in your local so that in next connection will be established automatically. i entered yes and it was saved.
In kettle tool, i need this RSA key file to connect to my server through SFTP.
So kindly help me to find the location where RSA key was saved.

Thanks,
mohan

---

### Post by I8NY on 2012-01-17
Well since you don't list the SFTP program I'll make my best guess on where it might be.  SSH and generated RSA keys (and your program too maybe) are placed in ~/.ssh called id_rsa usually.  Hopefully this works for you.

---

### Post by pmohankumar on 2012-01-20
Thanks friend,
I found the rsa key.

---

### Post by I8NY on 2012-01-20
I'm glad you found it.  A good habit is to mark the thread as solved when you are done.  It makes it easier for users the find stuff on the forums quicker.

---

