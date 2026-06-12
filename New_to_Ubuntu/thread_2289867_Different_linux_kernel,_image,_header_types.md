---
title: "Different linux kernel, image, header types"
date: 2015-08-07
forum: New to Ubuntu
---

### Post by rattskjelke on 2015-08-07
Why are there so many different linux kernel types?
linux-headers, linux-image, generic, signed, extra, low latency, and combinations of those.
Anybody have links that explain what they are for or are they something different than the linux kernel?
When I boot from the live CD they are different than what gets installed. Why is that?

---

### Post by oldfred on 2015-08-10
Signed is the UEFI secure boot version with the signing keys.
Low Latency is used by Ubuntu studio flavor.
Generic is the standard install for BIOS or UEFI without secure boot.

You may need headers to allow binary blob drivers like nVidia, AMD or others to be integrated into the kernel.

Not sure what extra is now?

---

### Post by sandyd on 2015-08-10
> **oldfred said:**
> Signed is the UEFI secure boot version with the signing keys.
Low Latency is used by Ubuntu studio flavor.
Generic is the standard install for BIOS or UEFI without secure boot.

You may need headers to allow binary blob drivers like nVidia, AMD or others to be integrated into the kernel.

Not sure what extra is now?

[http://packages.ubuntu.com/trusty/amd64/linux-image-extra-3.13.0-24-generic/filelist](http://packages.ubuntu.com/trusty/amd64/linux-image-extra-3.13.0-24-generic/filelist)

Seems like additional drivers that didn't make it into generic/signed for some reasons

---

### Post by yoshii on 2015-08-23
can the low-latency kernel be installed into Lubuntu?

---

