---
title: "Large Screen Error Message"
date: 2019-01-13
forum: New to Ubuntu
---

### Post by cantexitvim on 2019-01-13
First, I apologize if this is a dumb question.

When I was installing bluetooth drivers, I recieved a large error message that covered the entire screen. The message kept repeating and I was forced to shut-down the computer with the power button, which probably isn't a good thing. Thus, I was wondering what this message was and if there is any way to exit out of it or kill whatever process it is trying to run. 

Error: 
 [110.301616] Bluetooth: hci0: last event is not a cmd complete (0x0f)

Note: I have been able to  connect the bluetooth device by following some stackoverflow suggestions. Just want to know what this black screen is.

[ATTACH=CONFIG]282199[/ATTACH]

---

### Post by puddlemaker on 2019-01-21
You can run

```
$ sudo dmesg | tail
```

this will output the log of your last bootup.

If you require a full log, run

```
sudo dmesg | more
```

I added the pipe 'more' to allow for scrolling within the log via PgUp/PgDwn btw.

See Ubuntu Kernel Bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1748565](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1748565)

Hope that helps somewhat. Cheers!

---

### Post by deadflowr on 2019-01-21
See: [lpbug]1748565[/lpbug]

---

