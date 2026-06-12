---
title: "Could someone help me install AMD cool and quiet on Ubuntu?"
date: 2015-07-31
forum: New to Ubuntu
---

### Post by Mugen_H on 2015-07-31
I have the AMD Phenom2 X4 processor on an ASUS motherboard. 

1) Could someone please help me find out how to install AMD Cool and Quiet drivers on this? I'm googling around and getting complex answers which I can't make head or tails out of.

2) By chance if it's already installed then how can I check my CPU speed, temperature, RAM usage etc?

I'm using Ubuntu x64.

---

### Post by QIII on 2015-07-31
AMD Cool 'n Quiet is not an OS-level utility.  It is enabled/disabled in your BIOS/EFI setup on your motherboard.

To gain access to it from your OS, you need to install something like lm-sensors

```
sudo apt-get install lm-sensors
```

to add the module(s) to your kernel and then detect the available sensors with

```
sudo sensors-detect
```

Answer "Yes" to everything.  sensors-detect will suggest that you restart the service or reboot.  You can do either.

To check that everything is working, you can do

```
sensors
```.

The temperature for that CPU will be listed as "k10temp".  But be aware that AMD does not report an actual physical temperature, but an arbitrary differential in pseudo-celsius to control the cooling.  You may read an explanation of that in my blog at theleftcoastgeek.net (see the link in my signature).  Fan speed will be given in the motherboard section and you will have to consult your motherboard documentation to determine which one represents the CPU fan.

To monitor the temperature in the UI, here are three of the many possibilities:

1.  A sensor applet - usually easily configured, but limited in the amount of info given.

2.  gkrellm - moderately configurable with more information.

3.  conky - extremely configurable but not for the newcomer.  It takes a lot of time to learn, but you can get it to bring you toast and coffee in bed.

A simple command-line utility such as top or htop can be used to monitor memory and CPU load in real-time if you don't want to set up a more complex solution.  However, fan speed and temperature won't be included.  If you want to use the command line to monitor the sensors, you can simply do

```
watch -n 1 sensors
``` to get a readout of the sensor readings every second.

---

