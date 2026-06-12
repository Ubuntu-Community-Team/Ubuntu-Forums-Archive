---
title: "I need guidance about a specific bug and how to report it"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by chechojp on 2008-04-26
I am absolutely new to ubuntu. 1 month ago I started using dapper and yesterday i upgraded to hardy. Now, whenever i initialize the system i get a message telling me to report a bug. Since I am new I did not have any idea oin how to do that!!!

After a while searchin the web i found launchpad and reported a message vbery similar to this: I am using a NEC laptop LaVieM LM500/5 and just upgrade from the previous LTS version to the latest. The message i get when initializing tells me to report the following.

$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "jp", "jp106", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "jp", "jp106", ""
$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = []
 model = jp106
 options = [japan	japan:kana_lock]
 overrideSettings = true
$ sudo dmidecode -s system-product-name
PC-LM5005D                   

I am not sure if this is the correct way of reporting a bug and if the problem can be solved with the info i gave. If you have any ideas about the bug or the report i will be very grateful

---

### Post by frup on 2008-04-26
I'm going to go out on a limb here and say just report it on launchpad. The developers will respond and ask you for more information and can tell you what you need to do to help get the bug fixed.

---

### Post by kamitsukai on 2008-04-26
> **chechojp said:**
> I am absolutely new to ubuntu. 1 month ago I started using dapper and yesterday i upgraded to hardy

Do you mean to say you upgraded from the last lts to the latest? through the repositories?:confused: because thats not really a good idea you should always upgrade to the next one up before continuing, although a clean install is advised...

---

### Post by frup on 2008-04-26
> **kamitsukai said:**
> Do you mean to say you upgraded from the last lts to the latest? through the repositories?:confused: because thats not really a good idea you should always upgrade to the next one up before continuing, although a clean install is advised...

No with LTS, LTS to LTS upgrade is a supported method. Upgrades are just as good as clean install in many cases and in some situations (especially in terms of LTS) far more important.

---

