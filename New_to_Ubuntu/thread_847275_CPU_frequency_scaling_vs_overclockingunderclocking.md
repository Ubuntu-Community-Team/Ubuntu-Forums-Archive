---
title: "CPU frequency scaling vs overclocking/underclocking"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by meindian523 on 2008-07-02
What is the difference between CPU frequency scaling and over/underclocking?What are the advantages/disadvantages of each?

I searched the web,but even the usually reliable Wikipedia turned up stubs which hardly made any sense to a hardware n00b like me.

I've been given to understand by a friend that CPU frequency scaling is matching the clock frequency of the CPU to the Front Side Bus(Is that the same as the Northbridge?As you see,I've a long way to go :P) so that the CPU doesn't sit idle "wasting" cycles to save power.

But the same friend also told me that he is not sure whether idle cycles wherein no processing is done does use up power or not.

Also,I believe overclocking is trying to increase the frequency of the CPU clock as far as it can go without having a non-booting system to have a faster,more responsive box,at the cost of higher heat dissipation,which requires more cooling,and accordingly underclocking is the opposite of over.

---

### Post by wolfen69 on 2008-07-02
cpu frequency scaling is when the cpu speed is increased when demand is more, and speed is decreased when demand is less. overclocking/underclocking is done manually by the user. cpu frequency scaling is a good thing often used by laptops to extend battery life. personally, i dont believe in overclocking, as it can lead to instability and problems.

---

### Post by Titan8990 on 2008-07-02
> personally, i dont believe in overclocking, as it can lead to instability and problems.

When done right there will be no stability issues but can still shorten the life of your hardware. I have had my e6750 OCed to 3.4Ghz for about 6months now and have not had one issue with stability since I got the voltage at a optimal setting.

---

### Post by mcduck on 2008-07-02
> **wolfen69 said:**
> cpu frequency scaling is when the cpu speed is increased when demand is more, and speed is decreased when demand is less. overclocking/underclocking is done manually by the user. cpu frequency scaling is a good thing often used by laptops to extend battery life. personally, i dont believe in overclocking, as it can lead to instability and problems.

When done correctly, overclocked system is just as stable as normal. The whole point in overclocking is to increase the speed as much as possible while keeping it stable. This of course might require tricks like increasing CPU voltage and using more powerful cooling. And of course running tests to make sure that the system is stable. :)

Some might say that overclocking reduces the lifetime of the components, but in my opinion (and experience) all the hardware will be ridiculously outdated before it breaks from the extra stress..

Frequency scaling is, like you said, more or less automatic system that drops the CPU frequency when the CPU has little to do. This increases the battery lifetime on laptops, but also reduces heat generated from the CPU and when paired with controlled fans also reduces the noise your computer makes. So it's usefull on desktop machines as well.

---

### Post by piousp on 2008-07-02
Most people wont probably need to overclock their hardware, unless you really want that extra *pump* to get some more FPS, for example.

---

### Post by Daggo on 2008-07-02
When your cpu sits 'idle' yes it is processing. Your cpu always needs to be processing else it will lock up your system. An 'idle' process is when your cpu just sits there and waits for an interrupt request (keyboard, mouse, program) and takes up the absolute minimal amount of prosessing power. Essentially what 'idle' does is keeps the processor alive.

Concerning you overclocking needs. Try visiting the Overclock.net forums. There you will find a rich amount of information to start you off in clocking your cpu. Its what I have used in the past to clock my rig. 

Also find a program named 'Prime95' and 'Memtest' for stability testing while you are clocking. And remember, if you plan on clocking safely, invest in good coolant.

---

### Post by meindian523 on 2008-07-02
Advantages and Disadvantages of overclocking/underclocking and CPU frequency Scaling please?Does the idle cycle actually consume power?

EDIT:Actually,I don't plan on overclocking or anything.It's just for the knowledge.

---

### Post by Daggo on 2008-07-02
Oh, and get 'CPU-Z' to tell you the exact details of your chip. Build, steppings, frequency etc..

And find a program that tells you your exact temperatures. I use everest and it works fine, but there are many more out there.

