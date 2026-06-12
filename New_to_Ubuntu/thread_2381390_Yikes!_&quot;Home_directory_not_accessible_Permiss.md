---
title: "Yikes! &quot;Home directory not accessible: Permission denied&quot;"
date: 2017-12-30
forum: New to Ubuntu
---

### Post by kate.t on 2017-12-30
Hello, all!

While tinkering with my bluetooth problems, I uninstalled and reinstalled blueman. In between those two actions, I restarted my computer. I was planning to restart anyway, but I had also lost my wireless connection (this happens periodically, and a restart fixes it).

After I reinstalled blueman, I typed into the terminal:

```
sudo pactl load-module module-bluetooth-discover
```

This is the response I got:

```
Home directory not accessible: Permission denied
Failure: Module initialization failed
```

I am used to getting "module initialization failed", but I never saw "Home directory not accessible: Permission denied" before.

Is this as dire as it looks??? What should I do? I'm afraid to do a thing.

Thanks in advance!

Kate

---

### Post by jeremy31 on 2017-12-30
kate.t
Try the command without sudo

---

### Post by kate.t on 2017-12-30
Thanks, Jeremy31!

Well, that was simple! Such a newbie error! :oops:

Now I just get 

```
Failure: Module initialization failed
```

which is what always happens.

---

### Post by jeremy31 on 2017-12-30
Are you sure it isn't already loaded?
```
pactl list short | grep blue
```

---

### Post by kate.t on 2017-12-30
Jeremy31,

When I copy and paste that line of code in and hit enter, nothing happens at all, not that I can see. I'm just taken back to the prompt.

---

### Post by jeremy31 on 2017-12-30
Strange as mine returns
```
pactl list short | grep blue
8	module-bluetooth-policy		
9	module-bluetooth-discover		
10	module-bluez5-discover		
```

---

### Post by kate.t on 2017-12-30
Jeremy31,

No, I get nothing but the prompt.

I then separately tried to "load-module" each one, and for each one I got:

```
Failure: Module initialization failed


```

Could this be what's preventing bluetooth from working?

Kate

---

### Post by Autodave on 2017-12-30
Dumb question, but are you sure that your PC is Bluetooth ready?

---

### Post by deadflowr on 2017-12-30
Is bluetooth even loading per the system?
```
lsmod | grep bluetooth
```

---

### Post by kate.t on 2017-12-30
Deadflowr, this is the result, 

```
lsmod | grep bluetooth
bluetooth             557056  41 btrtl,btintel,bnep,btbcm,rfcomm,btusb

 
```

Kate

---

### Post by jeremy31 on 2017-12-30
> **Autodave said:**
> Dumb question, but are you sure that your PC is Bluetooth ready?
Autodave, if it is the same computer kate.t has posted about in the past, the answer is yes

---

### Post by kate.t on 2017-12-30
Autodave,

Sorry I missed your post! Thanks, but yes, my laptop is bluetooth ready.

---

