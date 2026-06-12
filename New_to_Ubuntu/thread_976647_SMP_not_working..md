---
title: "SMP not working."
date: 2008-11-09
forum: New to Ubuntu
---

### Post by Ougadas on 2008-11-09
I have a base Hardy install using kernel 2.6.24-19 generic. 

When I run 

```

uname -a

```

The system returns 

```

Linux ubuntu 2.6.24-19-generic #1 **SMP** Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

```

Yet my system monitor only shows one CPU, and when I run 

```

 cat /proc/cpuinfo | grep -i cores

```

The system tells me that 

```

cpu cores	: 1

```

My processor is an AMD X2 4800, and cpuinfo without piping to grep for just the cores does pick up the name correctly. 

I have compiled and installed a newer kernel with SMP support, which resolves the problem. Both CPU's show up in System Monitor, and the number of cores is shown properly as 2. 

However, the NVidia driver refuses to install by any method posted on this board or elsewhere with any kernel I compile. So I'm trashing the custom kernel option for now. 

So I'd like to find a way to make the generic kernel that says it supports SMP to actually support SMP. 

I've searched the forums, but haven't found this specific problem. 

Anyone have any ideas?

---

### Post by Butthead on 2008-11-09
What does typing "top" in terminal and then hitting (either?) the "1" or "2" key while in there show you?

Could be that the "grep" command you typed is misreporting the info you wanted somehow? :confused:

---

