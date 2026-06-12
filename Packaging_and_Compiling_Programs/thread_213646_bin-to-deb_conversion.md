---
title: "bin-to-deb conversion"
date: 2006-07-11
forum: Packaging and Compiling Programs
---

### Post by aev on 2006-07-11
Hi,

I know this may be a dumb-newbie question but does anyone know if a conversion .bin into .deb packages is possible?:confused:

---

### Post by s6dalane on 2006-07-11
Use these two commands in terminal:
> chmod +x {downloaded_file_name}.bin

fakeroot make-jpkg {downloaded_file_name}.bin

The first line gives the .bin file execution privileage. The second line converts .bin into .deb, a Debian version of the installation package.

---

### Post by simplyw00x on 2006-07-11
Errr... that only works for java bin packages. The short answer is it's not generally possible.

---

### Post by s6dalane on 2006-07-12
Oh, I didn't know that, sorry. Thanks for pointing out my mistake.

---

