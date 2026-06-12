---
title: "problem with downloading softs"
date: 2011-09-21
forum: New to Ubuntu
---

### Post by amitpokhrel on 2011-09-21
Hi everyone!!
I was trying to install few software after I installed ubuntu 11.04. When I try to install (some softwares) it tells me 
"The action would require the installation of packages from not authenticated sources."

I don't understand what the problem is? My net connection is running under a proxy server, can that cause this problem. Is there any way i can install these softwares!!!

---

### Post by mcduck on 2011-09-21
That error message is pretty much always a result of adding a software repository but not adding the signing key for that repository. The signing keys are used to verify that the packages come from the person owning the key and that nobody has modified the packages at any stage.

If you did add a repository, please give us a link to it and we should be able to give you instructions how to add the missing signing key.

---

### Post by amitpokhrel on 2011-09-21
Thanks for the reply ... but the problem also exist when i try to download softs directly from software centre....
and the problem also persists while updating..for eg I downloaded and installed shotwell photo manager, the software is working fine but while i try to update it it gives the same error..

---

### Post by mcduck on 2011-09-21
> **amitpokhrel said:**
> Thanks for the reply ... but the problem also exist when i try to download softs directly from software centre....
and the problem also persists while updating..for eg I downloaded and installed shotwell photo manager, the software is working fine but while i try to update it it gives the same error..

Yes, it will appear with any package management tool, as any extra repositories you add would use exactly the same package management (that's pretty much the very point of using repositories instead of downloading different programs and packages manually from web sites).

And the error will appear every time you use a package manager if it detects that there is even one configured repository without proper signing keys, it doesn't matter if the packages you are trying to install/update come from that specific repository or from some other one.

---

### Post by amitpokhrel on 2011-09-22
I didn't get any solution yet?

---

### Post by mcduck on 2011-09-22
> **amitpokhrel said:**
> I didn't get any solution yet?

You didn't answer my question yet. ;)

Have you added any software repositories, and if yes, can you give a link to it so I can give you instructions how to add the missing PGP key?

---

### Post by amitpokhrel on 2011-09-23
sorry i thought u would figure it out when i said shotwell....
the repo i added was
sudo add-apt-repository ppa:yorba/ppa

for shotwell

---

