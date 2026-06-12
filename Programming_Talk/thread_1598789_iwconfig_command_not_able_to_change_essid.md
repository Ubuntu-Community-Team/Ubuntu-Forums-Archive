---
title: "iwconfig command not able to change essid"
date: 2010-10-17
forum: Programming Talk
---

### Post by vksingh on 2010-10-17
Hi ,

I am using iwconfig command to change essid. 

[I]vivek@vivek-laptop:~$ sudo iwconfig eth2 essid "IIITB-Room-134-LW1"
vivek@vivek-laptop:~$ 
[/I]
But there is no effect. Can some body help me?


Thanks,

Vivek

---

### Post by zippaplick on 2010-10-17
When you say "no effect" do you mean the essid didn't change for the interface?

Running iwconfig by itself shows the wrong essid? Or you don't get a new address assigned?


Depending on the driver, you might need to bring the interface down before changing the settings. 
try:

```

sudo ifconfig eth2 down
sudo iwconfig eth2 essid "IIITB-Room-134-LW1"
sudo ifconfig eth2 up

```

Then depending on your network, you may need to get a new address:

```

sudo dhclient eth2

```

Note, to see what networks are visible, you can run:

```
sudo iwlist scan 
```



Also note that NetworkManager can screw things up if you are setting your network config manually. You might want to check how NetworkManager is configured and perhaps tell it to leave eth2 alone if that's what you want.

---

