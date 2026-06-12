---
title: "Public Key"
date: 2016-02-28
forum: New to Ubuntu
---

### Post by Fabian_Mena on 2016-02-28
Hello everyone!

I am a new user of Ubuntu, i use ubuntu gnome 15.10.
When i type a "sudo apt update" in terminal i have the following error: W: Error de GPG: [https://download.01.org](https://download.01.org) wily InRelease: Las firmas siguientes no se pudieron verificar porque su clave pública no está disponible: NO_PUBKEY A496EB03894A3A8D

Please i need help with this.

Thanks in advance mates!!!

Salutes!

---

### Post by QIII on 2016-02-29
Hello!

Why do you have [https://download.01.org/](https://download.01.org/) in your sources list?  What is it for?

It is most certainly not a Canonical source.

---

### Post by 1-moritz on 2016-02-29
> **QIII said:**
> Hello!

Why do you have [https://download.01.org/](https://download.01.org/) in your sources list?  What is it for?

It is most certainly not a Canonical source.

Hi! I've got the same problem. 
[https://download.01.org](https://download.01.org) points to the official Intel repositories, which I allegedly need for my Dell XPS12 on-board GPU drivers.
What do you recommend I do?

---

### Post by X-RED_Tech on 2016-02-29
When you use the Intel installer it adds that repository. There's no need because Ubuntu already includes drivers for Intel Graphics. Perhaps the ones from Intel repo are newer but I'm not sure. I used it once and noticed no difference.

---

### Post by 1-moritz on 2016-02-29
Ah, yes. The Intel drivers are newer and fix some serious bugs in 15.10, i.e. Xorg freezing up.

---

### Post by oldos2er on 2016-02-29
According to [http://askubuntu.com/questions/736057/intel-graphics-drivers-1-4-0-i915-4-3-3-4-2-0-dkms-isnt-available-no-pubkey-d](http://askubuntu.com/questions/736057/intel-graphics-drivers-1-4-0-i915-4-3-3-4-2-0-dkms-isnt-available-no-pubkey-d) this is an ongoing problem with the Intel repository.

---

### Post by Fabian_Mena on 2016-03-01
Sorry for answer late, but i fix the problem, in the page of intel linux drivers (video drivers) was the pulic key:

> [h=3]Signatures - Ubuntu*[/h] 
[LIST]
[*]NOTE: Whether installing for the first time or upgrading from an earlier release, be sure to run the following.
[/LIST]
 In order to "trust" the Intel® Graphics Installer for Linux*, you  will need to add keys to Ubuntu's software package manager ("apt"). Open  a terminal, and execute these lines:
 wget --no-check-certificate [https://download.01.org/gfx/RPM-GPG-KEY-ilg-3](https://download.01.org/gfx/RPM-GPG-KEY-ilg-3) -O - | \
sudo apt-key add -



With that i resolve my problem.

Thanks for your answers mates!!!

---

