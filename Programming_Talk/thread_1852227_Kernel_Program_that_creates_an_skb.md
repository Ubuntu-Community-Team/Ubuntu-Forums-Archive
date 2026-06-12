---
title: "Kernel Program that creates an skb"
date: 2011-09-29
forum: Programming Talk
---

### Post by emiller12345 on 2011-09-29
Trying to create a sample program that demonstrate working with an sk_buff packet, and sending it of over the wire.  I would like the program to eventually create (initialize) just one single packet and then send it on it's way.  Anyone know of a good source for examples?

---

### Post by emiller12345 on 2011-10-06
It seems that kernel programming is quite challenging.  I've been going through various notes and tutorials online, none really work well for modern linux networking. I was hoping this simple module code would demonstrate building an sk_buff packet locally and sending it off, but it's not working.  Anyone have any suggestions?

```
#include <linux/init.h>
#include <linux/module.h>
#include <linux/skbuff.h>
#include <linux/netdevice.h>
#include <linux/ip.h>
#include <net/ip.h>

static int temp_init(void)
{
    struct sk_buff *newskb;
    struct iphdr *newip;
    struct udphdr *newudp;
    //adding data will come later
    //u_char payload[] = "DATADATADATADATADATA";
    //u32 payload_len = 20;
    //u_char *data;

    printk(KERN_INFO "temp: registering lkm...\n");
    newskb = alloc_skb(LL_MAX_HEADER + sizeof(struct iphdr*) + 0x08 + 0x00, GFP_ATOMIC); //LL + IP + UDP + DATA
    //alloc_skb zero's the head, data, and tail; and sets end pointer

    if (skb_linearize(newskb) < 0)
        return NF_DROP;
    skb_reserve(newskb, LL_MAX_HEADER);
    //skb_reserve sets the data pointer, and re-zeros the tail

    skb_reset_network_header(newskb);

    newip = (void *)skb_put(newskb, sizeof(struct iphdr*));
    //skb_put sets the tail for iphdr
    newip->version  = IPVERSION;
    newip->ihl      = sizeof(struct iphdr) / 4;
    newip->tos      = 0;
    newip->id       = 0;
    newip->frag_off = htons(IP_DF);
    newip->protocol = IPPROTO_UDP;
    newip->check    = 0;
    newip->saddr    = htonl(0xC0A80101);
    newip->daddr    = htonl(0xC0A80102);
    printk(KERN_INFO "temp: newip setup ...\n");

    newudp = (void *)skb_put(newskb, sizeof(struct udphdr));
    //skb_put re-sets the tail for udphdr

    newudp->source = htons(0x1234); //4660
    newudp->dest   = htons(0x1235); //4661
    newudp->len    = htons(sizeof(struct udphdr));
    newudp->check  = 0;

    printk(KERN_INFO "temp: newudp setup ...\n");

    //ip_local_out will send the packet out 
    //  though, right now, it just crashes 
    //  the computer because newskb is not
    //  properly initialized...
    //ip_local_out(newskb);

free_nskb:
    kfree_skb(newskb); // save the planet, recycle!
    printk(KERN_INFO "temp: lkm loaded.\n");
    return 0;
}

static void temp_exit(void)
{
    printk(KERN_INFO "temp: unregistering lkm...\n");
    printk(KERN_INFO "temp: unloaded lkm\n");
}

module_init(temp_init);
module_exit(temp_exit);

MODULE_LICENSE("GPL");

```

---

