---
title: "new comer to understanding PCI device drivers"
date: 2010-11-20
forum: Programming Talk
---

### Post by jamesbon on 2010-11-20
Hi,
I have been reading some books about device driver development etc.I
made a char driver of bond (dummy) device.
My book says that PCI devices contain three addressable regions,
configuration space,IO ports,and device memory,the book talks about a
file include/linux/pci_ids.h and PCI addressing etc.I read about
following functions
1) pci_read_config_
2) pci_write_config_

some thing known as offset is defined to be passed on as an argument
to above functions
3) IRQ number assigned to a card function pci_read_config_byte_
,configuration register offsets
4) pci_request_region
I want to write a pci driver for my own understanding and I am reading
some books about it.
I am not clear with terms
1) configuration space,
2) I/O ports
3) device memory
4) the offsets defined in include/linux/pci_ids.h
5) PCI addressing.
Can some one point me to a resource for understanding this stuff.
The book I am reading does have good amount of information but just by
reading it I find myself
in a difficult situation and not able to appreciate the driver explained in it.
I am not clear as what should I be googling to understand my questions.

---

### Post by NathanB on 2010-11-20
Well, stop Googling.  Wikipedia has the stuff you are looking for:

[http://en.wikipedia.org/wiki/Conventional_PCI](http://en.wikipedia.org/wiki/Conventional_PCI)

[http://en.wikipedia.org/wiki/PCI_configuration_space](http://en.wikipedia.org/wiki/PCI_configuration_space)

[http://en.wikipedia.org/wiki/Interrupt_request](http://en.wikipedia.org/wiki/Interrupt_request)

[http://en.wikipedia.org/wiki/Memory-mapped_I/O](http://en.wikipedia.org/wiki/Memory-mapped_I/O)

Just copy the keywords from your post here and paste them (one by one) into Wikipedia's search field.

---

### Post by jamesbon on 2010-11-20
> **NathanB said:**
> Well, stop Googling.  Wikipedia has the stuff you are looking for:

Thanks I had been madly searching for such stuff.

---

