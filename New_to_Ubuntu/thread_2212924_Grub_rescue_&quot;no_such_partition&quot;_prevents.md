---
title: "Grub rescue &quot;no such partition&quot; prevents any other boot!"
date: 2014-03-23
forum: New to Ubuntu
---

### Post by tonio3 on 2014-03-23
Hello all, 
I am an amatuer in Ubuntu, and this is the very first time posting something. I always try to read pages and pages till I fix my issues, but this time i really am lost.

_So, the environment:_

[LIST]
[*]Macbook pro 5.5 (begin of 2010)
[*]Ubuntu Precise Pangolin 12.04 (64 bit) installed as unique OS one year ago.
[*]not sure about the partioning, but something like this, in this order: 4GB(?) swap, 10 GB root, 250 GB home, 5 GB unused.
[/LIST]

_The main issue:_

[LIST]
[*]Right after the white screen (mac style), it gives the error message "no such partition", then it goes in grub rescue mode.
[*]I tried several combinations (as [this]("http://www.hardwareforyou.it/tutorial-e-guide/linux/1480-grub-rescue-prompt-cosa-fare-quando-il-sistema-non-si-avvia-piu"), or [this]("http://tuxthink.blogspot.it/2013/10/error-no-such-partition-grub-rescue.html"), and more) for resetting root and path for the modules to (hdX,Y)boot/grub/ directory and then trying to launch linux.mod or normal.mod. Always returning a message of the like "boot/grub/i386-pc/linux.mod not found" (that make me think I failed resetting the path???)
[*]In no way I succeded in booting from CD nor USB because: I) my cd-room is somehow stucked, if I try to insert a cd there is some kind of lock preventing it (I know for sure it's empty); II) to the USB is connected an external HD with 2 partitions, and the first one is bootable (tested and it works fine on another pc) but it is ignored; III) I tried all the possible combinations of keys I know (escape, C, left alt, f12, esc and then f9) to get into whatever sort of boot menu,failing miserably.
[/LIST]

_The begining of the end:_
Despite my attempts to clean and keep under control the root partition, in little more than a year of upgrades it reached saturation. Before attempting to resize it (still can't belive 10 GB are not enough!!!), I wanted to try re-installing ubuntu fresh. Even more, I was curious about "Lubuntu". After a quick backup, Installed Lubuntu 13.10 on the last, unused partition of 5GB (when prompted I choosed "Install along side Ubuntu 12.04"). It had some issues, expecially with the graphic, so I just decided to leave it. Back on my ubuntu desktop, I created a bootable partition on my external HD with "startup disk creator" and the ubuntu 12.04 - 64bit .iso I still had.
**Now, what I believe it caused the disaster ->** At the end of the process, a window appeared asking me something about partitions or similar. I had no time to read/understand it, since I accidentally hitted the return key. Not really worried about that, i rebooted the system. And now I am here, locked in an endless grub rescue loop.

The odd part is that I can't really interact with this prompt. Most of the [commands]("https://help.ubuntu.com/community/Grub2/Troubleshooting") that should still work, look useless!
When I give ```
ls
```, it turns me back ```
(hd0) (hd0,gpt4) (hd0,gpt3) (hd0,gpt2) (hd0,gpt1)
```. Here, if I give again ls on (hd0), (hd0,gpt2), or (hd0,gpt1), they result as "unknown file system", (hd0,gpt3) is the root partition, and (hd0,gpt4) is the home partition.

I am extremely worried about this. Fortunately I can retrieve my data, but I am fearing I will have to trash a perfectly working laptop because of this!!!

Thanks for any possible help!

T

---

