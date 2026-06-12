---
title: "Permission denied even when using sudo"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by forseti42 on 2008-04-25
I'm trying to modify /etc/fstab to get my scanner working.
I'm using the following code, but it still says permission denied.
```

sudo echo 'none /proc/bus/usb usbfs auto,devmode=0666 0 0' >> /etc/fstab 
```

I'm using Hardy.

---

### Post by dstew on 2008-04-25
Does sudo work for other commands? Or is it only this command? Do you get to enter your password, or does it just fail at once?

---

### Post by PeterJS on 2008-04-25
> **forseti42 said:**
> I'm trying to modify /etc/fstab to get my scanner working.
I'm using the following code, but it still says permission denied.
```

sudo echo 'none /proc/bus/usb usbfs auto,devmode=0666 0 0' >> /etc/fstab 
```

I'm using Hardy.

The echo itself is running with elevated privileges, but the bash redirection (the >>) is running with your normal user permissions. Try:
```

echo 'none /proc/bus/usb usbfs auto,devmode=0666 0 0' | sudo tee /etc/fstab 
```
This way the tee will run with elevated privileges and thus have write access to the file.

---

### Post by dstew on 2008-04-25
Another way is to put quotes arount the whole line, to place it under sudo:```
sudo "echo 'none /proc/bus/usb usbfs auto,devmode=0666 0 0' >> /etc/fstab"
```At least that is supposed to work.

---

### Post by Oldsoldier2003 on 2008-04-25
or you could just edit /etc/fstab and add the line yourself

sudo nano /etc/fstab

---

### Post by Oldsoldier2003 on 2008-04-25
or you could just edit /etc/fstab and add the line yourself

sudo nano /etc/fstab

---

### Post by forseti42 on 2008-04-26
Thank you!  It works perfectly!  If only my printer would.

---

### Post by TylerRick on 2009-03-11
> **dstew said:**
> Another way is to put quotes arount the whole line, to place it under sudo:```
sudo "echo 'none /proc/bus/usb usbfs auto,devmode=0666 0 0' >> /etc/fstab"
```At least that is supposed to work.

I believe you mean this:
```
sudo sh -c "echo 'none /proc/bus/usb usbfs auto,devmode=0666 0 0' >> /etc/fstab"
```

---

