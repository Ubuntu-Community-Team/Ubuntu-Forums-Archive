---
title: "openoffice update failure"
date: 2006-07-27
forum: Repositories &amp; Backports
---

### Post by izle on 2006-07-27
Hi,

I got this error message in Synaptic Package Manager this morning while I was updating openoffice.org-calc writer ... _2.0.3-2dapper1_i386.deb  :

E: /var/cache/apt/archives/openoffice.org-calc_2.0.3-2dapper1_i386.deb: trying to overwrite `/usr/lib/openoffice/help/en/scalc.idx/DICTIONARY', which is also in package openoffice.org-help-en-us
E: /var/cache/apt/archives/openoffice.org-writer_2.0.3-2dapper1_i386.deb: trying to overwrite `/usr/lib/openoffice/help/en/swriter.idx/DICTIONARY', which is also in package openoffice.org-help-en-us
E: /var/cache/apt/archives/openoffice.org-draw_2.0.3-2dapper1_i386.deb: trying to overwrite `/usr/lib/openoffice/help/en/sdraw.idx/DICTIONARY', which is also in package openoffice.org-help-en-us
E: /var/cache/apt/archives/openoffice.org-impress_2.0.3-2dapper1_i386.deb: trying to overwrite `/usr/lib/openoffice/help/en/simpress.idx/DICTIONARY', which is also in package openoffice.org-help-en-us
E: /var/cache/apt/archives/openoffice.org-math_2.0.3-2dapper1_i386.deb: trying to overwrite `/usr/lib/openoffice/help/en/smath.idx/DICTIONARY', which is also in package openoffice.org-help-en-us
E: /var/cache/apt/archives/openoffice.org-base_2.0.3-2dapper1_i386.deb: trying to overwrite `/usr/lib/openoffice/help/en/sdatabase.idx/DICTIONARY', which is also in package openoffice.org-help-en-us

Any idea, shall I wait for the next update?

---

### Post by clast on 2006-07-27
Hi 
I got exactly the same error. I tried to remove openoffice.org-help-en-us but thats not possible because its required by openoffice.org. So we have to wait for the next update I guess. #-o

---

### Post by Oceola on 2006-07-27
I got a number of error messages when trying to re-install Open Office from the Security Repositories. I found you should also have the Main repository open along with the Security Repository and then things work properly. I don't know why this is other than there may be something which is needed by the update. Try this and see if it works.

---

### Post by calx on 2006-07-30
Yeah restoring the original sources.list and enabling all the repositories allowed me to run the update sucessfully.

Cheers izle ;) 

> **Oceola said:**
> I got a number of error messages when trying to re-install Open Office from the Security Repositories. I found you should also have the Main repository open along with the Security Repository and then things work properly. I don't know why this is other than there may be something which is needed by the update. Try this and see if it works.

---

### Post by adamkane on 2006-07-30
Some of the unofficial repositories don't do a good job keeping their dependencies consistent. Installer beware.

---

