---
title: "virtual box cannot access files?"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by paker on 2011-10-16
Virtual Box installed and runs well. But useless because I cannot access Downloads, Documents, Desktop, Music, etc. When I connect a USB thumb drive, VB doesn't see it.

---

### Post by ex1t on 2011-10-16
Have you tried mounting the files via Devices > Shared Folders from the host machine yet?
You won't be able to access any of your normal files from a guest virtual machine until you have shared the file/folders in the context menu.

---

### Post by paker on 2011-10-16
I am too ignorant to read your post. Where is DEVICES? Do you mean Root>dev? I don't see Shared under dev. Thanks.

---

### Post by haqking on 2011-10-16
> **paker said:**
> I am too ignorant to read your post. Where is DEVICES? Do you mean Root>dev? I don't see Shared under dev. Thanks.

You need to setup shared folders to access files between a VM or use dropbox or similar method if you dont get on with shared folders

Read the instructions on vbox website [http://www.virtualbox.org/manual/ch04.html#sharedfolders](http://www.virtualbox.org/manual/ch04.html#sharedfolders)

and this topic here
[https://forums.virtualbox.org/viewtopic.php?t=15868](https://forums.virtualbox.org/viewtopic.php?t=15868)

---

### Post by mister_playboy on 2011-10-16
Also, you need to be using the Oracle add-on pack if you want USB support in the VM.

---

### Post by haqking on 2011-10-16
> **mister_playboy said:**
> Also, you need to be using the Oracle add-on pack if you want USB support in the VM.

yes for usb you need the extensions pack

also maybe needed to add to vboxusers group

```
sudo usermod -a -G vboxusers username 
```

where username is your username

---

### Post by paker on 2011-10-16
Thank you for the replies. This seems to be too involved for me. The linked guide did not quite apply to what I have. Must be a version difference. I am giving it up. Maybe someone will post a writeup for Virtual Box for Dummies in the near future. Thank you all.

---

### Post by bodhi.zazen on 2011-10-16
> **paker said:**
> Maybe someone will post a writeup for Virtual Box for Dummies in the near future. Thank you all.

Someone already has

download.virtualbox.org/virtualbox/4.1.4/UserManual.pdf  

Just skip to the relevant section, it is well written.

---

