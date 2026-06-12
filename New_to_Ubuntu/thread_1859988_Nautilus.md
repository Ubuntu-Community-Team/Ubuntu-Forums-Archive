---
title: "Nautilus"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by dtay on 2011-10-14
Alright, whenever I use Nautilus as my SFTP client, it fails. Doesn't connect and then sends me to my ISP with an unfound address. My understanding is that you use sftp://username@sftp.server.com ...is this correct? any help would be appreciated...windows guy here finally seeing the light

---

### Post by An Sanct on 2011-10-14
The correct syntax for ftp would 

```

ftp://username:password@hostname/
ftps://username:password@hostname/

```But it is strongly advised not do it this way, since U:P go out unencrypted, thus loosing the point of a secure connection ...

If I'm mistaking, please somebody correct me, I am always glad if someone finds errors and corrects me (learning me something)

---

### Post by dniMretsaM on 2011-10-14
Why not use a different client? FileZilla is a great GUI client.

---

### Post by WasMeHere on 2011-10-14
Hi dtay,

This works for me. When mounted, I can drag the icon of the directory to the left side panel and have a quick launcher of it (but of course, I'm prompted to enter password each time).

In the Nautilus menu try
file -- connect to server -- service SSH
and fill in the form.

So do not use 'service FTP' but 'service SSH' to run the sftp mode.

Have fun finding out about Ubuntu :-)
Olle

---

### Post by collisionystm on 2011-10-14
Use fire ftp in firefox.

Best SFTP client you can get. Works just like WINSCP.

---

### Post by dtay on 2011-10-14
thanks you guys are awesome!

---