---

### Post by Daggo on 2008-07-02
CPU Frequency Scaling has the ability to alter the frequency of your cpu. So when your chip finds it needs more procesing power, it increases the frequency to give it more juice. This is a good way to save power and this is why you find it in laptops a lot. 

Overclocking/underclocking gives you a steady frequency and disallows your computer from fluctuating its frequency and possibly causing stability issues. 

Yes, the 'idle' process consumes power, but so little that if it consumed any less, you will find your computer is turned off. And it does not steal any processing power from any other programs. Its the 'keep alive' process that makes the cpu sit and wait for something to happen.

---

### Post by lazyart on 2008-07-02
Advantages to overclocking: More cpu power, save $$ over faster processor, bragging rights.
Disadvantages: Increased heat can possibly damage processor/shorten life.  Investment in costlier cooling solution to combat heat can surpass price difference of faster chip.

Often you can overclock and use your existing cooling fan.  I do this with my Opteron.  There are exotic cooling setups (I watercooled a system years ago but after three pumps in six months I abandoned it) and a whole community based on squeezing out every drop of performance.  Just know that in 18 months a bigger, badder chip will come out and make your overclock seem pedestrian.

On the other side of the spectrum, underclocking a chip can reduce it's power consumption and therefore it's heat output, which means you can use  a slower-moving, quieter fan, or ditch the fan completely and cool it passively (like we did with 386 chips).  The benefit there is silence which makes your system better suited for use as an entertainment box, DVR, etc.

With chips that become obsolete in three years but can last for 10 or more, you might not be concerned with shortening it's lifespan.  I'd read arguments that overclocking is immoral (trying to get more than what you paid for).  Amazingly, you can find video cards that are labeled as overclocked.

If you search the web you'll probably be able to find the story of the guy  who overclocked his system and cooled it by submerging the entire motherboard in baby oil.  I think maybe he didn't get too much trying to sell the used parts on ebay...

---

### Post by unutbu on 2008-07-02
Question 1: Would it be fair to say that
[list]
[*] if you have a 1.8GHz CPU, frequency scaling can alter the clock speed from about 1.2GHz to 1.8GHz.

[*] overclocking increases the clock speed above 1.8GHz (how high typically?)

[*] underclock decreases the clock speed below 1.2GHz
[/list]

Question 2: I recently read an interesting (and short!) argument why underclocking may actually consume more power than letting the CPU run in its normal "ondemand" setting:

