---
title: "Boot ubuntu23.04 error with risc-v UEFI EDKII"
date: 2023-06-29
forum: New to Ubuntu
---

### Post by edenzhang6688 on 2023-06-29
Hello&#65292;

When booting the ubuntu23.04&#65292;the following error has occurred&#12290;So, what do I need to do&#65311;&#65311;&#65311;


MotherBoard&#65306;Sifive Hifive Unmatched U740 Soc
Firmware&#65306;UEFI RISC-V EDKII


Ubuntu Error message as follow&#65306;


Loading, please wait...
Starting systemd-udevd version 252.5-2ubuntu3
[ 22.280928] Unable to handle kernel paging request at virtual address 000000000200bff8
[ 22.288326] Oops [#1]
[ 22.290399] Modules linked in: rtc_efi(+)
[ 22.294395] CPU: 1 PID: 64 Comm: kworker/u8:2 Not tainted 6.2.0-19-generic #19.1-Ubuntu
[ 22.302390] Hardware name: SiFive HiFive Unmatched A00 (DT)
[ 22.307946] Workqueue: efi_rts_wq efi_call_rts
[ 22.312370] epc : 0x200c1e7e
[ 22.315242] ra : 0x200c1b32
[ 22.318098] epc : 00000000200c1e7e ra : 00000000200c1b32 sp : ffffffd87f873cf0
[ 22.325314] gp : ffffffff8283f340 tp : ffffffd87f69c100 t0 : 000000011ffe4801
[ 22.332525] t1 : 000000000200bff8 t2 : 0000000000000000 s0 : ffffffd87f873d00
[ 22.339745] s1 : ffffffff829373e8 a0 : 0000000000000000 a1 : 0000000000000001
[ 22.346950] a2 : 0000000000000000 a3 : 0000000000000000 a4 : 0000000000000000
[ 22.354152] a5 : 0000000000000000 a6 : 0000000000000000 a7 : 00000000200a6448
[ 22.361369] s2 : ffffffdbfa873a18 s3 : ffffffdbfa873a08 s4 : 0000000200000022
[ 22.368572] s5 : 0000000000000000 s6 : 0000000000000000 s7 : ffffffd87ef05505
[ 22.375782] s8 : ffffffff80e81688 s9 : ffffffd87ef09400 s10: 0000000000000402
[ 22.382991] s11: ffffffd87f1fa180 t3 : 0000000000000000 t4 : 0000000000000000
[ 22.390205] t5 : 0000000000000000 t6 : ffffffd87ef8d000
[ 22.395510] status: 0000000200000120 badaddr: 000000000200bff8 cause: 000000000000000d
[ 22.403631] ---[ end trace 0000000000000000 ]---
[ 22.456172] da9063 0-0058: Device detected (chip-ID: 0x61, var-ID: 0x73)
[ 22.598958] macb 10090000.ethernet: Registered clk switch 'sifive-gemgxl-mgmt'
[ 82.600000] rcu: INFO: rcu_sched detected stalls on CPUs/tasks:
[ 82.605196] rcu: 3-...!: (0 ticks this GP) idle=8c44/1/0x4000000000000000 softirq=1372/1372 fqs=9
[ 82.614125] (detected by 1, t=15002 jiffies, g=2629, q=385 ncpus=4)
[ 82.620460] Task dump for CPU 3:
[ 82.623671] task:systemd-udevd state:R running task stack:0 pid:115 ppid:110 flags:0x00000008
[ 82.633579] Call Trace:
[ 82.636006] [<ffffffff80b8b15c>] __schedule+0x252/0x5fa
[ 82.641226] rcu: rcu_sched kthread timer wakeup didn't happen for 14982 jiffies! g2629 f0x0 RCU_GP_WAIT_FQS(5) ->state=0x402
[ 82.652427] rcu: Possible timer handling issue on cpu=2 timer-softirq=898
[ 82.659286] rcu: rcu_sched kthread starved for 14983 jiffies! g2629 f0x0 RCU_GP_WAIT_FQS(5) ->state=0x402 ->cpu=2
[ 82.669537] rcu: Unless rcu_sched kthread gets sufficient CPU time, OOM is now expected behavior.
[ 82.678483] rcu: RCU grace-period kthread stack dump:
[ 82.683517] task:rcu_sched state:I stack:0 pid:14 ppid:2 flags:0x00000000
[ 82.691859] Call Trace:
[ 82.694288] [<ffffffff80b8b15c>] __schedule+0x252/0x5fa
[ 82.699499] [<ffffffff80b8b550>] schedule+0x4c/0xde
[ 82.704362] [<ffffffff80b912f4>] schedule_timeout+0x8c/0x156
[ 82.710009] [<ffffffff8009eda8>] rcu_gp_fqs_loop+0x2fa/0x3aa
[ 82.715656] [<ffffffff800a0cc2>] rcu_gp_kthread+0x11a/0x142
[ 82.721214] [<ffffffff8003eb6e>] kthread+0xbe/0xd4
[ 82.725989] [<ffffffff80003e90>] ret_from_exception+0x0/0x16
[ 82.731639] rcu: Stack dump where RCU GP kthread last ran:
[ 82.737109] Task dump for CPU 2:
[ 82.740322] task:probe-bcache state:R running task stack:0 pid:142 ppid:120 flags:0x00000000
[ 82.750228] Call Trace:
[ 82.752655] [<ffffffff80b8b15c>] __schedule+0x252/0x5fa
[ 262.632000] rcu: INFO: rcu_sched detected stalls on CPUs/tasks:
[ 262.637191] rcu: 3-...0: (0 ticks this GP) idle=8c44/1/0x4000000000000000 softirq=1372/1372 fqs=9003
[ 262.646383] (detected by 1, t=60010 jiffies, g=2629, q=385 ncpus=4)
[ 262.652719] Task dump for CPU 3:
[ 262.655929] task:systemd-udevd state:R running task stack:0 pid:115 ppid:110 flags:0x00000008
[ 262.665838] Call Trace:
[ 262.668264] [<ffffffff80b8b15c>] __schedule+0x252/0x5fa

---

### Post by MAFoElffen on 2023-06-29
<< Duplicate thread to: [https://ubuntuforums.org/showthread.php?t=2488265](https://ubuntuforums.org/showthread.php?t=2488265) >>

---

