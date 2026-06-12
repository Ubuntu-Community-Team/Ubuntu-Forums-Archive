---
title: "SGX disabled by BIOS"
date: 2022-06-01
forum: New to Ubuntu
---

### Post by davyyg on 2022-06-01
Hello,


 I installed dual OS: Ubuntu & Win 11.  It normally works until  one day, when I tried to enter ubuntu it shows me this error message:

 
SGX disabled by BIOS.

 
I tried this solution: ref: [https://community.intel.com/t5/Intel-Software-Guard-Extensions/installing-SGX-driver-for-ubuntu/m-p/1094996](https://community.intel.com/t5/Intel-Software-Guard-Extensions/installing-SGX-driver-for-ubuntu/m-p/1094996)

 
In Advance Tab, I only see:

 VTX there is no SGX.

---

### Post by ActionParsnip on 2022-06-02
Does the system have a make and model?

---

### Post by tea for one on 2022-06-02
> **davyyg said:**
> 
 I installed dual OS: Ubuntu & Win 11.  It normally works until  one day, when I tried to enter ubuntu it shows me this error message:
SGX disabled by BIOS.

I do not think that this is an error message, probably just providing information.

It refers to Software Guard Extensions - a set of security-related instruction codes that are built into some Intel central processing units.

You should have the option to enable/disable this in UEFI settings (security tab?)
On my PC, It has been disabled for more than 3 years without presenting any problem.
The message appears for less than one second and I always ignore it.

Enterprise/business users may find it beneficial if each PC is used by more than one employee.
For home users, generally not essential.

---

### Post by davyyg on 2022-06-05
My Boot Mode is set to: Legacy (instead of UEFI).

---

### Post by davyyg on 2022-07-24
Ubuntu, with Linux 5.15.0 - 25 - generic
Ubuntu 22.04 LTS


[ 0.157991] x86/cpu: SGX disabled by BIOS.
/dev/sda5: clean, 174547/8298496 files, 2926401/33175138 blocks
[ 11.509132] nouveau 0000:01:00.0: bus: MMIO read of 00000000 FAULT at 6013d4
[ PRIVRING ]
You are in emergency mode. After loggin in, type "journalctl -xb" to view
system logs, "systemctl reboot" to reboot, "system ctl default" to "exit"
to boot into default mode.
Press Enter for maintenance
(or press Control-D to continue):


Any idea why the error appeared?

---