[http://www.lesswatts.org/projects/applications-power-management/race-to-idle.php](http://www.lesswatts.org/projects/applications-power-management/race-to-idle.php)

What do you guys think?

---

### Post by markbuntu on 2008-07-02
Way back at the beginning of time, a guy namde Linus Torvalds was fooling around trying to use all the available commands on a 386 prosessor chip. One of these was the halt command which no other operating system at the time took advantage of. When this command was used it stopped the clocking of the cpu while maintaining all the registers. The result was a processor that actually ran faster and better because performance was not degraded due to excess heat caused by the cpu continuosly running when it had nothing to do.

When you overclock your cpu you do it by increasing the voltage supplied to the chip. This, while speeding up the processor can also introduce more errors in internal chip processing due to increased thermal instability. Internal error correction in the chip will increase causing even greater power consumption. This can be only partially overcome by increasing external cooling but because silicon is not a very good heat conductor localized overheating cannot be fully compensated for.

Manufacturers set the voltage of their chips for a reasonable compromise between performance and longevity vs heat degradation for a wide range of uses and environments.

---

### Post by sdennie on 2008-07-03
> **unutbu said:**
> Question 1: Would it be fair to say that
[list]
[*] if you have a 1.8GHz CPU, frequency scaling can alter the clock speed from about 1.2GHz to 1.8GHz.

[*] overclocking increases the clock speed above 1.8GHz (how high typically?)

[*] underclock decreases the clock speed below 1.2GHz
[/list]


The number of frequencies available is chip dependent.  For example, an intel T9300 can use 2.5Ghz, 2Ghz, 1.6Ghz, 1.2Ghz and 800Mhz.  It's not very common for laptops to have the ability to properly under/overclock the CPU via BIOS so, I'm not sure how it would interact with the frequency max/min.  Presumably if you were able to overclock the maximum frequency while retaining the same minimum frequency, you would be able to actually save more power (because of the second part of your post) but, I have no way to verify that.

> 
Question 2: I recently read an interesting (and short!) argument why underclocking may actually consume more power than letting the CPU run in its normal "ondemand" setting:

[http://www.lesswatts.org/projects/applications-power-management/race-to-idle.php](http://www.lesswatts.org/projects/applications-power-management/race-to-idle.php)

What do you guys think?

This is not really about underclocking but about using a frequency governor that keeps the CPU at the lowest frequency.  Another article about this can be found here: [http://mjg59.livejournal.com/88608.html](http://mjg59.livejournal.com/88608.html).  Using "powersave" instead of "ondemand" can sometimes make the machine cooler but, it doesn't generally save extra power over "ondemand" under normal workloads.

---

### Post by mcduck on 2008-07-03
> **markbuntu said:**
> 
When you overclock your cpu you do it by increasing the voltage supplied to the chip. This, while speeding up the processor can also introduce more errors in internal chip processing due to increased thermal instability. Internal error correction in the chip will increase causing even greater power consumption. This can be only partially overcome by increasing external cooling but because silicon is not a very good heat conductor localized overheating cannot be fully compensated for.

Manufacturers set the voltage of their chips for a reasonable compromise between performance and longevity vs heat degradation for a wide range of uses and environments.


Increasing the voltage will not make your CPU run faster. And it definitely doesn't make it less stable. Quite the opposite, the whole point in increasing the CPU voltage is to make the CPU _more_ stable, and decrease errors.

In the end, a CPU is still an analog device. While it works with ones and zeroes, the voltage used to represent these values doesn't change immediately from one to other. Now, when you increase the CPU frequency the dealy it takes for the voltage can cause problems, the voltage might not be able to fully change from one value to other, giving the result of something in between. And these would cause errors. When the CPU voltage is increased the difference between the voltages used to represent 0 and 1 becomes bigger, which helps to get rid of the errors.

So, the COU speed is increased simply by changing it's bus frequency & multiplier, usually through BIOS. Depending on how much you overclocked, that might make your system less stable. This is compensated by increasing the CPU voltage, which then results in more heat generated. And then we introduce the better cooling. So neither the cooling, nor the higher voltage, will make your COU run faster. They are just used to make the overclocked system stable.

Manufacturers set the default voltage as something that is enough to provide a stable system with the default clock speeds. Ussually all the CPU models in same family will use the same voltage, regardless of their clock speed.

---

### Post by meindian523 on 2008-07-03
Thanks to all for the replies and a big grrr at hijackers ;)
I now summarise this thread as:

Overclocking is running a city sedan(CPU) in fourth gear(Max stable frequency) whether the road(demand for processing power) is a dirt track(low) or the freeway(high).While you get max speed,it shortens the life of the CPU.

Underclocking is running the city sedan in first gear whether the road is a dirt track or the freeway.You get the lowest speed and probably are bumped by other cars when on the freeway(you have a lower frequency processor,you lose bragging rights)But your car outdoes the life of those who don't underclock(presumably?)It also saves power.

CPU Frequency Scaling is an automatic transmission car,it will scale the gear depending the need.This is the best option provided the manufacturer of the car provided for it.

Now,how do I know whether CPU Frequency Scaling is enabled for my CPU( or is it a property of the motherboard?)

---

### Post by unutbu on 2008-07-03
To see what cpu scaling governor you are currently using, run:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```
To see the available cpu scaling governors:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors

```
To see what else you can see,
```
ls /sys/devices/system/cpu/cpu0/cpufreq
```

To change the scaling governor to "performance" (though I don't recommend this in general. See [http://mjg59.livejournal.com/88608.html):](http://mjg59.livejournal.com/88608.html):)
```
echo performance | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```
To watch your cpu clock speed:
```
watch -n 1 cat /sys/devices/system/cpu/*/cpufreq/scaling_cur_freq

```

If you have two CPUs, change cpu0 to cpu1 in the commands above to look at your second cpu.

---

### Post by meindian523 on 2008-07-03
Failed at the first step,got as far as cpu0,but there's no cpufreq in the path.FYI,my processor is Pentium D

---

### Post by unutbu on 2008-07-03
Try the advice in this article: 
[http://polishlinux.org/linux/debian/green-pcs-cpu-frequency-scaling-in-linux/](http://polishlinux.org/linux/debian/green-pcs-cpu-frequency-scaling-in-linux/)

---

### Post by meindian523 on 2008-07-03
Oh,coo!,I thought CPU frequency scaling wasn't supported on Pentium D.Are you sure this is not a property of the motherboard?I'm not on Ubuntu right now,so I will login later to report on my attempts to save power,provided this is not a property of the motherboard,of course.

---

### Post by meindian523 on 2008-07-05
I got this:
```
easwarh@l1nuxr0cks:/lib/modules/2.6.24-19-generic/kernel/arch/x86/kernel/cpu/cpufreq$ sudo modprobe speedstep-centrino
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.24-19-generic/kernel/arch/x86/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device
```
while trying to insert speedstep-centrino into the kernel
What do I do now?

---

### Post by unutbu on 2008-07-05
Run the following commands to ask the machine to detect the correct module:
```
. /usr/share/powernowd/cpufreq-detect.sh
echo $MODULE
echo $MODULE_FALLBACK
```

Try inserting it manually:
```
sudo modprobe $MODULE
```

if that doesn't work, try
```
sudo modprobe $MODULE_FALLBACK
```

The scripts /etc/init.d/powernowd and /etc/init.d/powernowd.early should handle the insertion of the right kernel module for you at boot time. To check that they are getting run at boot time, run

```
ls -l   /etc/rc2.d/*powernowd*
```

You should see
```

lrwxrwxrwx 1 root root 25 2008-01-15 05:14 /etc/rc2.d/S10powernowd.early -> ../init.d/powernowd.early
lrwxrwxrwx 1 root root 19 2008-01-15 05:14 /etc/rc2.d/S20powernowd -> ../init.d/powernowd

```
If the above commands do not work, please post the output of all the above commands, and
```
sudo lshw -C cpu
lsmod | grep cpu
```

---

### Post by meindian523 on 2008-07-05
I did
```
easwarh@l1nuxr0cks:~$cd /usr/share/powernowd/cpufreq-detect.sh and

easwarh@l1nuxr0cks:~$./cpufreq-detect.sh
```
I got
```
easwarh@l1nuxr0cks:/usr/share/powernowd$ ./cpufreq-detect.sh 
easwarh@l1nuxr0cks:/usr/share/powernowd$
```
I did
```
easwarh@l1nuxr0cks:~$echo $MODULE
easwarh@l1nuxr0cks:~$echo $MODULE_FALLBACK
```
I got respectively
```
easwarh@l1nuxr0cks:~$echo $MODULE
speedstep-ich
easwarh@l1nuxr0cks:~$echo $MODULE_FALLBACK
acpi-cpufreq
```
I did
```
easwarh@l1nuxr0cks:~$sudo modprobe $MODULE
```
I got
```
easwarh@l1nuxr0cks:~$sudo modprobe $MODULE
FATAL: Error inserting speedstep_ich (/lib/modules/2.6.24-19-generic/kernel/arch/x86/kernel/cpu/cpufreq/speedstep-ich.ko): No such device
```
I did
```
easwarh@l1nuxr0cks:~$sudo modprobe $MODULE_FALLBACK
```
I got
```
easwarh@l1nuxr0cks:~$sudo modprobe $MODULE_FALLBACK
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.24-19-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device
```
I did
```
easwarh@l1nuxr0cks:~$ls -l   /etc/rc2.d/*powernowd*
```
I got
```
easwarh@l1nuxr0cks:~$ls -l   /etc/rc2.d/*powernowd*
lrwxrwxrwx 1 root root 25 2008-06-03 19:57 /etc/rc2.d/S10powernowd.early -> ../init.d/powernowd.early
lrwxrwxrwx 1 root root 19 2008-06-03 19:57 /etc/rc2.d/S20powernowd -> ../init.d/powernowd
```
So now,I did
```
easwarh@l1nuxr0cks:~$sudo lshw -C cpu
```
I got
```
easwarh@l1nuxr0cks:~$sudo lshw -C cpu
  *-cpu:0                 
       description: CPU
       product: Intel(R) Pentium(R) D CPU 2.80GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: 15.4.7
       serial: 0000-0F47-0000-0000-0000-0000
       slot: Socket 775
       size: 2800MHz
       capacity: 3800MHz
       width: 64 bits
       clock: 200MHz
       capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl cid cx16 xtpr lahf_lm
       configuration: id=0
     *-logicalcpu:0
          description: Logical CPU
          physical id: 0.1
          width: 64 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 0.2
          width: 64 bits
          capabilities: logical
  *-cpu:1
       description: CPU
       vendor: Intel
       physical id: 5
       bus info: cpu@1
       version: 15.4.7
       serial: 0000-0F47-0000-0000-0000-0000
       slot: Socket 775
       size: 2800MHz
       capacity: 3800MHz
       clock: 200MHz
       capabilities: ht
       configuration: id=0
     *-logicalcpu:0
          description: Logical CPU
          physical id: 0.1
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 0.2
          capabilities: logical
easwarh@l1nuxr0cks:~$
```
And
```
easwarh@l1nuxr0cks:~$lsmod | grep cpu
```
gave
```
easwarh@l1nuxr0cks:~$ lsmod|grep cpu
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
xt_tcpudp               4096  14 
x_tables               16132  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
easwarh@l1nuxr0cks:~$
```

Hope that info helps you.Apologies for keeping it a I did,I got format.

---

### Post by unutbu on 2008-07-05
I'm not sure if I can help you. This is quickly moving beyond my very small domain of knowledge.

But on the off-chance that I can find a useful suggestion for you, please post

```
uname -a
lsmod
grep CPU_FREQ /boot/config-`uname -r`

```

One little thing I noticed is that in the output of your lshw command, your cpu lists its capabilities as

> capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl cid cx16 xtpr lahf_lm

Mine looks like this:
> capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm **cpufreq**

Note that mine includes cpufreq. I don't know, however, if this is the cause of the problem, or if it is just a symptom.

---

### Post by meindian523 on 2008-07-06
uname -a
```
easwarh@l1nuxr0cks:~$ uname -a
Linux l1nuxr0cks 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux
easwarh@l1nuxr0cks:~$ 
```
lsmod```

easwarh@l1nuxr0cks:~$ lsmod
Module                  Size  Used by
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ipv6                  267780  16 
ppdev                  10372  0 
video                  19856  0 
output                  4736  1 video
dock                   11280  0 
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
battery                14212  0 
speedstep_lib           6532  0 
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
ac                      6916  0 
lp                     12324  0 
snd_hda_intel         344728  0 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
serio_raw               7940  0 
gspca                 643920  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
videodev               29440  1 gspca
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
evdev                  13056  3 
v4l2_common            18304  1 videodev
v4l1_compat            15492  1 videodev
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
psmouse                40336  0 
pcspkr                  4224  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
fglrx                1555468  20 
i2c_piix4               9612  0 
button                  9232  0 
i2c_core               24832  1 i2c_piix4
ati_agp                 9996  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
agpgart                34760  2 fglrx,ati_agp
xt_limit                3584  8 
xt_tcpudp               4096  14 
ipt_LOG                 7296  8 
ipt_MASQUERADE          4608  0 
ipt_TOS                 3200  5 
ipt_REJECT              5632  1 
nf_conntrack_irc        7576  0 
nf_conntrack_ftp       10144  0 
xt_state                3328  6 
iptable_nat             8324  0 
nf_nat                 20396  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19080  8 iptable_nat
nf_conntrack           66752  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle          3712  1 
iptable_filter          3840  1 
ip_tables              14820  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16132  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
ext3                  136712  3 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
ide_cd                 32544  0 
cdrom                  37408  1 ide_cd
ide_disk               17536  8 
pata_atiixp             8960  0 
pata_acpi               8320  0 
8139cp                 24704  0 
ata_generic             8324  0 
floppy                 59588  0 
ehci_hcd               37900  0 
ohci_hcd               25348  0 
8139too                27520  0 
mii                     6400  2 8139cp,8139too
atiixp                  5648  0 [permanent]
ide_core              113996  3 ide_cd,ide_disk,atiixp
usbcore               146028  4 gspca,ehci_hcd,ohci_hcd
sata_sil               12296  0 
libata                159344  4 pata_atiixp,pata_acpi,ata_generic,sata_sil
scsi_mod              151436  1 libata
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  7 
easwarh@l1nuxr0cks:~$
```
grep CPU_FREQ /boot/config-`uname -r`
```

easwarh@l1nuxr0cks:~$ grep CPU_FREQ /boot/config-2.6.24-19-generic 
CONFIG_CPU_FREQ=y
# CONFIG_CPU_FREQ_DEBUG is not set
# CONFIG_CPU_FREQ_DEFAULT_GOV_CONSERVATIVE is not set
# CONFIG_CPU_FREQ_DEFAULT_GOV_ONDEMAND is not set
CONFIG_CPU_FREQ_DEFAULT_GOV_PERFORMANCE=y
# CONFIG_CPU_FREQ_DEFAULT_GOV_USERSPACE is not set
CONFIG_CPU_FREQ_GOV_CONSERVATIVE=m
CONFIG_CPU_FREQ_GOV_ONDEMAND=m
CONFIG_CPU_FREQ_GOV_PERFORMANCE=y
CONFIG_CPU_FREQ_GOV_POWERSAVE=m
CONFIG_CPU_FREQ_GOV_USERSPACE=m
CONFIG_CPU_FREQ_STAT=m
CONFIG_CPU_FREQ_STAT_DETAILS=y
CONFIG_CPU_FREQ_TABLE=m
easwarh@l1nuxr0cks:~$ 

```

---

### Post by meindian523 on 2008-07-06
But again,in the polishlinux article you pointed out,there was a module for Pentium D,speedstep-centrino IIRC.

---

### Post by unutbu on 2008-07-06
```
snack@tack:~% . /usr/share/powernowd/cpufreq-detect.sh
snack@tack:~% echo $MODULE
speedstep-centrino
snack@tack:~% echo $MODULE_FALLBACK
acpi-cpufreq
snack@tack:~% lsmod | grep cpu
acpi_cpufreq           10568  0 
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  2 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
processor              32072  2 acpi_cpufreq,thermal
snack@tack:~% lsmod | grep speed
```

The script /etc/init.d/powernowd is run at boot time. If you look inside the script you will see that the cpufreq-detect.sh script is run, and then (modprobe "$MODULE"||modprobe "$MODULE_FALLBACK") is run -- at least that's the way modprobe gets run on my machine. Depending on your configuration, yours may be different.

So first

```
modprobe $MODULE   (speedstep-centrino)
```

is run on my machine, and then if it fails,

```
modprobe $MODULE_FALLBACK   (acpi-cpufreq)
```

is run. My lsmod shows that on my machine insertion of speedstep-centrino failed, but insertion of acpi_cpufreq succeeded. 

Therefore, it may not be necessary for you to use speedstep-centrino to get cpu frequency scaling to work.

I have read that to get CPU frequency scaling you need both a CPU and a BIOS which supports frequency scaling. How to check your BIOS I have no idea. And, unfortunately, I just don't have the knowledge to tell you what command to try if 

```
modprobe $MODULE
```
and
```
modprobe $MODULE_FALLBACK
```
both fail.

---

### Post by meindian523 on 2008-07-15
bump.I belive I'm well within my rights.:)

---

### Post by meindian523 on 2008-08-27
bump again.

---

