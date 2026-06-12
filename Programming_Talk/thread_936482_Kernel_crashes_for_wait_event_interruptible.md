---
title: "Kernel crashes for wait_event_interruptible"
date: 2008-10-02
forum: Programming Talk
---

### Post by akshata on 2008-10-02
Hi,
    Im trying to create a kernel thread in linux that wakes up intermittently and performs some operations after the timeout value.
static DECLARE_WAIT_QUEUE_HEAD(wait);
static int mythread(void *data)
{
        while(1)
        {
             wait_event_interruptible_timeout(wq,0,HZ*4);
             ..................
              .................
        }
}
int init_module()
{
       static task struct *k=kthread_create(mythread,data,"thread 1");
       wake_up_process(k);
}

void cleanup_module()
{
}

Here if i give stop_thread(k) or force_sig(SIGKILL,k) in cleanup module, the machine hangs when i try to insmod my module.
However if i do not use both these, when i insmod and rmmod my module i get the following exception..
I get the same when i use wait_event_timeout() also.


[43617.893194] BUG: unable to handle kernel paging request at virtual address d0b394bf
[43617.893286] printing eip: d0b394bf *pde = 0f015067 *pte = 00000000 
[43617.893458] Oops: 0000 [#5] SMP 
[43617.893465] Modules linked in: ksocket isofs udf ipv6 af_packet rfcomm l2cap bluetooth ppdev cpufreq_ondemand cpufreq_conservative cpufreq_userspace cpufreq_powersave cpufreq_stats freq_table video output sbs sbshc dock battery iptable_filter ip_tables x_tables lp snd_ens1371 gameport snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm parport_pc parport snd_seq_dummy evdev serio_raw pcspkr psmouse snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq container snd_timer snd_seq_device snd soundcore snd_page_alloc ac button i2c_piix4 i2c_core shpchp pci_hotplug intel_agp agpgart ext3 jbd mbcache sg sr_mod cdrom sd_mod ata_generic floppy ehci_hcd pcnet32 mii BusLogic uhci_hcd usbcore ata_piix pata_acpi libata scsi_mod thermal processor fan fbcon tileblit font bitblit softcursor fuse
[43617.893554] 
[43617.893560] Pid: 11548, comm: thread 1 Tainted: P      D (2.6.24-16-generic #1)
[43617.893564] EIP: 0060:[<d0b394bf>] EFLAGS: 00010246 CPU: 0
[43617.893699] EIP is at 0xd0b394bf
[43617.893703] EAX: 00000000 EBX: c5ff7fa0 ECX: 00000282 EDX: 00000000
[43617.893706] ESI: c5ff7fb4 EDI: 000061a8 EBP: c5ff7fac ESP: c5ff7f8c
[43617.893709]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[43617.893715] Process thread 1 (pid: 11548, ti=c5ff6000 task=c6fcb0e0 task.ti=c5ff6000)
[43617.893718] Stack: d0b3989e 00000000 cd9d05a0 c04720e0 cec3aa80 00000000 c6fcb0e0 c0140b70 
[43617.893726]        d0b3a3f8 d0b3a3f8 48710002 0f05001e 00000000 00000000 fffffffc d0b39020 
[43617.893734]        d0b39380 00000000 c01408b2 c0140870 00000000 00000000 c0105677 cfb5fe74 
[43617.893741] Call Trace:
[43617.893754]  [<c0140b70>] autoremove_wake_function+0x0/0x40
[43617.893950]  [<c01408b2>] kthread+0x42/0x70
[43617.893955]  [<c0140870>] kthread+0x0/0x70
[43617.893963]  [<c0105677>] kernel_thread_helper+0x7/0x10
[43617.894013]  =======================
[43617.894015] Code:  Bad EIP value.
[43617.894095] EIP: [<d0b394bf>] 0xd0b394bf SS:ESP 0068:c5ff7f8c
[43617.894109] ---[ end trace 29a9b90959cc2403 ]---




This come initially, at the time i insmod the module. After this, the thread gets created and sleeps and wakes up as desired. The same thing happens if i remove the module. Could someone please provide a solution for this.

I am not able to debug this since this exception is printed before my thread is created,but i gather fromt the trace it has to do with some auto wake function?? Need help badly..

---

### Post by akshata on 2008-10-03
If anyone knows the answer please help!!!!

---

### Post by akshata on 2008-10-04
Please anybody out there? Somebody :(

---