### Post by Mugen_H on 2015-07-31
Thanks a load for replying. I typed yes for everything (sometimes in capital and sometimes in small text - don't know whether that matters). Finally it printed the following message:

> 
Monitoring programs won't work until the needed modules are
loaded. You may want to run 'service kmod start'
to load them.


So I typed "service kmod start" (without the quotes) and it gives me an error: 

> start: Unknown job: kmod



Do I need to go to /etc/init.d/

to run this service?

---

### Post by QIII on 2015-07-31
I'd probably just reboot.  I'm lazy.

---

### Post by Mugen_H on 2015-07-31
Okay great! Done. I'm able to monitor the temperatures. Now how do I get access to AMD Cool and Quiet?

---

### Post by QIII on 2015-07-31
Cool 'n Quiet, as I said, operates at the motherboard level.  You will have to enter the BIOS/EFI setup for your machine.  Some boards offer quite a bit of configuration, some offer only basic configuration.

AMD may provide some method for Windows to offer some utility for changes from the OS.  AMD doesn't provide Linux  any such access.

---

### Post by Mugen_H on 2015-07-31
Okay I'm really sorry to be such a bother but is there any way I could set it to decrease the processor a little bit? I think it's running them at full. 

I read somewhere about something called governors and I want to set it to "on-demand" or else something slower. But don't know if there's an alternative solution. Or should I create a new thread for that?

---

### Post by QIII on 2015-07-31
Let's first check to be sure how it is running.

Try

```
sudo watch -n 1 dmidecode -t processor | grep Speed
```

for a minute or two and see if it is running full blast all the time.

---

### Post by Mugen_H on 2015-08-01
> **QIII said:**
> Let's first check to be sure how it is running.

Try

```
sudo watch -n 1 dmidecode -t processor | grep Speed
```

for a minute or two and see if it is running full blast all the time.

I tried this code and didn't get any messages for 10 mins. So I tried the same code without the pipe and grep at the end and got the following output (I changed to 2seconds so I could copy it):

```

Every 2.0s: dmidecode -t processor                                                                                      Sat Aug  1 15:20:49 2015

# dmidecode 2.12
SMBIOS 2.5 present.

Handle 0x0004, DMI type 4, 40 bytes
Processor Information
        Socket Designation: AM3
        Type: Central Processor
        Family: Phenom II
        Manufacturer: AMD
        ID: 43 0F 10 00 FF FB 8B 17
        Signature: Family 16, Model 4, Stepping 3
        Flags:
                FPU (Floating-point unit on-chip)
                VME (Virtual mode extension)
                DE (Debugging extension)
                PSE (Page size extension)
                TSC (Time stamp counter)
                MSR (Model specific registers)
                PAE (Physical address extension)
                MCE (Machine check exception)
                CX8 (CMPXCHG8 instruction supported)
                APIC (On-chip APIC hardware supported)
                SEP (Fast system call)
                MTRR (Memory type range registers)
                PGE (Page global enable)
                MCA (Machine check architecture)
                CMOV (Conditional move instruction supported)
                PAT (Page attribute table)
                PSE-36 (36-bit page size extension)
                CLFSH (CLFLUSH instruction supported)
                MMX (MMX technology supported)
                FXSR (FXSAVE and FXSTOR instructions supported)
                SSE (Streaming SIMD extensions)
                SSE2 (Streaming SIMD extensions 2)
                HTT (Multi-threading)
        Version: AMD Phenom(tm) II X4 945 Processor
        Voltage: 1.5 V
        External Clock: 200 MHz
        Max Speed: 3000 MHz


```

I can't figure out where the current processor speed is.. :(  Does this mean that our processor speed is not being monitored?

---

### Post by QIII on 2015-08-01
Hi.  No, it means it's not going to work with watch.

Try

```
cat /proc/cpuinfo | grep "MHz"
```

To watch it over time, just up-arrow and repeat the command a few times.

(Sorry for the delay.  A fellow has to sleep and eat and spend some time with the Mrs. every now and then -- whether he wants to or not!  :) )

---

### Post by Mugen_H on 2015-08-01
Ya ya.. No worries. I'm really glad that you're replying actually. Thanks a lot for your help.:lolflag: I don't know how you people have managed to acquire such a huge amount of knowledge about Linux. It feels an insanely huge world.

Anyway, I ran the command that you provided and it woiked! Here are the results:

> mugen@mugen-comp:~$ cat /proc/cpuinfo | grep "MHz"
cpu MHz        : 1800.000
cpu MHz        : 800.000
cpu MHz        : 800.000
cpu MHz        : 800.000
mugen@mugen-comp:~$ cat /proc/cpuinfo | grep "MHz"
cpu MHz        : 800.000
cpu MHz        : 800.000
cpu MHz        : 2300.000
cpu MHz        : 800.000
mugen@mugen-comp:~$ cat /proc/cpuinfo | grep "MHz"
cpu MHz        : 800.000
cpu MHz        : 3000.000
cpu MHz        : 3000.000
cpu MHz        : 1800.000
mugen@mugen-comp:~$ cat /proc/cpuinfo | grep "MHz"
cpu MHz        : 3000.000
cpu MHz        : 800.000
cpu MHz        : 800.000
cpu MHz        : 800.000
mugen@mugen-comp:~$ cat /proc/cpuinfo | grep "MHz"
cpu MHz        : 800.000
cpu MHz        : 800.000
cpu MHz        : 3000.000
cpu MHz        : 3000.000
mugen@mugen-comp:~$ cat /proc/cpuinfo | grep "MHz"
cpu MHz        : 1800.000
cpu MHz        : 800.000
cpu MHz        : 3000.000
cpu MHz        : 800.000
mugen@mugen-comp:~$ cat /proc/cpuinfo | grep "MHz"
cpu MHz        : 2300.000
cpu MHz        : 800.000
cpu MHz        : 1800.000
cpu MHz        : 800.000
mugen@mugen-comp:~$ cat /proc/cpuinfo | grep "MHz"
cpu MHz        : 800.000
cpu MHz        : 3000.000
cpu MHz        : 800.000
cpu MHz        : 800.000
mugen@mugen-comp:~$ cat /proc/cpuinfo | grep "MHz"
cpu MHz        : 800.000
cpu MHz        : 1800.000
cpu MHz        : 800.000
cpu MHz        : 800.000
mugen@mugen-comp:~$ cat /proc/cpuinfo | grep "MHz"
cpu MHz        : 800.000
cpu MHz        : 3000.000
cpu MHz        : 800.000
cpu MHz        : 800.000
mugen@mugen-comp:~$ cat /proc/cpuinfo | grep "MHz"
cpu MHz        : 800.000
cpu MHz        : 800.000
cpu MHz        : 800.000
cpu MHz        : 1800.000
mugen@mugen-comp:~$ cat /proc/cpuinfo | grep "MHz"
cpu MHz        : 800.000
cpu MHz        : 800.000
cpu MHz        : 800.000
cpu MHz        : 800.000
mugen@mugen-comp:~$ cat /proc/cpuinfo | grep "MHz"
cpu MHz        : 800.000
cpu MHz        : 800.000
cpu MHz        : 3000.000
cpu MHz        : 1800.000


