---
title: "Desktop or server"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by GROMS on 2008-06-28
Here is the new hardware I have:
  Asus Striker MB with 8 GB mem and Intel Core 2 quad Q6600 CPU.
  3ware SATA controller with 4 - 500 GB SATA drives.
  XFXforce GF7950 video card.
  Acer AL2416M monitor
  NEC Black 16X DVD+R Burner

Unit has NEVER been powered up and there is nothing on the hard drives.

What I want on it:

  * OS that will let me use it as a workstation and server (Pref 64 bit that can run 32 bit).
  * Have Pearl, PHP, Python, Apachie webserver, MySQL, Java,
    Ruby, C++, Ajax and more.
  * Set up the hard drives Raid 1.
  * Be the center of a VPN.
  * have all the usual workstation stuff.

Now then, can I do this with the desktop release or do I need to get the server code??

In either case, I think I need to get the new drivers for the video card. Being a MS want to get away, do I need it before I do the install or after> If before, do I just download it onto a CD and use it during the install?

TIA

---

### Post by hyper_ch on 2008-06-28
well, use 64bit desktop (so you can use all the 8gb ram out of the box) and install then apache and the other webserver stuff...

---

### Post by MasterJS on 2008-06-28
As said before, use the 64bit Ubuntu. I'd say just use the desktop one. The difference between the two is that the server edition has less programs installed by default and doesn't contain a graphical interface. The nice thing about Ubuntu, and Linux in general, is that your not limited to what the OS starts with. You can install everything you want after the installation.
About the video card, if Ubuntu doesn't already have the correct driver, Ubuntu will start off with an opensource generic driver. This will allow you to use your graphics card, maybe not to the fullest. You'll just have to install the correct closed-source driver after if you want.

---

### Post by hyper_ch on 2008-06-28
masterjs: also the kernel is different between desktop and server ;)

---

### Post by GROMS on 2008-06-28
Hyper_cg,

Thanks for the info, wasn't sure if could install Apachie etc. on desktop.

Get Rid Of Micro Soft

---

### Post by hyper_ch on 2008-06-28
sure you can install apache on a desktop... but generally if you want to operate a real server you won't install a gui on it and use the server optimized "server kernel".

---

### Post by defrex on 2008-06-28
:KS sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

What I do is run Ubuntu desktop with vmware and ubuntu server as a guest. That way you get the best of both worlds! You certainly have enough RAM...

---

### Post by hyper_ch on 2008-06-28
and what would be the benefit of that?

---

### Post by wagb278 on 2008-06-28
I will throw my 2-cents in, if it helps.

Install the 64-bit desktop then install the LAMP suite, and any other applications you desire. 

On an old 32-bit machine I installed the server and then the desktop on top of that (it works fine). But on a newer 64-bit machine, I went the other route (Desktop first then LAMP) and that worked too.  But the second sequence was smoother.

If I might suggest - get a Live-CD of GParted and configure your dives as the first step.  Then the Ubuntu install uses the drive configuration. Doing this first helped me.

Good Luck

---

### Post by GROMS on 2008-06-28
Thank you MasterJS. Most helpful.

---

### Post by GROMS on 2008-06-28
> **wagb278 said:**
> I will throw my 2-cents in, if it helps.

Install the 64-bit desktop then install the LAMP suite, and any other applications you desire. 

On an old 32-bit machine I installed the server and then the desktop on top of that (it works fine). But on a newer 64-bit machine, I went the other route (Desktop first then LAMP) and that worked too.  But the second sequence was smoother.

If I might suggest - get a Live-CD of GParted and configure your dives as the first step.  Then the Ubuntu install uses the drive configuration. Doing this first helped me.

Good Luck

LAMP?? GParted?? and from where??

---

### Post by defrex on 2008-06-28
> **hyper_ch said:**
> and what would be the benefit of that?

For me? I only want a server running when I'm doing development. While I could fiddle with apache to make it not start at boot or put /etc/init.d/apache2 stop in the sessions manager or something it all feels a little kludgey to me. Plus it's nice to give each project I'm working on it's own server.

It's certainly not the best option for performance, but
it is the best option for convenience. And if the OP is using one machine for a server and a workstation (like me) I assume they're not terribly concerned with scalability.

---

### Post by GROMS on 2008-06-28
Ok, dumb dumb just looked up LAMP - got that part.

---

### Post by GROMS on 2008-10-31
> **wagb278 said:**
> I will throw my 2-cents in, if it helps.

Install the 64-bit desktop then install the LAMP suite, and any other applications you desire. 

On an old 32-bit machine I installed the server and then the desktop on top of that (it works fine). But on a newer 64-bit machine, I went the other route (Desktop first then LAMP) and that worked too.  But the second sequence was smoother.

If I might suggest - get a Live-CD of GParted and configure your dives as the first step.  Then the Ubuntu install uses the drive configuration. Doing this first helped me.

Good Luck

Got a little sidetracked so .... any way, Have 8.04 desktop up and updated. Looked at Apache site and they gave the command:

 sudo tasksel install lamp-server

to install Apache2,PHP 5 and MYSQL 5. But there is a lot of reference to "server" version of Ubuntu. From the responses here I 'assume' this is ok???
But, is the command above correct nd should it be executed in the Synamptic Package Manager??
If I want to add Pearl, Ruby and Python, How would I do that??
This is a steep learning curve and all the help for this old man is greatly appreciated. 

I think I got the 4 drives mirrored right. did the command:
  sudo lshw -html > sysinfo.html
