---
title: "Booting from encrpyted USB drive?"
date: 2016-09-27
forum: New to Ubuntu
---

### Post by Citta on 2016-09-27
I would like to install the OS via .iso on a stick. To prevent problems, e.g. after loss, I want to have it encrypted. But booting might be not possible, if the stick is encrypted? Thanks for your hints!

---

### Post by phyosithumaung on 2016-09-27
As my understand, bootable USB can't encrypt after you setting up as "bootable". It will harmful to your USB Drive. Thanks.

---

### Post by mastablasta on 2016-09-27
it should work, if you separate the  /boot (will not be encrypted) and do a full install. i am not sure if full encryption would also be possible.

---

### Post by Citta on 2016-09-27
Is a step-by-step instruction in the mentioned Manual? If not, how is it done/where is it explained?

---

### Post by mastablasta on 2016-09-28
procedure for a full install on USB is same as normal install procedure. in this case you would want to manually create /boot.

also migh be good to read this: [SIZE=2]https://help.ubuntu.com/community/EncryptedFilesystems
[/SIZE]
and this: [SIZE=2]https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorage
[/SIZE]

---

