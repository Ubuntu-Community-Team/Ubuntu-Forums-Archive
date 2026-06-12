---
title: "C code: killall"
date: 2010-02-02
forum: Programming Talk
---

### Post by erotavlas on 2010-02-02
Hi,

Can you indicate which code is necessary to obtain the equivalent of the following system call

```
system(killall -e process name)
```

thank

---

### Post by Some Penguin on 2010-02-02
[http://psmisc.sourceforge.net/](http://psmisc.sourceforge.net/)

---

### Post by erotavlas on 2010-02-02
> **Some Penguin said:**
> [http://psmisc.sourceforge.net/](http://psmisc.sourceforge.net/)

Ok, but how can i use it?

---

### Post by dwhitney67 on 2010-02-02
see if this will work for you:
```

#include <sys/types.h>
#include <signal.h>
#include <string.h>
#include <stdlib.h>
#include <stdio.h>

int main(int argc, char** argv)
{
   if (argc < 2)
   {
      fprintf(stderr, "Usage: %s <process name>\n", argv[0]);
      return -1;
   }

   char cmd[256];
   snprintf(cmd, sizeof(cmd),
            "ps -fu %s | grep %s | egrep -v grep | egrep -v %s | awk '{ print $2 }'",
            getenv("USER"), argv[1], argv[0]);

   FILE* cmdresults = popen(cmd, "r");
   char  pidstr[6]  = {0};

   while (fgets(pidstr, sizeof(pidstr), cmdresults))
   {
      //kill(atoi(pidstr), SIGTERM);

      printf("pid = %s", pidstr);
   }

   return 0;
}

```

---

### Post by erotavlas on 2010-02-02
Thank you very much. :D I have modified the code as


```
#include <sys/types.h>
#include <signal.h>
#include <string.h>
#include <stdlib.h>
#include <stdio.h>

int main()
{

   char * processName ="vlc";
   char cmd[256];
   snprintf(cmd, sizeof(cmd), "ps -fu %s | grep %s | egrep -v grep | awk '{ print $2 }'",getenv("USER"), processName);

   printf("command %s\n",cmd);
   FILE* cmdresults = popen(cmd, "r");
   char pidstr[6]  = {0};

   while (fgets(pidstr, sizeof(pidstr), cmdresults))
   {
      kill(atoi(pidstr), SIGTERM);

      printf("pid = %s", pidstr);
   }
    pclose(cmdresults);    
   return 0;

}
```Is argv[0] necessary?
The code (my version) works as stand-alone program but fails in my "complete" program.
Why?

---

### Post by dwhitney67 on 2010-02-02
Your version is specific for killing 'vlc' processes only, so no, the argv[0] is not necessary.

If you want to develop the app to be generic, thus allowing you to kill whatever process your heart desires (and you own), then it would be best to accept the process name from the command line.  In such case, you would not want to kill the tool your are running, and hence the reason argv[0] is needed for egrep portion of the cmd string.

Play around with the app (tool) till you get what you want; I recommend that you comment out the kill() function until you are ready for "prime time" results.

---

### Post by erotavlas on 2010-02-02
I have found the problem...the process vlc-wrapper is launched by root user and the process vlc as generic user. So the code doesn't work because the getenv("USER") has the value root.

How can I solve it?

PS
If I don't wrong argv[0] is the name of the process of the complete program...

---

### Post by dwhitney67 on 2010-02-02
I cannot comment on your specific needs because I haven't a clue what you are trying to accomplish.

If you, as a regular system user, launch 'vlc', then presumably you should be able to terminate that process using the new app you are working on.

As for the argv[0], is does contain the application name.  My original program was designed to accept the process name that I wanted to kill via the command line.  Something like:
```

mykillall vlc

```
Now, in such case, I do not want to kill the process 'mykillall'.  Thus the need to use argv[0] in the call to egrep.  For example:
```

ps -fu $USER | grep bash | egrep -v ps

```
This will list all of the processes, being run by the $USER, that have the word "bash".  Obviously, I do not want the "ps" command to be listed there, thus it is removed from the results.  Similarly, if I were using 'mykillall', I would need to do the same.  In the earlier example, 'mykillall' is stored in argv[0], and by now hopefully the light-bulb is illuminated over your head such that you understand the rationale for its use.

---

