---
title: "Ubuntu memory slots 3 &amp; 4 not recognized"
date: 2012-11-20
forum: New to Ubuntu
---

### Post by BramPat on 2012-11-20
I've just bought some extra 2x8GB rams to add to my existing 2x4GB. My setup is now:

- ASRock 970 Extreme4 motherboard.
- Memory:
Bank 0: 8GB
Bank 1: 4GB
Bank 2: 8GB
Bank 3: 4GB
- 32-bit Ubuntu 11.04 (also tried 64-bit Ubuntu 12.10, see below)

Just now I noticed that those existing rams were 2x4 and not 2x2. When I installed the 2x8GB rams, my System Monitor only show about 12GB (11.8 GiB) of RAM. When I boot to UEFI, I see all 24GB of RAM recognized in expected setup:

Also, when I run "sudo lshw" I can see all 4 slots sum up to 24 GiB:
     *-memory
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 24GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: CL9-9-9 D3-1333
             vendor: Undefined
             physical id: 0
             serial: 00000000
             slot: A1_DIMM0
             size: 8GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: CL9-9-9 DDR3-1333
             vendor: Undefined
             physical id: 1
             serial: 00000000
             slot: A1_DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: CL9-9-9 D3-1333
             vendor: Undefined
             physical id: 2
             serial: 00000000
             slot: A1_DIMM2
             size: 8GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: CL9-9-9 DDR3-1333
             vendor: Undefined
             physical id: 3
             serial: 00000000
             slot: A1_DIMM3
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)

Being 32-bit would limit me to 3.x GB and not to 11.8 GB, so aparently that's not the issue? Also, I've booted from 64-bit 12.10, but had the exact same results.

Any help?

---

### Post by squakie on 2012-11-20
Check the docs for the motherboard.  Some motherboards only allow certain combinations of memory, and it may be yours isn't currently in one of those comfigurations.  I didn't actually check mine when I built my desktop, but I'm also not using a mix of memory stick sizes.

---

### Post by BramPat on 2012-11-21
Did that. I've set it up in the way the manual instructs:
Bank 0 (Blue slot): 8GB
Bank 1 (White slot): 4GB
Bank 2 (Blue slot): 8GB
Bank 3 (White slot): 4GB

The manual instructs (as most mobo-manuals do) to put identical dimms in the same colored slots. But somehow the 3rd and 4th (numbered 2 and 3, I know why) are available in the hardware and command 'lshw' shows them they're available, but Ubuntu doesn't use them.

---

### Post by squakie on 2012-11-24
And you're not mixing memory speeds, cas latenencies, etc., right?

---

### Post by 2F4U on 2012-11-24
Did you already run memtest, for example, from a liveCD to see if there is a problem with the RAM modules?

---

