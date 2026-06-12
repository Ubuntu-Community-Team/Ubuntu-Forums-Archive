---
title: "[SOLVED] how do I completly remove a program and ALL settings"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by tropdoug on 2008-06-08
I need to completely remove all files relating to my HP printer, as I seem to have a setting problem somewhere so that it is only printing a half a page. 

I tried completly removing Hplip and Hpijs using synaptic and ticking the "completely remove" option, however when I checked to see if there were any Hp files left I found a huge amount of directories relating to other models of hp printer and all sorts of other stuff . 
I left that alone, and reinstalled hp lip and hpjis and started hp toolbox found the printer, all went well, did a test print and only one half again printed. The same set-up on the laptop works fine with the same documents. Therefore it must be something to do with a corrupt setup.

My thought is to purge all references to Hp printers, re boot, and then re install through synaptic. 

Any ideas welcomed thanks.

---

### Post by bumanie on 2008-06-08
Not 100% sure, but I think if you purge/completely remove hplip you will have to download linux drivers from the HP site as purging/completely removing will get rid of hplip out of synaptic. You could always download the driver from HP anyway and install it. It has self extracting installer for debian/ubuntu that works very well - just double check that your printer is supported first.

---

### Post by tropdoug on 2008-06-08
ok, but how do I do a purge?

---

### Post by dje on 2008-06-08
Do this in a terminal:
```
sudo apt-get autoremove --purge *program_name*
```

hope that helps,
dje

---

### Post by bumanie on 2008-06-08
If you wish to get rid of the configuration files as well it is better to use 
> sudo aptitude purge <package name>

---

### Post by tropdoug on 2008-06-09
Ok thanks guys, I have done that, don't have time to reinstall hplip yet, but I will complete this next week and post the result

Now completed, and all went well. By installing the hplip direct from the site, it seemed to make it much better, including installing some dependencies that were not installed the first time. So it is up and running again, thanks for the help guys.

---

