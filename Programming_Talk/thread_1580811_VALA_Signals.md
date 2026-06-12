---
title: "VALA: Signals"
date: 2010-09-23
forum: Programming Talk
---

### Post by ierosvin on 2010-09-23
Hi everyone.

im new here so kindly let me know if this new thread is out of place. :)

anyway, is anyone here familiar with vala? especially working with signals aka event handlers?
how am i supposed to catch the signal, say SIGUSR1, and assign an event handler for this?

```
//this must catch the signal SIGUSR1
my_handler.connect((t) => {
    printf("In SIGUSR1 handler!");
});
```thanks!

---

### Post by aanderse on 2010-10-06
like so:

void main () {
Posix.signal (Posix.SIGUSR1, (s) => {
stdout.printf ("In SIGUSR1 handler!");
});

---

### Post by ierosvin on 2010-10-08
hi!

anyone here familiar with developing apps using vala? could you please refer me to the most appropriate forum site you know regarding Vala?

anyhow, heres my problem:

im trying to use signal from posix.vapi(yes, not the signal of vala itself) to catch the signal SIGUSR1(signal from posix too) and print something when the signal is catched successfully:

```
sighandler_t resig_handler = (signum) => {
   stdout.printf("Success!");
};
signal(SIGUSR1, resig_handler);
```but everytime i compile the ff error is returned:

```
In function '_lambda0_':
test.vala.c:162: error: 'self' undeclared (first use in this function)
test.vala.c:162: error: (Each undeclared identifier is reported only once
test.vala.c:162: error: for each function it appears in.)
test.vala.c: In function 'test_open_vt':
test.vala.c:176: error: 'sighandler_t' undeclared (first use in this function)
test.vala.c:176: error: expected ';' before 'resig_handler'
test.vala.c:186: error: 'resig_handler' undeclared (first use in this function)
error: cc exited with status 256
Compilation failed: 1 error(s), 0 warning(s)
```Looks like my lambda expression is causing the problem.
Please help.

Thanks!

---

### Post by ibuclaw on 2010-10-10
Merged post with original thread.

---

### Post by aanderse on 2010-10-14
what version of valac are you using?

i've found some references on the internet that say sighandler_t is a gnu extension
your c compiler isn't including the definition of sighandler_t for some reason... you should find out why and how to fix that (mine isn't either)

once you figure out how to get your c compiler to properly define sighandler_t then the errors your c compiler reported for line 176 and 186 should be fixed.

the error on line 162 is a different error though, and i have a suspicion that you should update your valac compiler to a newer version because it might be a bug in (which has been fixed in my version of valac - 0.9.8)

and you should post problems to the vala mailing list, lots of helpful friendly people

---

