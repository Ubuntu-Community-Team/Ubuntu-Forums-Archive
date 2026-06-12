---
title: "Clever use of fork and exec?"
date: 2013-10-21
forum: Programming Talk
---

### Post by akshay-sulakhe on 2013-10-21
Hello friends,
                    Before starting off, apologies for the misguided title, but i really dont know what to write in title for this programming doubt. 


compute_credit(param1, param2 , param3){
// How to replace this computation logic with a executable C file, to which i will pass these 3 parameters. Ideally, fork replicates the process. I was thinking of calling the fork here and then exec. But then everytime this function is called, there would be a fork call and soon I will have numerous processes in my system? Any ideas?
}

I hope I was clear, If there is any doubt, please let me know. Thank you for your time!

---

### Post by Bachstelze on 2013-10-21
Well, if you want to run a program, you must have a process for it, I don't see any way around it. Why is it a problem?

---

### Post by akshay-sulakhe on 2013-10-21
Hello, Thank you for your reply. That is my exact question, Inside the loop, how can i call another executable, as far as i know it can be achieved with exec...

---

### Post by Bachstelze on 2013-10-21
You want something like this (I wrap it in a function just for demonstation):

```

int compute(char *program, char *arg1, char *arg2, char *arg3)
{
    pid_t p = fork();
    if (p == -1) {
        perror("Error forking");
        return -1;
    }

    /* Child */
    if (p == 0) {
        int exec = execl(program, program, arg1, arg2, arg3, (char*)NULL);
        if (exec == -1) {
            perror("Error executing");
            exit(EXIT_FAILURE);
        }
    }

    /* Parent */
    int status;
    wait(&status);
    return WEXITSTATUS(status);
}

```

---

