---
title: "System Monitor?"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by linux_newf on 2008-04-29
The resources screen/tab -

How can i take a screen shot of that? I like to show it to some of you folks to explain it to me. :guitar:

---

### Post by Monicker on 2008-04-29
> **linux_newf said:**
> The resources screen/tab -

How can i take a screen shot of that? I like to show it to some of you folks to explain it to me. :guitar:


Using the Print Screen key will take a screen shot of your desktop.

---

### Post by PmDematagoda on 2008-04-29
> **linux_newf said:**
> The resources screen/tab -

How can i take a screen shot of that? I like to show it to some of you folks to explain it to me. :guitar:

Pressing the Print Screen button?

---

### Post by linux_newf on 2008-04-29
Lookin at my laytop i tried the key labeled "Insert" with "prt sc" in a small box under the former quote.

Where do i paste it?

---

### Post by PmDematagoda on 2008-04-29
> **linux_newf said:**
> Lookin at my laytop i tried the key labeled "Insert" with "prt sc" in a small box under the former quote.

Where do i paste it?

The screenshot? Put it as an attachment of a post.

---

### Post by linux_newf on 2008-04-29
I got it fellows, so what is this trying to tell me?

Don't believe this will work...

[http://mail.google.com/mail/?ui=2&ik=7e4951d5e3&realattid=f_ffm3hyn20&attid=0.1&disp=inline&view=att&th=11998dc1bdd968f8]("http://mail.google.com/mail/?ui=2&ik=7e4951d5e3&realattid=f_ffm3hyn20&attid=0.1&disp=inline&view=att&th=11998dc1bdd968f8")

F%%K i have a buzz fellows i just uploaded it to ubuntu.

---

### Post by niteshifter on 2008-04-29
Hi,
> 
Don't believe this will work...

[http://mail.google.com/mail/?ui=2&ik...998dc1bdd968f8](http://mail.google.com/mail/?ui=2&ik...998dc1bdd968f8)

It didn't :)

Let's try this:

With System Monitor up and having the focus, press Alt+PrntScrn.

A dialog should appear titled "Save Screenshot" and it defaults to saving the image (as a .png) file on the Desktop. Then attach that file to your post.

---

### Post by PmDematagoda on 2008-04-29
> **linux_newf said:**
> I got it fellows, so what is this trying to tell me?

Don't believe this will work...

[http://mail.google.com/mail/?ui=2&ik=7e4951d5e3&realattid=f_ffm3hyn20&attid=0.1&disp=inline&view=att&th=11998dc1bdd968f8]("http://mail.google.com/mail/?ui=2&ik=7e4951d5e3&realattid=f_ffm3hyn20&attid=0.1&disp=inline&view=att&th=11998dc1bdd968f8")

F%%K i have a buzz fellows i just uploaded it to ubuntu.

Post the output of:-
```
top
```

---

### Post by c4v3m4n on 2008-04-29
> **niteshifter said:**
> Hi,


It didn't :)

Let's try this:

With System Monitor up and having the focus, press Alt+PrntScrn.

A dialog should appear titled "Save Screenshot" and it defaults to saving the image (as a .png) file on the Desktop. Then attach that file to your post.

Or possibly Fn+PrntScrn, depending on keyboard layout

---

### Post by linux_newf on 2008-04-29
> **PmDematagoda said:**
> Post the output of:-
```
top
```

I have only used yum. What's the full command line(s), if you don't mind.

---

### Post by PmDematagoda on 2008-04-29
> **linux_newf said:**
> I have only used yum. What's the full command line(s), if you don't mind.

Top isn't a package management system, it's a command to list the processes in order of CPU usage.

---

### Post by linux_newf on 2008-04-29
> **PmDematagoda said:**
> Top isn't a package management system, it's a command to list the processes in order of CPU usage.

Really? Come on!

Jokes dude, i figured you had to put something before too, like sudo.

Anyhow, this is what i got after i tried this. :guitar:

```
top - 04:32:43 up 3 days,  4:17,  2 users,  load average: 0.08, 0.21, 0.26
Mem:    969360k total,   892152k used,    77208k free,    28984k buffers
Swap:  2835432k total,    38008k used,  2797424k free,   429928k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
31583 root      20   0 67068  34m 8344 S    7  3.7  13:36.47 Xorg               
  414 brad      20   0 74308  20m  11m S    4  2.2   0:01.64 gnome-terminal     
  300 brad      20   0  220m  91m  24m S    1  9.7   2:32.57 firefox            
31809 brad      20   0 56200  30m 9292 S    1  3.2   1:11.55 compiz.real        
  434 brad      20   0  2440 1168  856 R    1  0.1   0:00.34 top                
 4782 root      15  -5     0    0    0 S    1  0.0   0:04.30 kondemand/0        
31945 brad      20   0 21248  11m 7196 S    1  1.2   0:07.30 gtk-window-deco    
    1 root      20   0  2844 1692  544 S    0  0.2   0:01.50 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.08 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.08 watchdog/0         
    9 root      15  -5     0    0    0 S    0  0.0   0:01.28 events/0           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   47 root      15  -5     0    0    0 S    0  0.0   0:00.08 kblockd/0          
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid             
   52 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify       
  160 root      15  -5     0    0    0 S    0  0.0   0:00.06 kseriod            
  202 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush            


```

What can i take from these numbers?

---

### Post by PmDematagoda on 2008-04-29
It seems that the list is fine, just check the Resources tab of System Monitor again to see if the CPU usage has returned to normal.

---

### Post by c4v3m4n on 2008-04-29
> **linux_newf said:**
> I have only used yum. What's the full command line(s), if you don't mind.

Ick, i hate yum :lolflag:

---

