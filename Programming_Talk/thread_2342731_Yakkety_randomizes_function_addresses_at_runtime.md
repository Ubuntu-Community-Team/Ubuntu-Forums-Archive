---
title: "Yakkety randomizes function addresses at runtime"
date: 2016-11-09
forum: Programming Talk
---

### Post by mogeb2 on 2016-11-09
Hi,

I was using -finstrument-functions to profile function entry and exit. On function entry and exit, I print the address of the function entered or exited (parameter func) and then use nm to resolve address to symbol name translation. After upgrading to Yakkety, I just realized that the addresses of the func parameter are always very high; all functions used to be close to the begining of the address space of the process, as expected for the text section. I looked at /proc/PID/maps, the text section now actually starts at a higher address, which is weird because they're in a completely different range than whatever nm shows, so a direct translation doesn't work anymore. Not only are the addresses much higher, but they're also randomized. And this, I have difficulty understanding: I understand randomizing the address of writable sections for security reasons, but the text section is not writable. In any case, my question is regarding the address space of the text section: any idea what happened to yet on Yakkety, and how can I disable this behavior?

Thanks.

---

