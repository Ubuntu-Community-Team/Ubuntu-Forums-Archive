---
title: "Real-Time Computation"
date: 2010-01-22
forum: Programming Talk
---

### Post by Haptics on 2010-01-22
[COLOR=black][FONT=Verdana]Hello,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I have a pretty strange problem, maybe someone has had a similar experience. In a simple C program I am periodically completing a task by measuring the current time, doing the task, and then using the clock_nanosleep() function from timer.h to suspend until the particular period has elapsed (1 ms desired). I'm specifying the use of CLOCK_REALTIME. Additionally, I have the pthread scheduled as FIFO with a priority > 50.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Although my intended delay is 1 000 000 ns (1 ms), the actual measured delay is always 4 000 0XX ns with an occasional 8 000 0XX ns flicker. This result is independent of what I specify as the desire delay period ( 2, 1, or 0.5 ms). I have also confirmed the 4 ms delay with a parallel port pin output and scope. My assumption is that the clock's update resolution is 4ms, somehow. I have seen numerous times, however, this same tactic being used to achieve periodic timing well under 1 ms.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Any ideas on what could be causing such large granularity?[/FONT][/COLOR]

---

### Post by MindSz on 2010-01-22
I don't know why this is happening to you, but when I want to achieve something similar, I use the alarm() funciton. Here's a small program so you can take a look at it.

```
#include <stdio.h>
#include <sys/time.h>
#include <signal.h>
#include <stdlib.h>
#include <unistd.h>
#include <time.h>

volatile sig_atomic_t keep_going = 1;
clock_t clk_end;
time_t sec_start, sec_end, sec_tmp1, sec_tmp2;

int a = 0;
int i = 0;

void catch_alarm(int);

int main()
{
  sec_start = time(NULL);
  sec_tmp1 = time(NULL);

  //printf("B\n");

  signal(SIGALRM, catch_alarm);
  ualarm(500000, 500000);

  while(1){
    sleep(5);
  }
  
  clk_end = clock();
  sec_end = time(NULL);

  printf("\n");
  printf("\nCLKS = %ld\n", clk_end);
  printf("\nSECS = %ld\n", sec_end-sec_start);
  return EXIT_SUCCESS;
}

void catch_alarm(int sig)
{
  keep_going = 0;
  sec_tmp2 = time(NULL);
  if(sec_tmp2 - sec_tmp1 >= 60) {
    sec_tmp1 = time(NULL);
    printf("\t%d\n", i);
    i = 0;
  }
  else {
    i++;
    printf("A");
  }
}

```

---

### Post by Haptics on 2010-01-23
[COLOR=black][FONT=Verdana]Thank you, I will investigate this option.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]After some more research, I found that the default HZ value for newer kernel versions is 250HZ (as opposed to the traditional 1000Hz). This parameter can be found in param.h and is responsible for how frequently the software system clocks are actually updated from hardware layer. My observed minimum resolution of 4 ms corresponds with the 250Hz update rate. I think this is more than coincidence![/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Now for my next question, I read that the value can be changed. Essentially, change the default value in the file and recompile the kernel module. I am fairly new to Linux, could someone explain to me how to go about this (change and recompile)? If I can change the value, I can confirm if this indeed the issue, and hopefully contribute to anyone else having this issue. I apologies for my newness on the subject, but explicit guidance would be greatly, greatly appreciated![/FONT][/COLOR]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]

---

### Post by tgalati4 on 2010-01-23
I believe it was changed to allow processors to "sleep" more with less interrupts from the hardware layer.  You can change it to whatever you want.  I'm not sure where the switch is.  It's not in /etc/sysctl.conf.  It might be in the kernel configuration tool that you use to compile a new kernel.

I think I found it:

grep HZ /boot/config*

# CONFIG_HZ_1000 is not set
# CONFIG_HZ_300 is not set
CONFIG_HZ=100
CONFIG_HZ_100=y
# CONFIG_HZ_250 is not set
CONFIG_MACHZ_WDT=m
CONFIG_NO_HZ=y

This is for Hardy server edition.  Do some research on the other switches.  Make changes to the kernel configuration file and recompile.

[http://www.kroah.com/lkn/](http://www.kroah.com/lkn/)

---

