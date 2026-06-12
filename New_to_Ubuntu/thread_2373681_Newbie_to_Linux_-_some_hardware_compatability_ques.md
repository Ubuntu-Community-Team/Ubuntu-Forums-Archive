---
title: "Newbie to Linux - some hardware compatability questions"
date: 2017-10-08
forum: New to Ubuntu
---

### Post by chaoticbob on 2017-10-08
Hi. First post - apologies if the question I'm going to ask have been answered 10^6 times before (I expect so!) but this looks like a big site and it would take me ages to search.

My reason for coming here, like many before me I imagine, is that I am  getting increasingly frustrated with MS Windows. W10 is the last straw.  It seems to be the hated paperclip writ large. I'm after an OS which  does what I tell it (even if it's rm -r * - I'll take the risk!), not what it thinks I want to do.

I've made half-hearted attempts to migrate before, but have been defeated by hardware problems. This is the setup I want to change:

Low end HP laptop running Win10 64-bit on an Intel 382SU Pentium @ 1.9GHz with 4GB RAM, 1TB disk with 617 GB free.

Realtek RTL8732 802.11 bgn Wi-Fi adapter

Ancient Netgear router - due for replacement

USB Audio (headphone socket on machine knackered)

HP DVDRW DU8A6HS  DVD reader/writer

Canon MG5650 wireless printer/scanner (a generic Linux driver is available on the Canon website).

So the question is - can I make these things work with Ubuntu reasonably easily, or is it going to be a steep learning curve? I 've had a lot of experience with Sun/Solaris machines at work, so Unix isn't a problem, it's more about getting hardware to work.

I really hope I can get back to a clean OS for home use.

Regards, Rob

---

### Post by jeremy31 on 2017-10-08
You can try it before installing.  Some newer HP laptops have only one wireless antenna on the rtl8723be card so you might need to use the ant_sel parameter for the rtl8723be module

---

### Post by DuckHook on 2017-10-08
> **chaoticbob said:**
> …I'm after an OS which  does what I tell it (even if it's rm -r * - I'll take the risk!), not what it thinks I want to do.Well… you've certainly chosen the right one, then. Linux won't molly-coddle you.> …I really hope I can get back to a clean OS for home use.
The definition of "clean OS" is very personal and therefore both vague and ambiguous. The last LTR of Ubuntu proper is 16.04. However, Ubuntu has announced the end of Unity development, which is currently the DE in Ubuntu proper. Therefore, in the interest of "clean OS", you may prefer one of the other flavours, especially Ubuntu-Gnome, which Ubuntu proper will be transitioning to in future. Some would recommend one of the lighter flavours: Xubuntu, Lubuntu, Mate or Budgie (if by "clean", you mean "lighter").
> **jeremy31 said:**
> You can try it before installing…+1

@chaoticbob

The usual (good) advice for situations like yours is to run a LiveUSB session. That will quickly show you whether your equipment will work out of the box or not.

---

### Post by Mark Phelps on 2017-10-09
The hardship of switching over to Linux rests in two areas: drivers and apps.

Regarding drivers, running in Live mode will see how well the kernel detects your hardware and installs working drivers.  Any hardware that does not work is then going to range from simple (if they provide Linux drivers) to impossible (there are no Linux drivers) to fix.

Regarding apps, the ones most commonly used in Windows (e.g., Edge, Internet Explorer, MS Office) generally do NOT work well, or in many cases, not at ALL, in Linux --despite claims about stuff like Wine and Play on Linux.  So, there is going to be some learning involved in using different apps to do much the same stuff.  If you're willing to do that, then great; but if you plan on continuing to use Windows Apps, then Linux is the wrong choice.

---

### Post by chaoticbob on 2017-10-09
Thanks for replies. 

Jeremy31 - sounds good,from your and  DuckHook's suggestions it seems that I should be able to run Ubuntu from  a USB stick, so that's the best way forward.

DuckHook -  apologies for my 'vague and ambiguous' use of the word 'clean'. Guilty  as charged! When I posted I was annoyed because W10 seems to have  installed Word on my machine and set it as the default app to read .doc  files (no doubt with financial consequences in the pipeline!) rather  than OpenOffice which is what I normally use. Seemed a bit of a dirty  trick, hence the inapproriate use of 'clean'. Thanks for your suggestion  of LiveUSB, which I shall investigate.

Mark - thanks for  clarifying the areas of difficulty in migrating. I don't use MS apps  more than necessary - main things for me Firefox/Thunderbird,  OpenOffice, GIMP, Maple, GCC, all of which which should run fine in  Linux (I think). It's getting the hardware to work reliably with the OS  that is more of a problem.

I'll root around for instructions as  to how to get make the LiveUSB thing work, but if anyone can give me a  pointer to instructions, that would be good.

Thanks again for your help, Robin

---

### Post by DuckHook on 2017-10-09
> **chaoticbob said:**
> …apologies for my 'vague and ambiguous' use of the word 'clean'.Apologies not remotely necessary. My comments were not meant reproachfully; just factually. Because all 'buntu flavours cost you only the price of your data usage, you may wish to try them all out in LiveUSB form to see which one best suits you.> I'll root around for instructions as  to how to get make the LiveUSB thing work, but if anyone can give me a  pointer to instructions, that would be good.This might help: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0)

---

