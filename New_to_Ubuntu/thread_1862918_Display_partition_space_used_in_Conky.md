---
title: "Display partition space used in Conky"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-10-17
Hi Everyone,

I just did a clean install of 11.10 and got conky running.

I had conky set to tell me how much space I am using in Ubuntu and how much on an external drive.

```

${color black}Ubuntu: ${color black}${fs_used /home}/ ${fs_size /home}(${fs_free /home} ${fs_free_perc /home}% ${color black}free)
${color1}ExtHD: ${color1}${fs_used /media/Elements}${color1}/${color1}${fs_size /media/Elements} ${color1}(${color1}${fs_free /media/Elements}, ${fs_free_perc /media/Elements}% ${color1}free)

```

The thing is that the space used on Ubuntu keeps increasing even though I am not doing anything!

Does anyone know if this is a glitch due to 11.10? or how I can check to see how much space I am actually using?

Thank you

---

### Post by Sector11 on 2011-10-17
> **GrouchyGaijin said:**
> Hi Everyone,

I just did a clean install of 11.10 and got conky running.

I had conky set to tell me how much space I am using in Ubuntu and how much on an external drive.

```

${color black}Ubuntu: ${color black}${fs_used /home}/ ${fs_size /home}(${fs_free /home} ${fs_free_perc /home}% ${color black}free)
${color1}ExtHD: ${color1}${fs_used /media/Elements}${color1}/${color1}${fs_size /media/Elements} ${color1}(${color1}${fs_free /media/Elements}, ${fs_free_perc /media/Elements}% ${color1}free)

```

The thing is that the space used on Ubuntu keeps increasing even though I am not doing anything!

Does anyone know if this is a glitch due to 11.10? or how I can check to see how much space I am actually using?

Thank you

What does ```
df -H
``` tell you?
```
  11:45:33 ~
         $ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1               20G   3.1G    16G  17% /
tmpfs                  1.1G      0   1.1G   0% /lib/init/rw
udev                   1.1G   226k   1.1G   1% /dev
tmpfs                  1.1G   4.1k   1.1G   1% /dev/shm
/dev/sda2               40G   9.7G    28G  26% /home
/dev/sda5               99G    19G    75G  21% /media/5
/dev/sda6               87G   193M    82G   1% /media/6
/dev/sdb1              251G    91G   160G  37% /media/disk

  11:45:38 ~
         $ 
```

---

### Post by GrouchyGaijin on 2011-10-17
Conky shows the usage as 4.20 Gigabytes
[IMG]http://dl.dropbox.com/u/23115609/Ubuntu-HD.png[/IMG]

The terminal shows:
[IMG]http://dl.dropbox.com/u/23115609/termHD.png[/IMG]

That doesn't look the same to me.  Am I wrong?

I guess my question is why does the 4.20 GB number fluctuate so much.  Today I saw it go from 4.17 to 4.25 then back to 4.20.  I installed some packages but the fluctuation occurred a while after everything was installed.

---

