---
title: "What is the meaning of line  while((dvp-&gt;csr &amp; (READY | ERROR)) == 0)"
date: 2012-03-16
forum: Programming Talk
---

### Post by c2tarun on 2012-03-16
Hi Friends
I was reading an article on const and volatile type qualifiers from this page [http://publications.gbdirect.co.uk/c_book/chapter8/const_and_volatile.html](http://publications.gbdirect.co.uk/c_book/chapter8/const_and_volatile.html) I found following code from this page.

```
/* Standard C example but without const or volatile */
/*
 * Declare the device registers
 * Whether to use int or short
 * is implementation dependent
 */

struct devregs{
        unsigned short  csr;    /* control & status */
        unsigned short  data;   /* data port */
};

/* bit patterns in the csr */
#define ERROR   0x1
#define READY   0x2
#define RESET   0x4

/* absolute address of the device */
#define DEVADDR ((struct devregs *)0xffff0004)

/* number of such devices in system */
#define NDEVS   4

/*
 * Busy-wait function to read a byte from device n.
 * check range of device number.
 * Wait until READY or ERROR
 * if no error, read byte, return it
 * otherwise reset error, return 0xffff
 */
unsigned int read_dev(unsigned devno){

        struct devregs *dvp = DEVADDR + devno;

        if(devno >= NDEVS)
                return(0xffff);

        while((dvp->csr & (READY | ERROR)) == 0)
                ; /* NULL - wait till done */

        if(dvp->csr & ERROR){
                dvp->csr = RESET;
                return(0xffff);
        }

        return((dvp->data) & 0xff);
}

```

I am not able to understand the meaning of line in bold, can anyone please explain me.
Thank you.

---

### Post by satsujinka on 2012-03-16
Basically, what that line does is loop until csr is equal to either READY or ERROR. I assume there's another thread running somewhere that will update dvp's csr and data fields. So the loop will check whether or not something needs to be done (we're ready to use the data or there was an error.)

---

### Post by c2tarun on 2012-03-17
> **satsujinka said:**
> Basically, what that line does is loop until csr is equal to either READY or ERROR. I assume there's another thread running somewhere that will update dvp's csr and data fields. So the loop will check whether or not something needs to be done (we're ready to use the data or there was an error.)
 
 
csr is EQUAL to?? How? I am not able to understand the meaning of single '?' and '|'
 
 
OMG!!! they are bitwise operators, I am an idiot :(
it will first manipulate (READY | ERROR) and then the result will be manipulated to csr(state register). If any value is 0 it will wait otherwise it will come out of loop.
 
Please correct me if I am wrong.

---

### Post by schauerlich on 2012-03-17
> **c2tarun said:**
> csr is EQUAL to?? How? I am not able to understand the meaning of single '?' and '|'
 
 
OMG!!! they are bitwise operators, I am an idiot :(
it will first manipulate (READY | ERROR) and then the result will be manipulated to csr(state register). If any value is 0 it will wait otherwise it will come out of loop.
 
Please correct me if I am wrong.

```
ERROR = 0x1 = 0001
READY = 0x2 = 0010
(READY | ERROR) = (0010 | 0001) = 0011

```
dvp->csr & (READY | ERROR) == 0 exactly when neither the last nor the second to last bits of dvp->csr are 1. That is, when the state is neither READY nor ERROR. So, wait until the state is ready or an error.

---

### Post by c2tarun on 2012-03-17
> **schauerlich said:**
> ```
ERROR = 0x1 = 0001
READY = 0x2 = 0010
(READY | ERROR) = (0010 | 0001) = 0011

```
dvp->csr & (READY | ERROR) == 0 exactly when neither the last nor the second to last bits of dvp->csr are 1. That is, when the state is neither READY nor ERROR. So, wait until the state is ready or an error.
 
Thanks for the awesome explanation, I am marking this thread as solved. :)

---

### Post by matt_symes on 2012-03-17
Hi

It's a busy wait loop. Don't use them if possible.

Kind regards

---

