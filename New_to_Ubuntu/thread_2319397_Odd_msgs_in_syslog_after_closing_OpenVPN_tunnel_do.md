---
title: "Odd msgs in syslog after closing OpenVPN tunnel down?"
date: 2016-04-03
forum: New to Ubuntu
---

### Post by zephyr2 on 2016-04-03
Beginner here running UbuntuMATE 15.10 on a laptop. Please help me understand if I've misconfigured OpenVPN on my laptop in some very basic way? I've successfully connected before but ran into some odd behavior / errors today....

Today I tried opening an OpenVPN connection via terminal with

 ```
sudo openvpn US\ Seattle.conf
```

 (which gateway I have successfully connected to many times) and got the following error after the key exchange, etc.:

```
Sun Apr  3 16:35:14 2016 ERROR: Linux route add command failed: external program exited with error status: 2
Sun Apr  3 16:35:14 2016 /sbin/ip route add 128.0.0.0/1 via 10.100.5.5
RTNETLINK answers: File exists
Sun Apr  3 16:35:14 2016 ERROR: Linux route add command failed: external program exited with error status: 2
Sun Apr  3 16:35:14 2016 /sbin/ip route add 10.100.5.1/32 via 10.100.5.5
RTNETLINK answers: File exists
Sun Apr  3 16:35:14 2016 ERROR: Linux route add command failed: external program exited with error status: 2
Sun Apr  3 16:35:14 2016 Initialization Sequence Completed
```


So, assuming I wasn't successfully in connecting, I opened Firefox expecting to have my ISP's connection, only to find I was connected to a different VPN gateway, located in Japan (!). I killed the VPN session in terminal (or assumed I did) typing Ctrl + C and the 'exit' command. Curiously, though, my system was still trying to resolve multiple gateways--in fact, every gateway for which I had a .conf file saved in /etc/openvpn, *except* for the one in Seattle, the only one I actually tried to connect to with!

This was the output of 'ps aux | grep openvpn' even *after* I exited the terminal running OpenVPN and tried disconnecting from wifi:

```
user@laptop:~$ ps aux | grep openvpn
root      1020  0.0  0.0  39248  5768 ?        Ss   Apr02   0:00 /usr/sbin/openvpn --daemon ovpn-Finland --status /run/openvpn/Finland.status 10 --cd /etc/openvpn --config /etc/openvpn/Finland.conf
root      1021  0.0  0.0  39248  5736 ?        Rs   Apr02   1:02 /usr/sbin/openvpn --daemon ovpn-Japan --status /run/openvpn/Japan.status 10 --cd /etc/openvpn --config /etc/openvpn/Japan.conf
root      1022  0.0  0.0  39284  5740 ?        Ss   Apr02   0:00 /usr/sbin/openvpn --daemon ovpn-Ireland --status /run/openvpn/Ireland.status 10 --cd /etc/openvpn --config /etc/openvpn/Ireland.conf
root      1032  0.0  0.0  39284  5968 ?        Ss   Apr02   0:00 /usr/sbin/openvpn --daemon ovpn-Norway --status /run/openvpn/Norway.status 10 --cd /etc/openvpn --config /etc/openvpn/Norway.conf
user    5194  0.0  0.0  15192  2156 pts/0    S+   16:44   0:00 grep --color=auto openvpn
```


Even more weirdly, it seems to me, is the date: 'Apr02', i.e., yesterday. Does this indicate my system has been trying to connect to these gateways since yesterday??? 

And the following snipped from output of 'tail -f /var/log/syslog' after I killed the VPN and wifi:

