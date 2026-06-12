---
title: "LightWave 3D &amp; Fusion RenderSlaves  ( Run .bat in Ubuntu Wine )"
date: 2012-12-29
forum: New to Ubuntu
---

### Post by Carlo Jongen on 2012-12-29
This is an issue that came out of an other thread of mine:
 "[SOLVED] [**How to bring Windows mapped drive in linux wine**]("http://ubuntuforums.org/showthread.php?t=2098327")"


_**This is my SetUp:**_
- 1 Master PC Running Win7 with Lightwave 3D content and Eyeon Fusion Comp files on it.
- 2 Slave IntelPro Mac's running Ubuntu 12.10, Wine 1.5.19, Lightwave 11.02 and Eyeon RenderSlave 6.32.
- 1 Slave has a Sentinel HASP Dongle that contains the License key for the Eyeon Fusion RenderSlaves.


_**How I run my Eyeon Fusion RenderSlave:**_
I use a script that boots my RenderSlave in Ubuntu and it can find it's license on a Windows based Machine. ( Using LMTools.exe => [http://www.eyeonline.com/NetworkLicensing.html](http://www.eyeonline.com/NetworkLicensing.html) )
The point is that the OS of this machine ( running the license service ) needs to be replaced by Ubuntu as well.
So In this case it can't find its license because of a FlexLM Service- or HASP Driver problem.

Until now I've tried the next thing:
- Installed LMTools.exe in wine and setting it up like in the link above.
- In de Wine RegEdit I've made a System Variable like in the link above.
- Installed Hasp Driver, but I think this is the problem.

_**Issue:**_
* What driver do I need to have this HASP be recognized ( Linux or Windows in wine )?
* And how can I check if the Dongle is working properly in Ubuntu or in Wine?

---

