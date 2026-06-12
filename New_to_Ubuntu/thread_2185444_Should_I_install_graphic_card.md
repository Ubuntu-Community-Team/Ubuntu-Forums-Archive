---
title: "Should I install graphic card?"
date: 2013-11-02
forum: New to Ubuntu
---

### Post by macakcira on 2013-11-02
I am a new Ubuntu user and after installation I have noticed that instead my ATI Radeon 4650 HD graphic card is not using its native driver, but this one: Gallium 0.4 on AMD RV730. So should I keep this driver or should I install ATI Radeon 4650 HD driver from ATI website?

---

### Post by deadflowr on 2013-11-02
No.
Your card can't use any of the AMD drivers anymore.
AMD stopped support for your card and the old drivers can't be installed on Ubuntu anymore.

Your card is using the open-source radeon driver, which is probably as good as it will be.

---

### Post by macakcira on 2013-11-02
So it's using this driver: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) ?

---

### Post by deadflowr on 2013-11-02
> **macakcira said:**
> So it's using this driver: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) ?

Most likely.
You can run this command
```
sudo lshw -C display | grep driver
```
And whatever driver is in use will show up.
The amd open source driver should say radeon. The AMD-closed source driver is called fglrx.

FYI, the sudo in front means the command is to be run as root. This means you'll need to use the password you set when you installed.
The password field will be blank(invisible), so enter it as best you can and then hit enter.

---

### Post by macakcira on 2013-11-02
Yes, it says driver=radeon. Hopefully it will work fine. Thanks.

---

### Post by mörgæs on 2013-11-03
If this solves your problem please mark the thread so.

---