```
Apr  3 16:47:23** laptop ovpn-Norway[1032]: RESOLVE: Cannot resolve host address: no.privateinternetaccess.com: Temporary failure in name resolution**
Apr  3 16:47:25 laptop kernel: [ 2471.484673] [UFW AUDIT] IN= OUT=tun0 SRC=10.100.5.6 DST=209.222.18.218 LEN=97 TOS=0x00 PREC=0x00 TTL=64 ID=379 DF PROTO=UDP SPT=36393 DPT=53 LEN=77 
Apr  3 16:47:25** laptop ovpn-Finland[1020]: RESOLVE: Cannot resolve host address: fi.privateinternetaccess.com: Temporary failure in name resolution**
Apr  3 16:47:25 laptop kernel: [ 2471.518177] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.1.1 LEN=94 TOS=0x00 PREC=0x00 TTL=64 ID=62781 DF PROTO=UDP SPT=53341 DPT=53 LEN=74 
Apr  3 16:47:28** laptop ovpn-Japan[1021]: RESOLVE: Cannot resolve host address: japan.privateinternetaccess.com: Temporary failure in name resolution**
Apr  3 16:47:28** laptop ovpn-Ireland[1022]: RESOLVE: Cannot resolve host address: ireland.privateinternetaccess.com: Temporary failure in name resolution**
Apr  3 16:47:38 laptop kernel: [ 2484.582921] [UFW BLOCK] IN= OUT=tun0 SRC=10.100.5.6 DST=157.7.203.102 LEN=76 TOS=0x00 PREC=0xC0 TTL=64 ID=39013 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
Apr  3 16:47:41 laptop kernel: [ 2487.585442] [UFW BLOCK] IN= OUT=tun0 SRC=10.100.5.6 DST=202.181.103.212 LEN=76 TOS=0x00 PREC=0xC0 TTL=64 ID=57480 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
Apr  3 16:47:41 laptop kernel: [ 2487.585460] [UFW BLOCK] IN= OUT=tun0 SRC=10.100.5.6 DST=157.7.152.213 LEN=76 TOS=0x00 PREC=0xC0 TTL=64 ID=26641 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
Apr  3 16:47:43 laptop kernel: [ 2489.587178] [UFW BLOCK] IN= OUT=tun0 SRC=10.100.5.6 DST=106.187.50.84 LEN=76 TOS=0x00 PREC=0xC0 TTL=64 ID=14292 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
Apr  3 16:47:44 laptop kernel: [ 2490.588028] [UFW BLOCK] IN= OUT=tun0 SRC=10.100.5.6 DST=91.189.94.4 LEN=76 TOS=0x00 PREC=0xC0 TTL=64 ID=54530 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
Apr  3 16:47:44 laptop kernel: [ 2490.805165] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.1.1 LEN=74 TOS=0x00 PREC=0x00 TTL=64 ID=32 DF PROTO=UDP SPT=37306 DPT=53 LEN=54 
Apr  3 16:47:44 laptop kernel: [ 2490.805193] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.1.1 LEN=74 TOS=0x00 PREC=0x00 TTL=64 ID=32 DF PROTO=UDP SPT=37306 DPT=53 LEN=54 
Apr  3 16:48:05 laptop kernel: [ 2511.556267] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.1.1 LEN=77 TOS=0x00 PREC=0x00 TTL=64 ID=2468 DF PROTO=UDP SPT=50891 DPT=53 LEN=57 
Apr  3 16:48:05 laptop kernel: [ 2511.556287] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.1.1 LEN=77 TOS=0x00 PREC=0x00 TTL=64 ID=2468 DF PROTO=UDP SPT=50891 DPT=53 LEN=57 
Apr  3 16:48:15 laptop kernel: [ 2522.279782] INFO: task kworker/u16:7:2564 blocked for more than 120 seconds.
Apr  3 16:48:15 laptop kernel: [ 2522.279791]       Not tainted 4.2.0-34-generic #39-Ubuntu
Apr  3 16:48:15 laptop kernel: [ 2522.279793] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Apr  3 16:48:15 laptop kernel: [ 2522.279796] kworker/u16:7   D ffff88021f256640     0  2564      2 0x00000000
Apr  3 16:48:15 laptop kernel: [ 2522.279811] Workqueue: kmemstick memstick_check [memstick]
Apr  3 16:48:15 laptop kernel: [ 2522.279815]  ffff880213c13c48 0000000000000046 ffff880215a4a940 ffff8802128a3700
Apr  3 16:48:15 laptop kernel: [ 2522.279827]  ffff880213c13c58 ffff880213c14000 ffff8800d50a5c20 ffff8800d50a5c18
Apr  3 16:48:15 laptop kernel: [ 2522.279829]  ffff8802128a3700 ffff8800d50a5c00 ffff880213c13c68 ffffffff817eec67
Apr  3 16:48:15 laptop kernel: [ 2522.279830] Call Trace:
Apr  3 16:48:15 laptop kernel: [ 2522.279835]  [<ffffffff817eec67>] schedule+0x37/0x80
Apr  3 16:48:15 laptop kernel: [ 2522.279837]  [<ffffffff817f1d69>] schedule_timeout+0x189/0x250
Apr  3 16:48:15 laptop kernel: [ 2522.279841]  [<ffffffff813d625a>] ? kvasprintf+0x7a/0xa0
Apr  3 16:48:15 laptop kernel: [ 2522.279843]  [<ffffffff817ef6e3>] wait_for_completion+0xb3/0x140
Apr  3 16:48:15 laptop kernel: [ 2522.279845]  [<ffffffff810a6220>] ? wake_up_q+0x70/0x70
Apr  3 16:48:15 laptop kernel: [ 2522.279847]  [<ffffffffc04d734e>] memstick_set_rw_addr+0x4e/0x60 [memstick]
Apr  3 16:48:15 laptop kernel: [ 2522.279849]  [<ffffffffc04d7a9c>] memstick_check+0x10c/0x342 [memstick]
Apr  3 16:48:15 laptop kernel: [ 2522.279853]  [<ffffffff8109475a>] process_one_work+0x1aa/0x440
Apr  3 16:48:15 laptop kernel: [ 2522.279854]  [<ffffffff81094a3b>] worker_thread+0x4b/0x4c0
Apr  3 16:48:15 laptop kernel: [ 2522.279856]  [<ffffffff810949f0>] ? process_one_work+0x440/0x440
Apr  3 16:48:15 laptop kernel: [ 2522.279858]  [<ffffffff8109add8>] kthread+0xd8/0xf0
Apr  3 16:48:15 laptop kernel: [ 2522.279859]  [<ffffffff8109ad00>] ? kthread_create_on_node+0x1f0/0x1f0
Apr  3 16:48:15 laptop kernel: [ 2522.279861]  [<ffffffff817f311f>] ret_from_fork+0x3f/0x70
Apr  3 16:48:15 laptop kernel: [ 2522.279863]  [<ffffffff8109ad00>] ? kthread_create_on_node+0x1f0/0x1f0
Apr  3 16:48:24 laptop kernel: [ 2530.881270] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.1.1 LEN=94 TOS=0x00 PREC=0x00 TTL=64 ID=5867 DF PROTO=UDP SPT=49703 DPT=53 LEN=74 
Apr  3 16:48:24 laptop kernel: [ 2530.881304] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.1.1 LEN=94 TOS=0x00 PREC=0x00 TTL=64 ID=5867 DF PROTO=UDP SPT=49703 DPT=53 LEN=74 

```

Then it repeats, trying to resolve. And lastly, I rebooted the system and saw it hang up at the following for about 30 seconds or so, before resuming the shut down process:

```
Stopped target Remote File Systems.
Stopped target Remote File Systems (pre).
Stopped target User and Group Name Lookups.
```

So.... how 'normal' is any of this?  Are the messages from syslog above cause for concern?

---

