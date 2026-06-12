---
title: "dpkg error code (1)"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by imerljak on 2012-04-18
Edit: Forgot this was an english forum ;), ok..
I'm having this issue while trying to do an apt-get upgrade... i've disabled multiarch (cp multiarch multiarch.old, and cleansed the first file so we dont have i386) i cant say that this is the cause of the problem, but i'm quite sure it isn't cause i've enabled it back and the problem persists. I've already tried to fix with apt-get -f install, but it gives me lots of errors and nothing fixed. If any extra info is needed please post, and i'll provide.

> ~$ sudo apt-get upgrade
Lendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
Você pode querer executar 'apt-get -f install' para corrigí-los.
Os pacotes a seguir têm dependências desencontradas:
 glib-networking : Depende: glib-networking-services (>= 2.32.1-1) mas não está instalado
                   Depende: glib-networking-services (< 2.32.1-1.1~) mas não está instalado
 gvfs : Depende: gvfs-daemons (>= 1.12.1-0ubuntu1) mas não está instalado
        Depende: gvfs-daemons (< 1.12.1-0ubuntu1.1~) mas não está instalado
 gvfs-backends : Depende: gvfs-daemons (= 1.12.1-0ubuntu1) mas não está instalado
 libsane : Depende: libsane-common (= 1.0.22-7ubuntu1) mas não está instalado
E: Dependências desencontradas. Tente usar -f.

---

### Post by Daveth on 2012-04-18
it seems to be looking for newer versions of file dependencies than it is finding on your system, though I wish I had paid more attention in my Portuguese classes...

---

### Post by raja.genupula on 2012-04-18
have you look for them in the synaptic ?

---

### Post by imerljak on 2012-04-18
i'll try to get this infos in english, i guess it will be easier to understand =)

---

### Post by imerljak on 2012-04-18
> **raja.genupula said:**
> have you look for them in the synaptic ?

Oh, thanks.. i just marked them to fully remove, and now everything is fine, i guess it was a conflict because the 64bits packages where already installed, and it was trying to install 32bit over the old ones with same version number. hmm =) thanks alot.

SOLVED (by now)

---

