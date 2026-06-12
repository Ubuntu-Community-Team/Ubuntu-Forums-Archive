---
title: "Network keeps cutting out"
date: 2012-05-19
forum: New to Ubuntu
---

### Post by Slurpgeit on 2012-05-19
Hi,

I've recently built and configured my first Linux server (Ubuntu Server 12.04), running Apache, Plex, Samba, and some other multimedia applications. Lately, the network keeps cutting out under medium to heavy load, totally at random. With this in the dmesg log: 

```
[13093.890099] ------------[ cut here ]------------
[13093.890109] WARNING: at /build/buildd/linux-3.2.0/net/sched/sch_generic.c:255 dev_watchdog+0x25a/0x270()
[13093.890112] Hardware name: To Be Filled By O.E.M.
[13093.890115] NETDEV WATCHDOG: eth0 (r8169): transmit queue 0 timed out
[13093.890117] Modules linked in: ipt_MASQUERADE iptable_nat nf_nat iptable_mangle xt_mark bridge stp ipt_LOG xt_limit xt_recent xt_tcpudp nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack iptable_filter ip_tables x_tables nfsd nfs lockd fscache auth_rpcgss nfs_acl sunrpc ext2 ppdev psmouse serio_raw parport_pc mac_hid i915 drm_kms_helper drm i2c_algo_bit video w83627ehf hwmon_vid coretemp mei(C) lp parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov r8169 raid6_pq async_tx raid1 raid0 multipath linear
[13093.890167] Pid: 0, comm: swapper/0 Tainted: G         C   3.2.0-24-generic #37-Ubuntu
[13093.890170] Call Trace:
[13093.890172]  <IRQ>  [<ffffffff8106712f>] warn_slowpath_common+0x7f/0xc0
[13093.890182]  [<ffffffff81067226>] warn_slowpath_fmt+0x46/0x50
[13093.890187]  [<ffffffff8155e22a>] dev_watchdog+0x25a/0x270
[13093.890192]  [<ffffffff81110b80>] ? perf_rotate_context+0x110/0x220
[13093.890197]  [<ffffffff81083030>] ? __queue_work+0x320/0x320
[13093.890200]  [<ffffffff8155dfd0>] ? qdisc_reset+0x50/0x50
[13093.890203]  [<ffffffff8155dfd0>] ? qdisc_reset+0x50/0x50
[13093.890208]  [<ffffffff81076086>] call_timer_fn+0x46/0x160
[13093.890211]  [<ffffffff8155dfd0>] ? qdisc_reset+0x50/0x50
[13093.890216]  [<ffffffff810779d2>] run_timer_softirq+0x132/0x2a0
[13093.890221]  [<ffffffff810950c5>] ? ktime_get+0x65/0xe0
[13093.890226]  [<ffffffff8106e928>] __do_softirq+0xa8/0x210
[13093.890230]  [<ffffffff8101a779>] ? read_tsc+0x9/0x20
[13093.890234]  [<ffffffff8109c054>] ? tick_program_event+0x24/0x30
[13093.890239]  [<ffffffff81666cec>] call_softirq+0x1c/0x30
[13093.890244]  [<ffffffff81015305>] do_softirq+0x65/0xa0
[13093.890248]  [<ffffffff8106ed0e>] irq_exit+0x8e/0xb0
[13093.890253]  [<ffffffff8166768e>] smp_apic_timer_interrupt+0x6e/0x99
[13093.890257]  [<ffffffff8166555e>] apic_timer_interrupt+0x6e/0x80
[13093.890259]  <EOI>  [<ffffffff8109c054>] ? tick_program_event+0x24/0x30
[13093.890266]  [<ffffffff8136b42d>] ? intel_idle+0xed/0x150
[13093.890269]  [<ffffffff8136b40f>] ? intel_idle+0xcf/0x150
[13093.890274]  [<ffffffff81504a01>] cpuidle_idle_call+0xc1/0x280
[13093.890278]  [<ffffffff8101222a>] cpu_idle+0xca/0x120
[13093.890284]  [<ffffffff816235ae>] rest_init+0x72/0x74
[13093.890290]  [<ffffffff81cfbc0d>] start_kernel+0x3ba/0x3c7
[13093.890295]  [<ffffffff81cfb388>] x86_64_start_reservations+0x132/0x136
[13093.890299]  [<ffffffff81cfb140>] ? early_idt_handlers+0x140/0x140
[13093.890304]  [<ffffffff81cfb459>] x86_64_start_kernel+0xcd/0xdc
[13093.890307] ---[ end trace bba6d56bfd5ffb46 ]---
[13093.906639] r8169 0000:03:00.0: eth0: link up

```

After googling this problem seemed to be common with this network card (Onboard mobo card):

```
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

```

