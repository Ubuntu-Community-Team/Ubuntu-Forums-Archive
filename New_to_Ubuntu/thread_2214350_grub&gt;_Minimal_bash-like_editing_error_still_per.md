---
title: "grub&gt; Minimal bash-like editing error still persists after reinstalling grub"
date: 2014-03-31
forum: New to Ubuntu
---

### Post by aakanksha on 2014-03-31
Hi All,

Firstly, I can't thank ubuntu forums enough for being my savior until now for common issues seen in ubuntu. However, I am seeing a persistent issue here and want to understand what might be going wrong. I saw the grub prompt this morning when I switched on my ubuntu system. It is not a dual-boot system and just has Ubuntu 12.04 on it. I tried the command "boot" on the grub prompt in the hope that it would boot. I got the error "error: no loaded kernel". I came back and checked for the solution to that problem. It seemed that the bootloader had some problems that could be fixed using a live CD and booting from it. Then I had to reinstall grub using a few commands and that would solve it. So I followed the same procedure. I booted using a CD and typed in these commands:
[EMAIL="ubuntu@ubuntu.com"]ubuntu@ubuntu.com[/EMAIL]$ mount /dev/sda2 /mnt
[EMAIL="ubuntu@ubuntu.com"]ubuntu@ubuntu.com[/EMAIL]$ sudo grub-install --boot-directory=/mnt /dev/sda

I also ran the bootinfoscript. Attached is the output from the script. After successfully updating grub, I restarted my system and saw the same grub prompt again. On running the "boot" command, I see the "no loaded kernel" error again. I tried the following commands at the grub prompt:
grub>ls
(hd0) (hd0, gpt3) (hd0, gpt2) (hd0, gpt1) (fd0)
grub>search --file /vmlinuz
hd0, gpt2
grub>set root=(hd0, gpt2)
linux /vmlinuz root=/dev/sda2
error: no such disk
grub>set
prefix=(hd0, gpt2)/boot/grub
root = (hd0,

Could you please tell me what might be going wrong and why this error might be occurring? I don't know if this helps, but I have faced the "grub rescue no such disk" error once before and since it was a fresh install, I just reinstalled Ubuntu and it worked in my 2nd attempt. I have seen a range of answers for the "grub> minimal bash like..." error, but I wanted to know exactly what is going on, since grub seems to be having some recurring problems on my machine. Thanks a lot for your advice and help!

Regards,
Aakanksha

---

