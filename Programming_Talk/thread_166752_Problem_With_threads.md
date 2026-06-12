---
title: "Problem With threads ?"
date: 2006-04-27
forum: Programming Talk
---

### Post by kolichina_s_s on 2006-04-27
Hi,
 
    I am working with around 8 threads. In each thread I am running a while loop. in thread "1" I am writing to the serial port and in thread "2" I am reading from the serial port. the problem is that writing to port is getting resolved quickly but reading from the port in the second thread is done through select()   with a time out of 10 seconds. and this whole waiting is in a loop. and as long as this loop is running I am not able to switch to other threads. :confused: once this entire loop is finished then other threads get their time quantum and end them selves. Why is this so ? here is how the sample code looks for thread "2"
 
 
fcntl(fd_for_Serailport,... , FASYNC); 
int x = 0;
while(x!=10) {
 
    select(fd_for_Serailport,NULL,...,timeout); // timeout 10 secs.
    if(FD_ISSET(fd_for_Serailport)) {
                    
         ReadPort();
    }
    else {
 
        puts("timeout");
        
    }
 
    sleep(10);// even if I keep it to sleep it is not giving control other threads
    x++;
}
 
 
void ReadPort()
{
    just reads data from the Port and prints it.
}
 
 
 
Can I set the time quantum of the threads manually ? or what else i can do to avoid this problem . Please Help.
 
Thanks

---

### Post by LordHunter317 on 2006-04-27
[QUOTE=kolichina_s_s]I am working with around 8 threads. In each thread I am running a while loop. in thread "1" I am writing to the serial port and in thread "2" I am reading from the serial port. the problem is that writing to port is getting resolved quickly but reading from the port in the second thread is done through select()   with a time out of 10 seconds. and this whole waiting is in a loop. and as long as this loop is running I am not able to switch to other threads. :confused: once this entire loop is finished then other threads get their time quantum and end them selves. Why is this so ?[/quote]It means you're not actually blocking in a thread, preventing other threads from running.  You're spinning.

> here is how the sample code looks for thread "2"Not enough code, and please use code tages to format it next time.

Why are you using threads, and 8 of them, to do this anyway?  You should do all your I/O on a single thread, likely.   Especially if it's a serial port.

---

### Post by kolichina_s_s on 2006-04-27
> **LordHunter317]It means you're not actually blocking in a thread, preventing other threads from running.  You're **spinning**.[/QUOTE]

Please tell me what is spinning? and what problem it will create ?

[QUOTE=LordHunter317]
Not enough code,[/QUOTE] 
```
#include<errno.h>
#include<termios.h>
#include<termios.h>
#include <sys/types.h>
#include<sys/time.h>
#include<sys/select.h>



int initport(int fd)
{
struct termios options said:**
> ;


FD_SET(fd_port, &input);
max_fd = fd_port+1;
timeout.tv_sec = 2;
timeout.tv_usec = 0;
x = 0;
while(x != 10) {

n = select(max_fd, &input,NULL,NULL, &timeout);

if(n < 0)
perror("Select failed");
else if(n==0)
puts("Timeout");
else
{
if(FD_ISSET(fd_port, &input))
{
readport(fd_port,sCmd);
puts(sCmd);
}
}
x++; 
sleep(10);

}
puts(sCmd);

close(fd_port); 

pthread_exit(NULL);
}

int readport(int fd, char * result)
{
int iIn = read(fd, result, 254);
result[iIn -1]= 0x00;
if(iIn < 0) {
if(errno == EAGAIN) {
puts("SERIAL EAGAIN ERROR");
return 0;
}
}
else {
puts(strerror(errno));
return 0;
}
return 1;
}

```

Note i am launching these threads as detachable threads.

There is nothing much code in other threads as i am just exiting from them by putting a simple puts
[QUOTE=LordHunter317]
Why are you using threads, and 8 of them, to do this anyway?  You should do all your I/O on a single thread, likely.   Especially if it's a serial port.

I need to do this at different Intervals and if i am using timer than i guess i will not be able to accomplish all these tasks as each of them will take a long time.

---

