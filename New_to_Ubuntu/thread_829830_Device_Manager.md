---
title: "Device Manager"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by Tharakanuwanpro on 2008-06-15
There is a device manager type manager in ubuntu . A friend told me its there in Ubuntu 7.04 but where is it in Ubuntu 8.04 Hardy Heron

Please Help

I don't Have internet connection in ubuntu . Only in windows i have ubuntu

---

### Post by oldb0y on 2008-06-15
You will find one in the repos, it needs to be installed.

---

### Post by bumanie on 2008-06-15
Try this in terminal > sudo apt-get install gnome-device-manager

---

### Post by Tharakanuwanpro on 2008-06-15
I dont have internet connection on ubuntu . Only in windows .

---

### Post by KenBW2 on 2008-06-15
Do you know anyone else who runs Ubuntu?

---

### Post by Tharakanuwanpro on 2008-06-15
Nope . He is far away from where i live

---

### Post by bumanie on 2008-06-15
Go [here]("http://nonetdebs.unixpod.com/"), download from xp and transfer to ubuntu. It's a site for people without internet connection to download onto usb sticks etc. from internet cafe's or libraries or whatever to get programs/updates etc.

---

### Post by Tharakanuwanpro on 2008-06-15
Thanks , I tried it but They won't send me the mail activation or whatever . My mail is a GMail

---

### Post by Eisenwinter on 2008-06-15
You could simply go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and search for your packages there - that is the official repository.

---

### Post by Tharakanuwanpro on 2008-06-15
Thanks . Okay . But how can i install them .

---

### Post by Eisenwinter on 2008-06-15
Download the packages manually from the website.
Put them on your usb stick, or whatever medium you wish to use to transfer them.

Move them over to Ubuntu.

In Ubuntu, open up the terminal, and use this command:
```
sudo dpkg -i <package name>
```

The package name needs to be preceeded by the full path to it, of course.
A package which sits on desktop, for example, would be in /home/username/Desktop/

---

### Post by Tharakanuwanpro on 2008-06-15
THanks

---

### Post by Tomatz on 2008-06-15
Open a terminal and type:

```
hal-device-manager
```

I think this is what your friend means ;)

---

