---
title: "C: how to execute python script as system call"
date: 2014-07-26
forum: Programming Talk
---

### Post by erotavlas on 2014-07-26
Hi,

I cannot figure out how I can execute a python script from my C code. I read that I can embed the python code inside C, but I want simply to launch a python script as if I execute it from command line. I tried with the following code:

```


    char * paramsList[] = {"/bin/bash", "-c", "/usr/bin/python", "/home/mypython.py",NULL};
    pid_t pid1, pid2;
    int status;

    pid1 = fork();
    if(pid1 == -1)
    {
        char err[]="First fork failed";
        die(err,strerror(errno));
    }
    else if(pid1 == 0)
    {  
        pid2 = fork();

        if(pid2 == -1)
        {
            char err[]="Second fork failed";
            die(err,strerror(errno));
        }
        else if(pid2 == 0)
        {  
               int id = setsid(); 
               if(id < 0)
               {
                   char err[]="Failed to become a session leader while daemonising";
                die(err,strerror(errno));
               }
               if (chdir("/") == -1) 
               {
                char err[]="Failed to change working directory while daemonising";
                die(err,strerror(errno));
            }
            umask(0);
            
            execv("/bin/bash",paramsList); // python system call           
            
        }
        else
        {         
            exit(EXIT_SUCCESS);
        }
    }
    else
    {    
        waitpid(pid1, &status, 0); 
    }


```

I don't know where is the error since if I replace the call to python script with the call to another executable, it works well.
I have added at the beginning of my python script the line #!/usr/bin/python.
What can I do?

Thank you in advance

---

### Post by ofnuts on 2014-07-26
You are making things a lot more difficult than necessary. In Unix the python file itself (if marked executable, and containing the adequate shebang) can be given to the exec*() call:

```

#include <unistd.h>
#include <stdio.h>

int main(int argc, char **argv) {

    char *calledPython="./calledPython.py";  // it can also be resolved using your PATH environment variable
    char *pythonArgs[]={calledPython,"a","b","c",NULL};
    execvp(calledPython,pythonArgs);

    // if we get here it misfired
    perror("Python execution");
}

```

Otherwise, without executable bit or shebang, you call the python interpreter and pass the python file as the first argument:

```

#include <unistd.h>
#include <stdio.h>

int main(int argc, char **argv) {

    char *pythonIntrepreter="python"; // resolved using your PATH environment variable
    char *calledPython="./calledPython.py"; // explicit path necessary, not resolved using your PATH environment variable
    char *pythonArgs[]={pythonIntrepreter,calledPython,"a","b","c",NULL};
    execvp(pythonIntrepreter,pythonArgs);

    // if we get here it misfired
    perror("Python execution");
}

```

The latter method can also be used on Windows where the Python interpreter must be explicitly called.

---

### Post by erotavlas on 2014-07-27
Ok, thank you. I solve by unifying the two arguments of python like this:
```


char * paramsList[] = { "/bin/bash", "-c",
                        "/usr/bin/python /home/mypython.py", NULL };

```

---

### Post by ofnuts on 2014-07-27
You are still using a completely unnecessary instance of bash...

---

