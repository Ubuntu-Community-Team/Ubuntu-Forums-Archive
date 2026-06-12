---
title: "cant force mount hard drive"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by amaconinatl on 2008-07-31
i need help force mounting my hard drive i crashed my windows vista and the device indicates an unclean shutdown. faild to mount'dev/sda1':Operation not supported mount is denied because NTFS is marked to be in use. The options i have are to get ana adapter for my desktop computer to put my laptop hard drive in for force mount the hard drive in ubuntu. Ubuntu automatically named my hard disk " " so it told me to put this into terminal 
code:
mount -t ntfs-3g /dev/sda1 /media  -o force

when i put that in terminal it says only root can do that what do i do

---

### Post by lordadi on 2008-07-31
Hi,


If  it says that only root can do that, then use this
```
sudo mount -t ntfs-3g /dev/sda1 /media -o force

```

The sudo part gives you admin access and the command as run as an adminstrator. It will ask you for your password. Please remember that when you type in your password, you will **NOT** see it or asterisks or anything, however the password is being accepted. Finish typing it and hit enter.

This assumes that the command provided is correct.

However, I am not sure as to the safety of this command.


Cheers,


Lordadi.

---

### Post by sisco311 on 2008-07-31
If you are dual booting, then boot in windows and 
make a clean shutdown(no hibernation).

If you really want to force mount the partition:
```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/sda1 /media/windows -o force
```

---

### Post by amaconinatl on 2008-07-31
ok thank you but i forgot to mention im running ubuntu off disk not installed so i dont have a password

---

### Post by amaconinatl on 2008-07-31
ok nvm it worked didnt ask for password tyvm ppl

---

