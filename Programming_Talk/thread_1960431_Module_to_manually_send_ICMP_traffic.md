---
title: "Module to manually send ICMP traffic"
date: 2012-04-17
forum: Programming Talk
---

### Post by mpcadel on 2012-04-17
So here's what I am trying to do:
Capture all ICMP traffic echo_traffic at the LOCAL_OUT hook(using netfilter), and then try to manually send it over an interface using dev_queue_xmit();

I fill in the ethernet headers correctly(hard coding my source address and broadcasting the frame) then copy the rest of the original sk_buff and try to send.

So far, this's always caused the kernel to crash completely.
So what am I doing wrong here, please?  
```

static unsigned int post_icmp_check(unsigned int hooknum,
			       struct sk_buff *skb,
			       const struct net_device *in,
			       const struct net_device *out,
			       int (*okfn)(struct sk_buff *))
{
	struct iphdr *iph;
	struct icmphdr *icmph;
	struct sk_buff *sb;
	struct ethhdr *ethh;
	unsigned char *frame = NULL; //Used just to copy the skb->data and replace it, that's all
	unsigned char *ptr;
	
	/* Allocations and initial assignations  */
	sb = skb_copy(skb, GFP_ATOMIC);	/* Making a private copy because we cannot modify all fields in the public one */
	iph = (struct iphdr*) sb->data;

	if(iph->protocol == IPPROTO_ICMP){
		printk(KERN_ALERT"POST ICMP traffic!\n");
		
		icmph = (struct icmphdr*)(sb->data +(iph->ihl * 4));
		if(icmph->type == ICMP_ECHO){
			frame = (unsigned char *)kmalloc(iph->tot_len + (ETH_HLEN*8), GFP_KERNEL);
			ptr = (frame + 	(ETH_HLEN * 8));

			ethh = (struct ethhdr*) frame;		//00:1a:80:7e:96:ba
			ethh->h_source[0] = 0x00;	
			ethh->h_source[1] = 0x1a;			
			ethh->h_source[2] = 0x80;
			ethh->h_source[3] = 0x7e;
			ethh->h_source[4] = 0x96;
			ethh->h_source[5] = 0xba;
			ethh->h_dest[0] = 0xff;
			ethh->h_dest[1] = 0xff;
			ethh->h_dest[2] = 0xff;
			ethh->h_dest[3] = 0xff;
			ethh->h_dest[4] = 0xff;
			ethh->h_dest[5] = 0xff;
			ethh->h_proto = ETH_P_IP;
			memcpy(ptr, skb->data, (iph->ihl * 4)); /* Copying the rest of the data from the skb to sb */
			
			iph = (struct iphdr*) (frame + 	(ETH_HLEN * 8));
			icmph = (struct icmphdr*)(frame + (ETH_HLEN * 8) +(iph->ihl * 4));
					
			icmph->un.echo.sequence = htons(i++);			
			icmph->checksum = 0;
			icmph->checksum =  in_cksum((unsigned short *)icmph, ntohs(iph->tot_len) - sizeof(struct iphdr));
			sb->data = frame;
			dev_queue_xmit(sb);
			return NF_STOLEN;
		}		
	}/* If IPPROTO_ICMP */
	kfree_skb(sb);
	kfree(frame);
	return NF_ACCEPT;
}
```

---

### Post by dwhitney67 on 2012-04-17
You are stretching the boundaries of my knowledge, but if I had to guess, the issue lies with this line of code:
```

frame = (unsigned char *)kmalloc(iph->tot_len + (ETH_HLEN*8), GFP_KERNEL);

```

Try fixing it to use ntohs() for converting the length of the packet; something like:
```

frame = (unsigned char *)kmalloc(**ntohs**(iph->tot_len) + (ETH_HLEN*8), GFP_KERNEL);

```

---

### Post by mpcadel on 2012-04-17
Heh, I am kinda ashamed of myself that didn't cross my mind :P

Yep, that did solve it.
Again, thanks a lot =)

---

### Post by mpcadel on 2012-04-18
Well, here's another thing.
The crash did happen again, it happened because the sb->dev was null.
Fixed that, and now there's no crash.

But I am getting no reply for my ICMP echo traffic, which basically means my frames are being dropped at the other end.

Now, what are my frames missing? Should I add a footer or something?

---

