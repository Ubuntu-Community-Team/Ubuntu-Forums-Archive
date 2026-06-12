---
title: "Just installed ubuntu, now some questions.."
date: 2008-07-20
forum: New to Ubuntu
---

### Post by kramer65 on 2008-07-20
Hello,

I just installed ubuntu on my new computer. I have some problems now:

1. When I installed ubuntu I apparently had my capslock on. My password is therefore with only caps. How can I change my password?

2. I have a NVIDIA 9600 GT. It does'n say there are any drivers for it. I just installed EnvyNG which doesn't give anything either. Does anybody know where I can get them?

3. I think I installed /home on a separate. How can I check that?

4. When I am writing this, I see that when I want to write a ' (single quote), I need to tick that first, and then a space to get it to appear. How can I get it to appear immediately (without the space?

Hope you guys can help!

---

### Post by ConMan318 on 2008-07-20
1. Applications > Accessories > Terminal.  Type "passwd" without the quotes.  Self-explanatory from there.

Can't really help much with the others.  Good luck with Ubuntu!

---

### Post by drs305 on 2008-07-20
> **kramer65 said:**
> 
1. When I installed ubuntu I apparently had my capslock on. My password is therefore with only caps. How can I change my password?
```
sudo passwd ***username***
```

3. Run this command. If you have a separate home this will show the listing in fstab.
```

cat /etc/fstab | grep home

```

Here's what mine looks like:
```
UUID=eb10b281 /home ext3 nodev,nosuid 0 2
```

Welcome to ubuntu!
[B]
Added:[/B]

I found bug reports saying the 9600 wasn't supported but then I found this in a bug report
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/231989]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/231989"):
[B][I]
You can install EnvyNG and enable the hardy-proposed repositories so as
to get the latest release of the driver.

Read here for further details:
[http://albertomilone.com/wordpress/?p=210](http://albertomilone.com/wordpress/?p=210)
[/I][/B]

I further read that the 173.14.05 version of EnvyNG drivers should work.

---

### Post by asmoore82 on 2008-07-20
Here are some newbie-friendly GUI answers:

> **kramer65 said:**
> Hello,

I just installed ubuntu on my new computer. I have some problems now:

1. When I installed ubuntu I apparently had my capslock on. My password is therefore with only caps. How can I change my password?



Open "System -> Preferences -> About Me"
Then click "Change Password" in the upper-right

> **kramer65 said:**
> 2. I have a NVIDIA 9600 GT. It does'n say there are any drivers for it. I just installed EnvyNG which doesn't give anything either. Does anybody know where I can get them?

Open "System -> Administration-> Synaptic Package Manager"
search for and install `nvidia-glx-new` and maybe `nvidia-settings` too

If all else fails, I would say be patient and wait for
"System -> Administration -> Hardware Drivers" to be able to help you automagically
You could follow instructions at nvidia.com and probably get it working,
but this might make things harder on future Ubuntu Software Updates.

> **kramer65 said:**
> 3. I think I installed /home on a separate. How can I check that?

Open "System -> Administration -> System Monitor"
then click the "File Systems" tab (last one).
> **kramer65 said:**
> 4. When I am writing this, I see that when I want to write a ' (single quote), I need to tick that first, and then a space to get it to appear. How can I get it to appear immediately (without the space?

Hope you guys can help!
I'm not sure, this maybe just a cosmetic glitch, sometimes the blinking cursor makes it hard/impossible to see small charaters you just typed ?????

---

### Post by hyper_ch on 2008-07-20
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by kramer65 on 2008-07-20
Thanks a lot!

1, 2 and 3 are solved. 
I finally used the suggested manual driver that EnvyNG suggested and that works like a charm!

Also, I am happy to see that my home folder is done seperate. I hear that that is the best.. :-)

Anybody a tip for the 4th?

Everybody thanks anyway!

---

### Post by billgoldberg on 2008-07-20
> **kramer65 said:**
> Hello,

I just installed ubuntu on my new computer. I have some problems now:

1. When I installed ubuntu I apparently had my capslock on. My password is therefore with only caps. How can I change my password?

2. I have a NVIDIA 9600 GT. It does'n say there are any drivers for it. I just installed EnvyNG which doesn't give anything either. Does anybody know where I can get them?

3. I think I installed /home on a separate. How can I check that?

4. When I am writing this, I see that when I want to write a ' (single quote), I need to tick that first, and then a space to get it to appear. How can I get it to appear immediately (without the space?

Hope you guys can help!

I have no idea about the '.

All I can say that with my keyboard layout (azerty) this doesn't happen.

If it is even related to the keyboard layout.

Is that really such a big issue?

---

### Post by drs305 on 2008-07-20
> **kramer65 said:**
> 4. When I am writing this, I see that when I want to write a ' (single quote), I need to tick that first, and then a space to get it to appear. How can I get it to appear immediately (without the space?


Are you using the correct keyboard. Some international keyboards are set up this way. You can check your keyboard with System, Preferences, Keyboard, Layouts. If you want a US keyboard, you might try another (non-international) keyboard. 'Generic' is a good starting point if your keyboard isn't listed.

You can try resetting the keyboard setup with the following as well, which may be easier as it presents fewer choices at the outset:
```
sudo dpkg-reconfigure console-setup
```

---

