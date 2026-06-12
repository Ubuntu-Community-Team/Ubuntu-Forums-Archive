---
title: "general compilation problems on raring"
date: 2013-07-12
forum: Packaging and Compiling Programs
---

### Post by proutprout on 2013-07-12
Hi,

I reinstalled my computer with raring a few months ago.
I had no problems compiling some programs before and then I get often linker problems like
```
 /usr/bin/ld: seq-out.o: référence au symbole non défini «pthread_cancel@@GLIBC_2.2.5»/usr/bin/ld: note: «pthread_cancel@@GLIBC_2.2.5» est défini dans le DSO /lib/x86_64-linux-gnu/libpthread.so.0 donc essayez de l'ajouter à la ligne de commande du lieur
/lib/x86_64-linux-gnu/libpthread.so.0: could not read symbols: Opération invalide
collect2: erreur: ld a retourné 1 code d'état d'exécution
 
```

or 
```
/usr/bin/ld: CMakeFiles/termit.dir/termit_core_api.c.o: référence au symbole non défini «ceil@@GLIBC_2.2.5»/usr/bin/ld: note: «ceil@@GLIBC_2.2.5» est défini dans le DSO /lib/x86_64-linux-gnu/libm.so.6 donc essayez de l'ajouter à la ligne de commande du lieur
/lib/x86_64-linux-gnu/libm.so.6: could not read symbols: Opération invalide

```

i googled a lot without finding any solutions

thanks for help

---

