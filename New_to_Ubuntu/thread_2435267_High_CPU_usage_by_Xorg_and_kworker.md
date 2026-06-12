---
title: "High CPU usage by Xorg and kworker"
date: 2020-01-18
forum: New to Ubuntu
---

### Post by chybre on 2020-01-18
Hello I am currently having an issue with my computer (teclast-F5 with gemini lake cpu 8GB of ram) and I hope you can help me. 

The issue : 
The computer is new and on windows the task "system" and "system interrupt" were using a lot of CPU (about 80%). Since I wanted to change to linux I didn't try fix the problem and i have change for linux mint (xfce version). Which were very laggy but the task manager weren't showing anything strange even if I think that the cpu were also over use. So I have change to ubuntu and the same problem occur. Very laggy no problem on the process section of task manager but in the ressource section CPU1 is use at 50% and CPU2 at 100% (3 4 seems to have normal use). I have run a Top command in the terminal and it appear Xorg is using 100% CPU and kworker 50%. 


What have I try : 
The only thing that I have try is putting the bios setting of my computer to default which doesn't have change anything (there is a lot of different option in there but I am to afraid to touch anything). 
I have tried compatibility mod but haven't change anything

From what i have seen on different thread this problem can have many different cause and is often related to graphical driver. 

I fear that the problem is no more "hardware" than "software" and that I will have to dealt with warranty refund :(   

Thanks for your attention and I hope you will have a clue. 

My config from inxi command :
CPU~Quad core Intel Celeron N4100 (-MCP-) speed/max~1989/2400 MHz Kernel~5.3.0-26-generic x86_64 Up~1:22 Mem~1702.1/7792.6MB HDD~256.1GB(2.9% used) Procs~247 Client~Shell inxi~2.3.56

---

