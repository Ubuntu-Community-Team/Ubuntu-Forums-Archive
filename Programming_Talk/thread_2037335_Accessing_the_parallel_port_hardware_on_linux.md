---
title: "Accessing the parallel port hardware on linux"
date: 2012-08-04
forum: Programming Talk
---

### Post by ganeshredcobra on 2012-08-04
I wrote a parallel port Linux device driver but I cant access the parallel port hardware


#include <linux/init.h>
#include <linux/autoconf.h>
#include <linux/module.h>
#include <linux/kernel.h> 
#include <linux/slab.h> 
#include <linux/fs.h> 
#include <linux/errno.h> 
#include <linux/types.h>
#include <linux/proc_fs.h>
#include <linux/fcntl.h>
#include <linux/ioport.h>
#include <asm/system.h> 
#include <asm/uaccess.h> 
#include <asm/io.h> 
#define DRVNAME "parportleds"
#define BASEPORT 0x378

MODULE_LICENSE("Dual BSD/GPL");
MODULE_AUTHOR("Ganesh");
MODULE_DESCRIPTION("Parallel port LED driver.");


int parportleds_open(struct inode *inode, struct file *filp);
int parportleds_release(struct inode *inode, struct file *filp);
ssize_t parportleds_read(struct file *filp,char *buf,size_t count, loff_t *f_pos);
ssize_t parportleds_write(struct file *filp, const char *buf,size_t count, loff_t   *f_pos);

void parportleds_exit(void);
int parportleds_init(void);


struct file_operations parportleds_fops = {
  read: parportleds_read,
  write: parportleds_write,
  open: parportleds_open,
  release: parportleds_release
};

int parportleds_major = 61;
int port;

module_init(parportleds_init);
module_exit(parportleds_exit);

int parportleds_init(void) {
  int result;
  result = register_chrdev(parportleds_major, DRVNAME,&parportleds_fops);
  if (result < 0) {
    printk("<1>parport: cannot obtain major number %d\n",parportleds_major);
    return result;
  }
  port = check_region(BASEPORT, 1);
  if (port) {
    printk("<1>parportleds: cannot reserve 0x378 \n");
    result = port;
    goto fail;
  }
  request_region(BASEPORT, 1, DRVNAME);
  printk("<1>Inserting parportled module\n");
  return 0;
  fail:
    parportleds_exit();
    return result;
}
void parportleds_exit(void) {
  unregister_chrdev(parportleds_major, DRVNAME);
  if (!port) {
    release_region(BASEPORT,1);
  }
  printk("<1>Removing module parportleds\n");
}
int parportleds_open(struct inode *inode, struct file *filp) {
  return 0;
}
int parportleds_release(struct inode *inode, struct file *filp) {
  return 0;
}
ssize_t parportleds_read(struct file *filp, char *buf,size_t count, loff_t *f_pos) {
  char parportleds_buffer;
  parportleds_buffer = inb(BASEPORT);
  copy_to_user(buf,&parportleds_buffer,1);
  if (*f_pos == 0) {
    *f_pos+=1;
    return 1;
  } else {
    return 0;
  }
}
ssize_t parportleds_write( struct file *filp, const char *buf, size_t count, loff_t     *f_pos) {
  char *tmp;
  char parportleds_buffer;
  tmp=(char *)buf+count-1;
  copy_from_user(&parportleds_buffer,tmp,1);
  outb(parportleds_buffer,BASEPORT);
  printk("<1>parport write: %d\n",parportleds_buffer);
  return 1;
}

This is my code when I try to read and write to /dev/parportleds am getting a sucess msg in dmesg
But when i try to make a pin high of parallel port using echo 3 > /dev/parportleds
The voltage of the datapins of paralleport remains same.
can anyone help me to fix this issue.
its my first attempt to write device drivers.

---

### Post by xb12x on 2012-08-04
The first thing to check is the BIOS Setup:

The PC originally supported 3 parallel ports at LPT1-0x378, LPT2-0x278, LPT3-0x3BC. So go into the BIOS Setup and make sure the parallel port is actually at base-address 0x378, and also that it is Enabled.

---

### Post by ganeshredcobra on 2012-08-05
Thanks....i checked my bios in peripheral devices there is only one option to enable and disable parallelport there is no option to set base address....

---

### Post by xb12x on 2012-08-05
PC Parallel ports could be set to run in up to four different modes (depending on the age of the PC, its chipset, and its BIOS): 
1. Output-only
2. Bi-directional
3. EPP
4. ECP

Each mode had different hardware settings and pin-outs. You should check your BIOS Setup to see if there is a mode setting for the parallel port. 

Also, have you checked your system's '/proc/ioports' file? You should find entries similar to:

0378-037a : parport0
037b-037f : parport0

Make sure nothing else conflicts with the parallel port's address range. Just to be certain, try disabling your parallel port in the BIOS Setup, re-booting, and then re-checking the '/proc/ioports' file to see if something else then shows up at 0x378-0x37F. This might indicate a hardware initialization conflict of some sort.

---

