---
title: "Ram frequency"
date: 2011-12-15
forum: New to Ubuntu
---

### Post by kingrat89 on 2011-12-15
Guys, 

how can I detect my RAM Frequency in the Ubuntu lucid 10.04? Some terminal command?

Thanks a lot

---

### Post by bluexrider on 2011-12-15
> **kingrat89 said:**
> Guys, 

how can I detect my RAM Frequency in the Ubuntu lucid 10.04? Some terminal command?

Thanks a lot

```
sudo /usr/sbin/dmidecode | grep -i "current speed" 
```

---

### Post by Frogs Hair on 2011-12-15
```
sudo lshw -short -C memory
```

---

### Post by bluexrider on 2011-12-15
> **Frogs Hair said:**
> ```
sudo lshw -short -C memory
```

yeah, better

---

