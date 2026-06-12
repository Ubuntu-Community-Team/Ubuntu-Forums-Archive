---
title: "how to display the hello world module result in the command line?"
date: 2012-01-24
forum: Programming Talk
---

### Post by anoopajay87 on 2012-01-24
hi guys,
i was trying to run the simple hello world program...

```
#include <linux/init.h>
#include <linux/module.h>
MODULE_LICENSE("Dual BSD/GPL");

static int hello_init(void)
{
    printk(KERN_ALERT "Hello, world\n");
    return 0;
}

static void hello_exit(void)
{
    printk(KERN_ALERT "Goodbye, cruel world\n");
}

module_init(hello_init);
module_exit(hello_exit);

```

i used the following make file..


obj-m += hello.o
all:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

i was able to built the make file and isert the module in to kernel using insmod command
but when i tried using this command "sudo insmod ./hello.ko"
i was not able to get the result displayed on the command line,instead the result was written in the system log(syslog)

how can i get the result displayed in the command line on executing the program?
can you please help me?

---

### Post by WthIteh on 2012-01-24
Kernel messages get printed on tty1 by default.
Press Ctrl+Shift+F1 to see your messages.
Press Ctrl+Shift+F7 to return to your X11 screen ;)

---

### Post by epicoder on 2012-01-24
If I recall correctly, TTY1 by default is just a login shell, and TTY8 (Ctrl+Shift+F8) shows kernel messages.

Of course you could also just run [FONT=Courier New]dmesg | tail [/FONT]in the terminal.

---

### Post by anoopajay87 on 2012-01-25
thanks brother , [FONT=Courier New]dmesg | tail i[/FONT]s working for me
is there any way to specifically display that single result in the terminal?

---

