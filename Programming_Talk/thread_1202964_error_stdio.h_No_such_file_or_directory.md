---
title: "error: stdio.h: No such file or directory"
date: 2009-07-02
forum: Programming Talk
---

### Post by simitoco on 2009-07-02
[SIZE=2]Hi All, 
Im new to English, Ubuntu, Programming and LDD :) (nice he?) 
Im trying to write a virtual device driver and i have lots of err,and i don't know what to do.. they are killing me. Please someone help me.
Im posting the terminal output and my code.
[/SIZE]
[SIZE=2][I]errors:

mladen@Vprasix:~/Desktop/test2$ [COLOR=Red]**make**[/COLOR]
make -C /lib/modules/2.6.24-23-generic/build M=/home/mladen/Desktop/test2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
  CC [M]  /home/mladen/Desktop/test2/lmain.o
/home/mladen/Desktop/test2/lmain.c: In function ‘lunix_ioctl’:
/home/mladen/Desktop/test2/lmain.c:297: warning: passing argument 2 of ‘copy_from_user’ makes pointer from integer without a cast
/home/mladen/Desktop/test2/lmain.c: In function ‘lunix_llseek’:
/home/mladen/Desktop/test2/lmain.c:253: warning: control reaches end of non-void function
/home/mladen/Desktop/test2/lmain.c: In function ‘lunix_ioctl’:
/home/mladen/Desktop/test2/lmain.c:279: warning: ‘count’ may be used uninitialized in this function
  CC [M]  /home/mladen/Desktop/test2/countchar.o
