---
title: "How to hook iptable configuration events at the kernel"
date: 2013-06-04
forum: Programming Talk
---

### Post by dudigmail on 2013-06-04
Hi

I'd like to hook the event at the KERNEL when the following command is executed:
iptables -A PREROUTING -t nat -i eth0 -j DNAT --to-destination 192.168.42.14

If I understood correctly iptable events handled by Netlink infrastructure.
 
I code a Kernel module to listen to Netlink socket as follows:

void klna_nl_data_ready(struct sock *sk, int bytes)
{[INDENT]printk("Hello");[/INDENT]
}

struct socket *my_socket;
struct sock nl_sock;

static int __init my_module_init(void)
{[INDENT]sock_create_kern(AF_NETLINK , SOCK_RAW, NETLINK_NFLOG , &my_socket);[/INDENT]
[INDENT]..
..[/INDENT]
[INDENT]addr.nl_family = AF_NETLINK;[/INDENT]
[INDENT]addr.nl_pid = 0;[/INDENT]
[INDENT]addr.nl_groups = 0;[/INDENT]
[INDENT]kernel_bind(my_socket, (struct sockaddr *)&addr, sizeof(addr));
..
..[/INDENT]
[INDENT]/* set the socket up */[/INDENT]
[INDENT]nl_sock = my_socket->sk;[/INDENT]
[INDENT]nl_sock->sk_data_ready = nl_data_ready;[/INDENT]
[INDENT]nl_sock->sk_allocation = GFP_ATOMIC[/INDENT]


}

I'd appreciate your help

---

