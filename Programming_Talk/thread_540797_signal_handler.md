---
title: "signal handler"
date: 2007-09-02
forum: Programming Talk
---

### Post by saeedeh1363 on 2007-09-02
#include <signal.h>
#include <string.h>
#include <sys/types.h>
#include <sys/wait.h>
sig_atomic_t child_exit_status;
void clean_up_child_process (int signal_number)
{
/* Clean up the child process. */
int status;
wait (&status);
/* Store its exit status in a global variable. */
child_exit_status = status;
}
int main ()
{
/* Handle SIGCHLD by calling clean_up_child_process. */
struct sigaction sigchld_action;
memset (&sigchld_action, 0, sizeof (sigchld_action));
sigchld_action.sa_handler = &clean_up_child_process;
sigaction (SIGCHLD, &sigchld_action, NULL);
/* Now do things, including forking a child process. */
/* ... */
return 0;
}
Note how the signal handler stores the child process’s exit status in a global variable,
from which the main program can access it. Because the variable is assigned in a signal
handler, its type is sig_atomic_t.



Hi I has one question.please reply me that what responsed upper Code ??? reason of execute of upper cod whats ?
thanks

---

### Post by PaulFr on 2007-09-02
Many Unix kernels send a parent process a SIGCHLD on the death of any of their children - the first function receives and cleans up. If you do not clean up, a zombie process will result. That's the simple answer, please read Rich Stevens' books or similar to understand this.

To see how complicated things can get, see the definition of catch_sigchld in **[http://www.stg.brown.edu/service/xmlvalid/dist/source/xmlparse-0.9/sigstuff.c](http://www.stg.brown.edu/service/xmlvalid/dist/source/xmlparse-0.9/sigstuff.c)**

---