and got a list of the system. Under * - disk:0, it shows name as /dev/sda the volume and the 2 volumes (0 and 1). Also says its mounted. For * - disk:1  it shows /dev/sdb but doesn't say anything about it being mounted. In Places>computer it shows a floppy,scsi,dvd drives and file system.The properties of files ystem gives the size on on mirror. Properties of the scsi drive shows 'Type unknown'. So I'm not sure if I have access to the second mirror or is I have to mount the scsi and assume it is pointing to sdb (second mirror SATAs).
Here is text of html file:

<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
<head>
<meta name="generator"  content="lshw-B.02.12.01">
<style type="text/css">
  .first {font-weight: bold; margin-left: none; padding-right: 1em;vertical-align: top; }
  .second {padding-left: 1em; width: 100%; vertical-align: center; }
  .id {font-family: monospace;}
  .indented {margin-left: 2em; border-left: dotted thin #dde; padding-bottom: 1em; }
  .node {border: solid thin #ffcc66; padding: 1em; background: #ffffcc; }
  .node-unclaimed {border: dotted thin #c3c3c3; padding: 1em; background: #fafafa; }
  .node-disabled {border: solid thin #f55; padding: 1em; background: #fee; }
</style>
<title>linux-64</title>
</head>
<body>
<div class="indented">
<table width="100%" class="node" summary="attributes of linux-64">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">linux-64</div></td></tr></thead>
 <tbody>
    <tr><td class="first">description: </td><td class="second">Desktop Computer</td></tr>
    <tr><td class="first">product: </td><td class="second">System Product Name</td></tr>
    <tr><td class="first">vendor: </td><td class="second">System manufacturer</td></tr>
    <tr><td class="first">version: </td><td class="second">System Version</td></tr>
    <tr><td class="first">serial: </td><td class="second">System Serial Number</td></tr>
    <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
    <tr><td class="first">capabilities: </td><td class="second">smbios-2.4 dmi-2.4 smp-1.4 smp</td></tr>
    <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of linux-64"><tr><td class="sub-first"> boot</td><td>=</td><td>normal</td></tr><tr><td class="sub-first"> chassis</td><td>=</td><td>desktop</td></tr><tr><td class="sub-first"> cpus</td><td>=</td><td>0</td></tr><tr><td class="sub-first"> uuid</td><td>=</td><td>48FB6A62-5599-DB11-A814-2E05651390BF</td></tr></table></td></tr>
 </tbody></table></div>
<div class="indented">
        <div class="indented">
    <table width="100%" class="node" summary="attributes of core">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">core</div></td></tr></thead>
 <tbody>
       <tr><td class="first">description: </td><td class="second">Motherboard</td></tr>
       <tr><td class="first">product: </td><td class="second">StrikerExtreme</td></tr>
       <tr><td class="first">vendor: </td><td class="second">ASUSTeK Computer INC.</td></tr>
       <tr><td class="first">physical id: </td><td class="second"><div class="id">0</div></td></tr>
       <tr><td class="first">version: </td><td class="second">1.XX</td></tr>
       <tr><td class="first">serial: </td><td class="second">123456789000</td></tr>
 </tbody>    </table></div>
<div class="indented">
              <div class="indented">
       <table width="100%" class="node" summary="attributes of firmware">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">firmware</div></td></tr></thead>
 <tbody>
          <tr><td class="first">description: </td><td class="second">BIOS</td></tr>
          <tr><td class="first">vendor: </td><td class="second">Phoenix Technologies, LTD</td></tr>
          <tr><td class="first">physical id: </td><td class="second"><div class="id">0</div></td></tr>
          <tr><td class="first">version: </td><td class="second">ASUS StrikerExtreme ACPI BIOS Revision 1203 (06/04/2007)</td></tr>
          <tr><td class="first">size: </td><td class="second">128KiB</td></tr>
          <tr><td class="first">capacity: </td><td class="second">960KiB</td></tr>
          <tr><td class="first">capabilities: </td><td class="second">pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification</td></tr>
 </tbody>       </table></div>
       </div>
<div class="indented">
              <div class="indented">
       <table width="100%" class="node" summary="attributes of cpu">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">cpu</div></td></tr></thead>
 <tbody>
          <tr><td class="first">description: </td><td class="second">CPU</td></tr>
          <tr><td class="first">product: </td><td class="second">Intel(R) Core(TM)2 Quad CPU           @ 2.40GHz</td></tr>
          <tr><td class="first">vendor: </td><td class="second">Intel Corp.</td></tr>
          <tr><td class="first">physical id: </td><td class="second"><div class="id">5</div></td></tr>
          <tr><td class="first">bus info: </td><td class="second"><div class="id">cpu@0</div></td></tr>
          <tr><td class="first">version: </td><td class="second">Intel(R) Core(TM)2 Quad CPU           @ 2.40GHz</td></tr>
          <tr><td class="first">slot: </td><td class="second">Socket 775</td></tr>
          <tr><td class="first">size: </td><td class="second">2400MHz</td></tr>
          <tr><td class="first">capacity: </td><td class="second">3800MHz</td></tr>
          <tr><td class="first">width: </td><td class="second">64 bits</td></tr>
          <tr><td class="first">clock: </td><td class="second">266MHz</td></tr>
          <tr><td class="first">capabilities: </td><td class="second">fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm</td></tr>
 </tbody>       </table></div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of cache:0">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">cache:0</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">L1 cache</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">b</div></td></tr>
             <tr><td class="first">slot: </td><td class="second">L1 Cache</td></tr>
             <tr><td class="first">size: </td><td class="second">32KiB</td></tr>
             <tr><td class="first">capacity: </td><td class="second">32KiB</td></tr>
             <tr><td class="first">capabilities: </td><td class="second">synchronous internal write-back data</td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of cache:1">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">cache:1</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">L2 cache</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">c</div></td></tr>
             <tr><td class="first">slot: </td><td class="second">L2 Cache</td></tr>
             <tr><td class="first">size: </td><td class="second">4MiB</td></tr>
             <tr><td class="first">capacity: </td><td class="second">4MiB</td></tr>
             <tr><td class="first">capabilities: </td><td class="second">synchronous internal write-back unified</td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node-disabled" summary="attributes of cache:2">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id"><font color="gray">cache:2</font></div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">L3 cache</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">d</div></td></tr>
             <tr><td class="first">slot: </td><td class="second">L3 Cache</td></tr>
             <tr><td class="first">capabilities: </td><td class="second">synchronous internal varies</td></tr>
 </tbody>          </table></div>
          </div>
       </div>
<div class="indented">
              <div class="indented">
       <table width="100%" class="node" summary="attributes of memory">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">memory</div></td></tr></thead>
 <tbody>
          <tr><td class="first">description: </td><td class="second">System Memory</td></tr>
          <tr><td class="first">physical id: </td><td class="second"><div class="id">41</div></td></tr>
          <tr><td class="first">slot: </td><td class="second">System board or motherboard</td></tr>
          <tr><td class="first">size: </td><td class="second">8GiB</td></tr>
 </tbody>       </table></div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of bank:0">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">bank:0</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">DIMM 800 MHz (1.2 ns)</td></tr>
             <tr><td class="first">product: </td><td class="second">None</td></tr>
             <tr><td class="first">vendor: </td><td class="second">None</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">0</div></td></tr>
             <tr><td class="first">serial: </td><td class="second">None</td></tr>
             <tr><td class="first">slot: </td><td class="second">DIMM_A1</td></tr>
             <tr><td class="first">size: </td><td class="second">2GiB</td></tr>
             <tr><td class="first">clock: </td><td class="second">800MHz (1.2ns)</td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of bank:1">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">bank:1</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">DIMM 800 MHz (1.2 ns)</td></tr>
             <tr><td class="first">product: </td><td class="second">None</td></tr>
             <tr><td class="first">vendor: </td><td class="second">None</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">1</div></td></tr>
             <tr><td class="first">serial: </td><td class="second">None</td></tr>
             <tr><td class="first">slot: </td><td class="second">DIMM_A2</td></tr>
             <tr><td class="first">size: </td><td class="second">2GiB</td></tr>
             <tr><td class="first">clock: </td><td class="second">800MHz (1.2ns)</td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of bank:2">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">bank:2</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">DIMM 800 MHz (1.2 ns)</td></tr>
             <tr><td class="first">product: </td><td class="second">None</td></tr>
             <tr><td class="first">vendor: </td><td class="second">None</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">2</div></td></tr>
             <tr><td class="first">serial: </td><td class="second">None</td></tr>
             <tr><td class="first">slot: </td><td class="second">DIMM_B1</td></tr>
             <tr><td class="first">size: </td><td class="second">2GiB</td></tr>
             <tr><td class="first">clock: </td><td class="second">800MHz (1.2ns)</td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of bank:3">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">bank:3</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">DIMM 800 MHz (1.2 ns)</td></tr>
             <tr><td class="first">product: </td><td class="second">None</td></tr>
             <tr><td class="first">vendor: </td><td class="second">None</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">3</div></td></tr>
             <tr><td class="first">serial: </td><td class="second">None</td></tr>
             <tr><td class="first">slot: </td><td class="second">DIMM_B2</td></tr>
             <tr><td class="first">size: </td><td class="second">2GiB</td></tr>
             <tr><td class="first">clock: </td><td class="second">800MHz (1.2ns)</td></tr>
 </tbody>          </table></div>
          </div>
       </div>
<div class="indented">
              <div class="indented">
       <table width="100%" class="node" summary="attributes of pci">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">pci</div></td></tr></thead>
 <tbody>
          <tr><td class="first">description: </td><td class="second">Host bridge</td></tr>
          <tr><td class="first">product: </td><td class="second">C55 Host Bridge</td></tr>
          <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
          <tr><td class="first">physical id: </td><td class="second"><div class="id">100</div></td></tr>
          <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:00.0</div></td></tr>
          <tr><td class="first">version: </td><td class="second">a2</td></tr>
          <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
          <tr><td class="first">clock: </td><td class="second">66MHz</td></tr>
 </tbody>       </table></div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node-unclaimed" summary="attributes of memory:0">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id"><font color="gray">memory:0</font></div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">RAM memory</td></tr>
             <tr><td class="first">product: </td><td class="second">C55 Memory Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">0.1</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:00.1</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a1</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz (15.2ns)</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of memory:0"><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node-unclaimed" summary="attributes of memory:1">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id"><font color="gray">memory:1</font></div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">RAM memory</td></tr>
             <tr><td class="first">product: </td><td class="second">C55 Memory Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">0.2</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:00.2</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a1</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz (15.2ns)</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of memory:1"><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node-unclaimed" summary="attributes of memory:2">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id"><font color="gray">memory:2</font></div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">RAM memory</td></tr>
             <tr><td class="first">product: </td><td class="second">C55 Memory Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">0.3</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:00.3</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a1</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz (15.2ns)</td></tr>
             <tr><td class="first">capabilities: </td><td class="second">bus_master</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of memory:2"><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node-unclaimed" summary="attributes of memory:3">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id"><font color="gray">memory:3</font></div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">RAM memory</td></tr>
             <tr><td class="first">product: </td><td class="second">C55 Memory Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">0.4</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:00.4</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a1</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz (15.2ns)</td></tr>
             <tr><td class="first">capabilities: </td><td class="second">bus_master</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of memory:3"><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node-unclaimed" summary="attributes of memory:4">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id"><font color="gray">memory:4</font></div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">RAM memory</td></tr>
             <tr><td class="first">product: </td><td class="second">C55 Memory Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">0.5</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:00.5</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a2</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz (15.2ns)</td></tr>
             <tr><td class="first">capabilities: </td><td class="second">bus_master</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of memory:4"><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node-unclaimed" summary="attributes of memory:5">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id"><font color="gray">memory:5</font></div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">RAM memory</td></tr>
             <tr><td class="first">product: </td><td class="second">C55 Memory Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">0.6</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:00.6</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a1</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz (15.2ns)</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of memory:5"><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node-unclaimed" summary="attributes of memory:6">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id"><font color="gray">memory:6</font></div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">RAM memory</td></tr>
             <tr><td class="first">product: </td><td class="second">C55 Memory Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">0.7</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:00.7</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a1</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz (15.2ns)</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of memory:6"><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node-unclaimed" summary="attributes of memory:7">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id"><font color="gray">memory:7</font></div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">RAM memory</td></tr>
             <tr><td class="first">product: </td><td class="second">C55 Memory Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">1</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:01.0</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a1</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz (15.2ns)</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of memory:7"><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node-unclaimed" summary="attributes of memory:8">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id"><font color="gray">memory:8</font></div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">RAM memory</td></tr>
             <tr><td class="first">product: </td><td class="second">C55 Memory Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">1.1</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:01.1</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a1</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz (15.2ns)</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of memory:8"><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node-unclaimed" summary="attributes of memory:9">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id"><font color="gray">memory:9</font></div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">RAM memory</td></tr>
             <tr><td class="first">product: </td><td class="second">C55 Memory Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">1.2</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:01.2</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a1</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz (15.2ns)</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of memory:9"><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node-unclaimed" summary="attributes of memory:10">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id"><font color="gray">memory:10</font></div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">RAM memory</td></tr>
             <tr><td class="first">product: </td><td class="second">C55 Memory Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">1.3</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:01.3</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a1</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz (15.2ns)</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of memory:10"><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node-unclaimed" summary="attributes of memory:11">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id"><font color="gray">memory:11</font></div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">RAM memory</td></tr>
             <tr><td class="first">product: </td><td class="second">C55 Memory Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">1.4</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:01.4</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a1</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz (15.2ns)</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of memory:11"><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node-unclaimed" summary="attributes of memory:12">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id"><font color="gray">memory:12</font></div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">RAM memory</td></tr>
             <tr><td class="first">product: </td><td class="second">C55 Memory Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">1.5</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:01.5</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a1</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz (15.2ns)</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of memory:12"><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node-unclaimed" summary="attributes of memory:13">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id"><font color="gray">memory:13</font></div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">RAM memory</td></tr>
             <tr><td class="first">product: </td><td class="second">C55 Memory Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">1.6</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:01.6</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a1</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz (15.2ns)</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of memory:13"><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node-unclaimed" summary="attributes of memory:14">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id"><font color="gray">memory:14</font></div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">RAM memory</td></tr>
             <tr><td class="first">product: </td><td class="second">C55 Memory Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">2</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:02.0</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a1</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz (15.2ns)</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of memory:14"><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node-unclaimed" summary="attributes of memory:15">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id"><font color="gray">memory:15</font></div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">RAM memory</td></tr>
             <tr><td class="first">product: </td><td class="second">C55 Memory Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">2.1</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:02.1</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a1</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz (15.2ns)</td></tr>
             <tr><td class="first">capabilities: </td><td class="second">bus_master</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of memory:15"><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node-unclaimed" summary="attributes of memory:16">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id"><font color="gray">memory:16</font></div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">RAM memory</td></tr>
             <tr><td class="first">product: </td><td class="second">C55 Memory Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">2.2</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:02.2</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a1</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz (15.2ns)</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of memory:16"><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of pci:0">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">pci:0</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">PCI bridge</td></tr>
             <tr><td class="first">product: </td><td class="second">C55 PCI Express bridge</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">3</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:03.0</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a1</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second">pci pm msi ht pciexpress normal_decode bus_master cap_list</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of pci:0"><tr><td class="sub-first"> driver</td><td>=</td><td>pcieport-driver</td></tr></table></td></tr>
 </tbody>          </table></div>
<div class="indented">
                          <div class="indented">
             <table width="100%" class="node-unclaimed" summary="attributes of display">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id"><font color="gray">display</font></div></td></tr></thead>
 <tbody>
                <tr><td class="first">description: </td><td class="second">VGA compatible controller</td></tr>
                <tr><td class="first">product: </td><td class="second">G71 [GeForce 7950 GT]</td></tr>
                <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
                <tr><td class="first">physical id: </td><td class="second"><div class="id">0</div></td></tr>
                <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:01:00.0</div></td></tr>
                <tr><td class="first">version: </td><td class="second">a1</td></tr>
                <tr><td class="first">width: </td><td class="second">64 bits</td></tr>
                <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
                <tr><td class="first">capabilities: </td><td class="second">pm msi pciexpress vga_controller bus_master cap_list</td></tr>
                <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of display"><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr></table></td></tr>
 </tbody>             </table></div>
             </div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node-unclaimed" summary="attributes of memory:17">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id"><font color="gray">memory:17</font></div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">RAM memory</td></tr>
             <tr><td class="first">product: </td><td class="second">MCP55 Memory Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">9</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:09.0</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a1</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz (15.2ns)</td></tr>
             <tr><td class="first">capabilities: </td><td class="second">ht bus_master cap_list</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of memory:17"><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of isa">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">isa</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">ISA bridge</td></tr>
             <tr><td class="first">product: </td><td class="second">MCP55 LPC Bridge</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">a</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:0a.0</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a2</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second">isa bus_master</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of isa"><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of serial">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">serial</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">SMBus</td></tr>
             <tr><td class="first">product: </td><td class="second">MCP55 SMBus</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">a.1</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:0a.1</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a2</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second">pm cap_list</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of serial"><tr><td class="sub-first"> driver</td><td>=</td><td>nForce2_smbus</td></tr><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr><tr><td class="sub-first"> module</td><td>=</td><td>i2c_nforce2</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of usb:0">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">usb:0</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">USB Controller</td></tr>
             <tr><td class="first">product: </td><td class="second">MCP55 USB Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">b</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:0b.0</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a1</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second">pm ohci bus_master cap_list</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of usb:0"><tr><td class="sub-first"> driver</td><td>=</td><td>ohci_hcd</td></tr><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr><tr><td class="sub-first"> maxlatency</td><td>=</td><td>1</td></tr><tr><td class="sub-first"> mingnt</td><td>=</td><td>3</td></tr><tr><td class="sub-first"> module</td><td>=</td><td>ohci_hcd</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of usb:1">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">usb:1</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">USB Controller</td></tr>
             <tr><td class="first">product: </td><td class="second">MCP55 USB Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">b.1</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:0b.1</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a2</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second">debug pm ehci bus_master cap_list</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of usb:1"><tr><td class="sub-first"> driver</td><td>=</td><td>ehci_hcd</td></tr><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr><tr><td class="sub-first"> maxlatency</td><td>=</td><td>1</td></tr><tr><td class="sub-first"> mingnt</td><td>=</td><td>3</td></tr><tr><td class="sub-first"> module</td><td>=</td><td>ehci_hcd</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of ide:0">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">ide:0</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">IDE interface</td></tr>
             <tr><td class="first">product: </td><td class="second">MCP55 IDE</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">d</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:0d.0</div></td></tr>
             <tr><td class="first">logical name: </td><td class="second"><div class="id">scsi7</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a1</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second">ide pm bus_master cap_list emulated</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of ide:0"><tr><td class="sub-first"> driver</td><td>=</td><td>pata_amd</td></tr><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr><tr><td class="sub-first"> maxlatency</td><td>=</td><td>1</td></tr><tr><td class="sub-first"> mingnt</td><td>=</td><td>3</td></tr><tr><td class="sub-first"> module</td><td>=</td><td>pata_amd</td></tr></table></td></tr>
 </tbody>          </table></div>
<div class="indented">
                          <div class="indented">
             <table width="100%" class="node" summary="attributes of cdrom">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">cdrom</div></td></tr></thead>
 <tbody>
                <tr><td class="first">description: </td><td class="second">DVD-RAM writer</td></tr>
                <tr><td class="first">product: </td><td class="second">DVD RW AD-7190A</td></tr>
                <tr><td class="first">vendor: </td><td class="second">Optiarc</td></tr>
                <tr><td class="first">physical id: </td><td class="second"><div class="id">0.0.0</div></td></tr>
                <tr><td class="first">bus info: </td><td class="second"><div class="id">scsi@7:0.0.0</div></td></tr>
                <tr><td class="first">logical name: </td><td class="second"><div class="id">/dev/cdrom</div></td></tr>
                <tr><td class="first">logical name: </td><td class="second"><div class="id">/dev/dvd</div></td></tr>
                <tr><td class="first">logical name: </td><td class="second"><div class="id">/dev/scd0</div></td></tr>
                <tr><td class="first">logical name: </td><td class="second"><div class="id">/dev/sr0</div></td></tr>
                <tr><td class="first">logical name: </td><td class="second"><div class="id">/media/cdrom0</div></td></tr>
                <tr><td class="first">version: </td><td class="second">1.01</td></tr>
                <tr><td class="first">capabilities: </td><td class="second">removable audio cd-r cd-rw dvd dvd-r dvd-ram</td></tr>
                <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of cdrom"><tr><td class="sub-first"> ansiversion</td><td>=</td><td>5</td></tr><tr><td class="sub-first"> mount.fstype</td><td>=</td><td>iso9660</td></tr><tr><td class="sub-first"> mount.options</td><td>=</td><td>ro,nosuid,nodev,relatime</td></tr><tr><td class="sub-first"> state</td><td>=</td><td>mounted</td></tr><tr><td class="sub-first"> status</td><td>=</td><td>ready</td></tr></table></td></tr>
 </tbody>             </table></div>
<div class="indented">
                                <div class="indented">
                <table width="100%" class="node" summary="attributes of medium">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">medium</div></td></tr></thead>
 <tbody>
                   <tr><td class="first">physical id: </td><td class="second"><div class="id">0</div></td></tr>
                   <tr><td class="first">logical name: </td><td class="second"><div class="id">/dev/cdrom</div></td></tr>
                   <tr><td class="first">logical name: </td><td class="second"><div class="id">/media/cdrom0</div></td></tr>
                   <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of medium"><tr><td class="sub-first"> mount.fstype</td><td>=</td><td>iso9660</td></tr><tr><td class="sub-first"> mount.options</td><td>=</td><td>ro,nosuid,nodev,relatime</td></tr><tr><td class="sub-first"> state</td><td>=</td><td>mounted</td></tr></table></td></tr>
 </tbody>                </table></div>
                </div>
             </div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of ide:1">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">ide:1</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">IDE interface</td></tr>
             <tr><td class="first">product: </td><td class="second">MCP55 SATA Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">e</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:0e.0</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a2</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second">ide pm msi ht bus_master cap_list</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of ide:1"><tr><td class="sub-first"> driver</td><td>=</td><td>sata_nv</td></tr><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr><tr><td class="sub-first"> maxlatency</td><td>=</td><td>1</td></tr><tr><td class="sub-first"> mingnt</td><td>=</td><td>3</td></tr><tr><td class="sub-first"> module</td><td>=</td><td>sata_nv</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of ide:2">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">ide:2</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">IDE interface</td></tr>
             <tr><td class="first">product: </td><td class="second">MCP55 SATA Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">e.1</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:0e.1</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a2</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second">ide pm msi ht bus_master cap_list</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of ide:2"><tr><td class="sub-first"> driver</td><td>=</td><td>sata_nv</td></tr><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr><tr><td class="sub-first"> maxlatency</td><td>=</td><td>1</td></tr><tr><td class="sub-first"> mingnt</td><td>=</td><td>3</td></tr><tr><td class="sub-first"> module</td><td>=</td><td>sata_nv</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of ide:3">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">ide:3</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">IDE interface</td></tr>
             <tr><td class="first">product: </td><td class="second">MCP55 SATA Controller</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">e.2</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:0e.2</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a2</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second">ide pm msi ht bus_master cap_list</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of ide:3"><tr><td class="sub-first"> driver</td><td>=</td><td>sata_nv</td></tr><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr><tr><td class="sub-first"> maxlatency</td><td>=</td><td>1</td></tr><tr><td class="sub-first"> mingnt</td><td>=</td><td>3</td></tr><tr><td class="sub-first"> module</td><td>=</td><td>sata_nv</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of pci:1">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">pci:1</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">PCI bridge</td></tr>
             <tr><td class="first">product: </td><td class="second">MCP55 PCI bridge</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">f</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:0f.0</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a2</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second">pci ht subtractive_decode bus_master cap_list</td></tr>
 </tbody>          </table></div>
<div class="indented">
                          <div class="indented">
             <table width="100%" class="node" summary="attributes of firewire">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">firewire</div></td></tr></thead>
 <tbody>
                <tr><td class="first">description: </td><td class="second">FireWire (IEEE 1394)</td></tr>
                <tr><td class="first">product: </td><td class="second">IEEE 1394 Host Controller</td></tr>
                <tr><td class="first">vendor: </td><td class="second">VIA Technologies, Inc.</td></tr>
                <tr><td class="first">physical id: </td><td class="second"><div class="id">b</div></td></tr>
                <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:02:0b.0</div></td></tr>
                <tr><td class="first">version: </td><td class="second">c0</td></tr>
                <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
                <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
                <tr><td class="first">capabilities: </td><td class="second">pm ohci bus_master cap_list</td></tr>
                <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of firewire"><tr><td class="sub-first"> driver</td><td>=</td><td>ohci1394</td></tr><tr><td class="sub-first"> latency</td><td>=</td><td>32</td></tr><tr><td class="sub-first"> maxlatency</td><td>=</td><td>32</td></tr><tr><td class="sub-first"> module</td><td>=</td><td>ohci1394</td></tr></table></td></tr>
 </tbody>             </table></div>
             </div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of multimedia">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">multimedia</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">Audio device</td></tr>
             <tr><td class="first">product: </td><td class="second">MCP55 High Definition Audio</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">f.1</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:0f.1</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a2</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second">pm msi ht bus_master cap_list</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of multimedia"><tr><td class="sub-first"> driver</td><td>=</td><td>HDA Intel</td></tr><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr><tr><td class="sub-first"> maxlatency</td><td>=</td><td>5</td></tr><tr><td class="sub-first"> mingnt</td><td>=</td><td>2</td></tr><tr><td class="sub-first"> module</td><td>=</td><td>snd_hda_intel</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of bridge:0">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">bridge:0</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">Ethernet interface</td></tr>
             <tr><td class="first">product: </td><td class="second">MCP55 Ethernet</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">11</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:11.0</div></td></tr>
             <tr><td class="first">logical name: </td><td class="second"><div class="id">eth0</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a2</td></tr>
             <tr><td class="first">serial: </td><td class="second">00:1d:60:52:85:19</td></tr>
             <tr><td class="first">size: </td><td class="second">100000000</td></tr>
             <tr><td class="first">capacity: </td><td class="second">1000000000</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second">bridge pm msix msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of bridge:0"><tr><td class="sub-first"> autonegotiation</td><td>=</td><td>on</td></tr><tr><td class="sub-first"> broadcast</td><td>=</td><td>yes</td></tr><tr><td class="sub-first"> driver</td><td>=</td><td>forcedeth</td></tr><tr><td class="sub-first"> driverversion</td><td>=</td><td>0.61</td></tr><tr><td class="sub-first"> duplex</td><td>=</td><td>full</td></tr><tr><td class="sub-first"> ip</td><td>=</td><td>192.168.1.102</td></tr><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr><tr><td class="sub-first"> link</td><td>=</td><td>yes</td></tr><tr><td class="sub-first"> maxlatency</td><td>=</td><td>20</td></tr><tr><td class="sub-first"> mingnt</td><td>=</td><td>1</td></tr><tr><td class="sub-first"> module</td><td>=</td><td>forcedeth</td></tr><tr><td class="sub-first"> multicast</td><td>=</td><td>yes</td></tr><tr><td class="sub-first"> port</td><td>=</td><td>MII</td></tr><tr><td class="sub-first"> speed</td><td>=</td><td>100MB/s</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of bridge:1">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">bridge:1</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">Ethernet interface</td></tr>
             <tr><td class="first">product: </td><td class="second">MCP55 Ethernet</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">12</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:12.0</div></td></tr>
             <tr><td class="first">logical name: </td><td class="second"><div class="id">eth1</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a2</td></tr>
             <tr><td class="first">serial: </td><td class="second">00:1d:60:52:8e:ad</td></tr>
             <tr><td class="first">capacity: </td><td class="second">1000000000</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second">bridge pm msix msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of bridge:1"><tr><td class="sub-first"> autonegotiation</td><td>=</td><td>on</td></tr><tr><td class="sub-first"> broadcast</td><td>=</td><td>yes</td></tr><tr><td class="sub-first"> driver</td><td>=</td><td>forcedeth</td></tr><tr><td class="sub-first"> driverversion</td><td>=</td><td>0.61</td></tr><tr><td class="sub-first"> ip</td><td>=</td><td>192.168.1.102</td></tr><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr><tr><td class="sub-first"> link</td><td>=</td><td>no</td></tr><tr><td class="sub-first"> maxlatency</td><td>=</td><td>20</td></tr><tr><td class="sub-first"> mingnt</td><td>=</td><td>1</td></tr><tr><td class="sub-first"> module</td><td>=</td><td>forcedeth</td></tr><tr><td class="sub-first"> multicast</td><td>=</td><td>yes</td></tr><tr><td class="sub-first"> port</td><td>=</td><td>MII</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of pci:2">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">pci:2</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">PCI bridge</td></tr>
             <tr><td class="first">product: </td><td class="second">MCP55 PCI Express bridge</td></tr>
             <tr><td class="first">vendor: </td><td class="second">nVidia Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div class="id">13</div></td></tr>
             <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:00:13.0</div></td></tr>
             <tr><td class="first">version: </td><td class="second">a2</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
             <tr><td class="first">capabilities: </td><td class="second">pci pm msi ht pciexpress normal_decode bus_master cap_list</td></tr>
             <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of pci:2"><tr><td class="sub-first"> driver</td><td>=</td><td>pcieport-driver</td></tr></table></td></tr>
 </tbody>          </table></div>
<div class="indented">
                          <div class="indented">
             <table width="100%" class="node" summary="attributes of storage">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">storage</div></td></tr></thead>
 <tbody>
                <tr><td class="first">description: </td><td class="second">RAID bus controller</td></tr>
                <tr><td class="first">product: </td><td class="second">9650SE SATA-II RAID</td></tr>
                <tr><td class="first">vendor: </td><td class="second">3ware Inc</td></tr>
                <tr><td class="first">physical id: </td><td class="second"><div class="id">0</div></td></tr>
                <tr><td class="first">bus info: </td><td class="second"><div class="id">pci@0000:03:00.0</div></td></tr>
                <tr><td class="first">logical name: </td><td class="second"><div class="id">scsi0</div></td></tr>
                <tr><td class="first">version: </td><td class="second">01</td></tr>
                <tr><td class="first">width: </td><td class="second">64 bits</td></tr>
                <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
                <tr><td class="first">capabilities: </td><td class="second">storage pm msi pciexpress bus_master cap_list emulated</td></tr>
                <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of storage"><tr><td class="sub-first"> driver</td><td>=</td><td>3w-9xxx</td></tr><tr><td class="sub-first"> latency</td><td>=</td><td>0</td></tr><tr><td class="sub-first"> module</td><td>=</td><td>3w_9xxx</td></tr></table></td></tr>
 </tbody>             </table></div>
<div class="indented">
                                <div class="indented">
                <table width="100%" class="node" summary="attributes of disk:0">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">disk:0</div></td></tr></thead>
 <tbody>
                   <tr><td class="first">description: </td><td class="second">SCSI Disk</td></tr>
                   <tr><td class="first">product: </td><td class="second">9650SE-4LP DISK</td></tr>
                   <tr><td class="first">vendor: </td><td class="second">AMCC</td></tr>
                   <tr><td class="first">physical id: </td><td class="second"><div class="id">0.0.0</div></td></tr>
                   <tr><td class="first">bus info: </td><td class="second"><div class="id">scsi@0:0.0.0</div></td></tr>
                   <tr><td class="first">logical name: </td><td class="second"><div class="id">/dev/sda</div></td></tr>
                   <tr><td class="first">version: </td><td class="second">3.08</td></tr>
                   <tr><td class="first">serial: </td><td class="second">6QG0ZV63E9D3A100F5BA</td></tr>
                   <tr><td class="first">size: </td><td class="second">465GiB (499GB)</td></tr>
                   <tr><td class="first">capabilities: </td><td class="second">partitioned partitioned:dos</td></tr>
                   <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of disk:0"><tr><td class="sub-first"> ansiversion</td><td>=</td><td>5</td></tr><tr><td class="sub-first"> signature</td><td>=</td><td>0003eab6</td></tr></table></td></tr>
 </tbody>                </table></div>
<div class="indented">
                                      <div class="indented">
                   <table width="100%" class="node" summary="attributes of volume:0">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">volume:0</div></td></tr></thead>
 <tbody>
                      <tr><td class="first">description: </td><td class="second">EXT3 volume</td></tr>
                      <tr><td class="first">vendor: </td><td class="second">Linux</td></tr>
                      <tr><td class="first">physical id: </td><td class="second"><div class="id">1</div></td></tr>
                      <tr><td class="first">bus info: </td><td class="second"><div class="id">scsi@0:0.0.0,1</div></td></tr>
                      <tr><td class="first">logical name: </td><td class="second"><div class="id">/dev/sda1</div></td></tr>
                      <tr><td class="first">logical name: </td><td class="second"><div class="id">/</div></td></tr>
                      <tr><td class="first">logical name: </td><td class="second"><div class="id">/dev/.static/dev</div></td></tr>
                      <tr><td class="first">version: </td><td class="second">1.0</td></tr>
                      <tr><td class="first">serial: </td><td class="second">45578908-cb3b-4943-9bdd-99fb1bb00968</td></tr>
                      <tr><td class="first">size: </td><td class="second">446GiB</td></tr>
                      <tr><td class="first">capacity: </td><td class="second">446GiB</td></tr>
                      <tr><td class="first">capabilities: </td><td class="second">primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized</td></tr>
                      <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of volume:0"><tr><td class="sub-first"> created</td><td>=</td><td>2008-10-11 10:53:20</td></tr><tr><td class="sub-first"> filesystem</td><td>=</td><td>ext3</td></tr><tr><td class="sub-first"> modified</td><td>=</td><td>2008-10-30 13:19:07</td></tr><tr><td class="sub-first"> mount.fstype</td><td>=</td><td>ext3</td></tr><tr><td class="sub-first"> mount.options</td><td>=</td><td>rw,relatime,errors=remount-ro,data=ordered</td></tr><tr><td class="sub-first"> mounted</td><td>=</td><td>2008-10-30 09:38:43</td></tr><tr><td class="sub-first"> state</td><td>=</td><td>mounted</td></tr></table></td></tr>
 </tbody>                   </table></div>
                   </div>
<div class="indented">
                                      <div class="indented">
                   <table width="100%" class="node" summary="attributes of volume:1">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">volume:1</div></td></tr></thead>
 <tbody>
                      <tr><td class="first">description: </td><td class="second">Extended partition</td></tr>
                      <tr><td class="first">physical id: </td><td class="second"><div class="id">2</div></td></tr>
                      <tr><td class="first">bus info: </td><td class="second"><div class="id">scsi@0:0.0.0,2</div></td></tr>
                      <tr><td class="first">logical name: </td><td class="second"><div class="id">/dev/sda2</div></td></tr>
                      <tr><td class="first">size: </td><td class="second">18GiB</td></tr>
                      <tr><td class="first">capacity: </td><td class="second">18GiB</td></tr>
                      <tr><td class="first">capabilities: </td><td class="second">primary extended partitioned partitioned:extended</td></tr>
 </tbody>                   </table></div>
<div class="indented">
                                            <div class="indented">
                      <table width="100%" class="node" summary="attributes of logicalvolume">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">logicalvolume</div></td></tr></thead>
 <tbody>
                         <tr><td class="first">description: </td><td class="second">Linux swap / Solaris partition</td></tr>
                         <tr><td class="first">physical id: </td><td class="second"><div class="id">5</div></td></tr>
                         <tr><td class="first">logical name: </td><td class="second"><div class="id">/dev/sda5</div></td></tr>
                         <tr><td class="first">capacity: </td><td class="second">18GiB</td></tr>
                         <tr><td class="first">capabilities: </td><td class="second">nofs</td></tr>
 </tbody>                      </table></div>
                      </div>
                   </div>
                </div>
<div class="indented">
                                <div class="indented">
                <table width="100%" class="node" summary="attributes of disk:1">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">disk:1</div></td></tr></thead>
 <tbody>
                   <tr><td class="first">description: </td><td class="second">SCSI Disk</td></tr>
                   <tr><td class="first">product: </td><td class="second">9650SE-4LP DISK</td></tr>
                   <tr><td class="first">vendor: </td><td class="second">AMCC</td></tr>
                   <tr><td class="first">physical id: </td><td class="second"><div class="id">0.1.0</div></td></tr>
                   <tr><td class="first">bus info: </td><td class="second"><div class="id">scsi@0:0.1.0</div></td></tr>
                   <tr><td class="first">logical name: </td><td class="second"><div class="id">/dev/sdb</div></td></tr>
                   <tr><td class="first">version: </td><td class="second">3.08</td></tr>
                   <tr><td class="first">serial: </td><td class="second">6QG14BACE9D3A100A326</td></tr>
                   <tr><td class="first">size: </td><td class="second">465GiB (499GB)</td></tr>
                   <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of disk:1"><tr><td class="sub-first"> ansiversion</td><td>=</td><td>5</td></tr></table></td></tr>
 </tbody>                </table></div>
                </div>
             </div>
          </div>
       </div>
    </div>
</body>
</html>

---

### Post by ashmew2 on 2008-10-31
> **GROMS said:**
> Got a little sidetracked so .... any way, Have 8.04 desktop up and updated. Looked at Apache site and they gave the command:

 sudo tasksel install lamp-server

to install Apache2,PHP 5 and MYSQL 5. But there is a lot of reference to "server" version of Ubuntu. From the responses here I 'assume' this is ok???
But, is the command above correct nd should it be executed in the Synamptic Package Manager??
If I want to add Pearl, Ruby and Python, How would I do that??
This is a steep learning curve and all the help for this old man is greatly appreciated. 

I think I got the 4 drives mirrored right. did the command:
  sudo lshw -html > sysinfo.html
and got a list of the system. Under * - disk:0, it shows name as /dev/sda the volume and the 2 volumes (0 and 1). Also says its mounted. For * - disk:1  it shows /dev/sdb but doesn't say anything about it being mounted. In Places>computer it shows a floppy,scsi,dvd drives and file system.The properties of files ystem gives the size on on mirror. Properties of the scsi drive shows 'Type unknown'. So I'm not sure if I have access to the second mirror or is I have to mount the scsi and assume it is pointing to sdb (second mirror SATAs).
Here is text of html file:

**Contents of File Omitted **

:lolflag:...You could have made the file as an attachment instead of the ridiculously long post :P

---

### Post by GROMS on 2008-10-31
> **ashmew2 said:**
> :lolflag:...You could have made the file as an attachment instead of the ridiculously long post :P

Tried, but it just kept asking me to log in, even after I re logged in. Went for the nex available option. Appologize for the length - would have cut/paste if I new how to output lshw command in text file.
Do you have an answer?? To this or origional Q??

---

