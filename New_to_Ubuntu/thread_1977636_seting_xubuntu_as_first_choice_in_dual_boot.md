---
title: "seting xubuntu as first choice in dual boot?"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by cabz on 2012-05-10
Is there a way to have xubuntu listed first/ default in the dual boot up screen? I cant use windows on this pc because it overheats and shuts down in windows . I am trying to avoid a full clean and reinstall of xubuntu at this time.

---

### Post by kc1di on 2012-05-10
yes you can do that.
in a terminal type this command:

[CODEgrep menuentry /boot/grub/grub.cfg][/CODE]

you should see a list like this:

```
user@YourComputer:~$ grep menuentry /boot/grub/grub.cfg
menuentry 'Ubuntu, with Linux 2.6.35-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
```

your looking for the kernel that xubuntu is using.

in another terminal type:
```
sudo nano /etc/default/grub
```

you'll find a file that looks like this:

[CODE# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

**GRUB_DEFAULT=saved**
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="delayacct"
GRUB_CMDLINE_LINUX=""][/CODE]

change the line that says GRUB_DEFAULT=saved to 
GRUB_DEFAULT=**'Ubuntu, with Linux 2.6.35-31-generic'**

Save the file and exit 
now in terminal type :
```
sudo update-grub
```
Reboot xubuntu should now be the default boot.

---

### Post by cabz on 2012-05-11
> **kc1di said:**
> yes you can do that.
in a terminal type this command:

[CODEgrep menuentry /boot/grub/grub.cfg][/CODE]

you should see a list like this:

```
user@YourComputer:~$ grep menuentry /boot/grub/grub.cfg
menuentry 'Ubuntu, with Linux 2.6.35-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
```your looking for the kernel that xubuntu is using.

in another terminal type:
```
sudo nano /etc/default/grub
```you'll find a file that looks like this:

[CODE# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

**GRUB_DEFAULT=saved**
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="delayacct"
GRUB_CMDLINE_LINUX=""][/CODE]

change the line that says GRUB_DEFAULT=saved to 
GRUB_DEFAULT=**'Ubuntu, with Linux 2.6.35-31-generic'**

Save the file and exit 
now in terminal type :
```
sudo update-grub
```Reboot xubuntu should now be the default boot.

nope didnt work, I still get the windows first on startup. I rechecked and the grub default is saved right . any other ideas.

---

### Post by Enigmapond on 2012-05-11
Easy way-
Install Grub-Customizer and just make it the default top position.

---