[B]/home/mladen/Desktop/test2/countchar.c:2:19: error: stdio.h: No such file or directory
/home/mladen/Desktop/test2/countchar.c:3:19: error: ctype.h: No such file or directory
/home/mladen/Desktop/test2/countchar.c:4:19: error: fcntl.h: No such file or directory[/B]
/home/mladen/Desktop/test2/countchar.c:7: warning: function declaration isn’t a prototype
/home/mladen/Desktop/test2/countchar.c: In function ‘main’:
/home/mladen/Desktop/test2/countchar.c:9: error: implicit declaration of function ‘printf’
/home/mladen/Desktop/test2/countchar.c:13: warning: ISO C90 forbids mixed declarations and code
/home/mladen/Desktop/test2/countchar.c:15: error: implicit declaration of function ‘open’
/home/mladen/Desktop/test2/countchar.c:15: error: ‘O_RDONLY’ undeclared (first use in this function)
/home/mladen/Desktop/test2/countchar.c:15: error: (Each undeclared identifier is reported only once
/home/mladen/Desktop/test2/countchar.c:15: error: for each function it appears in.)
/home/mladen/Desktop/test2/countchar.c:20: error: expected ‘)’ before ‘(’ token
/home/mladen/Desktop/test2/countchar.c:20: warning: ISO C90 forbids mixed declarations and code
/home/mladen/Desktop/test2/countchar.c:22: error: implicit declaration of function ‘close’
make[2]: *** [/home/mladen/Desktop/test2/countchar.o] Error 1
make[1]: *** [_module_/home/mladen/Desktop/test2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
make: *** [all] Error 2[/I][/SIZE]









[B][SIZE=5]

Please help [/SIZE][/B]



These is my code so far: 
                                                   [COLOR=Red]_**[SIZE=4]lmain.c[/SIZE]**_[/COLOR]
     

     [LEFT]                      [COLOR=#000000] [COLOR=#ff8000]#include <linux/module.h>
#include <linux/kernel.h>
#include <linux/autoconf.h>
#include <linux/types.h>
#include <linux/kdev_t.h>
#include <linux/fs.h> // file_operations structure
#include <linux/init.h>
#include <linux/moduleparam.h>
#include <linux/slab.h> // kmalloc
#include <linux/errno.h>
#include <linux/proc_fs.h>
#include <linux/fcntl.h>
#include <linux/seq_file.h>
#include <linux/cdev.h> // Char Device Registration
#include <linux/stat.h>



#include <asm/system.h> // cli(), *_flags
#include <asm/uaccess.h> // copy_*_user

#include "lunix.h"


[/COLOR][COLOR=#0000bb]MODULE_LICENSE[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"Dual BSD/GPL"[/COLOR][COLOR=#007700]);
[/COLOR][COLOR=#ff8000]//MODULE_VERSION
//MODULE_DESCRIPTION
[/COLOR][COLOR=#0000bb]MODULE_AUTHOR[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"MSIM"[/COLOR][COLOR=#007700]);
[/COLOR][COLOR=#ff8000]//MODULE_DEVICE_TABLE
//MODULE_ALIAS


#define lunix_size 524288 //lunix size is 524288 bytes


[/COLOR][COLOR=#0000bb]int __init lunix_init[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]void[/COLOR][COLOR=#007700]);
[/COLOR][COLOR=#0000bb]void __exit lunix_cleanup[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]void[/COLOR][COLOR=#007700]);


static [/COLOR][COLOR=#0000bb]int lunix_open[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]struct inode [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]inode[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]struct file [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]lunix[/COLOR][COLOR=#007700]);
static [/COLOR][COLOR=#0000bb]int lunix_release[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]struct inode [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]inode[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]struct file [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]lunix[/COLOR][COLOR=#007700]);
static [/COLOR][COLOR=#0000bb]ssize_t lunix_read[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]struct file [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]lunix[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]char __user [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]buffer[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]size_t length[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]loff_t[/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]fileposition[/COLOR][COLOR=#007700]);
static [/COLOR][COLOR=#0000bb]ssize_t lunix_write[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]struct file [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]lunix[/COLOR][COLOR=#007700], const [/COLOR][COLOR=#0000bb]char __user [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]buffer[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]size_t length[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]loff_t [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]fileposition[/COLOR][COLOR=#007700]);
static [/COLOR][COLOR=#0000bb]int lunix_ioctl[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]struct inode [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]inode[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]struct file [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]lunix[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]unsigned int cmd[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]unsigned long arg[/COLOR][COLOR=#007700]);
static [/COLOR][COLOR=#0000bb]loff_t lunix_llseek[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]struct file [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]lunix[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]loff_t offset[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]int whence[/COLOR][COLOR=#007700]);



static [/COLOR][COLOR=#0000bb]struct file_operations lunix_fops [/COLOR][COLOR=#007700]= {
[/COLOR][/COLOR][INDENT][COLOR=#000000][COLOR=#007700]      .[/COLOR][COLOR=#0000bb]owner [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]THIS_MODULE[/COLOR][COLOR=#007700],[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]      .[/COLOR][COLOR=#0000bb]read [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]lunix_read[/COLOR][COLOR=#007700],[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]      .[/COLOR][COLOR=#0000bb]write [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]lunix_write[/COLOR][COLOR=#007700],[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]      .[/COLOR][COLOR=#0000bb]open [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]lunix_open[/COLOR][COLOR=#007700],[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]      .[/COLOR][COLOR=#0000bb]release [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]lunix_release[/COLOR][COLOR=#007700],[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]      .[/COLOR][COLOR=#0000bb]ioctl [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]lunix_ioctl[/COLOR][COLOR=#007700],[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]      .[/COLOR][COLOR=#0000bb]llseek [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]lunix_llseek[/COLOR][COLOR=#007700],[/COLOR][/COLOR]
[/INDENT][COLOR=#000000][COLOR=#007700]   };


[/COLOR][COLOR=#0000bb]module_init[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]lunix_init[/COLOR][COLOR=#007700]);
[/COLOR][COLOR=#0000bb]module_exit[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]lunix_cleanup[/COLOR][COLOR=#007700]);

[/COLOR][COLOR=#0000bb]int lunix_major [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]60[/COLOR][COLOR=#007700];


[/COLOR][COLOR=#0000bb]char [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]lunix_buffer[/COLOR][COLOR=#007700] 
[/COLOR][COLOR=#0000bb]int cur_len[/COLOR][COLOR=#007700];
[/COLOR][COLOR=#0000bb]int numopen[/COLOR][COLOR=#007700];
[/COLOR][COLOR=#0000bb]int numclose[/COLOR][COLOR=#007700];
[/COLOR][COLOR=#0000bb]int numread[/COLOR][COLOR=#007700];
[/COLOR][COLOR=#0000bb]int numwrite[/COLOR][COLOR=#007700];
[/COLOR][COLOR=#0000bb]int numlseek[/COLOR][COLOR=#007700];


[/COLOR][COLOR=#0000bb]void dev_initialization[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]void[/COLOR][COLOR=#007700])
{
[/COLOR][/COLOR][INDENT][COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#0000bb]memset[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]lunix_buffer[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]lunix_size[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#0000bb]cur_len [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#0000bb]numopen [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#0000bb]numclose [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#0000bb]numread [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#0000bb]numwrite [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#0000bb]numlseek [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[/INDENT][COLOR=#000000][COLOR=#007700] }

[/COLOR][COLOR=#ff8000]// *** INIT function *** //

[/COLOR][COLOR=#0000bb]int __init lunix_init[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]void[/COLOR][COLOR=#007700]){
[/COLOR][/COLOR][INDENT][COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#0000bb]int result[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700] [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#ff8000]/* Registering device */[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]       [/COLOR][COLOR=#0000bb]result [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]register_chrdev[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]lunix_major[/COLOR][COLOR=#007700], [/COLOR][COLOR=#dd0000]"lunix"[/COLOR][COLOR=#007700], &[/COLOR][COLOR=#0000bb]lunix_fops[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       if ([/COLOR][COLOR=#0000bb]result [/COLOR][COLOR=#007700]< [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700]) {[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]         [/COLOR][COLOR=#0000bb]printk[/COLOR][COLOR=#007700]( [/COLOR][COLOR=#dd0000]"<1>lunix: cannot obtain major number%d\n"[/COLOR][COLOR=#007700],[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]                [/COLOR][COLOR=#0000bb]lunix_major[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       return [/COLOR][COLOR=#0000bb]result[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[/INDENT][INDENT][COLOR=#000000][COLOR=#007700]       }[/COLOR][/COLOR]
[/INDENT][COLOR=#000000][COLOR=#007700] 
[/COLOR][/COLOR][INDENT][COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#ff8000]/* Allocating memory for the buffer */[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]       [/COLOR][COLOR=#0000bb]lunix_buffer [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]kmalloc[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]lunix_size[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]GFP_DMA [/COLOR][COLOR=#007700]| [/COLOR][COLOR=#0000bb]GFP_KERNEL[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       if (![/COLOR][COLOR=#0000bb]lunix_buffer[/COLOR][COLOR=#007700]) {[/COLOR][/COLOR]
[INDENT][COLOR=#000000][COLOR=#007700]         [/COLOR][COLOR=#0000bb]result [/COLOR][COLOR=#007700]= -[/COLOR][COLOR=#0000bb]ENOMEM[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]         [/COLOR][COLOR=#0000bb]goto fail[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[/INDENT][COLOR=#000000][COLOR=#007700]       }[/COLOR][/COLOR]
[/INDENT][COLOR=#000000][COLOR=#007700] 
[/COLOR][/COLOR][INDENT][COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#0000bb]dev_initialization[/COLOR][COLOR=#007700]();[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700] [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#0000bb]printk[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"<1>Inserting lunix module\n"[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       return [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700] [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#0000bb]fail[/COLOR][COLOR=#007700]:[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]     [/COLOR][COLOR=#0000bb]lunix_cleanup[/COLOR][COLOR=#007700]();[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       return [/COLOR][COLOR=#0000bb]result[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[/INDENT][COLOR=#000000][COLOR=#007700] }




[/COLOR][COLOR=#ff8000]// *** EXIT function *** //

[/COLOR][COLOR=#0000bb]void __exit lunix_cleanup[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]void[/COLOR][COLOR=#007700])
{
[/COLOR][/COLOR][INDENT][COLOR=#000000][COLOR=#007700] [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#ff8000]/* Freeing the major number */[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]       [/COLOR][COLOR=#0000bb]unregister_chrdev[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]lunix_major[/COLOR][COLOR=#007700], [/COLOR][COLOR=#dd0000]"lunix"[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700] [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#ff8000]/* Freeing lunix buffer */[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]       [/COLOR][COLOR=#007700]if ([/COLOR][COLOR=#0000bb]lunix_buffer[/COLOR][COLOR=#007700]) {[/COLOR][/COLOR]
[INDENT][COLOR=#000000][COLOR=#007700]         [/COLOR][COLOR=#0000bb]kfree[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]lunix_buffer[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
[/INDENT][COLOR=#000000][COLOR=#007700]       }[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700] [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#0000bb]printk[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"<1>Removing lunix module\n"[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
[/INDENT][COLOR=#000000][COLOR=#007700] }


static [/COLOR][COLOR=#0000bb]int lunix_open[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]struct inode [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]inode[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]struct file [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]lunix[/COLOR][COLOR=#007700])
{
[/COLOR][/COLOR][INDENT][COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#0000bb]numopen[/COLOR][COLOR=#007700]++ ;[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       return [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[/INDENT][COLOR=#000000][COLOR=#007700] }

static [/COLOR][COLOR=#0000bb]int lunix_release[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]struct inode [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]inode[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]struct file [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]lunix[/COLOR][COLOR=#007700])
{
[/COLOR][/COLOR][INDENT][COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#0000bb]numclose[/COLOR][COLOR=#007700]++ ;[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       return [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[/INDENT][COLOR=#000000][COLOR=#007700] }

static [/COLOR][COLOR=#0000bb]ssize_t lunix_read[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]struct file [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]lunix[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]char __user [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]buffer[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]size_t length[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]loff_t [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]fileposition[/COLOR][COLOR=#007700])
{
[/COLOR][/COLOR][INDENT][COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#0000bb]numread[/COLOR][COLOR=#007700]++ ;[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#0000bb]printk[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"<1>read function start\n"[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700] [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#ff8000]//checking if the user [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]       [/COLOR][COLOR=#007700]if (*[/COLOR][COLOR=#0000bb]fileposition [/COLOR][COLOR=#007700]+ [/COLOR][COLOR=#0000bb]length [/COLOR][COLOR=#007700]> [/COLOR][COLOR=#0000bb]cur_len[/COLOR][COLOR=#007700])[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]         [/COLOR][COLOR=#0000bb]length [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]cur_len [/COLOR][COLOR=#007700]- *[/COLOR][COLOR=#0000bb]fileposition[/COLOR][COLOR=#007700]; [/COLOR][COLOR=#0000bb]doesnt want to much[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#0000bb] [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#0000bb]       printk[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"<1>read. checked if the user ...\n"[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700] [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       if([/COLOR][COLOR=#0000bb]copy_to_user[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]buffer[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]lunix_buffer [/COLOR][COLOR=#007700]+ *[/COLOR][COLOR=#0000bb]fileposition[/COLOR][COLOR=#007700],[/COLOR][COLOR=#0000bb]length[/COLOR][COLOR=#007700]) != [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700])[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]         return -[/COLOR][COLOR=#0000bb]EFAULT[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]   [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#0000bb]printk[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"<1>read.after copy user \n"[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700] [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#ff8000]// updating the file position[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]      [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]fileposition [/COLOR][COLOR=#007700]= *[/COLOR][COLOR=#0000bb]fileposition [/COLOR][COLOR=#007700]+ [/COLOR][COLOR=#0000bb]length[/COLOR][COLOR=#007700]; [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]      [/COLOR][COLOR=#0000bb]printk[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"<1>read.before return length \n"[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]      return [/COLOR][COLOR=#0000bb]length[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[/INDENT][COLOR=#000000][COLOR=#007700] 
}

static [/COLOR][COLOR=#0000bb]ssize_t lunix_write[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]struct file [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]lunix[/COLOR][COLOR=#007700], const [/COLOR][COLOR=#0000bb]char __user [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]buffer[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]size_t length[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]loff_t [/COLOR][COLOR=#007700]* [/COLOR][COLOR=#0000bb]fileposition[/COLOR][COLOR=#007700])
{
[/COLOR][/COLOR][INDENT][COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#0000bb]numwrite[/COLOR][COLOR=#007700]++ ;[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#0000bb]printk[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"<1>write function started\n"[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700] [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#ff8000]//checking if the user doesnt want to much[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]       [/COLOR][COLOR=#007700]if (*[/COLOR][COLOR=#0000bb]fileposition [/COLOR][COLOR=#007700]+ [/COLOR][COLOR=#0000bb]length [/COLOR][COLOR=#007700]> [/COLOR][COLOR=#0000bb]lunix_size[/COLOR][COLOR=#007700])[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]         [/COLOR][COLOR=#0000bb]length [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]lunix_size [/COLOR][COLOR=#007700]- *[/COLOR][COLOR=#0000bb]fileposition[/COLOR][COLOR=#007700]; [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#0000bb]printk[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"<1> write checking if the user...\n"[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       if ([/COLOR][COLOR=#0000bb]cur_len [/COLOR][COLOR=#007700]< [/COLOR][COLOR=#0000bb]length [/COLOR][COLOR=#007700]+ *[/COLOR][COLOR=#0000bb]fileposition[/COLOR][COLOR=#007700])[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]         [/COLOR][COLOR=#0000bb]cur_len [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]length [/COLOR][COLOR=#007700]+ *[/COLOR][COLOR=#0000bb]fileposition[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700] [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       if ([/COLOR][COLOR=#0000bb]copy_from_user[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]lunix_buffer [/COLOR][COLOR=#007700]+ *[/COLOR][COLOR=#0000bb]fileposition[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]buffer [/COLOR][COLOR=#007700],[/COLOR][COLOR=#0000bb]length[/COLOR][COLOR=#007700]) != [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700])[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]         return -[/COLOR][COLOR=#0000bb]EFAULT[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#ff8000]// updating the file position[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]       [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]fileposition [/COLOR][COLOR=#007700]= *[/COLOR][COLOR=#0000bb]fileposition [/COLOR][COLOR=#007700]+ [/COLOR][COLOR=#0000bb]length[/COLOR][COLOR=#007700]; [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       [/COLOR][COLOR=#0000bb]printk[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"<1>write.before return length, length is %d \n"[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]length[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       return [/COLOR][COLOR=#0000bb]length[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[/INDENT][COLOR=#000000][COLOR=#007700] 
}


static [/COLOR][COLOR=#0000bb]loff_t lunix_llseek[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]struct file [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]lunix[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]loff_t offset[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]int whence[/COLOR][COLOR=#007700])
{

[/COLOR][/COLOR][INDENT][COLOR=#000000][COLOR=#007700]     [/COLOR][COLOR=#ff8000]/* numlseek++ ;[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]       loff_t newpos;[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000] [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]       switch(whence) {[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]         case 0: // SEEK_SET[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]         break;[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000] [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]         case 1: // SEEK_CUR[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]         break;[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000] [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]         case 2: // SEEK_END[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]         break;[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000] [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]         default:[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]         return -EINVAL;[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]       }[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000] [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]       return newpos;[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]     */[/COLOR][/COLOR]
[/INDENT][COLOR=#000000][COLOR=#ff8000] [/COLOR][COLOR=#007700]}

static [/COLOR][COLOR=#0000bb]int lunix_ioctl[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]struct inode [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]inode[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]struct file [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]lunix[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]unsigned int cmd[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]unsigned long arg[/COLOR][COLOR=#007700])
{

[/COLOR][/COLOR][INDENT][COLOR=#000000][COLOR=#ff8000]#define LUNIX_IOC_MAGIC 'Z'[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]      #define LUNIX_IOC_INITIALIZE _IOW(LUNIX_IOC_MAGIC, 0, int)[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]      #define LUNIX_IOC_GETDEVSIZE _IOR(LUNIX_IOC_MAGIC, 1, int)[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]      #define LUNIX_IOC_GETSTATS _IOR(LUNIX_IOC_MAGIC, 2, int)[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]      #define LUNIX_IOC_COUNTCHAR _IOWR(LUNIX_IOC_MAGIC, 3, int)[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]      #define LUNIX_IOC_MAXNR 4[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#0000bb]int retval [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]      switch([/COLOR][COLOR=#0000bb]cmd[/COLOR][COLOR=#007700]) {[/COLOR][/COLOR]
[INDENT][INDENT][COLOR=#000000][COLOR=#ff8000]//int tmp;[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#0000bb]int theLetter[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#0000bb]int i[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#0000bb]int count [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700];[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#007700]        case [/COLOR][COLOR=#0000bb]LUNIX_IOC_INITIALIZE[/COLOR][COLOR=#007700]:[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]// lunix_size = tmp[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]        //dev_initialization(void);[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]break;[/COLOR][/COLOR]
[/INDENT][INDENT][COLOR=#000000][COLOR=#007700]        case [/COLOR][COLOR=#0000bb]LUNIX_IOC_GETDEVSIZE[/COLOR][COLOR=#007700]:[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#0000bb]printk [/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"<1>The size of Lunix is %d \n"[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]lunix_size[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]        break;[/COLOR][/COLOR]
[/INDENT][COLOR=#000000][COLOR=#007700] [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700] [/COLOR][/COLOR][INDENT][LEFT][COLOR=#000000][COLOR=#007700]        case [/COLOR][COLOR=#0000bb]LUNIX_IOC_GETSTATS[/COLOR][COLOR=#007700]:[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#0000bb]printk [/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"<1> SATISTIC: \n number of OPEN calls is %d \n numbervoid of CLOSE      calls is %d \n number of READ calls is %d \n number of WRITE calls is %d \n number of    lseek calls is %d \n " [/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]numopen[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]numclose[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]numread[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]numwrite[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]numlseek[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]     break;[/COLOR][/COLOR]
[/LEFT]
[/INDENT][COLOR=#000000][COLOR=#007700] [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700] [/COLOR][/COLOR][INDENT][COLOR=#000000][COLOR=#007700]     case [/COLOR][COLOR=#0000bb]LUNIX_IOC_COUNTCHAR[/COLOR][COLOR=#007700]:[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#ff8000]//if (copy_from_user(lunix_buffer + *fileposition, buffer ,length) != 0)[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]if ([/COLOR][COLOR=#0000bb]copy_from_user[/COLOR][COLOR=#007700]( &[/COLOR][COLOR=#0000bb]theLetter[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]arg[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]sizeof[/COLOR][COLOR=#007700](int)) != [/COLOR][COLOR=#0000bb]0 [/COLOR][COLOR=#007700])[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]       return -[/COLOR][COLOR=#0000bb]EFAULT[/COLOR][COLOR=#007700];[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#007700]     for([/COLOR][COLOR=#0000bb]i[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700]; [/COLOR][COLOR=#0000bb]i [/COLOR][COLOR=#007700]< [/COLOR][COLOR=#0000bb]cur_len [/COLOR][COLOR=#007700]; [/COLOR][COLOR=#0000bb]i[/COLOR][COLOR=#007700]++)[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]     {[/COLOR][/COLOR]
[INDENT][COLOR=#000000][COLOR=#007700]       if ([/COLOR][COLOR=#0000bb]lunix_buffer[/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000bb]i[/COLOR][COLOR=#007700]] == [/COLOR][COLOR=#0000bb]theLetter[/COLOR][COLOR=#007700]){[/COLOR][/COLOR]
[INDENT][COLOR=#000000][COLOR=#0000bb]count[/COLOR][COLOR=#007700]++;[/COLOR][/COLOR]
[/INDENT][COLOR=#000000][COLOR=#007700]     }[/COLOR][/COLOR]
[/INDENT]   [/INDENT][INDENT][COLOR=#000000][COLOR=#007700]   }[/COLOR][/COLOR]
[/INDENT][INDENT][COLOR=#000000][COLOR=#0000bb]printk[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"<1> \n The letter '%c' appears %d times in the document. \n\n"[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]theLetter[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]count [/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]   break;[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]   default:[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]  return -[/COLOR][COLOR=#0000bb]ENOTTY[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[/INDENT][/INDENT]         [/INDENT][INDENT]     [COLOR=#000000][COLOR=#007700]   }[/COLOR][/COLOR]
[/INDENT][COLOR=#000000][COLOR=#007700] 
return [/COLOR][COLOR=#0000bb]retval[/COLOR][COLOR=#007700];

}  
[/COLOR] [/COLOR]               [/LEFT]
 

[SIZE=4][COLOR=Red][B][U]
                 countchar.c[/U][/B][/COLOR][/SIZE]
          [LEFT]                      [COLOR=#000000] [COLOR=#0000bb]

[/COLOR][COLOR=#ff8000]#include <stdio.h>
#include <ctype.h>
#include <fcntl.h>
#include "lunix.h"
[/COLOR][COLOR=#0000bb]int main [/COLOR][COLOR=#007700]()
{
  [/COLOR][/COLOR][INDENT][COLOR=#000000][COLOR=#0000bb]printf[/COLOR][COLOR=#007700]( [/COLOR][COLOR=#dd0000]"\nThis program counts the appearance of a letter in  [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#dd0000]          LUNIX.\n\n"[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#0000bb]printf[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"\n Type letter to be calculated the appearance of and [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#dd0000]           press enter: \n\n"[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#0000bb]int fd[/COLOR][COLOR=#007700];[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#0000bb]fd [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]open[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"/dev/lunix"[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]O_RDONLY[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]   if([/COLOR][COLOR=#0000bb]fd [/COLOR][COLOR=#007700]< [/COLOR][COLOR=#0000bb]0 [/COLOR][COLOR=#007700]) {[/COLOR][/COLOR][INDENT][COLOR=#000000][COLOR=#0000bb]printf[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"Error: can't open file.\n"[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]   return [/COLOR][COLOR=#0000bb]1[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[/INDENT][COLOR=#000000][COLOR=#007700]   }[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#0000bb]extern ioctl[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]fd[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]LUNIX_IOC_COUNTCHAR[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#0000bb]close[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]fd[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#007700]   return [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[/INDENT][COLOR=#000000][COLOR=#007700] }  
[/COLOR] [/COLOR]               [/LEFT]
 
[SIZE=4][COLOR=Red]_**lunix.h**_[/COLOR][/SIZE]


     

     [LEFT]                      [COLOR=#000000] [COLOR=#ff8000]#ifndef _LUNIX_H_
#define _LUNIX_H_

#include <linux/ioctl.h>


#ifndef LUNIX_MAJOR
#define LUNIX_MAJOR 60
#endif

[/COLOR][COLOR=#0000bb]extern int lunix_major[/COLOR][COLOR=#007700];

[/COLOR][COLOR=#ff8000]/*
static int lunix_open(struct inode *inode, struct file *lunix);
static int lunix_release(struct inode *inode, struct file *lunix);
static ssize_t lunix_read(struct file *lunix, char __user *buffer, size_t length, loff_t *fileposition);
static ssize_t lunix_write(struct file *lunix, const char __user *buffer, size_t length, loff_t *fileposition);
static int lunix_ioctl(struct inode *inode, struct file *lunix, unsigned int cmd, unsigned long arg);
static loff_t lunix_llseek(struct file *lunix, loff_t offset, int whence);
*/




#define LUNIX_IOC_MAGIC 'Z'


#define LUNIX_IOC_MAGIC 'Z'
#define LUNIX_IOC_INITIALIZE _IOW(LUNIX_IOC_MAGIC, 0, int)
#define LUNIX_IOC_GETDEVSIZE _IOR(LUNIX_IOC_MAGIC, 1, int)
#define LUNIX_IOC_GETSTATS _IOR(LUNIX_IOC_MAGIC, 2, int)
#define LUNIX_IOC_COUNTCHAR _IOWR(LUNIX_IOC_MAGIC, 3, int)
#define LUNIX_IOC_MAXNR 4



#endif  [/COLOR][/COLOR][/LEFT]


[B] [SIZE=4][U][COLOR=Red]
makefile [/COLOR][/U]
[/SIZE]  
lunix-objs := lmain.o countchar.o

obj-m := lunix.o

all:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

[/B]

---

### Post by simitoco on 2009-07-02
please someone say something ](*,)

---

### Post by ad_267 on 2009-07-02
Have you installed the build-essential package?

sudo apt-get install build-essential

---

### Post by simitoco on 2009-07-02
oo thank God, someone is reading me :) 

 yes, i did...

 Do you  think that i am doing something wrong with user space / kernel space ???

should i specify in the makefile or somewhere that countchar.c is userspace ??

---

### Post by ad_267 on 2009-07-02
I don't know about kernel/userspace issues sorry, but Ubuntu doesn't include those header files by default and they should be included in the build-essential package.

What do you get from:
```
sudo updatedb
locate stdio.h
```

---

### Post by simitoco on 2009-07-02
this is the output...

/usr/include/stdio.h
/usr/include/bits/stdio.h
/usr/include/c++/4.2/tr1/stdio.h
/usr/include/glib-2.0/glib/gstdio.h
/usr/lib/perl/5.8.8/CORE/nostdio.h
/usr/share/man/man7/stdio.h.7posix.gz

---

### Post by monkeyking on 2009-07-02
lmain.c
[PHP]
#include <linux/module.h>
#include <linux/kernel.h>
#include <linux/autoconf.h>
#include <linux/types.h>
#include <linux/kdev_t.h>
#include <linux/fs.h> // file_operations structure
#include <linux/init.h>
#include <linux/moduleparam.h>
#include <linux/slab.h> // kmalloc
#include <linux/errno.h>
#include <linux/proc_fs.h>
#include <linux/fcntl.h>
#include <linux/seq_file.h>
#include <linux/cdev.h> // Char Device Registration
#include <linux/stat.h>



#include <asm/system.h> // cli(), *_flags
#include <asm/uaccess.h> // copy_*_user

#include "lunix.h"


MODULE_LICENSE("Dual BSD/GPL");
//MODULE_VERSION
//MODULE_DESCRIPTION
MODULE_AUTHOR("MSIM");
//MODULE_DEVICE_TABLE
//MODULE_ALIAS


#define lunix_size 524288 //lunix size is 524288 bytes


int __init lunix_init(void);
void __exit lunix_cleanup(void);


static int lunix_open(struct inode *inode, struct file *lunix);
static int lunix_release(struct inode *inode, struct file *lunix);
static ssize_t lunix_read(struct file *lunix, char __user *buffer, size_t length, loff_t *fileposition);
static ssize_t lunix_write(struct file *lunix, const char __user *buffer, size_t length, loff_t *fileposition);
static int lunix_ioctl(struct inode *inode, struct file *lunix, unsigned int cmd, unsigned long arg);
static loff_t lunix_llseek(struct file *lunix, loff_t offset, int whence);



static struct file_operations lunix_fops = {
.owner = THIS_MODULE,
.read = lunix_read,
.write = lunix_write,
.open = lunix_open,
.release = lunix_release,
.ioctl = lunix_ioctl,
.llseek = lunix_llseek,
};


module_init(lunix_init);
module_exit(lunix_cleanup);

int lunix_major = 60;


char *lunix_buffer;
int cur_len;
int numopen;
int numclose;
int numread;
int numwrite;
int numlseek;


void dev_initialization(void)
{
  memset(lunix_buffer, 0, lunix_size);
  cur_len = 0;
  numopen = 0;
  numclose = 0;
  numread = 0;
  numwrite = 0;
  numlseek = 0;
}

// *** INIT function *** //

int __init lunix_init(void){
  int result;

  /* Registering device */
  result = register_chrdev(lunix_major, "lunix", &lunix_fops);
  if (result < 0) {
    printk( "<1>lunix: cannot obtain major number%d\n",\
           lunix_major);
  return result;
  }

  /* Allocating memory for the buffer */
  lunix_buffer = kmalloc(lunix_size, GFP_DMA | GFP_KERNEL);
  if (!lunix_buffer) {
    result = -ENOMEM;
    goto fail;
  }

  dev_initialization();

  printk("<1>Inserting lunix module\n");
  return 0;

  fail:
  lunix_cleanup();
  return result;
}




// *** EXIT function *** //

void __exit lunix_cleanup(void)
{

  /* Freeing the major number */
  unregister_chrdev(lunix_major, "lunix");

  /* Freeing lunix buffer */
  if (lunix_buffer) {
    kfree(lunix_buffer);
  }

  printk("<1>Removing lunix module\n");
}

static int lunix_open(struct inode *inode, struct file *lunix)
{
  numopen++ ;
  return 0;
}

static int lunix_release(struct inode *inode, struct file *lunix)
{
  numclose++ ;
  return 0;
}

static ssize_t lunix_read(struct file *lunix, char __user *buffer, size_t length, loff_t *fileposition)
{
  numread++ ;
  printk("<1>read function start\n");

  //checking if the user 
  if (*fileposition + length > cur_len)
    length = cur_len - *fileposition; doesnt want to much

  printk("<1>read. checked if the user ...\n");

  if(copy_to_user(buffer, lunix_buffer + *fileposition,length) != 0)
    return -EFAULT;

  printk("<1>read.after copy user \n");

  // updating the file position
  *fileposition = *fileposition + length; 
  printk("<1>read.before return length \n");
  return length;

}

static ssize_t lunix_write(struct file *lunix, const char __user *buffer, size_t length, loff_t * fileposition)
{
  numwrite++ ;
  printk("<1>write function started\n");

  //checking if the user doesnt want to much
  if (*fileposition + length > lunix_size)
    length = lunix_size - *fileposition; 
  printk("<1> write checking if the user...\n");
  if (cur_len < length + *fileposition)
    cur_len = length + *fileposition;

  if (copy_from_user(lunix_buffer + *fileposition, buffer ,length) != 0)
    return -EFAULT;
  // updating the file position
  *fileposition = *fileposition + length; 
  printk("<1>write.before return length, length is %d \n", length);
  return length;

}


static loff_t lunix_llseek(struct file *lunix, loff_t offset, int whence)
{

/* numlseek++ ;
  loff_t newpos;

  switch(whence) {
    case 0: // SEEK_SET
    break;

    case 1: // SEEK_CUR
    break;

    case 2: // SEEK_END
    break;

    default:
    return -EINVAL;
  }

  return newpos;
*/
}

static int lunix_ioctl(struct inode *inode, struct file *lunix, unsigned int cmd, unsigned long arg)
{

  #define LUNIX_IOC_MAGIC 'Z'
  #define LUNIX_IOC_INITIALIZE _IOW(LUNIX_IOC_MAGIC, 0, int)
  #define LUNIX_IOC_GETDEVSIZE _IOR(LUNIX_IOC_MAGIC, 1, int)
  #define LUNIX_IOC_GETSTATS _IOR(LUNIX_IOC_MAGIC, 2, int)
  #define LUNIX_IOC_COUNTCHAR _IOWR(LUNIX_IOC_MAGIC, 3, int)
  #define LUNIX_IOC_MAXNR 4
  int retval = 0;
  switch(cmd) {
    //int tmp;
    int theLetter;
    int i;
    int count = 0;
    case LUNIX_IOC_INITIALIZE:

    // lunix_size = tmp
    //dev_initialization(void);
    break;
    case LUNIX_IOC_GETDEVSIZE:
    printk ("<1>The size of Lunix is %d \n", lunix_size);
    break;

    case LUNIX_IOC_GETSTATS:
  printk ("<1> SATISTIC: \n number of OPEN calls is %d \n numbervoid of CLOSE calls is %d \n number of READ calls is %d \n number of WRITE calls is %d \n number of lseek calls is %d \n " , numopen, numclose, numread, numwrite, numlseek);
    break;

    case LUNIX_IOC_COUNTCHAR:
      //if (copy_from_user(lunix_buffer + *fileposition, buffer ,length) != 0)
    if (copy_from_user( &theLetter, arg, sizeof(int)) != 0 )
      return -EFAULT;

    for(i=0; i < cur_len ; i++)
    {
      if (lunix_buffer[i] == theLetter){
        count++;
    }
  }
  printk("<1> \n The letter '%c' appears %d times in the document. \n\n", theLetter, count );
  break;
  default:
 return -ENOTTY;
  }

return retval;

}
[/PHP]
countchar.c
[PHP]


#include <stdio.h>
#include <ctype.h>
#include <fcntl.h>
#include "lunix.h"
int main ()
{
  printf( "\nThis program counts the appearance of a letter in  
         LUNIX.\n\n");
  printf("\n Type letter to be calculated the appearance of and 
          press enter: \n\n");
  int fd;

  fd = open("/dev/lunix", O_RDONLY);
  if(fd < 0 ) {
    printf("Error: can't open file.\n");
  return 1;
  }

  extern ioctl(fd, LUNIX_IOC_COUNTCHAR);

  close(fd);

  return 0;
}
[/PHP]
lunix.h


[PHP]
#ifndef _LUNIX_H_
#define _LUNIX_H_

#include <linux/ioctl.h>


#ifndef LUNIX_MAJOR
#define LUNIX_MAJOR 60
#endif

extern int lunix_major;

/*
static int lunix_open(struct inode *inode, struct file *lunix);
static int lunix_release(struct inode *inode, struct file *lunix);
static ssize_t lunix_read(struct file *lunix, char __user *buffer, size_t length, loff_t *fileposition);
static ssize_t lunix_write(struct file *lunix, const char __user *buffer, size_t length, loff_t *fileposition);
static int lunix_ioctl(struct inode *inode, struct file *lunix, unsigned int cmd, unsigned long arg);
static loff_t lunix_llseek(struct file *lunix, loff_t offset, int whence);
*/




#define LUNIX_IOC_MAGIC 'Z'


#define LUNIX_IOC_MAGIC 'Z'
#define LUNIX_IOC_INITIALIZE _IOW(LUNIX_IOC_MAGIC, 0, int)
#define LUNIX_IOC_GETDEVSIZE _IOR(LUNIX_IOC_MAGIC, 1, int)
#define LUNIX_IOC_GETSTATS _IOR(LUNIX_IOC_MAGIC, 2, int)
#define LUNIX_IOC_COUNTCHAR _IOWR(LUNIX_IOC_MAGIC, 3, int)
#define LUNIX_IOC_MAXNR 4



#endif
[/PHP]

This should make it somewhat easier to read,
but could you try a simple hello wold,
to check if you tool chain is working

---

### Post by simitoco on 2009-07-02
i apologize for the ugly code,  I've tried hello - working  
before writing the ioctl i have loaded the module, read and write working..

do you know if i have to tell "make" to look for  [COLOR=#000000][COLOR=#ff8000]<stdio.h>, <ctype.h>, <fcntl.h>[/COLOR][/COLOR], for countchar.c   in     /usr/include ???  and if so, how do i do it?

---

### Post by PmDematagoda on 2009-07-02
> **simitoco said:**
> i apologize for the ugly code,  I've tried hello - working  
before writing the ioctl i have loaded the module, read and write working..

do you know if i have to tell "make" to look for  [COLOR=#000000][COLOR=#FF8000]<stdio.h>, <ctype.h>, <fcntl.h>[/COLOR][/COLOR], for countchar.c   in     /usr/include ???  and if so, how do i do it?

Im not too experienced in kernel stuff either, but I'll try and help. First off, can you post the Makefile you're using?

And also, could you please edit your first post to make it more readable? Thanks:).

---

### Post by dwhitney67 on 2009-07-03
> **simitoco said:**
> [SIZE=2]
makefile [/COLOR][/U]
[/SIZE]  
lunix-objs := lmain.o countchar.o

obj-m := lunix.o

all:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

[/B]

I think the problem is shown above... you are trying to compile a user-program (countchar.c) as a kernel module.  You should be compiling/linking this module using a separate Makefile.

P.S.  Do not ever post code or Makefiles using color tags.  It makes hard for anyone to copy/test your code on their own system.  A long time ago on this forum, someone attempted to sway/push developers to post code like this, but the concept was a wash.  If you want to post code, use either the CODE or the PHP blocks; the former is preferred.

---

### Post by simitoco on 2009-07-03
dwhitney67, 
can you please show me how to do that ? 
Im new to everything and there is still confusion in my head.. 


P.S. I will learn how to post for next time:)

---

### Post by dwhitney67 on 2009-07-03
Here's what I did to build and test your Linux kernel module...

Makefile:
```

SRCS   = lmain.c
OBJS   = $(SRCS:.c=.o)

obj-m += $(OBJS)

EXTRA_CFLAGS = -O2


all:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) modules

clean:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) clean
        $(RM) Module.markers modules.order

```

lunix.h:
```

#ifndef _LUNIX_H_
#define _LUNIX_H_

#include <linux/ioctl.h>


#ifndef LUNIX_MAJOR
#define LUNIX_MAJOR 60
#endif

extern int lunix_major;

/*
static int lunix_open(struct inode *inode, struct file *lunix);
static int lunix_release(struct inode *inode, struct file *lunix);
static ssize_t lunix_read(struct file *lunix, char __user *buffer, size_t length, loff_t *fileposition);
static ssize_t lunix_write(struct file *lunix, const char __user *buffer, size_t length, loff_t *fileposition);
static int lunix_ioctl(struct inode *inode, struct file *lunix, unsigned int cmd, unsigned long arg);
static loff_t lunix_llseek(struct file *lunix, loff_t offset, int whence);
*/




#define LUNIX_IOC_MAGIC 'Z'


#define LUNIX_IOC_MAGIC 'Z'
#define LUNIX_IOC_INITIALIZE _IOW(LUNIX_IOC_MAGIC, 0, int)
#define LUNIX_IOC_GETDEVSIZE _IOR(LUNIX_IOC_MAGIC, 1, int)
#define LUNIX_IOC_GETSTATS _IOR(LUNIX_IOC_MAGIC, 2, int)
#define LUNIX_IOC_COUNTCHAR _IOWR(LUNIX_IOC_MAGIC, 3, int)
#define LUNIX_IOC_MAXNR 4



#endif

```

lmain.c (note, I had to make corrections to get this thing to compile):
```

#include <linux/module.h>
#include <linux/kernel.h>
#include <linux/autoconf.h>
#include <linux/types.h>
#include <linux/kdev_t.h>
#include <linux/fs.h> // file_operations structure
#include <linux/init.h>
#include <linux/moduleparam.h>
#include <linux/slab.h> // kmalloc
#include <linux/errno.h>
#include <linux/proc_fs.h>
#include <linux/fcntl.h>
#include <linux/seq_file.h>
#include <linux/cdev.h> // Char Device Registration
#include <linux/stat.h>



#include <asm/system.h> // cli(), *_flags
#include <asm/uaccess.h> // copy_*_user

#include "lunix.h"


MODULE_LICENSE("Dual BSD/GPL");
//MODULE_VERSION
//MODULE_DESCRIPTION
MODULE_AUTHOR("MSIM");
//MODULE_DEVICE_TABLE
//MODULE_ALIAS


#define lunix_size 524288 //lunix size is 524288 bytes


int __init lunix_init(void);
//void __exit lunix_cleanup(void);
void lunix_cleanup(void);


static int lunix_open(struct inode *inode, struct file *lunix);
static int lunix_release(struct inode *inode, struct file *lunix);
static ssize_t lunix_read(struct file *lunix, char __user *buffer, size_t length, loff_t *fileposition);
static ssize_t lunix_write(struct file *lunix, const char __user *buffer, size_t length, loff_t *fileposition);
static int lunix_ioctl(struct inode *inode, struct file *lunix, unsigned int cmd, unsigned long arg);
static loff_t lunix_llseek(struct file *lunix, loff_t offset, int whence);



static struct file_operations lunix_fops = {
.owner = THIS_MODULE,
.read = lunix_read,
.write = lunix_write,
.open = lunix_open,
.release = lunix_release,
.ioctl = lunix_ioctl,
.llseek = lunix_llseek,
};


module_init(lunix_init);
module_exit(lunix_cleanup);

int lunix_major = 60;


char *lunix_buffer;
int cur_len;
int numopen;
int numclose;
int numread;
int numwrite;
int numlseek;


void dev_initialization(void)
{
  memset(lunix_buffer, 0, lunix_size);
  cur_len = 0;
  numopen = 0;
  numclose = 0;
  numread = 0;
  numwrite = 0;
  numlseek = 0;
}

// *** INIT function *** //

int __init lunix_init(void){
  int result;

  /* Registering device */
  result = register_chrdev(lunix_major, "lunix", &lunix_fops);
  if (result < 0) {
    printk( "<1>lunix: cannot obtain major number%d\n",
           lunix_major);
  return result;
  }

  /* Allocating memory for the buffer */
  lunix_buffer = kmalloc(lunix_size, GFP_DMA | GFP_KERNEL);
  if (!lunix_buffer) {
    result = -ENOMEM;
    goto fail;
  }

  dev_initialization();

  printk("<1>Inserting lunix module\n");
  return 0;

  fail:
  lunix_cleanup();
  return result;
}




// *** EXIT function *** //

//void __exit lunix_cleanup(void)
void lunix_cleanup(void)
{

  /* Freeing the major number */
  unregister_chrdev(lunix_major, "lunix");

  /* Freeing lunix buffer */
  if (lunix_buffer) {
    kfree(lunix_buffer);
  }

  printk("<1>Removing lunix module\n");
}

static int lunix_open(struct inode *inode, struct file *lunix)
{
  numopen++ ;
  return 0;
}

static int lunix_release(struct inode *inode, struct file *lunix)
{
  numclose++ ;
  return 0;
}

static ssize_t lunix_read(struct file *lunix, char __user *buffer, size_t length, loff_t *fileposition)
{
  numread++ ;
  printk("<1>read function start\n");

  //checking if the user 
  if (*fileposition + length > cur_len)
    length = cur_len - *fileposition;  //doesnt want to much

  printk("<1>read. checked if the user ...\n");

  if(copy_to_user(buffer, lunix_buffer + *fileposition,length) != 0)
    return -EFAULT;

  printk("<1>read.after copy user \n");

  // updating the file position
  *fileposition = *fileposition + length; 
  printk("<1>read.before return length \n");
  return length;

}

static ssize_t lunix_write(struct file *lunix, const char __user *buffer, size_t length, loff_t * fileposition)
{
  numwrite++ ;
  printk("<1>write function started\n");

  //checking if the user doesnt want to much
  if (*fileposition + length > lunix_size)
    length = lunix_size - *fileposition; 
  printk("<1> write checking if the user...\n");
  if (cur_len < length + *fileposition)
    cur_len = length + *fileposition;

  if (copy_from_user(lunix_buffer + *fileposition, buffer ,length) != 0)
    return -EFAULT;
  // updating the file position
  *fileposition = *fileposition + length; 
  printk("<1>write.before return length, length is %d \n", length);
  return length;

}


static loff_t lunix_llseek(struct file *lunix, loff_t offset, int whence)
{
  loff_t newpos = -EINVAL;

/*
  numlseek++;

  switch(whence) {
    case 0: // SEEK_SET
    break;

    case 1: // SEEK_CUR
    break;

    case 2: // SEEK_END
    break;

    default:
    return -EINVAL;
  }
*/

  return newpos;
}

static int lunix_ioctl(struct inode *inode, struct file *lunix, unsigned int cmd, unsigned long arg)
{

  #define LUNIX_IOC_MAGIC 'Z'
  #define LUNIX_IOC_INITIALIZE _IOW(LUNIX_IOC_MAGIC, 0, int)
  #define LUNIX_IOC_GETDEVSIZE _IOR(LUNIX_IOC_MAGIC, 1, int)
  #define LUNIX_IOC_GETSTATS _IOR(LUNIX_IOC_MAGIC, 2, int)
  #define LUNIX_IOC_COUNTCHAR _IOWR(LUNIX_IOC_MAGIC, 3, int)
  #define LUNIX_IOC_MAXNR 4
  int retval = 0;
  //int tmp;
  int theLetter;
  int i;
  int count = 0;
  switch(cmd) {
    case LUNIX_IOC_INITIALIZE:

    // lunix_size = tmp
    //dev_initialization(void);
    break;
    case LUNIX_IOC_GETDEVSIZE:
    printk ("<1>The size of Lunix is %d \n", lunix_size);
    break;

    case LUNIX_IOC_GETSTATS:
  printk ("<1> SATISTIC: \n number of OPEN calls is %d \n numbervoid of CLOSE calls is %d \n number of READ calls is %d \n number of WRITE calls is %d \n number of lseek calls is %d \n " , numopen, numclose, numread, numwrite, numlseek);
    break;

    case LUNIX_IOC_COUNTCHAR:
      //if (copy_from_user(lunix_buffer + *fileposition, buffer ,length) != 0)
    if (copy_from_user(&theLetter, &arg, sizeof(int)) != 0)
      return -EFAULT;

    for(i=0; i < cur_len ; i++)
    {
      if (lunix_buffer[i] == theLetter){
        count++;
    }
  }
  printk("<1> \n The letter '%c' appears %d times in the document. \n\n", theLetter, count );
  break;
  default:
 return -ENOTTY;
  }

return retval;

}

```

To build the module, and insert it:
```

make
sudo insmod lmain.ko

```

------------------------------------------

Now for the counter test, which by the way fails (for me) because I do not have a /dev/lunix device file on my system.  Was the kernel driver supposed to create that???

MakeCounter (just name it this, so that it does not clash with the Linux kernel module's makefile):
```

APP      = countchar

SRCS     = countchar.c
OBJS     = $(SRCS:.c=.o)

INCLUDES = -I./
CFLAGS   = -Wall -pedantic -ansi -std=gnu99 -c $(INCLUDES)

LDFLAGS  =


.PHONY: all clean

all: $(APP)

$(APP): $(OBJS)
	$(CC) $^ $(LDFLAGS) -o $@

.c.o:
	$(CC) $(CFLAGS) $<

clean:
	$(RM) $(OBJS)
	$(RM) $(APP)

```
This makefile and the counter.c reside in the same directory as the lunix.h file.  If this were not the case, then the INCLUDES variable in the makefile above would need to be updated.

countchar.c (with corrections):
```

#include <sys/ioctl.h>   // for ioctl
#include <unistd.h>      // for close
#include <stdio.h>
#include <fcntl.h>
#include <lunix.h>

int main ()
{
  printf( "\nThis program counts the appearance of a letter in LUNIX.\n\n");
  printf("\n Type letter to be calculated the appearance of and press enter: \n\n");

  int fd = open("/dev/lunix", O_RDONLY);

  if (fd < 0 ) {
    printf("Error: can't open file.\n");
   return 1;
  }

  ioctl(fd, LUNIX_IOC_COUNTCHAR);

  close(fd);

  return 0;
}

```

To build/run the counter test:
```

make -f MakeCounter
./countchar

```

Results:
```

This program counts the appearance of a letter in LUNIX.


 Type letter to be calculated the appearance of and press enter: 

Error: can't open file.

```

P.S.  Big thanks to MonkeyKing for providing the reformatted code which made my task immensely easier.

---

### Post by simitoco on 2009-07-03
Thank you very much, the lunix device is created manually 

**sudo mknod /dev/lunix c 60 0 **

[B]sudo chmod 0777 /dev/lunix 
[/B]
i am testing the read function with   ** cat /dev/lunix **
and the write with   **echo   some text  > /dev/lunix **

im usually opening another terminal, and with **tail -f /var/log/kern.log** i follow what is happening 

The countchar.c compiles but i think the problem still exist, it seems like it is not connected in anyway to the lmain.c, 'cause it doesn't  give the opportunity to type a letter and it does no work, but this might be due to bugy code.. can you look at it ? 

P.S.  why this ??? I mean, they are both working..
//void __exit lunix_cleanup(void);
void lunix_cleanup(void);

---

### Post by dwhitney67 on 2009-07-03
> **simitoco said:**
> ...give the opportunity to type a letter and it does no work, but this might be due to bugy code.. can you look at it ? 

You never prompt the user/operator for input; perhaps you should look into scanf(), fgetc(), getchar().

But once you get the input, then what?  Your program is not calling any function that would use this input.  Or have I missed something?

> **simitoco said:**
> 
P.S.  why this ??? I mean, they are both working..
//void __exit lunix_cleanup(void);
void lunix_cleanup(void);
The compiler complained that you were calling a function that is designated as an "exit" function, in your "init" function.

---

### Post by simitoco on 2009-07-03
the countchar.c  should make a call to the kernel space : 

**[SIZE=3][COLOR=Red]in lmain.c  [/COLOR][/SIZE]**
[B]
case LUNIX_IOC_COUNTCHAR:
      
    
if (copy_from_user(&theLetter, &arg, sizeof(int)) != 0)
      return -EFAULT;

    for(i=0; i < cur_len ; i++)
    {
[/B][INDENT]**      if (lunix_buffer[i] == theLetter){**
**        count++;**
**     }**
[/INDENT][B]  }
  printk("<1> \n The letter '%c' appears %d times in the document. \n\n", theLetter, count );
  break;[/B]


[COLOR=Red]**[SIZE=3]_in countchar.c _[/SIZE]**[/COLOR]

[B] int fd = open("/dev/lunix", O_RDONLY);

  if (fd < 0 ) {
    printf("Error: can't open file.\n");
   return 1;
  }

  ioctl(fd, LUNIX_IOC_COUNTCHAR);

  close(fd);[/B]





 is this correct way to call the [B]LUNIX_IOC_COUNTCHAR ???

[/B]

---

### Post by dwhitney67 on 2009-07-03
When calling functions, sometimes you need to provide parameters.  Yes, you are passing LUNIX_IOC_COUNTCHAR correctly, however you are not passing the user's input (a single character), nor are you passing the address of the long variable where to store the result.

I would expect the ioctl call to look something like:
```

// prompt user for input
...
int ch = getchar();

unsigned int numLetters = 0;

ioctl(fd, LUNIX_IOC_COUNTCHAR, ch, &numLetters);

...

// display results

```

Unfortunately, your kernel module's ioctl handler is not expecting the parameter for the user's input, and worse, there is no way for the function to return the result.

If you refer to the man-page for ioctl(), it generally takes 2 parameters, but can accept a variable number of others.  Since I am not a guru when it comes to kernel module development, I do not know how to handle the variable parameter thing.

So I cheated and came up with the following solution...

Here's a synopsis of the changes I made, but I could not get fully working because I was unable to read the /dev/lunix char-device.  Your code needs further updates.

lunix.h
```

...

struct UserData
{
  char letter;
  unsigned int count;
};

...

```

lmain.c:
```

...
static int lunix_ioctl(struct inode *inode, struct file *lunix, unsigned int cmd, struct UserData* data);
...

static int lunix_ioctl(struct inode *inode, struct file *lunix, unsigned int cmd, struct UserData* data)
{
  ...

  switch(cmd)
  {
    ...

    case LUNIX_IOC_COUNTCHAR:
    {
      printk("\nUser passed character: %c\n", data->letter);

      //if (copy_from_user(lunix_buffer + *fileposition, buffer ,length) != 0)
      //if (copy_from_user(&count, &data->count, sizeof(count)) != 0)
      //  return -EFAULT;

      data->count = 0;

      // TODO: the lunix_buffer does not contain any information AND/OR cur_len is 0.
      for (i = 0; i < cur_len ; ++i)
      {
        if (lunix_buffer[i] == data->letter)
          ++data->count;
      }
      printk("<1> \n The letter '%c' appears %d times in the document. \n\n", data->letter, data->count);
    }
    break;

    ...
  }

  ...
}

```

This warning also appears, which truly shows that I do not know what I am doing.
```

  CC [M]  /home/whitney/Languages/KernelModule/test/lmain.o
/home/whitney/Languages/KernelModule/test/lmain.c:56: warning: initialization from incompatible pointer type

```
Nevertheless, I am able to pass data successfully to the kernel module and return a value to the user.

The only thing lacking is to populate the lunix_buffer and/or set the cur_len as appropriate.

---

### Post by simitoco on 2009-07-06
Thanks to everyone for the help ;)
I finally managed to clear up the errors and explain myself what is going on.

this is the final code for countchar.c 
the comments explain what i fixed.



#include <sys/ioctl.h>   // for ioctl
#include <unistd.h>      // for close
#include <stdio.h>
#include <fcntl.h>
#include "lunix.h"      // in the previous version i was including **<lunix.h>** 
#include <assert.h>




int main ()
{    
  printf( "\nThis program counts the appearance of a letter in LUNIX.\n\n");
  printf("\n Type letter to be calculated the appearance of and press enter: \n\n");
  
  int theLetter = getchar() ;
  int fd; // before that was ***fd**
  fd = open("/dev/lunix", O_RDONLY | O_NONBLOCK ); // **(O_RDONLY , O_NONBLOCK) = 0 **

  if (fd < 0 ) {
    printf("Error: can't open file.\n");
   return 1;
  }


  ioctl(fd, LUNIX_IOC_COUNTCHAR, &theLetter); // before, when i pass theLeter to the kernel module i was converting the address of the address: see LUNIX_IOC_COUNTCHAR in lmain.c for more info 

  close(fd);

 return 0;

}    



:lolflag:




**this is lmain.c **



#include <linux/module.h>
#include <linux/kernel.h>
#include <linux/autoconf.h>
#include <linux/types.h>
#include <linux/kdev_t.h>
#include <linux/fs.h> /* file_operations structure */
#include <linux/init.h>
#include <linux/moduleparam.h>
#include <linux/slab.h> /* kmalloc*/
#include <linux/errno.h>
#include <linux/proc_fs.h>
#include <linux/fcntl.h>
#include <linux/seq_file.h>
#include <linux/cdev.h> /* Char Device Registration */
#include <linux/stat.h>



#include <asm/system.h> /* cli(), *_flags */
#include <asm/uaccess.h> /* copy_*_user */

#include "lunix.h"


MODULE_LICENSE("Dual BSD/GPL");
/*MODULE_VERSION */
/*MODULE_DESCRIPTION */
MODULE_AUTHOR("MSIM");
/*MODULE_DEVICE_TABLE */
/*MODULE_ALIAS */


int lunix_size = 524288; /*lunix size is 524288 bytes */


int __init lunix_init(void);
void __exit lunix_cleanup(void);



static int lunix_open(struct inode *inode, struct file *lunix);
static int lunix_release(struct inode *inode, struct file *lunix);
static ssize_t lunix_read(struct file *lunix, char __user *buffer, size_t length, loff_t *fileposition);
static ssize_t lunix_write(struct file *lunix, const char __user *buffer, size_t length, loff_t *fileposition);
static int lunix_ioctl(struct inode *inode, struct file *lunix, unsigned int cmd, unsigned long arg);
static loff_t lunix_llseek(struct file *lunix, loff_t offset,int fileposition);


static struct file_operations lunix_fops = {
.owner = THIS_MODULE,
.read = lunix_read,
.write = lunix_write,
.open = lunix_open,
.release = lunix_release,
.ioctl = lunix_ioctl,
.llseek = lunix_llseek,
}
;

module_init(lunix_init);
module_exit(lunix_cleanup);

int lunix_major = 60;


char *lunix_buffer;
int cur_len;
int numopen;
int numclose;
int numread;
int numwrite;
int numlseek;


void dev_initialization(void)
{
  memset(lunix_buffer, 0, lunix_size);
  cur_len = 0;
  numopen = 0;
  numclose = 0;
  numread = 0;
  numwrite = 0;
  numlseek = 0;
}

/* INIT function */

int __init lunix_init(void){
  int result;

  /* Registering device */
  result = register_chrdev(lunix_major, "lunix", &lunix_fops);
  if (result < 0) {
    printk( "<1> lunix: cannot obtain major number%d\n",
           lunix_major);
  return result;
  }

  /* Allocating memory for the buffer */
  lunix_buffer = kmalloc(lunix_size, GFP_DMA | GFP_KERNEL);
  if (!lunix_buffer) {
    result = -ENOMEM;
    goto fail;
  }

  dev_initialization();

  printk("<1> Inserting lunix module\n");
  return 0;

  fail:
  lunix_cleanup();
  return result;
}




/* EXIT function */

void __exit lunix_cleanup(void)
/*void lunix_cleanup(void)*/
{

  /* Freeing the major number */
  unregister_chrdev(lunix_major, "lunix");

  /* Freeing lunix buffer */
  if (lunix_buffer) {
    kfree(lunix_buffer);
  }

  printk("<1> Removing lunix module\n");
}

static int lunix_open(struct inode *inode, struct file *lunix)
{
  numopen++ ;
  return 0;
}

static int lunix_release(struct inode *inode, struct file *lunix)
{
  numclose++ ;
  return 0;
}

static ssize_t lunix_read(struct file *lunix, char __user *buffer, size_t length, loff_t *fileposition)
{
  numread++ ;
  printk("<1> read function start\n");

  /*checking if the user */
  if (*fileposition + length > cur_len)
    length = cur_len - *fileposition;  /*doesnt want to much*/

  printk("<1> read. checked if the user ...\n");

  if(copy_to_user(buffer, lunix_buffer + *fileposition,length) != 0)
    return -EFAULT;

  printk("<1> read.after copy user \n");

  /* updating the file position*/
  *fileposition = *fileposition + length; 
  printk("<1> read.before return length \n");
  return length;

}

static ssize_t lunix_write(struct file *lunix, const char __user *buffer, size_t length, loff_t * fileposition)
{
  numwrite++ ;
  printk("<1> write function started\n");

  /*checking if the user doesnt want to much*/
  if (*fileposition + length > lunix_size)
    length = lunix_size - *fileposition; 
  printk("<1> write checking if the user...\n");
  if (cur_len < length + *fileposition)
    cur_len = length + *fileposition;

  if (copy_from_user(lunix_buffer + *fileposition, buffer ,length) != 0)
    return -EFAULT;
  /* updating the file position*/
  *fileposition = *fileposition + length; 
  printk("<1> write.before return length, length is %d \n", length);
  return length;

}

  
static loff_t lunix_llseek(struct file *lunix, loff_t offset,int fileposition)

{

  numlseek++;

  loff_t newpos;

  switch(fileposition) {
    case 0: /* SEEK_SET  The new position is set to offset bytes.*/
    newpos = offset;
    break;

    case 1: /* SEEK_CUR  The offset is set to its current location plus offset bytes.*/
    newpos = fileposition + offset;
    break;

    case 2: /* SEEK_END  The offset is set to the size of the file plus offset bytes.*/
    newpos = lunix_size + offset;
    break;

    default:
    return -EINVAL;
   }


  return newpos;
}


static int lunix_ioctl(struct inode *inode, struct file *lunix, unsigned int cmd, unsigned long arg)
{

  
  int retval = 0;
  int lunsize;
  int theLetter;
  int i;
  int count = 0;
printk("<1> \n i am before switch \n"); 
  switch(cmd) {
    case LUNIX_IOC_INITIALIZE:

      
      if (copy_from_user(&lunsize, (void*)arg, sizeof(int)) != 0)
      return -EFAULT;
        lunix_size = lunsize ;
    dev_initialization();
      printk("<1> \n The new devise size is set to %d bytes. \n ", lunix_size);

    break;
    case LUNIX_IOC_GETDEVSIZE:
    printk ("<1>\n The size of Lunix is %d bytes. \n", lunix_size);
    

    break;

    case LUNIX_IOC_GETSTATS:
  printk ("<1> \n SATISTIC: \n number of OPEN calls is %d \n number of CLOSE calls is %d \n number of READ calls is %d \n number of WRITE calls is %d \n number of lseek calls is %d \n " , numopen, numclose, numread, numwrite, numlseek);
    break;

    case LUNIX_IOC_COUNTCHAR:
  
     printk("<1> \n i am before COPY_FROM_USER \n"); 
      if (copy_from_user(&theLetter, (void*)arg, sizeof(int)) != 0)  // here i had &arg(wrong) i need just arg.  I am coppyng the arg (&theLetter from countchar.c) to &theLetter (in lmain.c) with sizeof(int) and check if is good. 
      return -EFAULT;

    for(i=0; i < cur_len ; i++)
    {
      if (lunix_buffer[i] == theLetter){
        count++;
    }
  }
  printk("<1> \n The letter '%c' appears %d times in the document. \n\n", theLetter, count );
  break;
  default:
 return -ENOTTY;
  }

return retval;

}


**Thank you everyone !!! **

---

