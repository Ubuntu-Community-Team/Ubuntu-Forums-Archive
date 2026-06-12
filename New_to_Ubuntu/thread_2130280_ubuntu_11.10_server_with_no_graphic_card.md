---
title: "ubuntu 11.10 server with no graphic card"
date: 2013-03-28
forum: New to Ubuntu
---

### Post by qyuu02 on 2013-03-28
Hi, I'm newbie, please help me

the server is work fine, once i shutdown it, and going to turn it on, it will stuck on booting

"loading linux 3.0.0-12-server"

here is the before boot command

record fail
insmod gzio
insmod part_gpt
insmod ext2
set root ='(hd0,gpt2)'
search --no-floppy --fs-uuid --set=root (series of number and alphabet here)
linux /vmlinuz-3.0.0-12-server root=/dev/mapper/root ro recovery nomodest
initrd /initrd.img-3.0.0-12-server

please help me :) i need to reach text/console

---

### Post by mastablasta on 2013-03-29
have you tried any of the boot options? or perhaps recovery mode?

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

