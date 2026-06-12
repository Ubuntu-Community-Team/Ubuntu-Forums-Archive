---
title: "making a daemon process out of program"
date: 2005-03-01
forum: Programming Talk
---

### Post by isaac on 2005-03-01
HI,

I having problem making a initial startup program at in ubuntu. I have refer to the documentation on wiki's UbuntuBootHowto in making a custom program runs in background during startup but... my system crash. 

Then i have rever a website [http://www.yolinux.com/TUTORIALS/LinuxTutorialInitProcess.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialInitProcess.html) which teachs me on making a init mode ... but the script seems to be too general to me? and ubuntu seems do not have either "chkconfig" command and "service" commond

the script below are my reference from that sites 

#!/bin/sh
#
# Startup script for program
#
# chkconfig: 345 85 15          - This statement tells the chkconfig command how to add or delete this process to the boot process
# description: Description of program
# processname: process-name
# pidfile: /var/run/process-name.pid

# Source function library.      This creates the operating environment for the process to be started
. /etc/rc.d/init.d/functions

case "$1" in
  start)
        echo -n "Starting  process-name: "
        daemon  process-name                 - Starts only one process of a given name.
        echo
        touch /var/lock/subsys/process-name
        ;;
  stop)
        echo -n "Shutting down process-name: "
        killproc process-name
        echo
        rm -f /var/lock/subsys/process-name
        rm -f /var/run/process-name.pid      - Only if process generates this file
        ;;
  status)
        status process-name
        ;;
  restart)
        $0 stop
        $0 start
        ;;
  reload)
        echo -n "Reloading process-name: "
        killproc process-name -HUP
        echo
        ;;
  *)
        echo "Usage: $0 {start|stop|restart|reload|status}"
        exit 1
esac

exit 0

the problem is that i can't figure out how is this script link to my current program i build in "/var/www" directory? :confused:  :confused:

---

### Post by rsay on 2005-03-01
I used a guide found here:

[Tricks of the trade 3](http://www.joshgentry.com/egoburp/archives/2004/12/tricks-of-the-trade-3/) 

This seemed to work pretty well for me. I used it to make  a renderfarm daemon for cinelerra based on /etc/init.d/skeleton.

* Remember you can test what you wrote from the command line before rebooting so that you have less chance of your system crashing.

---

### Post by isaac on 2005-03-02
i get what you mean say.. and the files works wonderful... i just have some problem..

my program suppost to save some jpeg files ... but it can't be done.. there's nothing wrong with the program i have tried it on terminal

it just that initializing the script with this program in it won't have the authorization to save the files..

Which chmod ??? should i use? or is it the run time is wrong? i put it to be 80 in 
#sudo update-rc.d myscript start 80 S. 

51 for me is still the same problem.

does anyone know the problem?

thanks in advance =)

---

### Post by isaac on 2005-03-02
i have try to run
sudo update-rc.d myscript start 80 2 3 4 5 . stop 20 0 1 6 .

but the problem still the same ... my program run as normal but when i reaches the saving files part it always mention the same thing

below is the running program

put_picture() Unable to create file save motion directory/n: Permission denied
put_picture() Unable to create file save directory/n: No such file or directory
can't write picture!: No such file or directory
can't write picture!: Permission denied

---

### Post by isaac on 2005-03-02
trouble after it install that script my ubuntu boot up in level to is stuck...

it keeps now running my program which is a looping program.. i intend to run it at the backgroung using child process but it is what i ended up with... can someone help me?

how can i remove this init script without reinstalling the whole system?

do i really need to us the fork() command to make it a child process in my program so that i won't run into these trouble again??!!??

---

### Post by isaac on 2005-03-02
i have remove the script by update-rc.d -f myscript remove in level 3 ... i some how manage to get there during the 2nd boot which ubuntu asked about debuging option.. phew .. that was close man...

but i still have problem running my program in background... are there any option for me? to do it? it's fork() is really the issue here? if i put the child process in my program... will my system crush again during boot up?

---

