---
title: "no sound any output"
date: 2020-12-28
forum: New to Ubuntu
---

### Post by mocneogniwo on 2020-12-28
hi i got problem with elementary and ubuntu i dont have sound and i dont know how to repair i dont have any sound driver modules to make sudo alsa force-reload

---

### Post by mastablasta on 2020-12-28
first we need to know what is recognised by the os if anything and what hardware you actually have.

please post output of 
```
lshw --sanitize
```


or if you have inxi installed you can also get audio info from the following command :
```
inxi -A
```

if you know what audio chip you have, then let us know. if you use the one on motherboard or if this is a laptop, then let us know the exact models.

---

### Post by mocneogniwo on 2020-12-28
nothing happens if i use this command when i instal inxi its nothing show

---

### Post by mocneogniwo on 2020-12-28
tobi@tobi:~$ lshw -sanitize
WARNING: you should run this program as super-user.
computer                    
    description: Computer
    width: 64 bits
    capabilities: smp vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 6094MiB
     *-cpu
          product: Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx rdtscp x86-64 constant_tsc rep_good nopl xtopology cpuid pni pclmulqdq ssse3 cx16 pcid sse4_1 sse4_2 popcnt aes xsave avx hypervisor lahf_lm pti ssbd ibrs ibpb stibp xsaveopt flush_l1d arch_capabilities
     *-scsi
          physical id: 2
          logical name: scsi0
        *-cdrom
             description: SCSI CD-ROM
             product: Virtual DVD-ROM
             vendor: Msft
             physical id: 0.0.1
             bus info: scsi@0:0.0.1
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/sr0
             version: 1.0
             capabilities: removable audio
             configuration: status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth0
       serial: [REMOVED]
       size: 10Gbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=hv_netvsc duplex=full firmware=N/A ip=[REMOVED] link=yes multicast=yes speed=10Gbit/s
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---

### Post by mastablasta on 2020-12-29
commands in linux are case sensitive.

lshw shows that either hardware is not detected at all or you didn't copy and paste the whole thing.

if you run alsamixer in terminal does it show a sound chip info in the upper right corner? while you are running it you can check if all outputs are unmuted and if you have volume maxed out on all of them.

---

### Post by mocneogniwo on 2020-12-29
i know about this something alsamixer dont work after reinstall sound drivers like dont working i dont know what happens

---

### Post by mocneogniwo on 2020-12-29
its a dummy output and input

---

