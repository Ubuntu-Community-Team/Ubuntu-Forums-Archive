---
title: "How to keep grub from hanging on the menu"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by AndyCanfield on 2012-05-13
Ubuntu 12.04 Server. Normal boot goes OK. But if something bad happens, like a power failure, grub hangs on the grub menu waiting for somebody to press Enter on the console.

This is an unattended server system; there will be no one on the console. There may not even be a console.

I found one kludge: replace /boot/grub/grubenv with an unreadable unwritable unsearchable directory. That way whoever is setting "recordfail=1" can not. But any other grub feature that depends on grubenv will also fail. I can't find any option anywhere that tells grub "Do not wait on the menu under any circumstances".

---

### Post by jtarin on 2012-05-13
[Possible fix for you.]("http://serverfault.com/questions/243343/headless-ubuntu-server-machine-sometimes-stuck-at-grub-menu")
[And here.]("http://askubuntu.com/questions/55551/how-can-i-force-ubuntu-to-boot-on-a-stuck-boot-menu")

---

### Post by AndyCanfield on 2012-05-13
Great! FYI Ubuntu 12.04 (grub 1.99) has a file /etc/grub.d/00_header and in there is a function that reads:
```
make_timeout ()
{
    cat << EOF
if [ "\${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=${2}
fi
EOF
}
```I changed that to:
```
make_timeout ()
{
    cat << EOF
  set timeout=0
EOF
}\

```and re-ran grub-mkconfig and now it works. Thanks!

---

### Post by jtarin on 2012-05-14
FYI that configuration is in the second link I posted.:P

---

### Post by AndyCanfield on 2012-05-17
> **jtarin said:**
> FYI that configuration is in the second link I posted.:P
It certainly is. And there's a good chance that the solution shown in that link is better than my solution, because it will show the menu without hanging on it, whereas my 'fix' just bypasses the menu. I don't know why I missed that when I first saw your post. Please pardon me.

---

### Post by jtarin on 2012-05-17
> **AndyCanfield said:**
> It certainly is. And there's a good chance that the solution shown in that link is better than my solution, because it will show the menu without hanging on it, whereas my 'fix' just bypasses the menu. I don't know why I missed that when I first saw your post. Please pardon me.No problem. I do it frequently. :P

---

### Post by brenthaag on 2013-03-02
Here's a tip from the bug that says it will be backported to 12.04:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/669481/comments/13]("http://https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/669481/comments/13")

```
echo GRUB_RECORDFAIL_TIMEOUT=0 | sudo tee -a /etc/default/grub
sudo update-grub
```

---

