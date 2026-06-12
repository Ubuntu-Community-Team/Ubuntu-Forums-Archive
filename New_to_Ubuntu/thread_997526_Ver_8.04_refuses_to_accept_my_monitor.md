---
title: "Ver 8.04 refuses to accept my monitor"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by thadacto on 2008-11-29
Why oh why?
The system absolutely refuses to accept my monitor which is a Samsung SyncMaster 794v- Every time I change it to that, it just goes back to what 8.04 wants - a Plug n Play monitor which only goes to a 800x600 resolution.
How can I get it to stay as I want it and not as the machine wants it - I thought they didn't have minds of their own!!

I am also using nVidia GeForce graphics card and from what I see here in the helps, nVidia seems to be the most problematic manufacturer for users of Ubuntu.

Any help greatly received. Thanks in advance

---

### Post by jimmy the saint on 2008-11-29
nvidia is the best manufacturer for linux.  You see so many support reqruests because so many people use it.  

If you are using the restricted driver, then type
```
nvidia-settings
``` 
in a terminal which will take you to the nvidia setup program.  Setting it up through there should work just fine.  Make sure you save your changes by telling it to write the changes to the xorg file.  restart.  you should be good to go.

---

