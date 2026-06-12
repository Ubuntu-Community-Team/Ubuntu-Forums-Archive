---
title: "Colored stripes at the end of install"
date: 2012-08-19
forum: New to Ubuntu
---

### Post by Nunud on 2012-08-19
Hello there!

I'm absolutely new to Linux (former Apple fan), and I'm here because I'm unable de complete the installation of 12.04 on my new PC... So here I am, asking for a little guidance please! ;)

It all goes well until the very first reboot, and then instead of a regular desktop display, I get weird looking multicolor stripes, and nothing moves...

Here's what's inside the PC in question:

- Motherboard: Gigabyte GA-Z77-D3H 
- CPU: intel Core I5
- Graphics card: NVIDIA GeForce GTX 560 Ti

Do you guys think I'll be eventually able to run Ubuntu on this machine?

Thank you in advance for your time...

(PS: Yes I know, my english is a bit 'rough', sorry about that! ):P)

---

### Post by Bashing-om on 2012-08-19
Hi nunud;

  Seems you have a graphics display problem ... fixable! Try this:

Boot up and hold the shift key to bring up the grub menu ...as the only kernel available is presently highlighted, press e to edit the boot parameters. arrow down to the line that is  ***GRUB_CMDLINE_LINUX_DEFAULT=***"quiet splash"//
insert nomodeset after "quiet splash" ...ctl-x to continue to boot... when you get into the ubuntu system ,,,from system =>administration =>hardware drivers (not sure of this path on 12.04 edition) but, hardware drivers will enable you to select an appropriate driver for your nvidia graphics card.
[INDENT]let us know how this works out///
[/INDENT]

---

### Post by Nunud on 2012-08-19
Hey!

Thanks for the quick reply! I'll try this as soon as I get home, and I'll keep you posted!

---