Looks like Linux is really changing my CPU a lot. It would still be cool to change the govenors or whatever it is to decrease the CPU load even further. My system makes a lot of noise actually that's why. Ready for next orders boss. :p

Edit: P.S.: What sorcery is this?

---

### Post by QIII on 2015-08-01
I'm pretty sure 800MHz is the lowest speed your CPU runs at without going to the BIOS/EFI and undervolting it or changing the clock speed.  So don't look for it to go much lower.

Remember that you are getting a snapshot of the performance each time you run the command -- probably at a rate of 1 - 1.5Hz.  Your machine, at idle, is running at 800MHz -- a lot faster than you can press keys.

The change in clock speed can take just a few cycles.  To get a perfect readout, you'd have to be able to repeat the command pretty fast indeed.

So, what I am saying is that your motherboard is correcting for load very quickly -- a lot more quickly than a software-based governor could.  Those occasional spikes are due to your computer doing some sort of process, which occurs even just running the OS.  Things are working just as they should.

As for the noise, that could be a lot of things.  Worn fan, poor air circulation, poor cooling, dust kittens in the fins of your HSF -- many things.

How is the temperature doing?

(The sorcery is simply telling the system to give you a section of an in-memory file created "on-the-fly" when you execute that command.  It gives information about the cpu and its state, which is updated very quickly by the kernel, and in this case we specify that it should return only the lines that contain "MHz".)

(PS:  I started with Unix in the 70s, so I've had a little time to pick up a thing or two here and there.  Most of it, of course, I have forgotten ...)

---

### Post by Mugen_H on 2015-08-01
Okay cool. So sounds like the motherboard is doing its job properly.

The noise could be due to dust no doubt. My cabinet has a lot of areas for dust to enter through so that could be possible. The temperature.. well just by touching the cabinet there's nothing unusual. It's never hot as such. The room also isn't heating up noticeably in any way. But one thing's sure. Things were quieter back with Windows 7. In case  it's the fan speed it was running more eased up I guess.

hmm.. Ya I guess working with a technology does make a difference. As for me I gamed my way through the 80s on my 386 PC..

---

### Post by QIII on 2015-08-01
Dust gets blown in by the fans and pushed into the heatsink by your CPU fan.  Even a very light coat of dust on the fins of your heatsink can have an inordinate negative effect on its performance.

I take my machines (well, the 5 I have at home) out to the garage for a visit with the air compressor every two weeks.  You'd be surprised how much that improves cooling -- which means the fans don't run as fast.

---

### Post by Mugen_H on 2015-08-01
Well... alrighty then. I'm updating this thread as solved. Thanks a load for your help! :biggrin:

---

