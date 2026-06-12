---
title: "some error"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by fmpfmpf on 2008-05-09
i am using Ubuntu 8.04 and i am trying to install some drivers
[http://www.elotouch.com/Support/Downloads/dnld.asp#mac](http://www.elotouch.com/Support/Downloads/dnld.asp#mac)
i am installnig the Serial interface driver.

At chapter 4, after typing the command "./elova -nvram", i get the follownig error:-
./elova: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory

can someone pls help sme solve this?

Thank you very very much

---

### Post by hermes0710 on 2008-05-09
It seems that you are missing a package. Run synaptic and search with the filter "Provides" and insert "libXm.so". Find what the package is and install it (It might be something like "openmotif" what you are looking for)

---

### Post by fmpfmpf on 2008-05-09
0 search results

any other methods?

TQTQTQ

---

### Post by hermes0710 on 2008-05-09
The package is "openmotif" and you have to enable the multiverse repositories in order to be able to obtain it (System>Administration>Software Sources)

---

### Post by fmpfmpf on 2008-05-09
the "Software restricted by copyright or legal issues (multiverse)" is checked.
Is that correct?
if yes, it still gives 0 result

---

### Post by hermes0710 on 2008-05-09
Try installing "libmotif3". Is this found?

---

### Post by fmpfmpf on 2008-05-09
not found too :(

---

### Post by hermes0710 on 2008-05-09
Go here and download manually (there are links at the bottom of the page):

[http://packages.ubuntu.com/hardy/libmotif3]("http://packages.ubuntu.com/hardy/libmotif3")

---

### Post by fmpfmpf on 2008-05-09
> **hermes0710 said:**
> Go here and download manually (there are links at the bottom of the page):

[http://packages.ubuntu.com/hardy/libmotif3]("http://packages.ubuntu.com/hardy/libmotif3")

which architecture shoudl i choose?
TQ

---

### Post by hermes0710 on 2008-05-09
Which version of ubuntu did you install? If the 32-bit then choose the i386, otherwise the amd64.

---

### Post by fmpfmpf on 2008-05-09
> **hermes0710 said:**
> Which version of ubuntu did you install? If the 32-bit then choose the i386, otherwise the amd64.

mine is Ubuntu 8.04
what is 32-bit and amd64?
sorry, this is my 1st linux experience

---

### Post by hermes0710 on 2008-05-09
Don't apologize, no problem. When you downloaded the iso image for installing ubuntu which one did you choose to download? 

Go to this page: [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

It asks: What type of computer do you have?

What had you chosen?

If your choice was the first option then you use the 32bit version.

---

### Post by fmpfmpf on 2008-05-09
i chose the standard personal computer
so, i should go for the 32-Bit, right?

---

### Post by hermes0710 on 2008-05-09
Yeap

---

### Post by fmpfmpf on 2008-05-09
i have downloaded the file and extracted them.
i now have 3 files
1. control.tar.gz
2. data.tar.gz
3. debian-binary

what do i need to do now?

TQ

---

### Post by hermes0710 on 2008-05-09
It was a .deb file which means that it can be immediately installed (Right click on it and select open with Deb Installer or something like this). You don't have to extract it.

---

### Post by fmpfmpf on 2008-05-09
ok
thank you very very much

---

### Post by hermes0710 on 2008-05-09
Glad I helped :)

---

