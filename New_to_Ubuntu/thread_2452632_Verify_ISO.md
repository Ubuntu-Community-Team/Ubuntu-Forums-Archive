---
title: "Verify ISO"
date: 2020-10-26
forum: New to Ubuntu
---

### Post by foxine on 2020-10-26
Can someone please explain to me how to verify my iso download. A few weeks ago I downloaded LubuntuOS but I really struggled with verifying the iso because I don't understand what gpg sha256sum etc etc.

---

### Post by coffeecat on 2020-10-26
Welcome to the forum. I've moved your post to its own thread and given it a relevant title. Please start your own threads.

To answer your question, this is a good place to start: [https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview](https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview)

---

### Post by ActionParsnip on 2020-10-26
If you use torrents then you don't have to. The torrent protocol checks data during the download and after the download is complete. Far easier

---

### Post by SeijiSensei on 2020-10-26
Use the sha256sum utility at the command prompt:

```
$ sha256sum groovy-desktop-amd64.iso 
bcbbb9d4b62b9244b63883146b6f2d918420ee506c42b5a5a1c05c8d3f0066e3  groovy-desktop-amd64.iso
```

Be patient. This will take a few minutes.

---

### Post by TheFu on 2020-10-26
I don't know what the Lubuntu ISO does, but other Ubuntu ISO files automatically validate themselves at the first boot from the media unless you break out of the default check.

Also, someone really new to Linux shouldn't install 20.10, they should use 20.04 for at least a year first, unless your computer is bleeding edge and absolutely refuses to work with 20.04.  20.04 has support for 5 yrs.  20.10 only gets 9 months of support. This is not a long time and you will be forced to install a new OS every 6 months until 22.04 is released in April 2022 to retain any support.

Typical end users shouldn't really load non-LTS releases, IMHO, unless you are planning to wipe the OS after a few weeks and just want a system to play around on.  Use LTS releases only for production work.  Please.

---

### Post by Deep_Peasant on 2020-10-27
> **foxine said:**
> Can someone please explain to me how to verify my iso download. A few weeks ago I downloaded LubuntuOS but I really struggled with verifying the iso because I don't understand what gpg sha256sum etc etc.


Assuming you are allready are running an ubuntu flavour, install through software-center gtkhash.
You can use it to generate a checksum of the iso file you have downloaded on your pc and compare it
 to the given checksum on the download site,

[https://lubuntu.me/downloads/](https://lubuntu.me/downloads/)

for example the 20.04.1 LTS (Focal Fossa) iso has a SHA256sums of:
> 
0727253098c998c0b7b7963326690419710cdce2479472ca7cfe7adda7a31174 *lubuntu-20.04.1-desktop-amd64.iso

this code,
> 
0727253098c998c0b7b7963326690419710cdce2479472ca7cfe7adda7a31174

should match the code that the program gtkhash outputs of the downloaded lubuntu-20.04.1-desktop-amd64.iso


> **TheFu said:**
> **I don't know what the Lubuntu ISO does, but other Ubuntu ISO files automatically validate themselves at the first boot from the media unless you break out of the default check.**

Also, someone really new to Linux shouldn't install 20.10, they should use 20.04 for at least a year first, unless your computer is bleeding edge and absolutely refuses to work with 20.04.  20.04 has support for 5 yrs.  20.10 only gets 9 months of support. This is not a long time and you will be forced to install a new OS every 6 months until 22.04 is released in April 2022 to retain any support.

Typical end users shouldn't really load non-LTS releases, IMHO, unless you are planning to wipe the OS after a few weeks and just want a system to play around on.  Use LTS releases only for production work.  Please.

Interesting, my live usb stick seemed to do that, verifying files. Learned something :)

---

### Post by guiverc on 2020-10-27
I'll assume this has already been answered, but I'll still provide some links.

For Lubuntu I'd recommend looking at the Lubuntu manual, ie. [https://manual.lubuntu.me/stable/1/Installing_lubuntu.html](https://manual.lubuntu.me/stable/1/Installing_lubuntu.html) for installation specifics.

The first subsection of **Installing Lubuntu** includes an example ([https://manual.lubuntu.me/stable/1/1.1/retrieving_the_image.html](https://manual.lubuntu.me/stable/1/1.1/retrieving_the_image.html)) that has already been covered well in this *UF* thread.

I usually use `zsync` to download my ISOs, which performs a validation on completion of download (*I use `zsync` so I'm not downloading the whole ISO, I tell it to update a file I provide which is usually a prior release, or different flavor reducing the bandwidth used as I have monthly quotas*).

I find it's rare the download fails, it's the write to media that fails most (*this is detected by the self-validation which is  reliable unless the ISO itself was faulty thus why ISO should still be checked*)

---

### Post by foxine on 2020-11-03
thank you guys for your replies. it finally worked out.  writing this from my ubuntu 20.04 powered machine. although i do have to say that there is so much to learn in the world of linux, but with a community of people like you, i look forward to it.  cheers,   p.s sorry for the late reply, its been a hectic week for me

---

### Post by ActionParsnip on 2020-11-04
You'll learn as you go. Same way you learned Windows

---

