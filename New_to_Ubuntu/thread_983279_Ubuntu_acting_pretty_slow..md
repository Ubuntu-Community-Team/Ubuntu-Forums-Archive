---
title: "Ubuntu acting pretty slow."
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Obero on 2008-11-15
I've been using Ubuntu for a little while now, and I've installed all the basic software and updates I need. But every once in a while, Ubuntu kind of slows down a lot and it takes a while to come back to regular speed.  Anyway reason why? I figure you guys need some kind of terminal output or screenshot or something, so tell me what to do.

Thanks in advance.

---

### Post by sirjoebob on 2008-11-15
I'm not sure what would cause it but a good place to start would be listing your system specs. Give us Ram, CPU, and if you are using any SWAP space. 

Also, do you notice any pattern such as flash in firefox or anything else that seems to preface the slowdowns?

---

### Post by jenkinbr on 2008-11-15
You could probably post some computer specs such as Computer model, Ram, cpu, as well as some examples of what you are doing when the slowdowns occur.

---

### Post by mikewhatever on 2008-11-15
There isn't a set of commands to troubleshoot slowdowns. Providing more info on the problem might help, for example, how long is a while? Mentioning your hardware is also a good idea, so let's start with that.

cat /proc/cpuinfo
cat /proc/meminfo | grep MemTotal
cat /proc/swaps

---

### Post by Obero on 2008-11-15
> **mikewhatever said:**
> There isn't a set of commands to troubleshoot slowdowns. Providing more info on the problem might help, for example, how long is a while? Mentioning your hardware is also a good idea, so let's start with that.

cat /proc/cpuinfo
cat /proc/meminfo | grep MemTotal
cat /proc/swaps

It takes around 10 seconds during slow times. Also, you guys are asking my specs. Anyway to get that information using the terminal? I can give you guys the output.

---

### Post by jenkinbr on 2008-11-15
> **mikewhatever said:**
> There isn't a set of commands to troubleshoot slowdowns. Providing more info on the problem might help, for example, how long is a while? Mentioning your hardware is also a good idea, so let's start with that.

cat /proc/cpuinfo
cat /proc/meminfo | grep MemTotal
cat /proc/swaps

> **Obero said:**
> It takes around 10 seconds during slow times. Also, you guys are asking my specs. Anyway to get that information using the terminal? I can give you guys the output.

Run the three commands that mikewhatever posted and post the output for each here.

---

### Post by Obero on 2008-11-15
> **jenkinbr said:**
> Run the three commands that mikewhatever posted and post the output for each here.

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Pentium(R) 4 CPU 2.40GHz
stepping	: 7
cpu MHz		: 2400.078
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid
bogomips	: 4800.15
clflush size	: 64
power management:

```

```
MemTotal:       351940 kB

```

```
Filename				Type		Size	Used	Priority
/dev/sda5                               partition	1028120	245260	-1

```

Here you go guys. Hopefully it'll help solve my problem.

---

### Post by Obero on 2008-11-15
You guys still there?

---

### Post by SunnyRabbiera on 2008-11-15
Well I am here, I was reading up on your specs.
Did you try turning off desktop effects?

---

### Post by Obero on 2008-11-15
> **SunnyRabbiera said:**
> Well I am here, I was reading up on your specs.
Did you try turning off desktop effects?

I don't even think I have that on, dude. How would I go about doing this, though?

---

### Post by mikewhatever on 2008-11-15
> **Obero said:**
> It takes around 10 seconds during slow times. Also, you guys are asking my specs. Anyway to get that information using the terminal? I can give you guys the output.

What takes 10 seconds? May I assume that by slowing down you mean freezing for 10 seconds? May I also assume that it's graphics related? Would it be accurate to say that a window takes 10 seconds to open/close. Give out more details, please.

---

### Post by Obero on 2008-11-15
> **mikewhatever said:**
> What takes 10 seconds? May I assume that by slowing down you mean freezing for 10 seconds? May I also assume that it's graphics related? Would it be accurate to say that a window takes 10 seconds to open/close. Give out more details, please.

Other than the graphics (which I have no idea of), you're pretty much accurate. You know how like, when it freezes, you type a bunch of words like you would normally do, but it's frozen, then when it's done being frozen all the words pile out automatically. Am I putting a picture in your head? Kind of hard to explain, though.

---

### Post by Obero on 2008-11-15
Anyone still here?

---

### Post by lakris61 on 2008-11-15
Well, that could happen when another process is hogging resources.

Does it happen often?

It could be a scheduled job, a download/upload writing/reading files, it could be anything. If it happens frequently I suggest You have a command prompt window open all the time, running top. when the slowdown happens You will have a chance to see what's going on, if some program is using a lot of CPU. Note that it is not unusual, or a cause for alarm, for a process to utilise close to 100%, it is only a matter of the kernel (OS) thinking that there is no competition for resources. But if some program is continuously high on CPU-utilisation when Your problems occur, It can at least give You a clue. 

And I think it is more likely that it will be a slower device such as hard disk or network that cause the delays. File IO is often an issue with slowdowns.

/Lakris

---

### Post by mikewhatever on 2008-11-15
Well, it's hard to advise, especially because we can't isolate the causes of freezing. It's not quite clear if the freezing occurs during the use of a text editor of some kind or no particular application. In short, the problem needs to be further observed.
There are several things that may be relevant, and if done, will generally increase overall performance:
- If possible, add more RAM. With about 350 MB, some of it probably shared with the graphics card, the system would be swapping quite a lot.
- Disable or optimize indexing under System ->Preferences->Search and Indexing.
- Disable unnecessary services under System->Admin->Services, such as AutoCrashReport, BlueTooth, MailAgent. Careful though, don't kill useful ones.

---

### Post by epswinde on 2008-11-15
Linux, by default, will swap out many other programs when you preform a large file operation (such as unzipping a big archive, anything that's really resource intensive) linux swaps in order to get that large file operation done quickly. 

you can adjust your "swappiness", as this behaviour is called, by changing the value in 
```
/proc/sys/vm/swappiness
```

Valid entries are from 0-100, default is 60.  A higher number means that the system swaps more aggressively.  

Try fiddling with this number and see if your system starts to behave more like you want. hope this info helps

---

### Post by mikewhatever on 2008-11-15
> **epswinde said:**
> 
Try fiddling with this number and see if your system starts to behave more like you want. hope this info helps

With 350 MB of RAM, not a good idea.

---

### Post by halitech on 2008-11-15
typically you are going to want at least 384meg of ram to have a decently usable system so even though your speed is fine, try adding more ram. Otherwise, disable things like Compiz and use lighter apps (Abiword instead of Open Office write). You could also try Xubuntu instead of Ubuntu (uses a lighter DE so should be a little more responsive)

---

### Post by mikewhatever on 2008-11-16
The OP has abandoned this thread and started another one [HERE.]("http://ubuntuforums.org/showthread.php?t=984365") Take a look if you have further suggestions.

---

