---
title: "steam will not open."
date: 2015-09-04
forum: New to Ubuntu
---

### Post by Ben_Crow on 2015-09-04
i had steam up and running but my graphics card wasnt being recognized by my pc, 

so none of my games ran on anything more than min settings. 

i just got ubuntu to recognize my graphics card, but now steam wont open.

this is the message i get when i try to open it in terminal. 

Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1440016726)
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast

please help asap, my friends are waiting for me to get on. haha

---

### Post by ethan27 on 2015-09-04
A solution which may work is:

```
sudo apt-get purge steam
sudo apt-get install steam
```

Run the Purge first and when it's done Install. Might work just give it a try!

Best Regards,
Ethan

---

