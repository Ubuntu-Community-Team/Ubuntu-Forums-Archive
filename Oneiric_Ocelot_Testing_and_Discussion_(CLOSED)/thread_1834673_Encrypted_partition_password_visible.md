---
title: "Encrypted partition password visible"
date: 2011-08-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Qdlaty on 2011-08-27
Hi,
since forever I've problem with setting up a proper encrypted partition under Ubuntu.
I came from OpenSuse with my /home and /media/Data encrypted with Luks and spent some time in figuring out how to make it work during system boot.

Now it is simple with /etc/crypttab and proper line in fstab but there is a much bigger problem.

As the binary nVidia drivers are a pain in a neck with the plymouth (the trick with uvesafb doesn't work with PAE kernel) my boot screen is text terminal and when there is a prompt for encryption password the text I enter appears directly on the screen.
There are no ***** but exact letters I'm typing.

How can I fix that! This is a bit odd to leave my passphrase in open text in the terminal for someone to read.

BTW. Installing KUbuntu is quick but setting up proper nVidia drivers takes 10x longer since the nouveau drivers were introduced as default.

---

