---
title: "LKM netfilter hooks error"
date: 2011-09-07
forum: Programming Talk
---

### Post by emiller12345 on 2011-09-07
Im running into a problem when running a module that contains the below code, with the 2 lines of commented code, uncommented. I want to verify that the packet is ETH_P_IP (IP protocol) before I go on an try to create an iphdr. I get a kernel oops when I try to run it.

```
unsigned int process_packet(unsigned int hooknum, struct sk_buff *skb, const struct net_device *in, const struct net_device *out, int (*okfn)(struct sk_buff *))
{
    struct ethhdr *eth = (struct ethhdr *)skb_mac_header(skb);
    //if(eth->h_proto == htons(ETH_P_IP)){
        /*Found IP Packet!*/
        struct iphdr *ip_header = (struct iphdr *)skb_network_header(skb);

        if (ip_header->protocol==IPPROTO_TCP){
            /*Found TCP Packet!*/
            struct tcphdr *tcp_header = (struct tcphdr *)skb_transport_header(skb);
            printk(KERN_INFO "IP: TCP: FOUND\n");
            return NF_ACCEPT;
        }
        printk(KERN_INFO "IP: FOUND\n");
        return NF_ACCEPT;
    //}
    return NF_ACCEPT;
}

```

---

### Post by emiller12345 on 2011-09-10
The mac header, including the h_proto, is handled earlier in the hook process, by (struct nf_hook_ops)->pf.  Once inside the netfilter hook function, only the network layer and beyond is available. So no need to filter it!

---