### Post by isaac on 2005-03-02
i have try to make a daemon source code .. but it seems to be not working at all..

it seems like fork wasn't running?

below are the code:

#include <sys/types.h>
#include <sys/stat.h>
#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <errno.h>
#include <unistd.h>
#include <syslog.h>
#include <string.h>

int main(void) {
        
        /* Our process ID and Session ID */
        pid_t pid, sid;
        printf("progam 1st stage b4 fork()\n");
        /* Fork off the parent process */
        pid = fork();
        if (pid < 0) {
		printf("fail create child\n");
                exit(EXIT_FAILURE);
        }
        /* If we got a good PID, then
           we can exit the parent process. */
        if (pid > 0) {
                exit(EXIT_SUCCESS);
		prinf("able to creat child\n");
        }

        /* Change the file mode mask */
        umask(0);
                
        /* Open any logs here */        
                
        /* Create a new SID for the child process */
        sid = setsid();
        if (sid < 0) {
		printf("able to create SID\n");
                /* Log the failure */
                exit(EXIT_FAILURE);
        }
        

        
        /* Change the current working directory */
        if ((chdir("/var/www/ispy")) < 0) {
                /* Log the failure */
                exit(EXIT_FAILURE);
        }
        
        /* Close out the standard file descriptors */
        close(STDIN_FILENO);
        close(STDOUT_FILENO);
        close(STDERR_FILENO);
        
        /* Daemon-specific initialization goes here */
        printf("run process");
        system("/var/www/ispy/ispy");

   exit(EXIT_SUCCESS);
}


i have try to intial it in the terminal but it only print the line before i used fork()
how really is fork() function here? or is it the ubuntu did not support fork? but why wasn't any error during compilling this code(c source code)?

---

### Post by NULL on 2005-03-05
That piece of code should be IN ispy... so then there will be no need to call ispy (the 'system(/var/www/ispy' bit)

And it will always only print the first line because your closing the standard input/output (wich is what it supposed to do since it's daemon).  for example, add a infinite loop to it:

#include <sys/types.h>
#include <sys/stat.h>
#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <errno.h>
#include <unistd.h>
#include <syslog.h>
#include <string.h>

int main(void) {

/* Our process ID and Session ID */
pid_t pid, sid;
printf("progam 1st stage b4 fork()\n");
/* Fork off the parent process */
pid = fork();
if (pid < 0) {
printf("fail create child\n");
exit(EXIT_FAILURE);
}
/* If we got a good PID, then
we can exit the parent process. */
if (pid > 0) {
exit(EXIT_SUCCESS);
prinf("able to creat child\n");
}

/* Change the file mode mask */
umask(0);

/* Open any logs here */

/* Create a new SID for the child process */
sid = setsid();
if (sid < 0) {
printf("able to create SID\n");
/* Log the failure */
exit(EXIT_FAILURE);
}



/* Change the current working directory */
if ((chdir("/var/www/ispy")) < 0) {
/* Log the failure */
exit(EXIT_FAILURE);
}

/* Close out the standard file descriptors */
close(STDIN_FILENO);
close(STDOUT_FILENO);
close(STDERR_FILENO);

/* Daemon-specific initialization goes here */
printf("run process");
//system("/var/www/ispy/ispy");

//infinite loop here
while(1){}

exit(EXIT_SUCCESS);
}

run it and you'll get your prompt back, now do 'ps -e | grep foobar' (change foobar to whatever your executable is called, a.out if you didn't specify the -o at compile) and you'll see that it's running

---

### Post by jaishreepadma on 2008-06-07
Hi isaac

       I have same problem.What is the solution for it?

---

### Post by jaishreepadma on 2008-06-07
Hi isaac

       I have same problem.What is the solution for it?
ACtually i am using ACE Library.
I am connecting to the server using ACE::connect
When i did daemon it is not connecting to the server
To do daemon i referred [http://www.yolinux.com/TUTORIALS/Lin...itProcess.html](http://www.yolinux.com/TUTORIALS/Lin...itProcess.html)

Now it is not connecting to the server

Thank in advance

---

