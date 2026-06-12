---
title: "Is the Qemu version 6.1 supported in Ubuntu 22.04"
date: 2022-08-01
forum: New to Ubuntu
---

### Post by hareeshk0007 on 2022-08-01
[COLOR=#000000]Hi all,[/COLOR]

[COLOR=#000000]I would like to know the compatibility of Qemu 6.1 with Ubuntu 22.04. Ubuntu 22.04 ships the Qemu version 6.2. But can I use the Qemu version 6.1 in Ubuntu 22.04? If Ubuntu 22.04 directly doesn't support Qemu 6.1, what are the changes I need to do in the code to support that ?[/COLOR]

[COLOR=#000000]Any help/suggestions would be really appreciated !![/COLOR]

---

### Post by grahammechanical on 2022-08-01
Ubuntu Software in Ubuntu 22.04 offers versions of Qemu as snap packages. It offers Qemu 4.2.0 as the latest/stable version and 6.2.0 as latest/edge version. Where do you intend to get version 6.1 from? Why is version 6.2 not acceptable? Will version 6.1 be deb packaged?

Regards

---

### Post by hareeshk0007 on 2022-08-02
Hi,

Thank you very much for your reply.

Our current development is with Qemu 6.1. We had taken the qemu from the [https://download.qemu.org](https://download.qemu.org) (version 6.1). Version 6.2 is acceptable for us, eventually we will move to version 6.2. But before that, we would like to confirm that is the version 6.1 has supported in Ubuntu 22.04 or not. I am not sure about the Debian packaging of 6.1.

---

### Post by Impavidus on 2022-08-02
Qemu 6.1 is not in the repositories for Ubuntu 22.04, so it's not supported by Canonical, the company behind Ubuntu. You could say it's not supported by Ubuntu, or by us on the forum. That doesn't necessarily mean it won't work, but it means you're on your own if you try to make it work. With effort, most things can be made to work, but it may require installation from source, manually installing additional versions of libraries and such. Not something you want to do, unless there's no way around. Or maybe it's easy; I can't say. It may depend on the exact components of Qemu you want or need. You could try, but if it's not easy, don't try too hard.

---

