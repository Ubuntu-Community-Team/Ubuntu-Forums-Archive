---
title: "How to completely 'sudo uninstall' Firefox please"
date: 2022-12-21
forum: New to Ubuntu
---

### Post by jonfisher on 2022-12-21
My Firefox browser keeps bugging out.  I completely removed it with Synaptics, but that didn't help upon reinstall.
With the command line, what do I type into terminal to really completely uninstall it - uninstall everything associated with it so I can reinstall it - please.

I unserstand it is probably 
sudo apt-get --purge remove package_name

but when typing "Firefox" for package_name, it doesn't work....   Must be another name?

```

michael@michael-HP-EliteDesk-800-G1-SFF:~$ sudo apt-get --purge remove Firefox
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package Firefox
michael@michael-HP-EliteDesk-800-G1-SFF:~$ 

```

---

### Post by pantazi on 2022-12-21
I used this:

[https://askubuntu.com/questions/16758/removing-firefox-in-ubuntu-with-all-add-ons-like-it-never-existed](https://askubuntu.com/questions/16758/removing-firefox-in-ubuntu-with-all-add-ons-like-it-never-existed)

then installed Brave browser.

---

### Post by ActionParsnip on 2022-12-21
Lower case F. Linux is very case sensitive

---

### Post by ActionParsnip on 2022-12-21
```

sudo apt --purge remove firefox

```
If you want to remove your settings and you don't use Thunderbird for email (If you do then DON'T run this command), you can run:
```

rm -rf ~/.mozilla

```
Now, if you reinstall the browser, you will get a vanilla profile rather than the one from the files from your profile. Depends what you are trying to do.....

---

### Post by ian-weisser on 2022-12-21
How you remove Firefox currently depends upon your release of Ubuntu. In 22.04 and newer, Firefox is a Snap...so apt doesn't know anything about it.

---

### Post by mIk3_08 on 2022-12-21
IF that is from snap please run the command below. 
```
sudo snap remove firefox
```

---

### Post by pantazi on 2022-12-22
Isn't 'Thanks' part of forum etiquette these days?

---

