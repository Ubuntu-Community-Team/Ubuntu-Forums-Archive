---
title: "How can I auto-mount a filesystem after/during boot process?"
date: 2014-05-17
forum: New to Ubuntu
---

### Post by Luis_Estevez on 2014-05-17
If I run this command:

```
mount -t ntfs /dev/sda3 /media/PuntoMontajeMP3
```

I can mount the filesystem that I need to use. 
My questions are: 

How can I mount this filesystem automatically during/after boot process?
Where must I place this command? Inside one specific file? Is it possible?

I've tried to place that command inside /etc/rc.local but nothing happens.
I'm using Lubuntu 10.04, and I need to mount a filesystem automatically during/after boot process. 
Thanks for your help.

---

### Post by coldcritter64 on 2014-05-17
Add your partition details to /etc/fstab to mount the partition from startup. Some information about /etc/fstab for you, [[COLOR=#0000ff]--link--[/COLOR]]("https://help.ubuntu.com/community/Fstab"). & [[COLOR=#0000ff] Mounting windows partitions (link)[/COLOR]]("https://help.ubuntu.com/community/MountingWindowsPartitions")

---

### Post by Ralph Hinkley on 2014-05-17
I haven't used 10.04 in a while, but have you tried this? :
1.) Copy "[COLOR=#000000][FONT=Ubuntu Mono]mount -t ntfs /dev/sda3 /media/PuntoMontajeMP3" into a text file, saving it with ".sh" as a file extension.
2.) Right click on the icon and select "properties". From there, check the "Allow file to execute as a program" under the "permissions" tab.
3.) Add the file to "Startup applications".

I'm sure it'll probably be more involved that that, but I'm not on 10.04, so I'm unable to get super specific. Hope that helps, though.[/FONT][/COLOR]

---