Being fairly new to Linux, I'm very much at a loss here. The only solution I could find was adding "pcie_aspm=off" to the boot parameters, but that doesn't actually seem to do anything. What else can I try, besides buying another NIC?

---

### Post by Slurpgeit on 2012-05-21
FYI, this also happens on the newly released 3.4 kernel:

```
[  611.923629] ------------[ cut here ]------------
[  611.923641] WARNING: at /build/buildd/linux-3.4.0/net/sched/sch_generic.c:256 dev_watchdog+0x24a/0x260()
[  611.923643] Hardware name: To Be Filled By O.E.M.
[  611.923646] NETDEV WATCHDOG: eth0 (r8169): transmit queue 0 timed out
[  611.923648] Modules linked in: iptable_mangle ipt_MASQUERADE iptable_nat nf_nat xt_mark bridge stp xt_LOG xt_limit xt_recent xt_tcpudp nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack iptable_filter ip_tables x_tables nfsd nfs lockd fscache auth_rpcgss nfs_acl sunrpc ext2 psmouse ghash_clmulni_intel cryptd serio_raw microcode w83627ehf hwmon_vid coretemp ppdev parport_pc mac_hid i915 drm_kms_helper drm i2c_algo_bit video mei(C) lp parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov r8169 raid6_pq async_tx raid1 raid0 multipath linear
[  611.923700] Pid: 0, comm: swapper/0 Tainted: G         C   3.4.0-2-generic #6-Ubuntu
[  611.923702] Call Trace:
[  611.923704]  <IRQ>  [<ffffffff8105025f>] warn_slowpath_common+0x7f/0xc0
[  611.923715]  [<ffffffff81050356>] warn_slowpath_fmt+0x46/0x50
[  611.923722]  [<ffffffff8158874a>] dev_watchdog+0x24a/0x260
[  611.923728]  [<ffffffff81139180>] ? bdi_arm_supers_timer+0x50/0x50
[  611.923733]  [<ffffffff81588500>] ? dev_graft_qdisc+0x90/0x90
[  611.923739]  [<ffffffff810601bd>] run_timer_softirq+0x13d/0x340
[  611.923743]  [<ffffffff81057786>] __do_softirq+0xb6/0x1d0
[  611.923747]  [<ffffffff8103264d>] ? lapic_next_event+0x1d/0x30
[  611.923753]  [<ffffffff8168671c>] call_softirq+0x1c/0x30
[  611.923758]  [<ffffffff810150f5>] do_softirq+0x75/0xb0
[  611.923761]  [<ffffffff81057b55>] irq_exit+0xa5/0xb0
[  611.923765]  [<ffffffff8168705e>] smp_apic_timer_interrupt+0x6e/0x99
[  611.923769]  [<ffffffff81685dca>] apic_timer_interrupt+0x6a/0x70
[  611.923771]  <EOI>  [<ffffffff81374eaa>] ? intel_idle+0xea/0x150
[  611.923779]  [<ffffffff81374e8b>] ? intel_idle+0xcb/0x150
[  611.923784]  [<ffffffff8151eec9>] cpuidle_enter+0x19/0x20
[  611.923787]  [<ffffffff8151f4f9>] cpuidle_idle_call+0xa9/0x240
[  611.923791]  [<ffffffff8101c3ef>] cpu_idle+0xaf/0x120
[  611.923797]  [<ffffffff816499ce>] rest_init+0x72/0x74
[  611.923801]  [<ffffffff81cf6bd2>] start_kernel+0x3c1/0x3ce
[  611.923804]  [<ffffffff81cf6666>] ? do_early_param+0x90/0x90
[  611.923810]  [<ffffffff81cf6346>] x86_64_start_reservations+0x131/0x135
[  611.923814]  [<ffffffff81cf644a>] x86_64_start_kernel+0x100/0x10f
[  611.923817] ---[ end trace d9047a563b008004 ]---

```

---

### Post by Slurpgeit on 2012-05-23
Well, this is turning into quite the monologue. For anyone finding this thread in the future, i've solved it by installing this driver: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false) (The 2.6 version)

---

### Post by OmegaPhil on 2012-06-03
I use Debian and also have this issue - thanks for posting the link to the official realtek driver page, I am also using this to unbrick the onboard LAN.

I have added to the kernel bug [r8169 hangs when your transmission speed is really high]("https://bugzilla.kernel.org/show_bug.cgi?id=14962#c24") - given that it has been 3 years since the bug has been reported, I'm guessing noone cares.[URL="https://bugzilla.kernel.org/show_bug.cgi?id=14962#c24"]
[/URL]

---

### Post by OmegaPhil on 2012-06-07
Good news - courtesy of Francois Romieu I have been able to patch the default driver to get full networking capability back (so far) - see [https://bugzilla.kernel.org/show_bug.cgi?id=14962#c26](https://bugzilla.kernel.org/show_bug.cgi?id=14962#c26)

---

