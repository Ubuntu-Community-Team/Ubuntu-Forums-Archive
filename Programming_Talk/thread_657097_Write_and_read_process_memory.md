---
title: "Write and read process memory"
date: 2008-01-03
forum: Programming Talk
---

### Post by rootslash on 2008-01-03
Happy newyear all!

This is my question, is there on ubuntu an api for writeprocessmemory and readprocessmemory(what you can use in windows)?  

If there is any library or anything else I prefer to have it done in Python (or maybe C++).
Hope to get a quick answer!

RootSlash

---

### Post by stroyan on 2008-01-03
You can read and write one word at a time using the ptrace system call.  See "man ptrace".```
#include <sys/ptrace.h>
val = ptrace(PTRACE_PEEKDATA, pid, address, 0);
ptrace(PTRACE_POKEDATA, pid, address, data);
```
There is a python binding for ptrace in the *subterfugue* package available from the ubuntu universe repository.

---

### Post by meatpan on 2008-01-03
> **rootslash said:**
> Happy newyear all!

This is my question, is there on ubuntu an api for writeprocessmemory and readprocessmemory(what you can use in windows)?  


Can you give a few more details about what these commands are supposed to do?  Is this attempting some kind of interprocess communication?

---

### Post by WitchCraft on 2009-01-20
> **meatpan said:**
> Can you give a few more details about what these commands are supposed to do?  Is this attempting some kind of interprocess communication?

Usually you need them either for debuggers, or for hacking programs, e.g. aimbots for ego-shooter games.

you can for example overwrite a function that verifies a product key and exits a program when the correct key is not provided.

if (keynotcorrect)
    InitiateShutdown();

So you use WriteProcessMemory to either overwrite keynotcorrect with false, or you write a RET instruction at &InitiateShutdown + 0, and the problem is solved. Cool, isn't it?

Or you are the "key issuing company" and use ReadProcessMemory to read &InitiateShutdown + 0, to check whether or not there is a RET instruction, that is to say whether the function was hacked or not...

It's a very useful thing from a hacker's perspective - a very dangerous thing from everybody else's point of view...

---

### Post by WitchCraft on 2009-01-21
To write a wrapper for Read/Write ProcessMemory, you need to get the PID of the executable you want to ptrace.

I've written a function implementation for this .
GetPID.c / cpp

featuring: 
- C Function Overloading workaround
- compiles with gcc and g++

I request comment / critique for the C/C++ code below.

What it does:
It reads all folders in /proc
if the foldername is numeric, it cats cmdline to get the process name
the numeric foldername is the PID
if the process name coressponds with the searched process name (strstr or strcmp, case sensitive or not), it returns the pid
if it doesn't find the process, it returns -1, if it cannot access /proc it returns -2; if several processes with the same name run, it returns the one with the lower number

