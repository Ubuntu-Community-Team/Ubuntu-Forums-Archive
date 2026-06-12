---
title: "oprofile help"
date: 2011-10-13
forum: Programming Talk
---

### Post by raghulnt on 2011-10-13
Hello Experts,
I'm trying to profile the pcie driver using oprofile. From the FAQ i see that -p option is given to profile the kernel modules. But i get invalid arguement when i execute the -p option. Below are the steps I tried:
---------------------
opcontrol --setup --no-vmlinux
opcontrol --reset
opcontrol -p pcie.ko   >> specifying the kernel module name gives invalid arguement
opcontrol --start
./myapp
opcontrol --dump
opcontrol --shutdown
opreport -l
---------------------
Please let me know if i'm missing anything. Do i need to make changes in makefile to build the .ko module? Any events i need to set? I've tried setting up BUS_TRANS_ANY events opcontrol --event=BUS_TRAN_ANY:500:0x40  but i dont get any useful info . My driver is fpga based pcie driver which reads and writes the data. 

Appreciate your help.

Thanks,
Raghu

---

