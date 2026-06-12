---
title: "SEGFAULT - Unable to handle kernel paging request at virtual address"
date: 2013-01-18
forum: Programming Talk
---

### Post by mhaines4102 on 2013-01-18
I am trying to compile sierra.ko for Quantal. I am using OMAP4 and linaro. sierra_net compiles just fine, but it looks like usb/serial has changed how the registration and deregistration function calls.

(from Ubuntu 12:10 - /usr/src/linux-headers-3.4.0-2-linaro-llt-omap/include/linux/usb/serial.h )
extern int usb_serial_register_drivers(struct usb_driver *udriver,
struct usb_serial_driver * const serial_drivers[]);
extern void usb_serial_deregister_drivers(struct usb_driver *udriver,
struct usb_serial_driver * const serial_drivers[]);

Instead of (from Ubuntu 12:04 - /usr/src/linux-headers-3.2.0-1412/include/linux/usb/serial.h)
extern int usb_serial_register(struct usb_serial_driver *driver);
extern void usb_serial_deregister(struct usb_serial_driver *driver);


ISSUE: I made the changes necessary in sierra.c. Compilation is clean now. Modprobe blows up. I put in a printk so I can see the structure data. It looks good (in the log it is offset by ^^^). The driver seems to register fine but then I get a segfault on a memory page request. 

I am a little stuck now. Any help would be great.

I am attaching the latest code and the segfault from syslog:

*************** SYSLOG ****************

Jan 18 14:53:56 linaro-server kernel: [ 233.561981] USB Serial support registered for generic
Jan 18 14:53:56 linaro-server kernel: [ 233.598419] usbserial: USB Serial Driver core

^^^ My printk ^^^
Jan 18 14:53:56 linaro-server kernel: [ 233.621246] registering driver: sierra - described as: Sierra USB modem
^^^

