---
title: "Purple screen on boot no grub menu"
date: 2013-04-04
forum: New to Ubuntu
---

### Post by stat3631 on 2013-04-04
I have a Toshiba satellite a105 that have a fresh install of Ubuntu gnome 12.10 and I have a problem. When I start the computer I get a blank purple screen then a black screen it requires turning computer off and back on then I get the grub menu.  I have done a lot of searching.
So far I have tried:
[http://askubuntu.com/questions/120096/ubuntu-hangs-at-purple-screen](http://askubuntu.com/questions/120096/ubuntu-hangs-at-purple-screen)
[COLOR=#000000]Then do the following commands once you're dropped to the root shell:[/COLOR]
[COLOR=#000000]sudo apt-get update [/COLOR]
[COLOR=#000000]sudo apt-get upgrade [/COLOR]
[COLOR=#000000]sudo apt-get install fglrx [/COLOR]
[COLOR=#000000]sudo aticonfig --initial[/COLOR]
[COLOR=#000000]sudo reboot

This booted great but I have only wallpaper no icons or menu so I had to uninstall fglrx

Then I tried changing grub to nomodeset or acpi_osi from here [/COLOR][http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
but after entering passphrase I got black screen.

Is there a fix for the  purple screen or a way to get back the icons with fglrx?

Thanks for any help.

---

