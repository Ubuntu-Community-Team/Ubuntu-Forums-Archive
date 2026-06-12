---
title: "New PCI Usb Hub not working"
date: 2012-07-14
forum: New to Ubuntu
---

### Post by jllipke on 2012-07-14
I just bought a Usb Hub PCI Card. I put the card in, and it simply won't run. 

Are there any other solutions than taking it out and putting it back in?

thanks, :KS

---

### Post by Sealbhach on 2012-07-14
What make and model is it? Does it show up when you run lspci?

'

---

### Post by NikTh on 2012-07-14
Hi , 
Of course we will need additional info .. 
As @Sealbhach said .. open a terminal (ctrl + alt + t) and copy-paste these commands one at time ...
```
cat /etc/lsb-release && uname -r 
lspci -nn
``` 
post the results back here. 
**Put the results inside [CODE] tags by highlighting the text and click on # symbol at the top of message pane. **

Also be careful with plug . Is plugged  correct in pci port ? 
Thanks

---

### Post by jllipke on 2012-07-14
I made sure it was plugged in correctly. I'm not sure of what I'm looking for exactly when I type that code like, what are the  keywords I need to look for?

Thanks again,

---

