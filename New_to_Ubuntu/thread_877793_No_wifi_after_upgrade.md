---
title: "No wifi after upgrade"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by Bukarts on 2008-08-02
No wifi after upgrade, can anyone help me. I am using Acer Aspire 5710.
---------------------------------------------------------------------------
Ok reinstalling Broadcom 43xx helped! WiFi is back! :))
____________________________________________________________________________
I am not sure that there is any diference but before other things I disabled broadcom 43xx restricted driver. 
then write down in terminal  

sudo apt-get remove bcm43xx-fwcutter

Then I tried to enable it again, it asked for download location
just download it from  [http://xeve.de/down/wl_apsta.o](http://xeve.de/down/wl_apsta.o)
And thats it. Just log in your WiFi.

---

### Post by ingeva on 2008-08-02
> **Bukarts said:**
> No wifi after upgrade, can anyone help me. I am using Acer Aspire 5710.
---------------------------------------------------------------------------
Ok reinstalling Broadcom 43xx helped! WiFi is back! :))

Telling how might help someone else?

After only a week with Ubuntu I already know that Broadcom needs some special attention... :)

---

