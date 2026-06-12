---
title: "Slow graphics since 14.04 even with Metacity. VIA K8M890."
date: 2014-07-09
forum: New to Ubuntu
---

### Post by benawhile on 2014-07-09
Hello
I have a slow graphics problem.
12.04 was OK, problem is since fresh install 14.04.
 Unity was too slow to use at all, everything in desktop was jerky, jerking at regular intervals. (Sorry, that's the only way I can describe it!)
 Tried Gnome compliz , also too slow, jerky, regular intervals.
 Gnome metacity a little jerky but generally usable, however all videos, internet and  in the computer, i.e. in the onboard video application, are too jerky unless played on small screen. The frequency of the jerks decreases, i.e. resolution decreases, in direct proportion to increase of screen size.

 From settings details  

 Mobo MSI K9VGM-V purchased 2007
 Chipset
 Northbridge VIA K8M890CE
 Southbridge VIA 8237A
 graphics Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
 Processor AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ × 2  
 32 bit

 Since install to try and get an improvement I have done the following;
 First, to be able to watch C4OD, channel 4 on demand at all, (UK) I had to get hal thus:

     sudo add-apt-repository ppa:mjblenner/ppa-hal     
sudo apt-get update && sudo apt-get install hal 

Resolution was still poor (jerky picture) so tried this:

 sudo add-apt-repository ppa:pipelight/stable 
sudo apt-get update 
sudo apt-get install --install-recommends pipelight-multi 
sudo pipelight-plugin &#8211;update 

Made no difference to resolution.!

 System test all ok, graphics OK.

 The &#8220;system&#8221; &#8220;details&#8221; under &#8220;display&#8221; do not list the chipset, only the gallium thing. I have looked for additional drivers, none available.

 I am aware of many others experiencing slow graphics since 14.04. There is some info about openchrome drivers, but nothing since 2009, presumably it is now installed by default?  

 Can you advise on updating anything for this specific graphics chip? Needless to say, MSI support only offers windows drivers.

 Failing that could you advise on a state of the art graphics card? There is a spare extension slot on the mobo.

---

### Post by slooksterpsv on 2014-07-10
Xubuntu with compositing disabled or Lubuntu would work better. As for videos online, you would need a new graphics card, that one's just too old. Chrome's PPAPI (Pepper) is very CPU intensive. Hmm... as for a GPU I can't recommend one. Someone may know one which is great.

You could always try WINE for Silverlight to watch Silverlight content (Netflix for example) with Firefox - [http://compholio.com/netflix-desktop/](http://compholio.com/netflix-desktop/)

Other than that, I'm kind of out of suggestions.

---

### Post by benawhile on 2014-07-10
Thank you for replying. Is there a reason why my graphics chip worked OK in 12.04 but not 14.04?

---

### Post by slooksterpsv on 2014-07-10
Things get heavier in the code, they process a lot more information - and 14.04 vs 12.04 just the system itself 14.04 uses a lot more graphical leverage for its UIs at least for Ubuntu, Ubuntu-Gnome, and Kubuntu. 12.04 I believe only required 384MB for 32-bit and 512MB for 64-bit. The minimum for either is 512MB now. I recommend Xubuntu or Lubuntu to see if that speeds things up.

---

### Post by benawhile on 2014-07-10
OK will have a look at that. I have lubuntu on my old laptop. But what's the downside of Lubuntu and Xubuntu? I use Audacity a lot, will that still work?

---

### Post by slooksterpsv on 2014-07-10
Yes, Audacity will still work. The main difference is the Desktop Environment.
Xubuntu uses XFCE
Kubuntu uses KDE
Ubuntu uses Unity
Lubuntu uses LXDE
Ubuntu Gnome uses Gnome

Lubuntu is more of an XP like look and feel.
Xubuntu isn't Gnome 2.x but has that gnome 2.x feel to it.

---

