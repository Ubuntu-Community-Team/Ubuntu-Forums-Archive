---
title: "How to add a C file and Enable it in Linux Kernel?"
date: 2012-07-06
forum: Programming Talk
---

### Post by geewhan on 2012-07-06
I would like to know how would you enable the Congestion Control Algorithm correctly (lets call it Tcp_quic or quic).

My code is almost exactly like the tcp_veno.c file. Just the algorithm in the tcp_veno_cong_avoid() function changed.
I would like to attached the code on here, but I got an upload error. I would post it as well, but it is pretty long.

I have successfully compile the Linux Kernel with the C file (in the directory linux-3.4-rc7\net\ipv4\tcp_quic.c)
I just need to enable it, so I can use my algorithm and add it to the Kernel. 

I know that most people said that you should not mess with the Kernel, but it is something I would like to try.

The code below is how I should be able to enable the Congestion Control Algorithm.

```
echo quic > /proc/sys/net/ipv4/tcp_congestion_control
```

This code works for vegas, cubic, and veno because they are in the Linux Kernel.

Is there another file or something that I need to edit to make this change?

```
bash: echo: write error: No such file or directory
```

---

### Post by hansdown on 2012-07-06
Hi geewhan.

You may wish to look at the second listing here...

---

### Post by geewhan on 2012-07-06
hansdown,

thanks for you help, but I feel like there may be still a problem with that line of code.

I believe when it says "newalgorithm", it uses the other congestion control algorithm. There are three congestion control algorithm there in the pic "Highspeed", "probe", and "yeah" and more if you were to look at that site. That is a way to enable a congestion control, but when I added my file/Congestion Control Algorithm call "quic" I cannot Enable it. Like I said I did this in the following.


```
echo quic > /proc/sys/net/ipv4/tcp_congestion_control
```

and got this error

```
bash: echo: write error: No such file or directory
```

---

### Post by hansdown on 2012-07-07
> **geewhan said:**
> hansdown,

thanks for you help, but I feel like there may be still a problem with that line of code.

I believe when it says "newalgorithm", it uses the other congestion control algorithm. There are three congestion control algorithm there in the pic "Highspeed", "probe", and "yeah" and more if you were to look at that site. That is a way to enable a congestion control, but when I added my file/Congestion Control Algorithm call "quic" I cannot Enable it. Like I said I did this in the following.


```
echo quic > /proc/sys/net/ipv4/tcp_congestion_control
```

and got this error

```
bash: echo: write error: No such file or directory
```

Please don't take this wrong.

Are you using 32BIT?

Something that "may help",

[http://wiki.freeswitch.org/wiki/Performance_testing_and_configurations](http://wiki.freeswitch.org/wiki/Performance_testing_and_configurations)

---

### Post by geewhan on 2012-07-07
I believe I am using 32 bits. I am not on my desktop that I can 100% confirm this, but it is most likely 32 bits.

However, how does this relate to the problem?

---

### Post by hansdown on 2012-07-07
> **geewhan said:**
> I believe I am using 32 bits. I am not on my desktop that I can 100% confirm this, but it is most likely 32 bits.

However, how does this relate to the problem?

Under recommended hardware/os, it kinda' says that.

---

### Post by geewhan on 2012-07-07
I just realize that in the Linux Kernel folder(kernel\linux-3.3.6\net\ipv4), where I added the tcp_quic.c file, does not have .mod.o or .o file. With means that the tcp_quic.c did not compile successfully, right? However why did the compile in the terminal compile successfully? I read on one forum that may be I need to change something in the MAKEFILE to have .o file, is this true? I am not sure how I would do this if it is so.

---

