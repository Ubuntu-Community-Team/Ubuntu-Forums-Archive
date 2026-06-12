---
title: "bluetooth"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by hazman on 2008-06-03
i noticed when booting up someting about bluetooth.how do i get my bluetooth dongle to work so i can transfer files form my phone and visa versa

---

### Post by rraj.be on 2008-06-03
First you have to configure your bluetooth devices.

To detect your bluetooth devices

open terminal and type

```
sudo hcitool scan
```

It will search for any bletooth devices connected.

then it will return the adrres f that bluetooth device.

Then type 

```
sudo hcitool cc your-phone-mac-address

```

then type

```
sudo hcitool auth your-phone-mac-address

```

  Enter a numeric code into the dialog box that pops up. 

  Accept the pairing from your phone handset.


  Enter the same number on your phone

now your phone will be connected with your pc through bluetooth

---

