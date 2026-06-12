---
title: "Apt-build worth it?"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by skymera on 2008-11-28
Hello all!

I'm in Ubuntu and kinda Googling around for stuffs and come across apt-build.

I believe it downloads the source and compiles it to your CPU spec and optimisation standards. 

Currently im doing "world" which is every program i have installed.
It's trundling along quite nicely.

But is doing apt-build worth it?
Is having packages optimised to your CPU and architecture a big bonus oppsed to generic packages?

---

### Post by sdowney717 on 2008-11-28
[http://polishlinux.org/linux/debian/apt-build-optimize-debian/](http://polishlinux.org/linux/debian/apt-build-optimize-debian/)

read the comments, maybe it is worth it and maybe not.

---

### Post by skymera on 2008-11-28
After about an hour and a half of downloading and compiling it stopped.

Binutils or something had no source ?

oh well. Was worth a try.

---

### Post by sdennie on 2008-11-28
It would probably be worth it for CPU bound applications but, for most applications, you probably won't notice any difference at all because the slowness is not being caused by the compiler not emitting highly optimized code but by things like disk access, poorly written software, etc.

---

### Post by skymera on 2008-11-28
So what would be beneficial?

Programs used for booting and Gnome based?

---

### Post by sdennie on 2008-11-28
> **skymera said:**
> So what would be beneficial?

Programs used for booting and Gnome based?

Those two things probably wouldn't benefit much, if it all.  The places where you might see benefits are things like audio/video encoding or long running math calculations.  Basically, anything that sits in tight CPU bound loops for a significant amount of time might benefit from custom compiler options whereas most interactive applications or things that spend a lot of time waiting on disk reads (like the boot process) probably won't benefit much.

---

### Post by skymera on 2008-11-28
Thank you for clarifying that

---

### Post by andrew.46 on 2008-11-28
Hi,

> **skymera said:**
> So what would be beneficial?

Programs used for booting and Gnome based?

One example would be MPlayer which ./configures itself to suit a particular machine. The option --enable-runtime-cpudetection which is routinely added to distro versions of MPlayer is a relatively inefficient substitute. 

But I am not sure that apt-build would be the best tool here anyway, compiling from svn would be more logical? 'apt-build world' looks  especially over the top :-). 

Does anybody have other specific examples?

  Andrew

---

### Post by sdennie on 2008-11-28
> **andrew.46 said:**
> 
One example would be MPlayer which ./configures itself to suit a particular machine. The option --enable-runtime-cpudetection which is routinely added to distro versions of MPlayer is a relatively inefficient substitute. 


Yes, mplayer would be an example where making the compiler aware of your target machine might be useful.  It probably wouldn't make mplayer "faster" really but, making the compiler aware of your CPU type, available instruction sets, L2 cache characteristics, etc, could potentially lower its CPU usage by a noticeable amount.

Any time you compile an app that is going to be constantly using a noticeable number of CPU cycles, making a (good) compiler aware of the target machine is probably going to benefit you.  I honestly don't know how good gcc is at emitting highly optimized code (or if the x86 instruction set even lends itself to such a notion (though I suspect it doesn't)).

Compilers are complex beasts and once you get past the "low hanging fruit" (which is where Ubuntu is compiled at), there is no guarantee that your compiler is smart enough to speed up your app in any appreciable manner no matter how hard you try to coax it into doing so.  At that point, it's time to look at the actual code and figure out why it's slow.  ;)

---

### Post by kerry_s on 2008-11-28
i didn't think it was worth it.
i got more speed by using xfonts(fixed,helvetica) for the desktop and most programs and a font server(xfs).
i do use msttf fonts in my browser, but i have antialias turned off for all but bold and italic in my ".fonts.conf".
i'm more use to non-smooth fonts like they are in win2k, fast and low resource. but then again i only have 450mhz 256mb ram, so i need every inch. :)

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

 <!-- disable antialias for regular fonts -->
 <match target="font">
  <test compare="more" name="pixelsize" qual="any">
   <double>9</double>
  </test>
  <test compare="less" name="pixelsize" qual="any">
   <double>18</double>
  </test>
  <edit mode="assign" name="antialias">
   <bool>false</bool>
  </edit>
 </match>

 <!-- antialias bold fonts -->
 <match target="font">
  <test name="weight">
   <const>bold</const>
  </test>
  <edit name="antialias" mode="assign">
   <bool>true</bool>
  </edit>
 </match>

 <!-- antialias italic fonts -->
 <match target="font">
  <test name="slant">
   <const>italic</const>
  </test>
  <edit name="antialias" mode="assign">
   <bool>true</bool>
  </edit>
 </match>

</fontconfig>

```

---

### Post by spinoza666 on 2010-05-11
> **sdennie said:**
> Those two things probably wouldn't benefit much, if it all.  The places where you might see benefits are things like audio/video encoding or long running math calculations.  Basically, anything that sits in tight CPU bound loops for a significant amount of time might benefit from custom compiler options whereas most interactive applications or things that spend a lot of time waiting on disk reads (like the boot process) probably won't benefit much.

Worth it for long running math calculations? Thanx:) Just the advice I was looking for.

---

### Post by maximAL on 2010-09-07
Is apt-build still properly supported? 
It's hard to find good information on it and it's mostly pretty old.
Most sources indicate that there are march and mcpu options in /etc/apt/apt-build.conf, what seems to no longer be true. Instead, there is an mtune option that stores the specific cpu.
Now, mtune is not the same as march (afair it optimizes programs for the particular processor, but without using any instruction set extension like SSE).
I tried to build a few programs with apt-build (e.g. gimp), but i couldn't find the options i set in the apt-build.conf anywhere in the output.

---

