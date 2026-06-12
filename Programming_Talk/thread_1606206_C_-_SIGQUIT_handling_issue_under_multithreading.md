---
title: "C - SIGQUIT handling issue under multithreading"
date: 2010-10-26
forum: Programming Talk
---

### Post by puppi on 2010-10-26
I'm having issues when trying to handle the SIGQUIT signal (triggered by default with CTRL-\) under a multithreaded program. Be it trying to handle it with SIG_IGN or a custom handling function, it simply doesn't work, the signal isn't handled and the program aborts. I've tried sigaction() along with pthread_sigmask() to block it in every thread, I've tried it with sigprocmask(), I've tried sigwait(), all of the above simultaneously, but it simply doesn't work. For other signals such as SIGINT or SIGTSTP everything goes according to plan, but SIGQUIT is a real issue.
What I really want to do is to make it impossible for SIGQUIT to be sent by a typed character (or, if sent, handled). The only approach that "sort of works" is using termios.h to configure the terminal to a non-canonical setting, and then disabling the ISIG flag. But I need signaling from input in this program, so that's a bad approach for me. I can also change the VQUIT control character, thus changing which character triggers SIGQUIT, but I don't know any character that simply cannot be received as input. Even \0 can be sent by pressing CTRL-SHIFT-2 (^@), and I receive EOFs from input due to some settings I've defined with termios.h.
Under a single-threaded program I have no issues. My threading implementation is NPTL 2.12.1. Since NPTL does not use a manager thread, the hypothesis that SIGQUIT is being caught by such thread can't be right. I'm using 64-bit libraries.

Any help would be greatly appreciated.

ps: I'm considering setting VQUIT to 128 or greater, but I'm not positive if such character definitely can't be received under any circunstances (EOF being a notable exception).

---

### Post by dwhitney67 on 2010-10-26
Could you please post some code showing what you have attempted?

I'm not very familiar with NPTL, other than what I have read today.  Most of my knowledge of pthreads lies with the "old-fashioned" way of doing things.

Here's some C++ code I through together.  The underlying code to handle the SIGQUIT works as expected.  All other signals are ignored, with the exception of course of SIGKILL.
```

#include <csignal>
#include <unistd.h>
#include <pthread.h>
#include <string>
#include <iostream>

class MyThread
{
public:
   MyThread() { pthread_create(&tid, NULL, thread, this); }

   pthread_t getTID() const { return tid; }

private:
   static void* thread(void* arg)
   {
      sigset_t mask;
      sigemptyset(&mask);
      sigaddset(&mask, SIGQUIT);
      pthread_sigmask(SIG_UNBLOCK, &mask, NULL);

      // setup handler
      struct sigaction sigact;
      sigemptyset(&sigact.sa_mask);

      sigact.sa_flags     = SA_SIGINFO;
      sigact.sa_sigaction = MyThread::sigHandler;

      sigaction(SIGQUIT, &sigact, 0);

      while (!quit)
      {
         std::cout << "Thread is running..." << std::endl;
         sleep(1);
      }
      std::cout << "Thread is quiting normally." << std::endl;

      return 0;
   }

   static void sigHandler(int sig, siginfo_t* info, void* context)
   {
      quit = (sig == SIGQUIT);
   }

   pthread_t   tid;
   static bool quit;
};

bool MyThread::quit = false;

int main(int argc, char** argv)
{
   sigset_t sigmask;
   sigfillset(&sigmask);
   pthread_sigmask(SIG_BLOCK, &sigmask, NULL);

   MyThread mt;

   int* status = 0;
   pthread_join(mt.getTID(), (void**) &status);

   std::cout << "Main thread is done." << std::endl;
}

```

---

### Post by puppi on 2010-10-26
Solved it.
My program actually uses a launcher, which forked itself via a system() call to open my program and then ended. It ended because the system() operand was "gnome-terminal ... -e \"sh -c ./MYPROGRAM\"", where the '...' stands for a few custom aesthetical options I inserted, so the shell invocation actually opened a terminal, which then opened my program. Since the launcher exited after the terminal was opened, I didn't give it much credit as a possible cause of my problem. Nevertheless, I decided to fiddle a little with it, and realized that upon switching "gnome-terminal ... -e \"sh -c ./MYPROGRAM\"" to "gnome-terminal ... -x ./MYPROGRAM" the signal handling issue with SIGQUIT disappeared in MYPROGRAM's execution.
I still don't understand why running it via sh -c causes the signal handling deviation. And neither why SIGQUIT is the only signal I've noticed to be affected. If I run it without the launcher through a straight sh -c ./MYPROGRAM command, the SIGQUIT handling issue also exists, as it was to be expected. My only guess is that SIGQUIT is being delivered to the shell, and not my program, but I'm not sure. I'll keep this thread open to see if anyone can enlighten my on such.

ps: The problem wasn't with multithreading afterall. I get the same thing when running a single-threaded program via sh -c.

---

