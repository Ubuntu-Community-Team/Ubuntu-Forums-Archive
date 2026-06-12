---
title: "[SOLVED] how to become super user ?"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by trigsenior on 2008-05-30
hello, 

I am trying to folow this tutorial to install Back track on a usb.

[http://www.i-hacked.com/content/view/260/1/](http://www.i-hacked.com/content/view/260/1/)

however when i run 

./bootinst.sh

which i ran as su,  i get permission denied is there any higher permission ?

thanxs =)

---

### Post by kpkeerthi on 2008-05-30
Run the command with sudo
```
sudo ./bootinst.sh
```

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by justleen on 2008-05-30
normally you'd use "sudo <command>" to run as root.
If you need a root login, you can use "sudo su" to become root.

---

### Post by vishzilla on 2008-05-30
Superuser Root is suppressed in Ubuntu by default. The sudo command temporarily gives us 'God-like' privileges ;)

---

### Post by x88a on 2008-05-30
```
sudo -s
```
then u will become root

---

### Post by kaboodle_fish on 2008-05-30
Wear your underpants on the outside and put on a cape

---

### Post by iaculallad on 2008-05-30
> **trigsenior said:**
> hello, 

I am trying to folow this tutorial to install Back track on a usb.

[http://www.i-hacked.com/content/view/260/1/](http://www.i-hacked.com/content/view/260/1/)

however when i run 

./bootinst.sh

which i ran as su,  i get permission denied is there any higher permission ?

thanxs =)

You might be running the command in a read-only mode USB, try to mount your USB for a read/write access then re-run ./bootinst.sh

---

### Post by trigsenior on 2008-05-30
ok i became root i still get permission denied


/media/disk-1/boot$ sudo ./bootinst.sh

-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
                        Welcome to Slax boot installer                         
-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-

This installer will setup disk /dev/sdg1 to boot only Slax.

Warning! Master boot record (MBR) of /dev/sdg will be overwritten.
If you use /dev/sdg to boot any existing operating system, it will not work
anymore. Only Slax will boot from this device. Be careful!

Press any key to continue, or Ctrl+C to abort...


Flushing filesystem buffers, this may take a while...
Setting up MBR on /dev/sdg...
./bootinst.sh: line 48: ./boot/syslinux/lilo: Permission denied


maby it is a problem with the script ?

permission on usb 

user ... my name

folder acces : create and delete files
file acces : read and write

---

### Post by trigsenior on 2008-05-30
> **kaboodle_fish said:**
> Wear your underpants on the outside and put on a cape

ps you made my day =)

---

### Post by iaculallad on 2008-05-30
You might as well try visiting their Wiki page.

[http://backtrack.offensive-security.com/index.php/Main_Page](http://backtrack.offensive-security.com/index.php/Main_Page)

---

### Post by trigsenior on 2008-05-30
thanxs for your help !
ok there is a tutorial on how to do it in windows might have more succses but , thanxs for your help and il keep you posted =)

---

### Post by deadrabbit on 2008-06-17
It's a permissions problem - syslinux and lilo under boot/syslinux need to be executable: cd to the boot/syslinx directory, then run ```
sudo chmod +Xx syslinux lilo
```

I don't know why they left that out of their documentation, but you can find it on their forums.

---

