---
title: "Irritating Konsole beep"
date: 2007-03-21
forum: Programming Talk
---

### Post by Tahir on 2007-03-21
I just figured out how to get rid of the irritating Konsole beep for good.  

Go to Settings -> Bell and change it to whatever you want.  I changed it to System Bell.  Then save the settings by clicking "Save as default" in the same menu.  

Bloody hell, took me time to figure out that you have to explicitly save settings you change, very big difference from windows world.

---

### Post by akudewan on 2007-03-22
Cool, so now you can actually run this program: 

```

#include<stdio.h>

int main()
{

while(1)
        printf("\a");

return 0;

}

```

---

### Post by Ragazzo on 2007-03-22
If you mean the PC Speaker beeping, the first thing I do on a Linux installation is to edit /etc/modprobe.d/blacklist and appending **blacklist pcspkr**
A temporary solution is to write **modprobe -r pcspkr** in the terminal. These methods remove the sound from everywhere.

---

### Post by Tahir on 2007-03-22
> **akudewan said:**
> Cool, so now you can actually run this program: 



very funny.

---

