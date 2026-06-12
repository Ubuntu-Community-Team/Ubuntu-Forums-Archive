---
title: "need help new to linux &amp; Kubuntu"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by jacsval on 2008-05-14
I'm a windows xp user, much more adept at software & hardware use than most PC users. I have no experience with a linux based system. I decided to try Kubuntu due to the reviews. Everything works fine on it but the wireless card. I cant seem to find any step by step idiot proof instructions. I'm trying it thru the Wubi intsaller. I can load windows xp or kubuntu at startup. All of the instructions assume some linux experience. I've installed the ndiswrapper but it doesnt seem to execute & the network manager cant enable the wireless network or even see my router. I even tried to manually config the wireless connection with no results. I have a dell inspiron 5150 with an intregated wirlesss mini-pci card. I like the appearance of Xubuntu but if I cant get the wireless to work soon. I'm afraid  I'll have to give up on linux. 

When i try to execute ndiswrapper I get this error: 
KDEInit could not launch 'gksu'.:
Could not find 'gksu' executable.

any help is greatly appreciated. keep in mind im a newbie on linux.

---

### Post by SunnyRabbiera on 2008-05-14
well first off be patient, you cant expect to learn a new OS in one day you know.
also use gksudo as opposed to gksu, as root access in ubuntu/kubuntu/ubuntu is used by sudo.

---

### Post by stevebakerj on 2008-05-14
On Kubuntu its  'kdesu'   rather than 'gksu'  which is for Gnome desktop

---

### Post by SunnyRabbiera on 2008-05-14
> **stevebakerj said:**
> On Kubuntu its  'kdesu'   rather than 'gksu'  which is for Gnome desktop

that too...
please be patient though, hey it took me days to get wireless working on my computer but I never gave up... and I got it working :D

---

### Post by Paqman on 2008-05-14
Do you know what type of wifi card you have? If not, post the output of:
```

lspci

```

---

