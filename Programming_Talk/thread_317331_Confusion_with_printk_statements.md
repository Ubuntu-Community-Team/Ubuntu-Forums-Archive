---
title: "Confusion with printk statements"
date: 2006-12-12
forum: Programming Talk
---

### Post by smith.norton on 2006-12-12
I am trying the following kernel module in Ubuntu-6.06 LTS.

#include <linux/module.h>
#include <linux/kernel.h>
#include <linux/init.h>

MODULE_LICENSE("GPL");

static int __init helloinit(void)
{
        printk(KERN_ALERT, "[helloinit1]\n");
        printk("[helloinit2]\n");
        return 0;
}

static void __exit helloexit(void)
{
        printk(KERN_ALERT, "[helloexit1]\n");
        printk("[helloexit2]\n");
}

module_init(helloinit);
module_exit(helloexit);

After compiling it with 'make', I 'insmod' it and then 'rmmod' it twice. The last few lines of /var/log/kern.log are as follows:-

Dec 11 23:14:40 localhost kernel: [4295711.583000] <1><1>[helloinit2]
Dec 11 23:14:45 localhost kernel: [4298099.296000] [helloexit2]
Dec 11 23:15:22 localhost kernel: [4298136.092000] [helloinit2]
Dec 11 23:15:27 localhost kernel: [4298141.000000] [helloexit2]

1. According to LKMPG '[helloinit1]' and '[helloexit1]' should have been printed. Why weren't they printed. Instead the <1> (KERN_ALERT) was printed. Here are all the macro defintions in my Ubuntu box:-

smith@smithbox:~/kernel/exp$ grep "define" /usr/src/linux-headers-`uname -r`/include/linux/kernel.h | grep "KERN_"
#define KERN_EMERG      "<0>"   /* system is unusable                   */
#define KERN_ALERT      "<1>"   /* action must be taken immediately     */
#define KERN_CRIT       "<2>"   /* critical conditions                  */
#define KERN_ERR        "<3>"   /* error conditions                     */
#define KERN_WARNING    "<4>"   /* warning conditions                   */
#define KERN_NOTICE     "<5>"   /* normal but significant condition     */
#define KERN_INFO       "<6>"   /* informational                        */
#define KERN_DEBUG      "<7>"   /* debug-level messages                 */

smith@smithbox:~/kernel/exp$ grep "int printk(" /usr/src/linux-headers-`uname -r`/include/linux/kernel.h
asmlinkage int printk(const char * fmt, ...)
static inline int printk(const char *s, ...)
static inline int printk(const char *s, ...) { return 0; }

Why aren't '[helloinit1]' and '[helloexit1]' getting printed?

2. According to the sequence of statements, the output should have been:-

<1>[helloinit2]
<1>[helloexit2]
<1>[helloinit2]
<1>[helloexit2]

But the output instead is:-

<1><1>[helloinit2]
[helloexit2]
[helloinit2]
[helloexit2]

Why?

---

### Post by duff on 2006-12-12
trying getting rid of the comma after KERN_ALERT.  This will concatinate those 2 strings.

---

