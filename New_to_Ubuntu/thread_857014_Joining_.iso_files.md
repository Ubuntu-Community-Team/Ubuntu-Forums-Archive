---
title: "Joining .iso files"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by sharks on 2008-07-12
i have four .iso files. i have gutsy gibbon. how do i join those four .iso files into one?

---

### Post by Josdell on 2008-07-12
Along down that link, there's a section for combining ISOs. Please always search the forums as this is how I found this ;)

[Linky]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Build_a_Super_Grub_DiskGParted")

---

### Post by fahadsadah on 2008-07-12
You should mount all of these using:
```
mount myiso1.iso /mnt/iso1/ -t iso9660 -o ro,loop=/dev/loop0
```
Change myiso1.iso to your first iso. Repeat three times, changing the number after /mnt/iso.

Then, ```
mkdir ~/isos/
cp /mnt/iso1/* ~/isos/
cp /mnt/iso2/* ~/isos/
cp /mnt/iso3/* ~/isos/
cp /mnt/iso4/* ~/isos/
```

Then roll this into one ISO with ```
mkisofs myiso ~/isos
```

---

### Post by maybeway36 on 2008-07-12
What ISOs are they? If they are live CDs, the script in my sig might help.

---

