---
title: "Ubuntu freezes randomly"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by kotsiosp on 2008-06-21
Sometimes the whole system freezes. The mouse cursor moves but i cannot click on anything. The keyboard appears to work because i can switch keyboard layouts but that's it. If i hit ctrl+alt+backspace then everything disappears except the wallpaper and just hangs there.
Does anyone know how to fix this, or at least find the cause of this?

---

### Post by Joeb454 on 2008-06-21
Well what are you doing at the time?

Is there anything you're running at the time (i.e. every time it crashes is there 1 app that is always open etc.)

---

### Post by kotsiosp on 2008-06-21
Well, i tried to answer that myself but i can't think of anything specific. Firefox is almost always open, and usually amarok. It's pretty much random. It can happen browsing the internet, browsing through files or playing a game. I don't think it's application-specific. Yet, i'm no expert.

---

### Post by kotsiosp on 2008-06-25
Well, it seems it's a Hardy problem after all.
Anyway, just if it helps someone i thought i'd post this:
I'm running Ubuntu Hardy Heron on an Acer Aspire 5024. This machine comes with an Ati X700 graphics card. I've been using Envy NG to download and install the latest Ati drivers. I removed the "Envy" drivers, uninstalled the program itself and installed the "Ati binary xorg drivers". So far, no crashes so i'm hoping the problem is gone for good (it's been a day already without any crashes).
Hope it solves someone other's problem too.

---

### Post by stalkier on 2008-06-25
> **kotsiosp said:**
> Well, i tried to answer that myself but i can't think of anything specific. Firefox is almost always open, and usually amarok. It's pretty much random. It can happen browsing the internet, browsing through files or playing a game. I don't think it's application-specific. Yet, i'm no expert.

Personally I experienced the same thing. I believe this is because of FireFox 3. I did a total removal and deleted the hidden directory. I then installed FF2. It works great. I have had no lockups in about 3+ days. I submitted the bug with lauchpad.net. Just try it and see if it works for you as well.

---

### Post by kotsiosp on 2008-06-26
Thanx for the reply stalkier, but as i posted before the problem appears to be solved. It seems it had something to do with the Ati drivers. 
At some point i did suspect Firefox too. Come to thing of it, it was ALWAYS "suspiciously" running when a crash would occur. But if you look around the fora you will see that a lot of people have lockup problems with Hardy for no apparent reason. No log messages, nothing. It could be anything. In my case, looks as it was the official Ati drivers.
I 'm going to wait for a while to see if i get any crashes before marking this as "solved".

---

### Post by stalkier on 2008-06-26
> **kotsiosp said:**
> Thanx for the reply stalkier, but as i posted before the problem appears to be solved. It seems it had something to do with the Ati drivers. 
At some point i did suspect Firefox too. Come to thing of it, it was ALWAYS "suspiciously" running when a crash would occur. But if you look around the fora you will see that a lot of people have lockup problems with Hardy for no apparent reason. No log messages, nothing. It could be anything. In my case, looks as it was the official Ati drivers.
I 'm going to wait for a while to see if i get any crashes before marking this as "solved".

Understood man. You are right it can be caused for 100s of reasons. Mine just happened to be cause by FF3 (I believe). No lockups yet with FF2 installed.

---

### Post by Tha-Fox on 2008-07-24
I had the "same" problem and I solved it by downgrading to Gutsy. Now I installed Hardy again and I haven't experienced this problem for now. Here is one big report that might suit to our case: [https://bugs.launchpad.net/bugs/204996](https://bugs.launchpad.net/bugs/204996)

kotsiosp: I have also Acer 5024.

---

### Post by Tha-Fox on 2008-07-24
> **Tha-Fox said:**
> I had the "same" problem and I solved it by downgrading to Gutsy. Now I installed Hardy again and I haven't experienced this problem for now.

