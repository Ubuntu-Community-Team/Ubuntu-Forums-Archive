---
title: "how to tweak hostname in custom live cd"
date: 2005-11-15
forum: Programming Talk
---

### Post by faz on 2005-11-15
hi,
I'd like to create a live cd changing the default hostname but all the tests I've done had no results, do you have a tip?

thank you very much!
fabrizio

---

### Post by Burke on 2005-11-15
I believe you can just edit the file /etc/hostname

I haven't tried it myself, but I think it should work.

You also might want to change your hostname in /etc/hosts so that your computer knows your new hostname is really 127.0.0.1

---

### Post by faz on 2005-11-16
[QUOTE=Burke]I believe you can just edit the file /etc/hostname

I haven't tried it myself, but I think it should work.

You also might want to change your hostname in /etc/hosts so that your computer knows your new hostname is really 127.0.0.1[/QUOTE]

it does not work because netcfg overwrite it
i'm doing some other tests right now

thanks anyway
bye
fabrizio

---

### Post by faz on 2005-11-16
Tollef Fog Heen told me that:
> I guess you might want to change the

Template: netcfg/get_hostname
Type: string
Default: ubuntu

in netcfg-1.16ubuntu1/debian/netcfg-common.templates.  Note that you
need to rebuild the initrd with the new netcfg available to the build
process to get the new default.

I still have to find how to rebuild initrd but I think that would be not a problem.
thank you tollef

---

### Post by bazzer on 2006-09-28
Did anyone end up with a solution to this?
I've noticed that 
**d-i netcfg/get_hostname string my-hostname**
doesn't work in a preseed file...

---