Jan 18 14:53:56 linaro-server kernel: [ 233.622619] usbcore: registered new interface driver sierra
Jan 18 14:53:56 linaro-server kernel: [ 233.639648] USB Serial support registered for Sierra USB modem
Jan 18 14:53:56 linaro-server kernel: [ 233.639739] Unable to handle kernel paging request at virtual address 0f3d004f
Jan 18 14:53:56 linaro-server kernel: [ 233.667114] pgd = eb03c000
Jan 18 14:53:56 linaro-server kernel: [ 233.670288] [0f3d004f] *pgd=00000000
Jan 18 14:53:56 linaro-server kernel: [ 233.674438] Internal error: Oops: 805 [#1] PREEMPT SMP THUMB2
Jan 18 14:53:56 linaro-server kernel: [ 233.680999] Modules linked in: sierra(O+) usbserial arc4 wl12xx wlcore mac80211 cfg80211 wlcore_sdio gator
Jan 18 14:53:56 linaro-server kernel: [ 233.692535] CPU: 1 Tainted: G O (3.4.0-2-linaro-llt-omap #2~ci+121213205950-Ubuntu)
Jan 18 14:53:56 linaro-server kernel: [ 233.702728] PC is at usb_serial_register_drivers+0x37/0x8c [usbserial]
Jan 18 14:53:56 linaro-server kernel: [ 233.710296] LR is at trace_hardirqs_on_caller+0xd3/0x110
Jan 18 14:53:56 linaro-server kernel: [ 233.716369] pc : [<bf918898>] lr : [<c005e493>] psr: 200f0133
Jan 18 14:53:56 linaro-server kernel: [ 233.716400] sp : ea887f28 ip : 00000020 fp : 01d38e40
Jan 18 14:53:56 linaro-server kernel: [ 233.729553] r10: bf9280e0 r9 : 00000000 r8 : 00000000
Jan 18 14:53:56 linaro-server kernel: [ 233.735504] r7 : bf9280e4 r6 : bf9280e0 r5 : bf9280dc r4 : bf9289cc
Jan 18 14:53:56 linaro-server kernel: [ 233.743041] r3 : 0f3d0003 r2 : 00000000 r1 : eb3a0a80 r0 : 00000000
Jan 18 14:53:56 linaro-server kernel: [ 233.750579] Flags: nzCv IRQs on FIQs on Mode SVC_32 ISA Thumb Segment user
Jan 18 14:53:56 linaro-server kernel: [ 233.759002] Control: 50c5387d Table: ab03c04a DAC: 00000015
Jan 18 14:53:56 linaro-server kernel: [ 233.765594] 
Jan 18 14:53:56 linaro-server kernel: [ 233.765594] LR: 0xc005e413:
Jan 18 14:53:56 linaro-server kernel: [ 233.770507] e410 d1262b00 781b4b2d f1f6b15b 2800fba9 4b28d04a 2b00681b 4827d146 2119f640
Jan 18 14:53:56 linaro-server kernel: [ 233.780181] e430 466ae013 53fff422 031ff023 f8d368db b1733458 fb94f1f6 d0352800 681b4b1d
Jan 18 14:53:56 linaro-server kernel: [ 233.789825] e450 d1312b00 f44f481c e8bd6122 f7ce4070 466ab9ff f4222501 210053ff 031ff023
Jan 18 14:53:56 linaro-server kernel: [ 233.799499] e470 f8c268da 68dc5484 f8c44620 f7ff5454 b180ff0d 346cf8d4 4620b123 f7ff4629
Jan 18 14:53:56 linaro-server kernel: [ 233.809143] e490 b140ff05 3440f8d4 6444f8c4 f8c43301 f8c43440 466a344c 53fff422 f0232200
Jan 18 14:53:56 linaro-server kernel: [ 233.818786] e4b0 68db031f 2484f8c3 bf00bd70 c07edf50 c081cc88 c0db822c c0628105 c079eac4
Jan 18 14:53:56 linaro-server kernel: [ 233.828460] e4d0 4670b500 eb04f85d bf72f7ff 41f0e92d f422466a 460553ff 031ff023 68df4688
Jan 18 14:53:56 linaro-server kernel: [ 233.838104] e4f0 681b4b18 d02b2b00 8400f3ef f7fdb672 2600f853 c480f8d7 eb052018 e0110208
Jan 18 14:53:56 linaro-server kernel: [ 233.847747] e510 7306fb00 6391f503 f10168d9 45450810 428ad201 3601d801 4638e004 f7fd4629
Jan 18 14:53:56 linaro-server kernel: [ 233.857421] 
Jan 18 14:53:56 linaro-server kernel: [ 233.857421] SP: 0xea887ea8:
Jan 18 14:53:56 linaro-server kernel: [ 233.862304] 7ea8 ea430020 bf91c420 00000000 00000001 0000001c bf9280dc 01d38e40 c02bc095
Jan 18 14:53:56 linaro-server kernel: [ 233.871948] 7ec8 eb3a0a80 bf918898 200f0133 ffffffff ea887f14 c046e679 00000000 eb3a0a80
Jan 18 14:53:56 linaro-server kernel: [ 233.881622] 7ee8 00000000 0f3d0003 bf9289cc bf9280dc bf9280e0 bf9280e4 00000000 00000000
Jan 18 14:53:56 linaro-server kernel: [ 233.891265] 7f08 bf9280e0 01d38e40 00000020 ea887f28 c005e493 bf918898 200f0133 ffffffff
Jan 18 14:53:56 linaro-server kernel: [ 233.900939] 7f28 bf928994 bf92b001 00000000 00006a18 c000c344 ea886000 00000000 bf92b01b
Jan 18 14:53:56 linaro-server kernel: [ 233.910583] 7f48 ea886000 bf928b60 bf92b001 c0008605 00000000 00000001 bf928b60 bf928b60
Jan 18 14:53:56 linaro-server kernel: [ 233.920227] 7f68 01d3bfd8 bf928b60 01d3bfd8 00000000 00006a18 c000c344 ea886000 c0065827
Jan 18 14:53:56 linaro-server kernel: [ 233.929901] 7f88 b6eea000 00006a18 01d3bfd8 01d380d8 00000008 00000000 00000080 c000c121
Jan 18 14:53:56 linaro-server kernel: [ 233.939544] 
Jan 18 14:53:56 linaro-server kernel: [ 233.939544] R1: 0xeb3a0a00:
Jan 18 14:53:56 linaro-server kernel: [ 233.944427] 0a00 eb3a09fc 00000000 00000000 eb3a09d4 c0d9f030 00000000 00000000 c0631339
Jan 18 14:53:56 linaro-server kernel: [ 233.954101] 0a20 eb3a0a20 eb3a0a20 00000000 00000000 00000000 ed0c0188 00000000 00000020
Jan 18 14:53:56 linaro-server kernel: [ 233.963867] 0a40 00000000 0000c350 0000c350 00000000 00000000 00000000 00000001 00000000
Jan 18 14:53:56 linaro-server kernel: [ 233.973632] 0a60 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
Jan 18 14:53:56 linaro-server kernel: [ 233.983398] 0a80 00000000 ea886000 00000002 00400100 00000000 00000000 00000001 00000001
Jan 18 14:53:56 linaro-server kernel: [ 233.993133] 0aa0 00000078 00000078 00000078 00000000 c047a63c 00000000 00000400 00400000
Jan 18 14:53:56 linaro-server kernel: [ 234.002899] 0ac0 eb332ac0 00000000 00000000 c1943f9c c1943f9c 00000001 6832c4b0 00000036
Jan 18 14:53:56 linaro-server kernel: [ 234.012664] 0ae0 034a619a 00000000 1f3051e0 00000004 02bc5ac5 00000000 00000006 00000000
Jan 18 14:53:56 linaro-server kernel: [ 234.022430] Process modprobe (pid: 2623, stack limit = 0xea8862f8)
Jan 18 14:53:56 linaro-server kernel: [ 234.029571] Stack: (0xea887f28 to 0xea888000)
Jan 18 14:53:56 linaro-server kernel: [ 234.034637] 7f20: bf928994 bf92b001 00000000 00006a18 c000c344 ea886000
Jan 18 14:53:56 linaro-server kernel: [ 234.043426] 7f40: 00000000 bf92b01b ea886000 bf928b60 bf92b001 c0008605 00000000 00000001
Jan 18 14:53:56 linaro-server kernel: [ 234.052185] 7f60: bf928b60 bf928b60 01d3bfd8 bf928b60 01d3bfd8 00000000 00006a18 c000c344
Jan 18 14:53:56 linaro-server kernel: [ 234.060943] 7f80: ea886000 c0065827 b6eea000 00006a18 01d3bfd8 01d380d8 00000008 00000000
Jan 18 14:53:56 linaro-server kernel: [ 234.069702] 7fa0: 00000080 c000c121 01d380d8 00000008 b6eea000 00006a18 01d3bfd8 00000001
Jan 18 14:53:56 linaro-server kernel: [ 234.078460] 7fc0: 01d380d8 00000008 00000000 00000080 01d3aa50 01d3a378 00000000 01d38e40
Jan 18 14:53:56 linaro-server kernel: [ 234.087219] 7fe0: 00018108 bee2f8f8 0000b043 b6f82270 600f0110 b6eea000 00000000 00000000
Jan 18 14:53:56 linaro-server kernel: [ 234.096008] [<bf918898>] (usb_serial_register_drivers+0x37/0x8c [usbserial]) from [<bf92b01b>] (sierra_init+0x1a/0x5b [sierra])
Jan 18 14:53:56 linaro-server kernel: [ 234.108367] [<bf92b01b>] (sierra_init+0x1a/0x5b [sierra]) from [<c0008605>] (do_one_initcall+0x69/0xf4)
Jan 18 14:53:56 linaro-server kernel: [ 234.118438] [<c0008605>] (do_one_initcall+0x69/0xf4) from [<c0065827>] (sys_init_module+0x4b/0x11c)
Jan 18 14:53:56 linaro-server kernel: [ 234.128143] [<c0065827>] (sys_init_module+0x4b/0x11c) from [<c000c121>] (ret_fast_syscall+0x1/0x52)
Jan 18 14:53:56 linaro-server kernel: [ 234.137817] Code: 4680 b9f8 462f e008 (64dc) f857 
Jan 18 14:53:56 linaro-server kernel: [ 234.155090] ---[ end trace ae63df9edb34bfc4 ]---

**************************************************************************************************** ****


************* Latest Code ***************
static struct usb_driver sierra_driver = {
        .name       = "sierra",
        .probe      = usb_serial_probe,
        .disconnect = usb_serial_disconnect,
        .suspend    = usb_serial_suspend,
        .resume     = usb_serial_resume,
        .reset_resume = sierra_reset_resume,
        .id_table   = id_table,

        .no_dynamic_id        = 1,
        .supports_autosuspend = 1,
};


static struct usb_serial_driver sierra_device = {
        .driver = {
                .owner =        THIS_MODULE,
                .name =         "sierra",
        },
        .description       = "Sierra USB modem",
        .id_table          = id_table,
        .usb_driver        = &sierra_driver,
        .calc_num_ports    = sierra_calc_num_ports,
        .probe             = sierra_probe,
        .open              = sierra_open,
        .close             = sierra_close,
        .dtr_rts           = sierra_dtr_rts,
        .write             = sierra_write,
        .write_room        = sierra_write_room,
        .set_termios       = sierra_set_termios,
        .tiocmget          = sierra_tiocmget,
        .tiocmset          = sierra_tiocmset,
        .attach            = sierra_startup,
        .release           = sierra_release,
        .port_probe        = sierra_create_sysfs_attrs,
        .port_remove       = sierra_remove_sysfs_attrs,
        .suspend           = sierra_suspend,
        .resume            = sierra_resume,
        .read_int_callback = sierra_instat_callback,

};


/************************
* Modified by Mike Haines
* 01-18-2013
************************/

static struct usb_serial_driver * const serial_drivers[1] = { &sierra_device };
static int __init sierra_init(void)
{

int retval = 0;

printk("registering driver: %s - described as: %s\n", sierra_driver.name, serial_drivers[0]->description );

retval = usb_serial_register_drivers(&sierra_driver, serial_drivers);
if (retval)
goto failed_device_register;

retval = usb_register(&sierra_driver);
if (retval)
goto failed_driver_register;

printk(KERN_INFO KBUILD_MODNAME ": " DRIVER_VERSION ":"
DRIVER_DESC "\n");

return 0;

failed_driver_register:
usb_serial_deregister_drivers(&sierra_driver, serial_drivers);

failed_device_register:
return retval;
}

static void __exit sierra_exit(void)
{
usb_deregister(&sierra_driver);
usb_serial_deregister_drivers(&sierra_driver, serial_drivers);
}

*******************************************************************************

---

### Post by mhaines4102 on 2013-01-18
I got that fixed. The issue was that the array of drivers is to be null terminated. I added a NULL pointer to the back of the array. I also changed my function and definition to look a little more standard. I have another problem now, but it has nothing to do with the segfault. 

/************************
* Modified by Mike Haines
* 01-18-2013
************************/
static struct usb_serial_driver * const serial_drivers[2] = { &sierra_device, NULL };
static int __init sierra_init(void)
{
        int retval = 0;

        printk("registering driver: %s - described as: %s\n", (*serial_drivers)->usb_driver->name, (*serial_drivers)->description );

        retval = usb_serial_register_drivers((*serial_drivers)->usb_driver, serial_drivers);
        if (retval)
                goto failed_device_register;

        retval = usb_register((*serial_drivers)->usb_driver);
        if (retval)
                goto failed_driver_register;

        printk(KERN_INFO KBUILD_MODNAME ": " DRIVER_VERSION ":"
               DRIVER_DESC "\n");

        return 0;

failed_driver_register:
        usb_serial_deregister_drivers((*serial_drivers)->usb_driver, serial_drivers);

failed_device_register:
        return retval;
}

static void __exit sierra_exit(void)
{
        usb_deregister(&sierra_driver);
        usb_serial_deregister_drivers(&sierra_driver, serial_drivers);
}
/******************************/

---

