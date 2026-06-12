---
title: "Does latest Ubuntu have 32 bits version?"
date: 2019-12-14
forum: New to Ubuntu
---

### Post by j2ee on 2019-12-14
I google it but the result is mix, any idea?

---

### Post by howefield on 2019-12-14
> **j2ee said:**
> I google it but the result is mix, any idea?

Latest Ubuntu ? No, there is no 32 bit version of the latest Ubuntu. I think you'd need to go back to 16.04 to get 32 bit, 16.04 is supported till April 2021.

Some of the flavours may have a later 32 bit release such as Lubuntu. Use this link to check out what is available to download for Ubuntu and all the flavours..

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by deadflowr on 2019-12-14
They seemed to have stopped building 32-bit kernels for 19.10 and newer.
They have compiled a list of 32-bit packages they have determined they will need to keep supporting,
which you can read here: [https://discourse.ubuntu.com/t/community-process-for-32-bit-compatibility/12598]("https://discourse.ubuntu.com/t/community-process-for-32-bit-compatibility/12598")

---

### Post by GhX6GZMB on 2019-12-14
32-bit ends at 18.10 and the .iso is longer available for download. It exists, though.
Lubuntu 18.04 can still be downloaded: [https://lubuntu.net/lubuntu-18-04-bionic-beaver-released/](https://lubuntu.net/lubuntu-18-04-bionic-beaver-released/)

Direct link: [http://cdimage.ubuntu.com/lubuntu/releases/18.04/release/lubuntu-18.04-desktop-i386.iso](http://cdimage.ubuntu.com/lubuntu/releases/18.04/release/lubuntu-18.04-desktop-i386.iso)

---

### Post by poorguy on 2019-12-14
Here's 32 bit Linux distro Peppermint 10 and it's an excellent Ubuntu based / built Linux distro that's easy to use and doesn't use a lot of system resources it also has an excellent forum.

[https://peppermintos.com/](https://peppermintos.com/)

[https://peppermintos.com/blog/](https://peppermintos.com/blog/)

[https://peppermintos.com/guide/](https://peppermintos.com/guide/)

[https://forum.peppermintos.com/](https://forum.peppermintos.com/)

---

### Post by sofiee on 2019-12-14
Also manjaro do a 32bit version of their os
its nice to see.
[https://osdn.net/projects/manjaro32/storage/](https://osdn.net/projects/manjaro32/storage/)

---

### Post by j2ee on 2019-12-14
Seem like no one suggest Lubuntu? Look like it is the only Ubuntu distro that will still have 32 bits version.

---

### Post by deadflowr on 2019-12-14
> **j2ee said:**
> Seem like no one suggest Lubuntu? Look like it is the only Ubuntu distro that will still have 32 bits version.

The last 32-bit for Lubuntu was 19.04. (same applies to Ubuntu in general)
As I posted there will be no more Ubuntu 32-bit after that since they don't build 32-bit kernels anymore.
And you cannot have a 32-bit system without a 32-bit kernel.
You can fake it, for sure (run a 64-bit kernel but have all the packages be 32-bit arch)
but you could never call it a 32-bit OS since you could never run it on 32-bit hardware.

---

### Post by j2ee on 2019-12-15
> **deadflowr said:**
> The last 32-bit for Lubuntu was 19.04. (same applies to Ubuntu in general)
As I posted there will be no more Ubuntu 32-bit after that since they don't build 32-bit kernels anymore.
And you cannot have a 32-bit system without a 32-bit kernel.
You can fake it, for sure (run a 64-bit kernel but have all the packages be 32-bit arch)
but you could never call it a 32-bit OS since you could never run it on 32-bit hardware.

So you mean none of the Ubuntu distro including Lubuntu supports 32 bits in future. Which other distro should I try then?

---

### Post by j2ee on 2019-12-15
> **poorguy said:**
> Here's 32 bit Linux distro Peppermint 10 and it's an excellent Ubuntu based / built Linux distro that's easy to use and doesn't use a lot of system resources it also has an excellent forum.

[https://peppermintos.com/](https://peppermintos.com/)

[https://peppermintos.com/blog/](https://peppermintos.com/blog/)

[https://peppermintos.com/guide/](https://peppermintos.com/guide/)

[https://forum.peppermintos.com/](https://forum.peppermintos.com/)


Peppermint is based on Ubuntu, if Ubuntu doesn't support 32 bits, I don't see how can Peppermint do that in future.

---

### Post by j2ee on 2019-12-15
> **poorguy said:**
> Here's 32 bit Linux distro Peppermint 10 and it's an excellent Ubuntu based / built Linux distro that's easy to use and doesn't use a lot of system resources it also has an excellent forum.

[https://peppermintos.com/](https://peppermintos.com/)

[https://peppermintos.com/blog/](https://peppermintos.com/blog/)

[https://peppermintos.com/guide/](https://peppermintos.com/guide/)

[https://forum.peppermintos.com/](https://forum.peppermintos.com/)

> **sofiee said:**
> Also manjaro do a 32bit version of their os
its nice to see.
[https://osdn.net/projects/manjaro32/storage/](https://osdn.net/projects/manjaro32/storage/)

I google it and look like it would eat up 1gb of ram just running the OS, not friendly for very old notebook.

---

### Post by guiverc on 2019-12-15
Many Ubuntu flavors have 18.04 LTS x86 or i386 (in debian/Ubuntu terminology, i686 actually) releases. 
They are supported until 2021-April (ie. 3 years).  To download go to [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)

Xubuntu & Lubuntu both had 18.10 releases too, and produced x86 (i386/686) ISO's until ~December 2018 or part-way through the 19.04 development cycle. Installs could be forced to upgrade to 19.04 (most would not have seen the daily 19.04 ISOs) HOWEVER x86 binaries have stopped for 19.10 and it would **NOT** be wise to use it, nor I suspect would it be possible to upgrade a current 19.04 install to 19.10 anymore (many binaries were deleted just in the week before 19.10's official release).  *I do have a x86 19.10 system, but it's purely used for testing; which is where I noticed the binaries disappearing.*

(FYI: My last 19.04 *official* daily ISOs follow - note the dates, which is well before release date!!)
```
-rw-------  1 guiverc guiverc 1529937920 Nov 28  2018  disco-desktop-i386.iso    (Xubuntu 19.04)
-rw-------  1 guiverc guiverc 1627389952 Dec 20  2018  disco-desktop-i386.iso    (Lubuntu 19.04)
```


If you want or need x86/i386/i686 32-bit ISO's I'd recommend using a Ubuntu 18.04 LTS flavor such as Lubuntu, Xubuntu, or try some of the others (Ubuntu-MATE etc) if they are more to your tastes. 

Yes x86/i386/i686 support continues, but only with 18.04 & flavors.   I'm one such user of it !

---

### Post by Dennis N on 2019-12-15
I have Ubuntu MATE 18.04 32-bit OS on my Dell Inspiron 1505 Laptop. I suggest that. When first released, the developer Mr. Wimpress promised to keep it supported for five years as an LTS. Ubuntu updates for the 32-bit packages keep arriving. Also, you can also install 32-bit versions of snap packages if you are interested in those. This laptop has 2 gB of RAM; Ubuntu MATE with Firefox running it's using 700 mB RAM right now. 

Manjaro XFCE 32-bit is only a project of a few maintainers that are trying to keep it alive. It's not an official release. They are doing their best, but it would require a lot more attention on your part.

---

### Post by guiverc on 2019-12-15
@Dennis N

The official Ubuntu MATE 18.04 LTS release is [https://ubuntu-mate.org/blog/ubuntu-mate-bionic-final-release/](https://ubuntu-mate.org/blog/ubuntu-mate-bionic-final-release/) which doesn't mention the end of support.  The main Ubuntu 18.04 LTS release statement can be seen at [https://fridge.ubuntu.com/2019/08/08/ubuntu-18-04-3-lts-released/](https://fridge.ubuntu.com/2019/08/08/ubuntu-18-04-3-lts-released/) which states

[B][I][COLOR=#333333]Maintenance updates will be provided for 5 years for Ubuntu Desktop, Ubuntu Server, Ubuntu Cloud, and Ubuntu Base. All the remaining flavours will be supported for 3 years.

[/COLOR][/I][/B][COLOR=#333333]Parts of all flavors are supported for the full five years; ie. those parts from the 'main' repository.  If you do a `ubuntu-support-status` on a Ubuntu-MATE 18.04 LTS system I think you'll find the MATE components all EOL 2021-April.[/COLOR]

---

### Post by Dennis N on 2019-12-15
I'm not worried. I remember what he wrote. It's in a blog post as I recall. It was celebrated as the first Ubuntu MATE LTS.

Edit: I should amend that claim of total 5 yr support - It's 78% correct. But that's not bad. Includes the security updates including kernel.

My Ubuntu MATE 18.04 32-bit support status. 78% of packages supported until 2023!
 
```
dmn@Kayleigh:~$ ubuntu-support-status --show-unsupported
Support status summary of 'Kayleigh':

You have 382 packages (20.2%) supported until April 2021 (Community - 3y)
You have 1487 packages (78.5%) supported until April 2023 (Canonical - 5y)
You have 3 packages (0.2%) supported until April 2021 (Canonical - 3y)

You have 0 packages (0.0%) that can not/no-longer be downloaded
You have 22 packages (1.2%) that are unsupported

```

---

### Post by mörgæs on 2019-12-15
You could try [Debian]("https://ubuntuforums.org/showthread.php?t=2130640&page=22&p=13902890&viewfull=1#post13902890"). Lightweight and fully supported.

---

### Post by j2ee on 2019-12-15
> **mörgæs said:**
> You could try [Debian]("https://ubuntuforums.org/showthread.php?t=2130640&page=22&p=13902890&viewfull=1#post13902890"). Lightweight and fully supported.


This should be too complicated for me now, I think I will try Linux Mint Debian version.

---

### Post by Dennis N on 2019-12-15
Another nice distro that I did not think of earlier is MX Linux, which has a current 32-bit version. I liked it when I reviewed it about a year ago.
[https://mxlinux.org/download-links/](https://mxlinux.org/download-links/)
By default, it came pretty much ready to roll. Debian is a free software stickler, and you have some amount of "customizing" to do there.

---

### Post by poorguy on 2019-12-15
I agree MX-19 Linux is an excellent choice.

[https://mxlinux.org/](https://mxlinux.org/)

---

### Post by Topsiho on 2019-12-15
Try Q4Os.
I have it on my 32-bit 11+ year old netbook, it's nice and  as far as  can see, it works well. Imitates the old KDE3 desktop!
Topsiho

---

### Post by TheFu on 2019-12-15
+1 for debian, just install a light WM and no DE at all.  No need for any DE.

---

