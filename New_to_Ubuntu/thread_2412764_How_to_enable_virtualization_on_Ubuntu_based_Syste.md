---
title: "How to enable virtualization on Ubuntu based System"
date: 2019-02-17
forum: New to Ubuntu
---

### Post by zak100 on 2019-02-17
Hi,
I bought a new machine from LinuxCertified but its an unbranded machine so I am facing problem in enabling virtualization. I dont know which menu i have to choose. I have attached the image of BIOS. I have gone through the following link but its related to HP:

[https://support.bluestacks.com/hc/en-us/articles/115003174386-How-can-I-enable-virtualization-VT-on-my-PC-](https://support.bluestacks.com/hc/en-us/articles/115003174386-How-can-I-enable-virtualization-VT-on-my-PC-)


I got following information about product using grep:
product: NBxxEZ
product: CT8G4SFD*24A.M16FE1

I have also followed the tutorial at:
[https://websiteforstudent.com/setup-linux-kvm-kernel-virtualization-module-on-ubuntu-18-04-lts-server](https://websiteforstudent.com/setup-linux-kvm-kernel-virtualization-module-on-ubuntu-18-04-lts-server)
Some body please guide me.

Zulfi.

---

### Post by deadflowr on 2019-02-17
Look in the BIOS' Advanced section which you can usually scroll with arrow keys.
See if anything relates to vt -x or virtualization.
You can also just check if virtualization is alreasy ready with
```
egrep -c '(vmx|svm)' /proc/cpuinfo
```
zero means no, any other number means yes.
You can also run
```
sudo lshw -sanitize
```
to see what info you can about the machine.
Run without the sanitize to get unadulterated info.
(the sanitize option removes some private info (ie serial numbers ip addresses, etc))

---

### Post by Dennis N on 2019-02-17
Your BIOS is from American Megatrends, so try:

Advanced > CPU Configuration > Secure Virtual Machine Mode > 

and set to 'enabled'

---

### Post by zak100 on 2019-02-18
Hi,
Thanks for your replies.

Denis: I have following option in advanced menu:
-->Advanced Chipset Control
SATA Mode ---------------------------------[AHCI Mode]
Power on Boot Beep                               [Disabled]
Battery Low Alarm Beep                          [Disabled]

There is no CPU Configuration option in advanced Tab

In Security Tab I have following options:
Set Supervisor password

System Mode -----------------------------------User
Secure Boot -------------------------------------Not active
Secure Boot-------------------------------------[Disabled]
TPM Configuration(which when clicked Shows me:
Security Device Support -----------------------[Enabled]
Pendinng Operation ----------------------------[None]
TPM20 Device Found

and the Boot Tab which shows me:
Boot Option Priorities
Boot Option #1 [Ubuntu (P4: Samsung SSD QV0 1TB)]
UEFI Setting

deadflowr:I got 12 value for egrep command.

Thanks for your help.

God bless you.

Zulfi.

---

### Post by mastablasta on 2019-02-18
you need to check the BIOS/UEFI version and then based on that, you can find information on internet how to enable virtualization. normally it is disabled for security reasons.

---

