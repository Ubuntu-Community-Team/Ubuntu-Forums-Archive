---
title: "Ubuntu 11.04 Unable to download Untrusted files!"
date: 2011-09-19
forum: New to Ubuntu
---

### Post by Draggem on 2011-09-19
I was going to install some Apps like 'Moovida Media Center using Ubuntu Software Centre and I got this message

"Failed to download package files. Check your internet connection."
"Unable to Install Untrusted Files.....lgpod....."

my internet is connected i still get the eror on som apps..


:lolflag:

---

### Post by Dry Lips on 2011-10-02
> **Draggem said:**
> I was going to install some Apps like 'Moovida Media Center using Ubuntu Software Centre and I got this message

"Failed to download package files. Check your internet connection."
"Unable to Install Untrusted Files.....lgpod....."

my internet is connected i still get the eror on som apps..


:lolflag:

Try running these commands from the Terminal:```
sudo -i 
apt-get update 
apt-get upgrade 
apt-get clean 
apt-get autoclean 
exit             
```

---

### Post by dopple on 2011-12-08
Thanks Dry Lips. This fixed my issue however I had to run each command separately using sudo. \\:D/

---

