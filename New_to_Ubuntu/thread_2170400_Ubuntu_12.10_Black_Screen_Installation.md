---
title: "Ubuntu 12.10 Black Screen Installation"
date: 2013-08-26
forum: New to Ubuntu
---

### Post by Karim_Kahale on 2013-08-26
[COLOR=#333333][FONT=UbuntuRegular]I am new to ubuntu. I am trying to install Ubuntu 12.10 on my hp with: Intel i3 CPU, AMD 5000 Radeon HD Grahics I am getting a black screen after the Ubuntu's installation. I already tried the nomodeset option and the noapic option but no luck. What can I do to bypass this problem? Thanks All!

Sorry For being a noob in ubuntu [/FONT][/COLOR]:(

---

### Post by Quackers on 2013-08-26
Welcome to UF.
Just an idea, but instead of using nomodeset try modeset=0 (that's a zero, not a letter o)
Add it to the kernel line leaving a space after quiet splash then type it there - ctrl+x to boot and see if anything changes

---

### Post by Karim_Kahale on 2013-08-26
> **Quackers said:**
> Welcome to UF.
Just an idea, but instead of using nomodeset try modeset=0 (that's a zero, not a letter o)
Add it to the kernel line leaving a space after quiet splash then type it there - ctrl+x to boot and see if anything changes
Okay I tried that but it didn't work sadly :/

---

