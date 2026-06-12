---
title: "Migrating from windows to ubuntu"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by Medaforce on 2013-01-04
I've run ubuntu as my secondary OS for a while now and I absolutely love ubuntu. The only reason Windows 7 still is my primary OS is that I like to game.
Now i've read about seamlessRDP and this looks like the perfect way for me to start using ubuntu 100% of the time and still game whenever i feel like it. But is it that good?
And if it's not, is there any way I can make it work on ubuntu? Or should i hope for more support on linux in the near future?

---

### Post by lykwydchykyn on 2013-01-04
I'm not a gamer, but I can't imagine you'd get anything like acceptable performance using RDP.

If gaming is important to you, keep Windows around for now and just use it for games.

---

### Post by Mark Phelps on 2013-01-04
IF you're talking about hardware-accelerated 3D gaming, Windows currently wins over Ubuntu because it has the drivers to make that happen.

AMD, and less so, Nvidia, periodically drop support for their accelerated drivers, so even if you have a card that is only one year old, there may be no drivers that will give you decent frame rates.

Plus, MS keeps improving their DirectX stuff, and while their drivers generally keep up, the Linux drivers typically do not.

So, Windows gaming in Ubuntu, using Wine or anything similar, is very much a hit-or-miss situation.

---

### Post by DuckHook on 2013-01-04
There simply is no alternative to Windows if you are a committed gamer--no magic wand, no magic bullet. All solutions sacrifice varying degrees of performance and playability. Even WINE (which I use for some old and exceptionally stable Windows games) is less efficient than running the game natively on Windows, and WINE is the most efficient method short of game developers issuing native Linux ports (at this point, still a pipe-dream). VMs are a non-starter and since seamlessRDP is just another variant of a VM, you won't like the experience at all. seamlessRDP will lag atrociously due to the graphics refresh rate needed for bleeding edge games, that is, if you can get them to run at all. This is due to the fact that virtual machines, by their very nature, are equivalent to a computer that is roughly three generations old. Therefore your game will be using a puny virtual video card that can't support the latest DirectX. So much efficiency is lost translating the virtual machine graphics onto the actual graphical hardware, that the results are only acceptable for very primitive games. Any newer game that relies on the latest GPU features will only choke on a VM. I understand that *Xen* is capable of passing video calls directly through to the GPU hardware, but I haven't installed *Xen* yet and have no idea how or even if this works. Forum inquiries regarding *Xen* were met with stony silence, so I suspect that any use of *Xen* constitutes exploration of the bleeding edge. Biggest drawback is that you still need a Windows install and license to use a VM anyway, so why not just dual boot and avoid all of the fuss and bother?

That said, I do manage to run a few ancient games on a VM quite happily. The key is, they must be ancient--designed to run on now-obsolete equipment of roughly the power and resources to which a VM equates. SimCity 2000 runs just fine. So does Civ 2 and Age of Wonders. SimCity 3000 chokes. Newer versions won't even install after their hardware detection phase concludes that the VM doesn't have the needed horsepower or hardware. Your mileage will vary, but not likely by much.

---

### Post by mysteriousdarren on 2013-01-11
Check out [www.winehq.org/](www.winehq.org/) to see what works with linux and Ubuntu. Search around for the specific game, many are not supported.

---

### Post by Abhinav Kumar on 2013-01-12
> **Medaforce said:**
> I've run ubuntu as my secondary OS for a while now and I absolutely love ubuntu. The only reason Windows 7 still is my primary OS is that I like to game.
Now i've read about seamlessRDP and this looks like the perfect way for me to start using ubuntu 100% of the time and still game whenever i feel like it. But is it that good?
And if it's not, is there any way I can make it work on ubuntu? Or should i hope for more support on linux in the near future?
Honestly speaking, many games are not designed for linux platforms. Some of them do run in wine while Some running in wine don't have full functionalities. As others have suggested, I also would say keep windows 7 for gaming. 

P.S. Trends in gaming on linux is changing now-a-days. Valve has recently announced that it would develop linux steam box. However, the reality is yet to come. 

[http://www.extremetech.com/gaming/144951-valve-confirms-linux-steam-box-for-2013-but-can-it-really-disrupt-pc-and-console-gaming](http://www.extremetech.com/gaming/144951-valve-confirms-linux-steam-box-for-2013-but-can-it-really-disrupt-pc-and-console-gaming)

---

