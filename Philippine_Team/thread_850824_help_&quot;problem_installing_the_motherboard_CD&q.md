---
title: "help &quot;problem installing the motherboard CD&quot;"
date: 2008-07-06
forum: Philippine Team
---

### Post by bagito on 2008-07-06
kakabili ko lang po ng bagong Rig po...
nainstall ko po yung ubuntu ng walang problem...
ngaun po ang problem ko di ko alam pano po iinstall yung chipset at yung mga drivers. hindi naman po support ng ubuntu yung mga *.exe pang windows po kasi sila...anu po gagawin ko?

---

### Post by pendletone on 2008-07-06
Hi bagito, nde mo na kelangan mag-install ng chipset drivers sa motherboard cd mo -- Ubuntu will run right off the bat without it. Pero kung may linux driver ang motherboard vendor mo sa site nila, you can try installing that.

---

### Post by bagito on 2008-07-06
i see po...e pano po yung sa iba kong drivers?? will ubuntu take care of them as well?? and how can i update them?salamat po..

---

### Post by jeffimperial on 2008-07-06
> **bagito said:**
> i see po...e pano po yung sa iba kong drivers?? will ubuntu take care of them as well?? and how can i update them?salamat po..
In most cases, Ubuntu works out of the box. Meron mga exceptions kapag super exotic ng iyong mga device. Pero karamihan sa kanila, Ubuntu takes care of. Sa kaso ko, lahat ng devices ko di na kinailangan ang drivers, save for my TV card (Prolink BT878, detected sya kaso di ko alam kung pano paganahin :) )

Anyways, kapag meron kang na-encounter na device sa system mo na hindi gumagana, tanong ka lang ulit dito :D

---

### Post by bagito on 2008-07-06
ah..so pag ganoon po wala na ako dapat gawin..di ko narin need magupgrade pa ng drivers?? auto update na po b siya? nakita ko nga wala mga pang linux driver ang intel execpt sa bios nila..kakacheck ko lng hehehe...ayun po...salamat po uli.

---

### Post by pendletone on 2008-07-06
well most of your hardware devices *should* work, but just like jeffimperial pointed out -- merong mga devices na kelangan ng konting "kalikot" para mapagana.

ang pinaka-common concern ng karamihan e yung tungkol sa video card driver. basically, some cards work better than others pag dating sa 3d acceleration. while some don't have 3d capabilities in linux at all.

don't worry about driver upgrades, ubuntu will do it for you automatically kung meron mang upgrades. :)

---

### Post by loell on 2008-07-06
pwede mo rin ipaalam sa lahat ang rig mo :)

sa terminal, 

```
lspci
```

copy / paste mo lang ang output dito.

---

### Post by bagito on 2008-07-06
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)


eto po Rig ko...ala pa ako video card bibili pa lang po maya...un nmn susunod kong popobremahin...

kuya tanong lang po..Bakit yung nreread ng ubuntu 3GB lng daw memory ko. e 4GB po dpt yan...i'm expecting na mababasa po ng ubuntu mga 3.8gb-3.9gb pero 3.2gb lang po yung nakikita...panu po yun?

---

### Post by loell on 2008-07-06
may intel graphics processor ka na, baka pwede mo na e-enable yung **(special) este desktop** effects without having to buy a graphics card. ;)  


hindi nakita yung 4 Gb mem mo kasi pag 32 bit ganyan talaga ang limitation nya, kung sa ubuntu 64 bit at kung ang rig mo ay pang 64 bit makikita nya yung 4 gb ram mo. 

may work around din para makita nang 32 bit yung 4 gb ram na walang bawas. :D , asan ba yun.. :D

---

### Post by bagito on 2008-07-06
pano po ba malalaman kng pang 64-bit yung rig ko?gusto ko kasi tlga maoptimize yung specs ko e..sayayng naman kasi eh..huhu...wala na ba ibang way?

---

### Post by loell on 2008-07-06
try mo tong command na'to,

```
dmesg | grep CPU
```

---

