---
title: "display driver issue for lenovo G580 laptop"
date: 2013-03-31
forum: New to Ubuntu
---

### Post by manjusun on 2013-03-31
Hi All,

I have issues with display drivers for my laptop on which i have installed ubuntu 12.10(32bit).
When launching android emulator got errors for display driver incompatability.

Now iam downloading latest drivers for the same, I have options in lenovo downloads as below
please let me know which one of below i should use
-Thanks & regards,
Manjunath S

1) Linux
2) Red hat enterprise linux 6 (32bit)
3) Red hat exterprise linux 6 (64bit)
4) Suse linux enterprise server 11(32bit)
5) Suse linux enterprise server 11(64bit)

---

### Post by carl4926 on 2013-03-31
> **manjusun said:**
> Hi All,

I have issues with display drivers for my laptop on which i have installed ubuntu 12.10(32bit).
When launching android emulator got errors for display driver incompatability.

Now iam downloading latest drivers for the same, I have options in lenovo downloads as below
please let me know which one of below i should use
-Thanks & regards,
Manjunath S

1) Linux
2) Red hat enterprise linux 6 (32bit)
3) Red hat exterprise linux 6 (64bit)
4) Suse linux enterprise server 11(32bit)
5) Suse linux enterprise server 11(64bit)

Probably not required
What graphics are they. My G550 uses intel
Graphics:  Card: Intel Mobile 4 Series Chipset Integrated Graphics Controller 
Works perfectly

---

### Post by Mark Phelps on 2013-03-31
If your laptop uses Intel drivers, they were installed automatically when you first intalled Ubuntu.

You could go to the link below to see if there are any newer drivers:

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13815&lang=eng]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13815&lang=eng")

---

### Post by manjusun on 2013-04-01
Hi All,

Thanks for your response,

My system configuration is below
from About this computer,
        ------------------------------
Overview
------------
Memory ==> 3.8GiB
Processor ==> Intel core i5-3210M CPU @ 2.5GHzx4
Graphics ==> Unknown
OS type 32 bit
Disk 488.2GB

Graphics
--------------
Driver ==> Unknown
Experience ==> Standard




here is the error message i get when launching emulator

Starting emulator for AVD 'Android_4_2_2_API_17'
Failed to load libGL.so
error libGL.so: cannot open shared object file: No such file or directory
Failed to load libGL.so
error libGL.so: cannot open shared object file: No such file or directory
emulator: emulator window was out of view and was recentered

---

### Post by carl4926 on 2013-04-01
Please do

```
sudo apt-get install inxi
```

then when that is done

```
inxi -F
```

Post result


FYI: I'm not sure you can equate your experience with this application as a issue with your graphics driver.

---

### Post by hometowndirectories on 2013-04-30
I'd like to point out something, not sure if it matters, but the G580 I have has a 64bit processor. Are you using the 64bit version & drivers?

---

