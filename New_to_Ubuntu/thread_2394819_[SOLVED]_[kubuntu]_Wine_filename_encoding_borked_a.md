---
title: "[SOLVED] [kubuntu] Wine filename encoding borked after upgrade to 16.04.4"
date: 2018-06-21
forum: New to Ubuntu
---

### Post by extant on 2018-06-21
I am running Kubuntu and have recently upgraded from 15.10 to 16.04.4. After upgrading, it seems that Wine no longer correctly reads filenames with special characters; it’s reading UTF-8 filenames as Windows-1252. So, for instance, a file named ```
09 Rákóczi-Marsch, for orchestra, S. 117 (LW G29).m4a
``` shows up in Wine Explorer as ```
09 RÃ¡kÃ³czi-Marsch, for orchestra, S. 117 (LW G29).m4a
```
Because of this, certain Wine applications are no longer able to read the files they need (as they’re searching for the UTF-8 encoded filename). How would one go about fixing this so that Wine reads filenames with the correct encoding? Thanks.

Edit: I’ve solved the issue. It was a locale problem; I had a custom locale installed before the upgrade, which the upgrade reset. In attempting to reinstall the custom locale, something went wrong somewhere in the process; having removed the locale and installed it again (correctly this time), filenames are now correctly encoded in Wine. A workaround which also worked before I fixed this was simply launching wine with a different locale, e.g. ```
LC_ALL=en_US.UTF-8 wine filename_of_wine_program
```

---

