---
title: "Netlinks in kernel 2.6.26.2"
date: 2009-06-17
forum: Programming Talk
---

### Post by ranthal on 2009-06-17
Hey all,

I've been working on a kernel module that makes use of netlink sockets and when i just tried to compile I recently found that creating the socket has changed since some of the sources I have read were written.  The function to create the socket now is:
```
extern void netlink_kernel_create(struct net *net,
                                  int unit, unsigned int groups,
                                  void (*input)(struct sk_buff *skb),
                                  struct mutex *cb_mutex,
                                  struct module *module);
```

What I had read from my research only consisted of the unit and input fields.  Groups I can guess but as for the others I'm not sure what the exact intent and effect of including these is.  Can anybody help me out with it?

On another note I will be compiling this for a 2.6.19 kernel as well.  Any idea if this uses the older or newer function prototype?

---

### Post by ranthal on 2009-06-17
So this is a bump I guess, but I've been doing more reading and it brought up a question:

What is the difference between a netlink and a generic netlink?

From my reading it seems like people were not satisfied with the implementation of netlink requiring knowledge of the network layer.  Maybe generic netlink was created so programmers could define their own protocol?  Being an EE background doing embedded SW and having reasonable knowledge of the network layer it seems to me that if this is the case they complicated the netlink for the sake of creating a more programmer friendly interface where it wasn't the original intent of netlink to begin with.

---

### Post by ranthal on 2009-06-18
I've pretty much reached a good spot on this so thought I'd post my conclusions on it since digging around online and posting on forums didn't do much.

After taking a look at some of the kernel source I found some good examples of the newer netlink_kernel_create in a lot of the /linux-2.6.26.2/net/ files.  One I used in particular as a reference was ipv4/netfilter/ip_queue.c.  Without going too far in depth into the use of the socket creation I will mention that the struct mutex *cb_mutex (cb being callback I assume) that I was most worried about ended up being passed in as NULL so that turned out ok.

As far as the netlink vs. generic netlink discussion goes I think I see the light.  First, generic netlinks are built on top of the netlink interface.  Netlink has changed a lot from kernel version to kernel version so using a generic netlink allows one to keep code more portable between versions and allow the linux kernel maintainers to deal with the interface from generic netlink to the constantly changing netlink.  The cost associated with using a generic netlink is that the message contains one more layer of headers and such since it has the standard netlink headers plus the generic netlink header.

Essentially, generic netlinks provide a transport layer built upon the netlink network layer using the OSI model.  Depending on your level of understanding of each along with the design of the system your are implementing them on both are good options and which you choose is all about being an engineer.  I hope somebody can appreciate this down the road.

---

