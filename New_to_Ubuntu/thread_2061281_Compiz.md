---
title: "Compiz"
date: 2012-09-22
forum: New to Ubuntu
---

### Post by Yezinki on 2012-09-22
When was trying to reboot it displayed Compiz not responding. How do I fix it?

How can one reach Compiz setting to disable effects of wobbly windows?

Thanks.

---

### Post by daslinkard on 2012-09-22
First you need to run the following commands:

```
gconftool-2 --recursive-unset /apps/compiz
```

Then you will need to restart your PC for the changes to take affect.

In order to access the changes for Compiz settings you will need to open up your Dash menu and type CCSM and this will call up your Compiz Config Settings Manager.  If you need more detail let me know.

---

### Post by Silent Warrior on 2012-09-22
[Edit] *Thwarted again!*

---

### Post by Yezinki on 2012-09-22
> **daslinkard said:**
> First you need to run the following commands:

```
gconftool-2 --recursive-unset /apps/compiz
```

Then you will need to restart your PC for the changes to take affect.

In order to access the changes for Compiz settings you will need to open up your Dash menu and type CCSM and this will call up your Compiz Config Settings Manager.  If you need more detail let me know.


```
vaio@VGC-LS1:~$ gconftool-2 --recursive-unset /apps/compiz
vaio@VGC-LS1:~$ 

```

Results.

Where is Dash menu located?

Thanks.

---

### Post by daslinkard on 2012-09-22
You can either tap the Windows sign on your keyboard to display the Dash home.

---

### Post by Yezinki on 2012-09-22
No results for CCSM............?

---

### Post by daslinkard on 2012-09-22
It sounds like it is not installed....you can install by doing the following sudo command:

```
sudo apt-get install compizconfig-settings-manager
```

Now you should be able to search for it.

---

### Post by Yezinki on 2012-09-22
Thanks got it........what tweaks do you normally do here if any?

---

### Post by daslinkard on 2012-09-22
Here you are able to customize ccsm to your preference whether you want wobbly windows, etc.  The best thing to do is to play around with compiz to get it how you want it.  If you mess it up you can run the following sudo command to reset compiz back to default.

```
gconftool-2 --recursive-unset /apps/compiz-1
``` ```
gconftool-2 --recursive-unset /apps/compizconfig-1
``` ```
unity --reset
```

---

### Post by Yezinki on 2012-09-22
Thanks.

---

### Post by daslinkard on 2012-09-22
No worries....any other questions we are here for you.

---

### Post by Yezinki on 2012-09-23
Thanks apprecaite it.

---