### Post by oldrocker99 on 2017-10-10
One thing I have found, using Ubuntu since 8.04, is that it "just works" on just about **any** computer made in the last five years, and will run very quickly. I personally highly recommend Ubuntu MATE, which IMHO is the awesomest distro I have ever used. Period.

And welcome to the superior world of Linux!

---

### Post by chaoticbob on 2017-10-10
> **DuckHook said:**
> Apologies not remotely necessary. My comments were not meant reproachfully; just factually. Because all 'buntu flavours cost you only the price of your data usage, you may wish to try them all out in LiveUSB form to see which one best suits you.This might help: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0)

Many thanks. I followed the instructions on your link, and all went well. I downloaded the latest LTS version of Ubuntu and it booted fine from the stick. Looking at settings/network, it found my wireless network OK and connected, but when I tried Firefox it was terribly slow and I was getting 'network disconnected' then 'network connected' popups every 30 seconds or so. 

If anyone can point me towards a diagnosis/resolution of this problem I'd be grateful - I really want to make this work! I didn't really understand Jeremy's comment about possible problems with antenna settings - could that be the cause?

Oldrocker - thanks for your welcome!

Rob

---

### Post by oldfred on 2017-10-11
See post #2.

May be better then to post a new thread since specific issue. Include in your title more details.
And post in this sub-forum.networking &  Wireless.
[https://ubuntuforums.org/forumdisplay.php?f=336](https://ubuntuforums.org/forumdisplay.php?f=336)

And read the "sticky" threads & run the script recommended. 
Those that help in that sub-form know a lot of details of wireless type issues.
One of which may be jeremy31. Also link to script in his post.

---

### Post by HermanAB on 2017-10-11
My usual advice is to install Linux and make a Virtualbox VM of Windows XP with the virtual network interface disabled for your legacy applications.  Then you can run Linux for most things and use Windows in a Window for MS Office or Quickbooks.

---

### Post by SeijiSensei on 2017-10-11
> **chaoticbob said:**
> If anyone can point me towards a diagnosis/resolution of this problem I'd be grateful - I really want to make this work! I didn't really understand Jeremy's comment about possible problems with antenna settings - could that be the cause?

Possibly, yes.  From [https://bbs.archlinux.org/viewtopic.php?id=208472](https://bbs.archlinux.org/viewtopic.php?id=208472)

> Apparently, the rtl8723be chipset supports dual-antenna-wifi, but some manufacturers only build one physical antenna into their products. The windows driver seems to autoselect an antenna in this case, whereas the linux driver just doesn't know that one antenna is disconnected

That refers to a different Realtek model than yours, but the problem is likely the same.  HP laptops are known for having only one antenna connected.

You can do some tests like this:

First, run the command "lsmod | grep rtl" to see the name of the driver module. It's probably called "rtl8732be".
```

sudo rmmod rtl8732be
sudo modprobe rtl8732be ant_sel=1
sudo iwlist wlan0 scan
sudo rmmod rtl8732be
sudo modprobe rtl8732be ant_sel=2
sudo iwlist wlan0 scan

```
That unloads the driver, reloads it with antenna 1, and scans for wifi hotspots.  Then it unloads and reloads the driver with antenna 2 and reruns the scan.

If you find one of the antennas works much better, you can force the appropriate ant_sel option to be loaded at boot with:

```
echo "options rtl87323be ant_sel=1" | sudo tee /etc/modprobe.d/rtl8732beant.conf
```

using "ant_sel=1" or "ant_sel=2" as appropriate.

---

### Post by chaoticbob on 2017-10-12
Thanks for your clear and detailed instructions SeijiSensei. When I tried to scan for available networks I got:

```

$ sudo iwlist wlan0 scan
wlan0        Interface doesn't support scanning.

```

However, I tried Firefox with both settings of the ant_sel parameter - ant_sel=2, no dice, ant_sel=1, immediate connection and fast (way quicker than under W10 actually) page downloads and no dropouts so far. So I'll mark this as solved, though I'd still like to understand why the scan didn't work.

Many thanks to all who have offered advice, much appreciated .
Bob

---

### Post by jeremy31 on 2017-10-12
If you are using Ubuntu, post results from terminal for ```
lspci -nnk | grep -iA3 net
```

---

### Post by chaoticbob on 2017-10-12
> **jeremy31 said:**
> If you are using Ubuntu, post results from terminal for ```
lspci -nnk | grep -iA3 net
```

```
 
ubuntu@ubuntu:~$ lspci -nnk | grep -iA3 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:80c1]
    Kernel driver in use: r8169
    Kernel modules: r8169
0d:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:804c]
    Kernel driver in use: rtl8723be
    Kernel modules: rtl8723be


```

Thanks, Bob

---

### Post by SeijiSensei on 2017-10-12
> Kernel modules: rtl8723be

Earlier you said you had an rtl8732, so in the commands I gave you would use "rtl8723be" instead.

---

### Post by chaoticbob on 2017-10-12
> **SeijiSensei said:**
> Earlier you said you had an rtl8732, so in the commands I gave you would use "rtl8723be" instead.

Yes, sorry, my bad, typo - I od that sometimes. "lsmod | grep rtl" revealed that it was actually rtl8723be, so I used that in subsequent commands.
Thanks again, connection now seems stable, a couple of hours without a dropout. Brilliant - it's like coming home again, the furniture has changed, but it's the same place.
Rob.

---