Now I have :( Today my Acer crashed twice in 15 minutes. First time there was Pidgin-conversation and Firefox (in Facebook) open. Second time I did nothing after booting. I just let it hang itself. It took about 10 minutes.

When I last time experienced these freezes right after the release of Hardy, I noticed that my clock started to slow down when this crash happened. If I left the desktop alone after booting, at some point clock was 1 minute behind, after a while it was 5 minutes behind and so on. I haven't checked if this is the case now, too.

When these freezes happen, I use sysrq + alt + r,e,i,s,u,b to reboot the machine. So Ubuntu is working at some level.

---

### Post by Tha-Fox on 2008-07-31
I've tried to put "pci=routeirq" to kernel options, no luck yet. I've had lockups almost daily. I've no desktop effects in use. I think I could try without fglrx-drivers and see what happens. Here's some logs from the lockup yesterday:

Daemon.log

Jul 28 06:59:39 ubuntu-laptop avahi-daemon[5083]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.4.222.
Jul 28 06:59:39 ubuntu-laptop avahi-daemon[5083]: New relevant interface wlan0.IPv4 for mDNS.
Jul 28 06:59:39 ubuntu-laptop avahi-daemon[5083]: Registering new address record for 169.254.4.222 on wlan0.IPv4.
Jul 28 06:59:43 ubuntu-laptop avahi-autoipd(wlan0)[18775]: Successfully claimed IP address 169.254.4.222
Jul 28 06:59:43 ubuntu-laptop NetworkManager: <info>  DHCP daemon state is now 8 (timeout) for interface wlan0 
Jul 28 06:59:43 ubuntu-laptop NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface wlan0 
Jul 28 06:59:43 ubuntu-laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface wlan0 

Debub-log:

Jul 28 06:18:47 ubuntu-laptop kernel: [ 8147.745836] wlan0: authenticate with AP 00:1a:9f:13:f4:6c
Jul 28 06:18:47 ubuntu-laptop kernel: [ 8147.945665] wlan0: authentication with AP 00:1a:9f:13:f4:6c timed out

Kern-log:

Jul 28 07:29:06 ubuntu-laptop kernel: t lockup - CPU#0 stuck for 11s! [swapper:0]
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.484591] 
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.484595] Pid: 0, comm: swapper Tainted: P        (2.6.24-20-generic #1)
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.484601] EIP: 0060:[mac80211:_spin_unlock_irqrestore+0xd/0x40] EFLAGS: 00000286 CPU: 0
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.484607] EIP is at _spin_unlock_irqrestore+0xd/0x20
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.484611] EAX: 00000286 EBX: 00000001 ECX: 00000286 EDX: 00000000
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.484617] ESI: ffffffff EDI: df852008 EBP: 00000000 ESP: c041df34
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.484622]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.484627] CR0: 8005003b CR2: 086248c8 CR3: 3365a000 CR4: 00000690
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.484632] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.484636] DR6: ffff0ff0 DR7: 00000400
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.484640]  [tick_notify+0x25b/0x390] tick_notify+0x25b/0x390
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.484699]  [notifier_call_chain+0x30/0x60] notifier_call_chain+0x30/0x60
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.484738]  [raw_notifier_call_chain+0x17/0x20] raw_notifier_call_chain+0x17/0x20
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.484757]  [processor:clockevents_notify+0x19/0x5770] clockevents_notify+0x19/0x60
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.484779]  [<f88695cd>] acpi_idle_enter_simple+0x166/0x1b9 [processor]
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.484831]  [cpuidle_idle_call+0x7c/0xb0] cpuidle_idle_call+0x7c/0xb0
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.484848]  [cpu_idle+0x45/0xd0] cpu_idle+0x45/0xd0
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.484870]  [start_kernel+0x31f/0x3b0] start_kernel+0x31f/0x3b0
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.484882]  [unknown_bootoption+0x0/0x1e0] unknown_bootoption+0x0/0x1e0
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.484942]  =======================
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.493973] BUG: soft lockup - CPU#0 stuck for 11s! [swapper:0]
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.493977] 
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.493981] Pid: 0, comm: swapper Tainted: P        (2.6.24-20-generic #1)
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.493986] EIP: 0060:[mac80211:_spin_unlock_irqrestore+0xd/0x40] EFLAGS: 00000286 CPU: 0
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.493993] EIP is at _spin_unlock_irqrestore+0xd/0x20
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.493997] EAX: 00000286 EBX: 00000001 ECX: 00000286 EDX: 00000000
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.494002] ESI: ffffffff EDI: df852008 EBP: 00000000 ESP: c041df34
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.494007]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.494012] CR0: 8005003b CR2: 086248c8 CR3: 3365a000 CR4: 00000690
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.494017] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.494022] DR6: ffff0ff0 DR7: 00000400
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.494025]  [tick_notify+0x25b/0x390] tick_notify+0x25b/0x390
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.494085]  [notifier_call_chain+0x30/0x60] notifier_call_chain+0x30/0x60
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.494124]  [raw_notifier_call_chain+0x17/0x20] raw_notifier_call_chain+0x17/0x20
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.494143]  [processor:clockevents_notify+0x19/0x5770] clockevents_notify+0x19/0x60
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.494165]  [<f88695cd>] acpi_idle_enter_simple+0x166/0x1b9 [processor]
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.494216]  [cpuidle_idle_call+0x7c/0xb0] cpuidle_idle_call+0x7c/0xb0
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.494233]  [cpu_idle+0x45/0xd0] cpu_idle+0x45/0xd0
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.494255]  [start_kernel+0x31f/0x3b0] start_kernel+0x31f/0x3b0
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.494267]  [unknown_bootoption+0x0/0x1e0] unknown_bootoption+0x0/0x1e0
Jul 28 07:29:06 ubuntu-laptop kernel: [12603.494325]  =======================

And then there's these soft-lockup -notifications about 50-100.

Messages

Jul 28 07:29:07 ubuntu-laptop kernel: [12604.423637]  =======================
Jul 28 07:52:57 ubuntu-laptop -- MARK --

System-log

Jul 28 07:30:01 ubuntu-laptop /USR/SBIN/CRON[32477]: (root) CMD (test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null)
Jul 28 07:30:02 ubuntu-laptop anacron[32502]: Anacron 2.3 started on 2008-07-28
Jul 28 07:30:02 ubuntu-laptop anacron[32502]: Normal exit (0 jobs run)
Jul 28 07:52:57 ubuntu-laptop -- MARK --

User.log

Jul 28 06:59:43 ubuntu-laptop dhcdbd: Unrequested down ?:3

---

### Post by Tha-Fox on 2008-07-31
And today it locked up again. I was sleeping, but according to the clock in the upper right corner and clock in the screenlet this happened 10:09 am. I searched logs for something useful and put them [here]("http://pastebin.com/f607b88ca").
The Finnish part 
"Vakava X-virhe – :0 käynnistetään uudelleen" 
means approximately 
"Serious X-error - :0 reboot".

Every time computer crashes I can click once somewhere and it doesn't work. Once there was Firefox on top and I tried to shut it down. I clicked "x" and nothing happened but I saw, how the button was activated. Then I tried to shut it from the panel below. I chose "close" and after a while it asked me to wait or force to quit. I forced and it worked. But after that nothing except ctrl-alt-backspace and alt-sysrq-REISUB worked. The first gives me always blank wallpaper with nothing on it. Then only the latter works and boots the machine.

Today I tried to shut the computer down by pushing the power button on upper right corner of the desktop. When I moved the cursor on it, button was activated. After clicking on it, nothing happened. So if I understand correctly, I can click something once and it doesn't work and after that everything except those two commands nothing works.

---

