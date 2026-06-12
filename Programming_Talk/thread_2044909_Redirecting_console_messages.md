---
title: "Redirecting console messages"
date: 2012-08-20
forum: Programming Talk
---

### Post by vbalaganesh on 2012-08-20
I am a newbie to device driver pgming..

Referred and tried the code from Linux device drivers 3rd edition book Pg.no 78.
or [http://www.makelinux.net/ldd3/chp-4-sect-2]("http://http://www.makelinux.net/ldd3/chp-4-sect-2") , under sec 4.2.2

Pgm calls the following fn to change the console automatically,

ioctl(STDIN_FILENO , TIOCLINUX ,other args);

The problem is after compiling the code gets successfully executed in any of the tty1 to tty6 in ubuntu.

But it is not executing successfully from the graphical 'terminal' of ubuntu.

Any one please reply the reason.........

---

### Post by ofnuts on 2012-08-21
You didn't read the small print. From your URL:
> Linux allows for some flexibility in console logging policies by letting you send messages to a specific virtual console ***[SIZE=4](if your console lives on the text screen)[/SIZE]***.

---

### Post by vbalaganesh on 2012-08-21
Hi ,,

I am clear that linux will allow us to send messages to specific console.

But the question is ,,

why this code for selecting the console is not able to execute in the 'terminal' application of Ubuntu.?????????? but executing in blank consoles i.e tty1 to tty6.

---

### Post by ofnuts on 2012-08-21
> **vbalaganesh said:**
> Hi ,,

I am clear that linux will allow us to send messages to specific console.

But the question is ,,

why this code for selecting the console is not able to execute in the 'terminal' application of Ubuntu.?????????? but executing in blank consoles i.e tty1 to tty6.
Because ioctl() is device-dependent (it talks to the device driver) and the standard output in a terminal window isn't handled by the same device as in the tty/* terminals. In a tty/* session:

```

> ls -l /dev/stdin
lrwxrwxrwx 1 root root 15 2012-08-21 01:22 /dev/stdin -> /proc/self/fd/0
> ls -l /proc/self/fd/0
lrwx------ 1 xx xx 64 2012-08-21 19:22 /proc/self/fd/0 -> /dev/tty1

```and in a terminal window:

```

> ls -l /dev/stdin
lrwxrwxrwx 1 root root 15 2012-08-21 01:22 /dev/stdin -> /proc/self/fd/0
> ls -l /proc/self/fd/0
lrwx------ 1 xx xx 64 2012-08-21 19:22 /proc/self/fd/0 -> /dev/pts/1

```dev/pts is simulated by the application managing the terminal window. You get something similar when you run ssh.

PS: examples above are with stdin. You can do the same with 'stdout' to find similar results.

---

### Post by vbalaganesh on 2012-08-24
Hi ,,
 
Got the point. Thank you for your help  :p

---