> 
all:~# cd /proc
all:/proc# ls
...
1      2313  2836  3102  3293  908        ide        pagetypeinfo
1513   2698  3027  3144  4929  crypto        kpagecount    sysrq-trigger
---
all:/proc# cd 3027
all:/proc/3027# ls
attr        coredump_filter  ...
cmdline     exe             loginuid  mountstats  root       statm
all:/proc/3027# cat cmdline
/usr/lib/libgconf2-4/gconfd-211
all:/proc/3027# 
```


#ifndef __cplusplus
    #define _GNU_SOURCE
#endif

#include <unistd.h>
#include <dirent.h>
#include <sys/types.h> // for opendir(), readdir(), closedir()
#include <sys/stat.h> // for stat()

#ifdef __cplusplus
    #include <iostream>
    #include <cstdlib>
    #include <cstring>
    #include <cstdarg>
#else
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    #include <stdarg.h>
#endif


#define PROC_DIRECTORY "/proc/"
#define CASE_SENSITIVE    1
#define CASE_INSENSITIVE  0
#define EXACT_MATCH       1
#define INEXACT_MATCH     0


int IsNumeric(const char* ccharptr_CharacterList)
{
    for ( ; *ccharptr_CharacterList; ccharptr_CharacterList++)
        if (*ccharptr_CharacterList < '0' || *ccharptr_CharacterList > '9')
            return 0; // false
    return 1; // true
}


int strcmp_Wrapper(const char *s1, const char *s2, int intCaseSensitive)
{
    if (intCaseSensitive)
        return !strcmp(s1, s2);
    else
        return !strcasecmp(s1, s2);
}

int strstr_Wrapper(const char* haystack, const char* needle, int intCaseSensitive)
{
    if (intCaseSensitive)
        return (int) strstr(haystack, needle);
    else
        return (int) strcasestr(haystack, needle);
}


#ifdef __cplusplus
pid_t GetPIDbyName(const char* cchrptr_ProcessName, int intCaseSensitiveness, int intExactMatch)
#else
pid_t GetPIDbyName_implements(const char* cchrptr_ProcessName, int intCaseSensitiveness, int intExactMatch)
#endif
{
    char chrarry_CommandLinePath[100]  ;
    char chrarry_NameOfProcess[300]  ;
    char* chrptr_StringToCompare = NULL ;
    pid_t pid_ProcessIdentifier = (pid_t) -1 ;
    struct dirent* de_DirEntity = NULL ;
    DIR* dir_proc = NULL ;

    int (*CompareFunction) (const char*, const char*, int) ;

    if (intExactMatch)
        CompareFunction = &strcmp_Wrapper;
    else
        CompareFunction = &strstr_Wrapper;


    dir_proc = opendir(PROC_DIRECTORY) ;
    if (dir_proc == NULL)
    {
        perror("Couldn't open the " PROC_DIRECTORY " directory") ;
        return (pid_t) -2 ;
    }

    // Loop while not NULL
    while ( (de_DirEntity = readdir(dir_proc)) )
    {
        if (de_DirEntity->d_type == DT_DIR)
        {
            if (IsNumeric(de_DirEntity->d_name))
            {
                strcpy(chrarry_CommandLinePath, PROC_DIRECTORY) ;
                strcat(chrarry_CommandLinePath, de_DirEntity->d_name) ;
                strcat(chrarry_CommandLinePath, "/cmdline") ;
                FILE* fd_CmdLineFile = fopen (chrarry_CommandLinePath, "rt") ;  // open the file for reading text
                if (fd_CmdLineFile)
                {
                    fscanf(fd_CmdLineFile, "%s", chrarry_NameOfProcess) ; // read from /proc/<NR>/cmdline
                    fclose(fd_CmdLineFile);  // close the file prior to exiting the routine

                    if (strrchr(chrarry_NameOfProcess, '/'))
                        chrptr_StringToCompare = strrchr(chrarry_NameOfProcess, '/') +1 ;
                    else
                        chrptr_StringToCompare = chrarry_NameOfProcess ;

                    //printf("Process name: %s\n", chrarry_NameOfProcess);
                    //printf("Pure Process name: %s\n", chrptr_StringToCompare );

                    if ( CompareFunction(chrptr_StringToCompare, cchrptr_ProcessName, intCaseSensitiveness) )
                    {
                        pid_ProcessIdentifier = (pid_t) atoi(de_DirEntity->d_name) ;
                        closedir(dir_proc) ;
                        return pid_ProcessIdentifier ;
                    }
                }
            }
        }
    }
    closedir(dir_proc) ;
    return pid_ProcessIdentifier ;
}

#ifdef __cplusplus
    pid_t GetPIDbyName(const char* cchrptr_ProcessName)
    {
        return GetPIDbyName(cchrptr_ProcessName, CASE_INSENSITIVE, EXACT_MATCH) ;
    }
#else
    // C cannot overload functions - fixed
    pid_t GetPIDbyName_Wrapper(const char* cchrptr_ProcessName, ... )
    {
        int intTempArgument ;
        int intInputArguments[2] ;
        // intInputArguments[0] = 0 ;
        // intInputArguments[1] = 0 ;
        memset(intInputArguments, 0, sizeof(intInputArguments) ) ;
        int intInputIndex ;
        va_list argptr;

        va_start( argptr, cchrptr_ProcessName );
            for (intInputIndex = 0;  (intTempArgument = va_arg( argptr, int )) != 15; ++intInputIndex)
            {
                intInputArguments[intInputIndex] = intTempArgument ;
            }
        va_end( argptr );
        return GetPIDbyName_implements(cchrptr_ProcessName, intInputArguments[0], intInputArguments[1]);
    }

    #define GetPIDbyName(ProcessName,...) GetPIDbyName_Wrapper(ProcessName, ##__VA_ARGS__, (int) 15)

#endif

int main()
{
    pid_t pid = GetPIDbyName("bash") ; // If -1 = not found, if -2 = proc fs access error
    printf("PID %d\n", pid);
    return EXIT_SUCCESS ;
}

```

---

