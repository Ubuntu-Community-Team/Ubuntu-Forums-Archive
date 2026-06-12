---
title: "is it there, a dvd burner"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by Griffin Bain on 2008-10-30
I just plugged in a dvd player burner and the computer doesn't even know its there. I have been reading a lot about what codecs to install and such but that is not helping because I don't even know how to get the computer to know it has dvd hardware. 

thanks for any help,

i have 8.04 desktop edition on a dell dimesion 4600

---

### Post by blackened on 2008-10-30
By "plugged in" do you mean you installed an internal DVD-RW or that you "pluggin in" an external DVD-RW via USB?

---

### Post by eternalnewbee on 2008-10-30
You could also reboot, and see if it is recognized.

---

### Post by Griffin Bain on 2008-10-30
it is an internal dvd player burner and I have restarted the computer a few times already and nothing happened

---

### Post by cariboo on 2008-10-30
Does the computer detect the drive on boot up? You may have to go into the BIOS and set it up before you can use it in any OS.

Jim

---

### Post by Griffin Bain on 2008-10-30
i'll poke around the bios right now and let you know how it goes

---

### Post by prshah on 2008-10-30
> **Griffin Bain said:**
> I just plugged in a dvd player burner and the computer doesn't even know its there.

Can you open a terminal (Applications-Accessories-Terminal) and then give the following command, and post back the output?```
sudo lshw -C disk | grep -i dvd
```

---

### Post by Ptero-4 on 2008-10-30
You might also want to consider upgrading to 8.10. It was released today.

---

### Post by Griffin Bain on 2008-10-30
yes, it breiefly states this:

CI (sysfs).

i would also consider 8.10 but not unless my nvidia card is going to work without having to do a lot of homework

---

