---
title: "Urgent: POSIX: Programming issue"
date: 2010-09-25
forum: Programming Talk
---

### Post by Amit_Oza on 2010-09-25
Hi all,
 
I am beginner level posix programmer :) . I want to make a thread, say thread1, suspend/resume from another thread say thread2 on Ubuntu 10.4. How do I achieve this in POSIX. I have read about pthread_suspend, pthread_resume, pthread_continue but I didnt find these APIs in "pthread.h" file.
 
Requesting forum members to help on this ASAP. pls :???:.
 
Regards,
Amit Oza

---

### Post by john newbuntu on 2010-09-25
One way to do this would be to make the first thread wait on a condition in a loop and then make the second thread give it the go signal whenever it is ready to relinquish control.  I think it is something like pthread_cond_wait and pthread_cond_signal.

---

### Post by slavik on 2010-09-25
what's the rush? is this a homework assignment? have you tried searching google?

---

