---
title: "Minecraft server can't keep up"
date: 2015-10-24
forum: New to Ubuntu
---

### Post by enes6 on 2015-10-24
hi

I have a minecraft server that is running on a ubuntu server
i get some times a error/warning : Can't keep up! Did the system time change, or is the server overloaded? Running 2852ms behind, skipping 57 tick(s)
Specs
2XCPU Intel Xeon processor1 E52403 3.00 GHz 6 MB L2 cache 1333 MHz FSB
Ram: 16gb ddr2
HHD: 130Gb KIngston

hope some one can help me.

---

### Post by mike376 on 2015-10-24
Could you post a list of all the running processes on you computer while the server is running. Also is this a modded server?

I'm looking at the score [here]("https://www.cpubenchmark.net/cpu.php?cpu=Intel+Xeon+E5-2403+%40+1.80GHz"), and it seems that those processors are on the low end of the Xeon name (admittedly though, they're rating it at half the speed you are). I was having a similar issue with some [AMD Opteron 4284]("https://www.cpubenchmark.net/cpu.php?cpu=AMD+Opteron+4284&id=1862&cpuCount=2")s but I upgraded to a single core [Xeon E5-2673]("https://www.cpubenchmark.net/cpu.php?cpu=Intel+Xeon+E5-2670+v3+%40+2.30GHz") (what an Azure VPS uses) and it was running fine

As long as it's not affecting you're gameplay though I wouldn't worry too much about it. If you don't want it clogging up your logs you can set a log4j regex filter

---

### Post by chemist931 on 2015-10-25
When is this happening? If it happens constantly on startup I would say that your hardware just isn't good enough, but its obviously fine.  How many people are playing in the server? I have a similarly-capable PC running a server, and sometimes, only sometimes, it puts out one of the same error messages.

---

### Post by enes6 on 2015-10-25
10 players
its a verry good server he can do anything what you want
2 cpu

---

### Post by enes6 on 2015-10-25
its a vanilla minecraft server with 10 - 20 players
my friends can play it only

---

### Post by chemist931 on 2015-10-25
The first answer is probably right, with that hardware and server load you probably have too many other processes going, and a two-socket server is pretty impressive. This seems unlikely, I've got an Intel i7- 4690K with 12GB 1600 RAM and a fairly capable HDD with *Windows* and it only it only gives that once in a while.

---

### Post by sandyd on 2015-10-25
Minecraft is single threaded, and can only use a single processor thread at a time.

That seems to be the problem for most times there is lag - there may be a few cores, but not enough power per core.

That being said, the E5 series is generally used more for setups that require less power per core, such as virtualization (There are E5 processors with 16 cores, 32 threads), while E3 series is generally used for more power per core.

Take a look: 
[Intel Xeon E5-2403 @ 1.80GHz]("http://www.cpubenchmark.net/cpu.php?cpu=Intel+Xeon+E5-2403+%40+1.80GHz")
Single Thread Performance: 909

[Intel Xeon E3-1230]("http://www.cpubenchmark.net/cpu.php?cpu=Intel+Xeon+E3-1230+%40+3.20GHz&id=1199")
Single Thread Performance: 1823

I'm a bit curious though. The E52403 (which is a Intel Xeon E5-2403 rebadged by Dell) does not run at 3.0 Ghz and does not have turbo-boost.

Can you post the output of
```

sudo lshw -class processor
cat /proc/cpuinfo
```

---

### Post by enes6 on 2015-10-27
sudo lsw -class processor = [https://gyazo.com/06926752dd27b39928abd134ba105179](https://gyazo.com/06926752dd27b39928abd134ba105179)
cat /proc /cpuinfo = [https://gyazo.com/c0a18b59c83fd26c88823fe2a6bc6ffb](https://gyazo.com/c0a18b59c83fd26c88823fe2a6bc6ffb)
and i use java -Xmx10240M -Xms10240M -jar minecraft.jar to start the server.

---

### Post by sandyd on 2015-10-27
Its a Xeon E5430, not Xeon E52403 - different things

[Intel Xeon E5430 @ 2.66GHz]("http://www.cpubenchmark.net/cpu.php?cpu=Intel+Xeon+E5430+%40+2.66GHz")
Single Thread Performance: 1146

Probably still too low if your still having issues.

---

### Post by enes6 on 2015-10-27
i have dubble I[ntel Xeon E5430 @ 2.66GHz]("http://www.cpubenchmark.net/cpu.php?cpu=Intel+Xeon+E5430+%40+2.66GHz")

---

### Post by sandyd on 2015-10-27
As said above, it is single thread performance that matters, not the cumulative power of the CPU.
Minecraft can only use a single processor thread.

---

