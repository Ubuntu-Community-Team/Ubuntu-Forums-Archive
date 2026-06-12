---
title: "Core2Duo one core always at 95%"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by terry123b99 on 2008-08-09
Is it normal that on my T7300 2.0Ghz Core2Duo, one of the cores is always at 95% +. This swaps between the cores on occasions.

For instance core 1 is 14% and core 2 is 95% then 10 minutes later its the other way around.

BTW this is when the system is idle.

Any suggestions?

---

### Post by meindian523 on 2008-08-09
Using desktop effects?

---

### Post by terry123b99 on 2008-08-09
> **meindian523 said:**
> Using desktop effects?

Yes using Screenlets, would that cause this to happen?

---

### Post by bpowell2005 on 2008-08-09
> **terry123b99 said:**
> Is it normal that on my T7300 2.0Ghz Core2Duo, one of the cores is always at 95% +. This swaps between the cores on occasions.

For instance core 1 is 14% and core 2 is 95% then 10 minutes later its the other way around.

BTW this is when the system is idle.

Any suggestions?

You could go to System, Administration, System Monitor and click on the "Processes" Tab, then click on %CPU (twice) to sort processes by how much CPU they're using..then see which one is eating up the processor. I am running no a dual-core, and this is not the behavior I've had...both are generally equal unless I'm running something big (like video compression or something) then I sometimes see a big load being shared back and fourth.

You could also go to the Console and type "top" and see the same list of processes, but the GUI way is prettier. (IMHO)

---

### Post by terry123b99 on 2008-08-09
> 
 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND  
27123 terry     20   0  231m  33m  15m S   96  1.7 258:11.75 java_vm     


So thats what eating my CPU, is that normal?

---

### Post by mcduck on 2008-08-09
Depends on what programs you are using. But it's definitely something that uses Java..

Try closing down all the programs, one by one, until you see the CPU usage to drop. Ubuntu itself doesn't use Java for anything so it must be some additional program you have open.

---

### Post by st33med on 2008-08-09
You could also check top:
```
top
```

---

### Post by terry123b99 on 2008-08-09
Have tried top and get the following:

> 

PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
27123 terry 20 0 231m 33m 15m S 96 1.7 258:11.75 java_vm


How can I find out what is using Java, I have no open applications.

Is there a way to stop this process in Terminal?

---

### Post by st33med on 2008-08-09
I think you are running a Virtualbox virtual machine. Try killing that.

---

### Post by mcduck on 2008-08-09
> **terry123b99 said:**
> Have tried top and get the following:



How can I find out what is using Java, I have no open applications.

Is there a way to stop this process in Terminal?

If you have nothing else open, it's probably one of the screenlets you are using.

Anyway, when in the System Monitor, go to View menu and enable the "Dependencies"-checkbox. This should help you to find out what application is using the Java virtual machine.

---

### Post by jpeddicord on 2008-08-09
> **st33med said:**
> I think you are running a Virtualbox virtual machine. Try killing that.

VirtualBox isn't written in Java. java_vm is the Java Virtual Machine, and is really just a layer for running Java applications. A little bit like Mono.

---

### Post by bpowell2005 on 2008-08-09
> **terry123b99 said:**
> So thats what eating my CPU, is that normal?

No, I don't think that's normal. One of the other posters pointed out it's probably one of your screenlets that's using Java...If it's a very cool screenlet, then it's all good...but I'd probably find the offending screenlet and get rid of it...I try to keep my laptop quiet, and running the CPU up like that makes the fans spin up something fierce.

---

### Post by st33med on 2008-08-09
> **jacobmp92 said:**
> VirtualBox isn't written in Java. java_vm is the Java Virtual Machine, and is really just a layer for running Java applications. A little bit like Mono.

Ah, yes, you are quite right. I get it mixed up because Sun made both of those...

---

### Post by bpowell2005 on 2008-08-09
> **terry123b99 said:**
> Have tried top and get the following:



How can I find out what is using Java, I have no open applications.

Is there a way to stop this process in Terminal?

To kill a process in Terminal...since you're already running "top" to see the offending process...while in top, just hit the letter "k" and you'll be prompted which PID to kill...in your example, it would be 27123...when asked for a kill signal, use "9" that always works for me.

---

