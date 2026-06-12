---
title: "LVM partition space disappeared"
date: 2015-07-20
forum: New to Ubuntu
---

### Post by ryantrappy on 2015-07-20
[FONT=Segoe UI]I am running a ubuntu server 14.02 on a homemade system. I followed a guide that suggested using an lvm as the partition to install the operating system on and now I am trying to mount the other half of the system to a folder.

```
[/FONT][COLOR=#333333][FONT=Segoe UI]root@trappserver:~# sudo pvs PV VG Fmt Attr PSize PFree[/FONT][/COLOR]
[COLOR=#333333][FONT=Segoe UI]/dev/sda5 trappserver-vg lvm2 a-- 931.27g 912.64g[/FONT][/COLOR][FONT=Segoe UI]
```

[/FONT][FONT=Segoe UI]But my lvdisplay only shows two lvms of 10.89gb and 7.73 gb. Is this because it is not seeing the other part of the volume as another partition or am I simply looking in the wrong place? Thank you in advance[/FONT]

---

### Post by TheFu on 2015-07-23
Please post output from:
pvs
vgs
lvs

---

