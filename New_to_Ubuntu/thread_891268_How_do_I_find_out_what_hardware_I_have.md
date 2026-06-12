---
title: "How do I find out what hardware I have?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by redfox1160 on 2008-08-15
How can I find out what kind of hardware the laptop I am using has. (I got it for free from someone)

---

### Post by iaculallad on 2008-08-15
> **redfox1160 said:**
> How can I find out what kind of hardware the laptop I am using has. (I got it for free from someone)

On your terminal:

```
sudo lshw
```

---

### Post by loell on 2008-08-15
you can have it by a command, post the output here if you want

```
dmesg
```

---

### Post by roquefilipe on 2008-08-15
there is also "lspci", "lspcmcia" and "lsusb"

---

### Post by loell on 2008-08-15
> **loell said:**
> you can have it by a command, post the output here if you want

```
dmesg
```


--edit : above beat me to it. ;)

---

### Post by iaculallad on 2008-08-15
> **loell said:**
> you can have it by a command, post the output here if you want

```
dmesg
```

dmesg? This would just be for diagnostic messages. For complete hardware listing, use **lswh** instead (hardware lister). It also covers "lspci", "lspcmcia" and "lsusb"

---

### Post by redfox1160 on 2008-08-15
```
 *-cdrom
                description: DVD reader
                product: CD-RW CRX880A
                vendor: Optiarc
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: KX07
                **capabilities: removable audio cd-r cd-rw dvd**
                configuration: ansiversion=5 status=open

```
Does that mean that I have a CD Burner?

---

### Post by iaculallad on 2008-08-15
> **redfox1160 said:**
> ```
 *-cdrom
                description: DVD reader
                product: CD-RW CRX880A
                vendor: Optiarc
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: KX07
                **capabilities: removable audio cd-r cd-rw dvd**
                configuration: ansiversion=5 status=open

```
Does that mean that I have a CD Burner?

You could test it yourself if you have a cd-r cd-rw dvd compatible drive.

---

### Post by Iowan on 2008-08-15
Does it look like [this]("http://www.sonynec-optiarc.com/products/slim_combo/index.html")?

---

### Post by redfox1160 on 2008-08-15
> **Iowan said:**
> Does it look like [this]("http://www.sonynec-optiarc.com/products/slim_combo/index.html")?

No

---

