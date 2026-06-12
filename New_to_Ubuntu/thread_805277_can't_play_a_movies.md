---
title: "can't play a movies ?"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by Tubby on 2008-05-23
Hi, when i put a dvd in and go and open up the Movie player, then press play, i get a mesage saying  " an error has occured ", anyone know what is happening ?
thanks

---

### Post by bm13084 on 2008-05-23
have you added the restricted extras that allow for dvd playback?

---

### Post by Tubby on 2008-05-23
No i haven't, were do i find those restricted ones. 
thanks for the help

---

### Post by Hobo Joe on 2008-05-23
I think the codecs come with VLC. It's a better player, anyway.


```

sudo aptitude install vlc

```

---

### Post by superprash2003 on 2008-05-23
normally when you open totem movie player if it is unable to play it would normally ask you to download codecs automatically, all you need to do is click on OK .. dont you see anything like that?

---

### Post by Maestro23 on 2008-05-23
Restricted Formats: [https://help.ubuntu.com/community/RestrictedFormats?highlight=(formats)|(Restricted](https://help.ubuntu.com/community/RestrictedFormats?highlight=(formats)|(Restricted))

> sudo apt-get install ubuntu-restricted-extras

---

### Post by Tubby on 2008-05-23
No it doesn't ask about downloading codecs, just the error message only.

---

### Post by bm13084 on 2008-05-26
just go to add/remove programs and search for "restricted extras"

---

### Post by Sinkingships7 on 2008-05-26
You need to use this command to install DVD support:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by ndo on 2008-05-27
> **Sinkingships7 said:**
> You need to use this command to install DVD support:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Tried this - says:

This is higly experimental, look out for what happens below.
If you want to stop, interrupt now (control-c), else press
return to proceed

Install debhelper and fakeroot, then run this script again


Any help on how to do this???

---

### Post by Sinkingships7 on 2008-05-27
> **ndo said:**
> Tried this - says:

This is higly experimental, look out for what happens below.
If you want to stop, interrupt now (control-c), else press
return to proceed

Install debhelper and fakeroot, then run this script again


Any help on how to do this???

I think it needs you to install debhelper and fakeroot. Why? I have no clue. Go ahead and run this command:
```
sudo apt-get install debhelper fakeroot
```
and then run my first code again.

---

