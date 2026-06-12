---
title: "How do I get xrdp to work form windows to linux"
date: 2013-08-27
forum: New to Ubuntu
---

### Post by lance bermudez on 2013-08-27
How do I get xrdp to work form windows to linux? I have it working from lubuntu to windows7. I just installed aptitude install xrdp but it will not go from windows 7 to lubuntu.

---

### Post by lah7 on 2013-08-27
If XRDP didn't install properly, try using** apt-get**. Open the terminal and type:
```
sudo apt-get install xrdp
```

As of Lubuntu 13.04; it appears that xrdp's configuration doesn't point to the desktop environment properly, so it may be all chequered grey when logging in remotely. We need to tell it to load up the desktop environment.

1. Open up the terminal and type:
```
sudo nano /etc/xrdp/startwm.sh
```
Then put a **#** in front of > . /etc/X11/Xsession
and type this underneath: > ~/.xsession
Press **CTRL+X **to exit then **Y** to save changes.

2. Now we will create a config file which will point to the Lubuntu Desktop:
```
echo "lxsession -s Lubuntu -e LXDE" > ~/.xsession
```

3. Make this file executable:
```
chmod +x ~/.xsession
```

4. Restart XRDP to reflect changes.
```
sudo service xrdp restart
```

After following this, you'll be able to remotely login and control another user session without kicking the local user off (unlike Windows' polices)

I hope this works for you :)

---

