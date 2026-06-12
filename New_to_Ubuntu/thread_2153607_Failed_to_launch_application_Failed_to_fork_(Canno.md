---
title: "Failed to launch application: Failed to fork (Cannot allocate memory)"
date: 2013-06-11
forum: New to Ubuntu
---

### Post by klintistwood on 2013-06-11
Hi all,

I'm accesssing my Ubuntu server through XRDP and I can't launch any application. 
With cat .xsession-errors I get a lot of error messages but the last one seems to correspond to the failed launch of an application:
unity-2d-shell: [WARNING] bool Application::launch(): Failed to launch application: Failed to fork (Cannot allocate memory)
unity-2d-shell: [WARNING] bool Application::launch(): Failed to launch application: Failed to fork (Cannot allocate memory)

If I look at how much free memory I have:
            total       used       free     shared    buffers     cached
Mem:       1572864     429412    1143452          0          0     162768
-/+ buffers/cache:     266644    1306220
Swap:            0          0          0

I don't know if this is related but if I try to update Ubuntu, I also get an error message: Reading package lists... Error!

So basically, I can't do anything with this server I ordered a few days ago :(
...and I'm a Linux total newbie...

Do you have any suggestions?

Thanks
Laurent

---

