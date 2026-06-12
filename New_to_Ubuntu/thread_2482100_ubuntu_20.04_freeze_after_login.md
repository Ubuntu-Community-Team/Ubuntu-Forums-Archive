---
title: "ubuntu 20.04 freeze after login"
date: 2022-12-19
forum: New to Ubuntu
---

### Post by juraj-papic on 2022-12-19
Hi all,

Yesterday after an update I login in to my notebook and my Ubuntu gets freeze, I don't have to many time to do some changes, because of the freeze, I did a grup / advance options / and selected 2 prior versions before the update and still the same. Any help more than appreciated. 

thanks.

---

### Post by MAFoElffen on 2022-12-19
What options were on that Grub > Advanced 0ptions menu?

---

### Post by juraj-papic on 2022-12-20
This is the output I have
ubuntu, with Linux 5.15.0-56-generic
ubuntu, with Linux 5.15.0-56-generic (recovery mode)
ubuntu, with Linux 5.15.0-52-generic
ubuntu, with Linux 5.15.0-52-generic (recovery mode)
ubuntu, with Linux 5.13.0-52-generic 
ubuntu, with Linux 5.13.0-52-generic  (recovery mode)
I have this until 5.8.0.63 
And Also now I see on the startup the option for Ubuntu on Wayland.

---

### Post by MAFoElffen on 2022-12-20
Try Wayland first... And what does this computer have for graphics? Please run the [UbuntuForums system-info script]("https://github.com/UbuntuForums/system-info") ... and post the URL of were you uploaded it.

---

### Post by juraj-papic on 2022-12-20
My system hangout before I can complete the task.

---

### Post by juraj-papic on 2022-12-20
I had to change the kernel to version Linux linux 5.13.0-52-generic #59~20.04.1-Ubuntu so I can run the script.

[https://termbin.com/p7yf](https://termbin.com/p7yf)

---

### Post by MAFoElffen on 2022-12-20
And what happens if you try Xorg? I see you are intel GPU and running wayland...

And you couldn't run the script with which Kernel? Why?

---

### Post by ajgreeny on 2022-12-21
I don't know the script very well but at the bottom of your report it looks,s as you were using the 5.15.0-56 kernel which you said doesn't work.
> The Linux Kernel Command Line use to boot was: 
BOOT_IMAGE=/boot/vmlinuz-5.15.0-56-generic root=UUID=44e760d4-48e9-469f-875d-c1338c59b38a ro quiet splash vt.handoff=7
Can you clarify this please so we can avoid potential problems.

---

### Post by juraj-papic on 2022-12-21
Is not saying Xorg is saying Ubuntu , and it freeze.

---

### Post by juraj-papic on 2022-12-21
I had to run ESC , and change to the Kernel 15.3 , I did a  uname -r to verify the kernel version.

---