### Post by bagito on 2008-07-06
[    0.000000] Initializing CPU#0
[   11.357486] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   11.437599] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
[   11.437610] CPU: L1 I cache: 32K, L1 D cache: 32K
[   11.437611] CPU: L2 cache: 4096K
[   11.437613] CPU: Physical Processor ID: 0
[   11.437614] CPU: Processor Core ID: 0
[   11.437616] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000000
[   11.693174] CPU0: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[   11.703995] Initializing CPU#1
[   11.780921] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
[   11.780927] CPU: L1 I cache: 32K, L1 D cache: 32K
[   11.780928] CPU: L2 cache: 4096K
[   11.780930] CPU: Physical Processor ID: 0
[   11.780930] CPU: Processor Core ID: 1
[   11.780931] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000000
[   11.781572] CPU1: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[   11.792399] Initializing CPU#2
[   11.872775] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
[   11.872781] CPU: L1 I cache: 32K, L1 D cache: 32K
[   11.872782] CPU: L2 cache: 4096K
[   11.872783] CPU: Physical Processor ID: 0
[   11.872784] CPU: Processor Core ID: 2
[   11.872785] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000000
[   11.873392] CPU2: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[   11.884005] Initializing CPU#3
[   11.960634] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
[   11.960640] CPU: L1 I cache: 32K, L1 D cache: 32K
[   11.960641] CPU: L2 cache: 4096K
[   11.960643] CPU: Physical Processor ID: 0
[   11.960643] CPU: Processor Core ID: 3
[   11.960644] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000000
[   11.961231] CPU3: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[   12.108460] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   12.128460] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[   12.148496] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[   12.168479] Brought up 4 CPUs
[   12.168515] CPU0 attaching sched-domain:
[   12.168524] CPU1 attaching sched-domain:
[   12.168531] CPU2 attaching sched-domain:
[   12.168538] CPU3 attaching sched-domain:
[   12.212307] Switched to high resolution mode on CPU 0
[   12.212370] Switched to high resolution mode on CPU 1
[   12.212576] Switched to high resolution mode on CPU 2
[   12.212640] Switched to high resolution mode on CPU 3
[   14.352444] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   14.352618] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   14.352808] ACPI: CPU2 (power states: C1[C1] C2[C2] C3[C3])
[   14.353011] ACPI: CPU3 (power states: C1[C1] C2[C2] C3[C3])

eto po output...panu ko po mabasa jan kung 64bit po?hmm..

---

### Post by rjmdomingo2003 on 2008-07-06
> **bagito said:**
> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

Kung sakali lang na di gumana yung sound, try to install linux-386 using synaptic.
From the terminal:
```
sudo synaptic
```

then, reboot.

Nice rig! Oooooh, core 2 quad....:guitar:

---

### Post by loell on 2008-07-06
yup, pang 64 bit na rig nga 'to :)

```
CPU0: Intel(R) Core(TM)2 Quad CPU Q6600 @ 2.40GHz
```

---

### Post by bagito on 2008-07-06
ok na po yung audio ko...ang problem ko ng lang po gusto ko mgamit yung memory ko to the max...3.2gb lng nkikita po kasi eh...salamat po s pagapreciate=D

edi loell anu pede ko gawin para po maoptimize yung mem ko?reinstall po ako OS?anung OS nmn po?

---

### Post by loell on 2008-07-06
Ubuntu 64 bit sana, para mas-optimize at para talaga sayong specs

pero, kung ayaw mong mag install nang 64 bit, pwede rin naman yang 32 bit muna ang gamitin mo,

para naman makita mo yung 4 GB ram mo sa 32 bit install mo

subukan mo ito

[http://samiux.wordpress.com/2008/06/15/use-more-than-3gb-ram-on-32-bit-ubuntu-804/]("http://samiux.wordpress.com/2008/06/15/use-more-than-3gb-ram-on-32-bit-ubuntu-804/")

kahit nga lang 3 gig eh, di mo naman yan magagamit lahat :)
kadalasan kasi magaan kasi ang apps sa linux :)

---

### Post by bagito on 2008-07-06
tnx po sa help...dami ko nalaman ngayong araw na to...hehe...salamat po=D

---

### Post by dodimar on 2008-07-06
OT...

Pano ba malaman kung 64 bit capable ang CPU?

---

### Post by loell on 2008-07-06
Walang ano man. :)

sige explore ka lang nang explore dyan. :KS

---

### Post by pendletone on 2008-07-06
> **dodimar said:**
> OT...

Pano ba malaman kung 64 bit capable ang CPU?

Sa mga common processors, alam ko anything na Intel Core 2 (Duo, Quad, Extreme) ay 64 bit capable. Sa AMD naman, anything na may '64' sa name (Athlon 64, X2, FX, Opteron, Turion 64, etc.) Am not sure pero meron din atang 64 bit extension ang Intel sa newer Celeron and Pentium 4 models.

---

### Post by dodimar on 2008-07-06
> **pendletone said:**
> Sa mga common processors, alam ko anything na Intel Core 2 (Duo, Quad, Extreme) ay 64 bit capable. Sa AMD naman, anything na may '64' sa name (Athlon 64, X2, FX, Opteron, Turion 64, etc.) Am not sure pero meron din atang 64 bit extension ang Intel sa newer Celeron and Pentium 4 models.

ah... okay.. tnx..... :)

---

