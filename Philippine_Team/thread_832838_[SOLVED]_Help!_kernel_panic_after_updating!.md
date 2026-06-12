---
title: "[SOLVED] Help! kernel panic after updating!"
date: 2008-06-18
forum: Philippine Team
---

### Post by kur0sawa on 2008-06-18
Help po im using kubuntu 7.10 and after downloading updates and restarted eto na lumabas na error:( 


error:

[15.264027] kernel panic - not  syncing: VFS: unable to mount fs on unknown-block(0,0)



maraming salamat po!


found a solution from googling:D and works like charm

sudo update-initramfs -k all -u -b /mnt/sda1/boot

---

### Post by Samhain13 on 2008-06-18
Tutal ikaw din ang nakahanap ng solusyon sa sarili mong problema, ako na lang ang magpapasalamat sa iyo. Ang labo naman kasi kung papasalamatan mo ang sarili mo, o tatanggap ka ng pasasalamat galing sa sarili mo, diba? :D

---

### Post by king leoric on 2008-06-18
Thanks din for sharing the solution. Sabi nga ni samhain eh di maganda kung you pasalamat sa sarili you kaya ako na lang din mag thank you:)

---

### Post by loell on 2008-06-18
wala di naman tayong "thank myself" feature :)

---

