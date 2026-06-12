---
title: "Memory usage - N/A"
date: 2012-12-28
forum: Programming Talk
---

### Post by bird1500 on 2012-12-28
Hi,
The system monitor shows "N/A" in the memory section of my app (ufbio). Any ideas why?
My app is simple - it sets up a listening (unix) socket and prints out anything one sends to it. No GUI.
See screenshot.

---

### Post by rnerwein on 2012-12-28
> **bird1500 said:**
> Hi,
The system monitor shows "N/A" in the memory section of my app (ufbio). Any ideas why?
My app is simple - it sets up a listening (unix) socket and prints out anything one sends to it. No GUI.
See screenshot.
hi
i am not sure but is it possible that your box is using some swap space ?
that is why i think it means Not Accessible ?!
if your proc is using less cpu-time it will be a candidte for to be swaped out
pleas post back if your system was using swap
cheers

---

### Post by bird1500 on 2012-12-28
Thanks, I'm probably not using swap cause I got 4GB of RAM and I'm barely using 800MB.
I'm still curious why it's not showing up the memory usage, maybe cause it's using too little RAM to show it up.. Anyway here's the complete app that builds with cmake (and requires libgtkmm-3.0-dev and libappindicator3-dev).

---

### Post by NikTh on 2012-12-28
Hi ,

you can try a command and see the results 

First run 
```
ps -e
``` will list all the processes are currently running . 
Find the PID of your application and run 
```
pmap -x <pid>
```

Thanks

---

### Post by bird1500 on 2012-12-28
Thanks, I think I figured it out.
I ran "ps -e" and it sayd "4174 pts/1    00:00:00 ufbio <defunct>".
"Defunct" probably because my main() function is:
[PHP]
int main(int argc, char *argv[]) {
    
    pthread_t thread;
    pthread_create(&thread, NULL, ufbioListenThread, NULL);
    
    pthread_exit(NULL);
    return 0;
}
[/PHP]It creates a thread and exits from the main thread while keeping the application/process running the other thread(s), and the "System Monitor" probably somehow relies on the main thread being alive.

I changed the code to avoid this situation (exiting the main thread with pthread_exit(NULL)) and the issue is gone - though the code itself will be reverted back to the previous state which exited the main thread.

BTW "pmap -x pid" gives this (with pthread_exit() used to exit the main thread):

> 
bin$ ps -e | grep ufbio
 2931 pts/1    00:00:00 ufbio <defunct>
bin$ pmap -x 2931
2931:   [ufbio]
Address           Kbytes     RSS   Dirty Mode   Mapping
----------------  ------  ------  ------
total kB               0       0       0
bin$ 

That is, apparently it too relies on the main thread being alive.

---

### Post by RaumTrug on 2012-12-29
Haha, you created a Zombie, mr. Frank N. Stein!

read other's babble about it:
[http://stackoverflow.com/questions/3559463/is-it-ok-to-call-pthread-exit-from-main](http://stackoverflow.com/questions/3559463/is-it-ok-to-call-pthread-exit-from-main)

Why are you doing this, what for? I'm curious for the motivation. I'd either let the main func call the routine that's to run all the time, instead of creating a thread, or let it wait for the other's thread's termination with pthread_join, so it could actually return the zero at the end.

---

### Post by bird1500 on 2012-12-29
Well, I split this program from a bigger one and since it originally ran in a different thread and since I wanted to change as little code as possible I just wrote the code in the main thread that fires the old one and do pthread_exit for the process not to terminate.
I also read the "programming with posix threads" book by Butenhof and recall him telling this is legal, but I don't recall him saying this makes the program a zombie or so, here:

> 
When the function main returns in the initial thread, the process will be terminated immediately. If you want to terminate the initial thread while allowing other threads in the process to continue running, call pthread_exit instead  of returning from main. 


---

