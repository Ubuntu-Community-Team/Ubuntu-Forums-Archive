---
title: "NOkia PC suite for ubuntu"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by harimurugan on 2012-03-18
plz tell any software like PC suite in ubuntu..

---

### Post by Holdolin on 2012-03-18
What does it do?  Taking a stap in the dark, Nokia is most popular (to me) as a camera/image company.  If your looking for imaging software, shotwell is a more poplular app in Ubuntu.

---

### Post by 2F4U on 2012-03-18
Its not official, but Nokuntu may be what you are looking for:

[http://mygeekopinions.blogspot.de/2011/07/nokuntu-unofficial-nokia-pc-suite-for.html](http://mygeekopinions.blogspot.de/2011/07/nokuntu-unofficial-nokia-pc-suite-for.html)

---

### Post by harimurugan on 2012-03-22
> **2F4U said:**
> Its not official, but Nokuntu may be what you are looking for:

[http://mygeekopinions.blogspot.de/2011/07/nokuntu-unofficial-nokia-pc-suite-for.html](http://mygeekopinions.blogspot.de/2011/07/nokuntu-unofficial-nokia-pc-suite-for.html)
  Nokuntu is not fully working.. not able to connect phone itself..

---

### Post by 3rdalbum on 2012-03-22
Wammu (and Gammu) may be an option for certain features that Nokia PC Suite has. Obviously you won't be able to do things like update your firmware, but then you can't do that with many phones anyway.

What exact function do you want anyhow? Nokia phones don't need PC Suite for managing videos, photos or music. If all you want to do is put video/photos/music onto your phone all you need to do is connect the phone, tell it to go into Mass Storage mode (it should ask you when you connect) and then drag and drop the media onto the disk on Ubuntu.

---

### Post by harimurugan on 2012-03-22
> **3rdalbum said:**
> Wammu (and Gammu) may be an option for certain features that Nokia PC Suite has. Obviously you won't be able to do things like update your firmware, but then you can't do that with many phones anyway.

What exact function do you want anyhow? Nokia phones don't need PC Suite for managing videos, photos or music. If all you want to do is put video/photos/music onto your phone all you need to do is connect the phone, tell it to go into Mass Storage mode (it should ask you when you connect) and then drag and drop the media onto the disk on Ubuntu.
  
i want to connect to internet using phone sometimes & automatic storage for new pictures in phone..

---

### Post by codemaniac on 2012-03-22
> **harimurugan said:**
> i want to connect to internet using phone sometimes & automatic storage for new pictures in phone..

If you want to connect to internet using your phone as a usb modem . use wvdial .It is available in the repos .

```
sudo apt-get install wvdial
```
In order to use your phone as data storage ,select "data storage" option when you connect your phone to the system via usb cable .

---

### Post by codemaniac on 2012-03-22
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

---

### Post by harimurugan on 2012-03-22
> **codemaniac said:**
> If you want to connect to internet using your phone as a usb modem . use wvdial .It is available in the repos .

```
sudo apt-get install wvdial
```In order to use your phone as data storage ,select "data storage" option when you connect your phone to the system via usb cable .

is this allows connectivity though bluetooth or i need USB cable????

---

### Post by codemaniac on 2012-03-22
you need a usb cable .
please go through the community documentation to set up wvdial in your system .
[https://help.ubuntu.com/community/Di...to/SetUpDialer](https://help.ubuntu.com/community/Di...to/SetUpDialer)

---

### Post by codemaniac on 2012-03-22
Here is the tutorial for bluetooth dialup .
[https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup)

---

