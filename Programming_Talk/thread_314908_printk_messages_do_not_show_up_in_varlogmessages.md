---
title: "printk messages do not show up in /var/log/messages"
date: 2006-12-08
forum: Programming Talk
---

### Post by smith.norton on 2006-12-08
I tried to compile this program using make.

#include <linux/module.h>
#include <linux/kernel.h>

int init_module(void)
{
        printk(KERN_ALERT, "hello world\n");
	return 1;
}

void cleanup_module(void)
{
        printk(KERN_ALERT, "Good bye world\n");
}

I have two questions regarding this:-

1. Why is it showing on the following warning on make?
/home/smith/kernel/hello1.c:6: warning: too many arguments for format

2. When I load this module and unload, why doesn't the printk logs appear in /var/log/messages

smith@smith-laptop:~/kernel$ sudo insmod hello1.ko
smith@smith-laptop:~/kernel$ sudo rmmod hello1.ko
smith@smith-laptop:~/kernel$ tail -3 /var/log/messages
Dec  8 00:02:59 smith-laptop gconfd (smith-5081): Resolved address "xml:readwrite:/home/smith/.gconf" to a writable configuration source at position 0
Dec  8 00:08:16 smith-laptop exiting on signal 15
Dec  8 00:08:17 smith-laptop syslogd 1.4.1#17ubuntu7: restart.

---

### Post by lnostdal on 2006-12-08
I think you want `less /var/log/kern.log'

...might check `dmesg | less'. Routing of log-messages is specified in `/etc/syslog.conf'.

---

### Post by dmcbob on 2008-11-06
forgive me if this is stupid, but I originally tried printk like:
```
char c = 'c';
 printk(KERN_ERR, "put_queue: char = %c",(unsigned char) ch);
```

this didn't work, and I saw elsewhere in the same file (drivers/chars/keyboard.c) that they were omitting the comma:
```
printk(KERN_ERR "keyboard.c: k_lowercase was called - impossible\n");
```

...I've never seen anything like this...since KERN_ERR is defined in kernel.h with:
```
#define KERN_ERR        "<3>"   /* error conditions */
```   
shouldn't it fail to compile? What the guy in the second example is doing is like writing printk("something" "something"); Why would that work?

---

### Post by slavik on 2008-11-06
what is the definition of printk???

---

### Post by dmcbob on 2008-11-07
> **slavik said:**
> what is the definition of printk???

it takes a format string, followed by any arguments...so now it makes sense why I kept getting "<3>" printed out from dmesg and /var/logs/kern.log instead of the whole sentence.

PS: why the heck do people do stuff like printk(KERN_ERR "my message that will never be output to /var/log/kern.log"); ?

---

### Post by eip on 2010-06-06
> **dmcbob said:**
> forgive me if this is stupid, but I originally tried printk like:
```
char c = 'c';
 printk(KERN_ERR, &quot;put_queue: char = %c&quot;,(unsigned char) ch);
```this didn't work, and I saw elsewhere in the same file (drivers/chars/keyboard.c) that they were omitting the comma:
```
printk(KERN_ERR &quot;keyboard.c: k_lowercase was called - impossible\n&quot;);
```...I've never seen anything like this...since KERN_ERR is defined in kernel.h with:
```
#define KERN_ERR        &quot;<3>&quot;   /* error conditions */
```shouldn't it fail to compile? What the guy in the second example is doing is like writing printk(&quot;something&quot; &quot;something&quot;); Why would that work?

I know this is a belated reply... Since KERN_ERR is a macro, it is treated as a literal string. Adjacent literal strings are concatenated during compilation in C.

---

### Post by vectorio on 2012-01-19
> **lnostdal said:**
> I think you want `less /var/log/kern.log'

...might check `dmesg | less'. Routing of log-messages is specified in `/etc/syslog.conf'.

I do not find syslog.conf in /etc. Ubuntu 11.10. I checked on 10.04 LTS, same thing.

---

### Post by nothingspecial on 2012-01-19
This thread is old. Please start a new one detailing your specific problem.

Closed.

---

