---
title: "sprintf problem in Ubuntu"
date: 2008-12-02
forum: Programming Talk
---

### Post by y_kavaguchi on 2008-12-02
Hi,

I was using this command in linux:

sprintf('filename1 %.16E > %s',number,filename2);

which reads filename1 and puts the value of number in the specified places with $ and write the whole new content in filename2.

The problem is that now I have installed Ubuntu 7.1 in my laptop and it seems it doesn't have "sprintf" command. Could someone help me how can i do this in Ubuntu?! which command should I use?!

Thanks.

---

### Post by dwhitney67 on 2008-12-02
Ubuntu does not come setup as a development system when you install it.  You need to add packages post-install.

For the development package, you need to run the following command:
```

sudo apt-get install build-essential

```

---

### Post by y_kavaguchi on 2008-12-02
Thnaks dwhitney67,

I typed "sudo apt-get install build-essential" in the command line and after getting password, it installed the package. I opened a new session. But still there is no "sprintf" command, when I try to run my command or man sprintf!

---

### Post by dwhitney67 on 2008-12-02
The manpages require yet another package...
```

sudo apt-get install manpage-dev

```

See if this program works:
[php]
#include <stdio.h>

int main()
{
  printf("it works!\n");
  return 0;
}
[/php]
To build and run it:
```

gcc test.c
./a.out

```
If the program above compiles/works, then I would tend to believe the sprintf() problem is related to your application, not the Ubuntu system.

---

### Post by dwhitney67 on 2008-12-02
> **y_kavaguchi said:**
> Hi,

I was using this command in linux:

sprintf('filename1 %.16E > %s',number,filename2);

which reads filename1 and puts the value of number in the specified places with $ and write the whole new content in filename2.

The problem is that now I have installed Ubuntu 7.1 in my laptop and it seems it doesn't have "sprintf" command. Could someone help me how can i do this in Ubuntu?! which command should I use?!

Thanks.
Your sprintf() function call is ill-formatted.

According to the manpage, the destination buffer is the first parameter; the second parameter is the format string; then the values (if any) that are needed within your format string come next.

```

int sprintf(char *str, const char *format, ...);

```

---

### Post by y_kavaguchi on 2008-12-02
It works. But my problem still exist. :(

Actually what I am doing is inside MATLAB with the command "system" like this:

system(sprintf('filename1 %.16E > %s',number,filename2));

The "system" command in MATLAB is a simple command that runs whatever inside the parenthesis in linux command line. The code is working in a linux machine properly, but in Ubuntu machine when I run it in MATLAb it gives me this error:

/bin/bash: cvode_odesolver: command not found 

that cvode_odesolver is filename1 inside the sprintf command.

But thanks for your helps.

---

### Post by dwhitney67 on 2008-12-02
I am familiar with the sprintf() command, in the context of the C standard library.  It does *not* return a char pointer (i.e. a string) that can be used by the system() function.  sprintf() return an int value that represents the number of characters written to the destination buffer (which your call to sprintf() lacks).

Now, MATLAB, which I am not familiar with, may treat sprintf() differently.

In C, to accomplish the call to system(), I believe you would need to declare a buffer, call sprintf(), then pass the buffer to system().

[php]
/* declare a buffer; initialize to all nulls */
char buffer[1024] = {0};

/* I use snprintf()... it is safer than regular sprintf(). */
snprintf(buffer, sizeof(buffer)-1, "filename1 %.16E > %s", number, filename2);

/* execute the command */
system(buffer);
[/php]

P.S.  I did not compile the code above; forgive me if there are any syntax errors.

---

### Post by y_kavaguchi on 2008-12-02
Thanks alot dwhitney67,

I solved the stupid problem.
Yes, the sprintf command in MATLAB is different from C.

when you type:
a = sprintf('filename1 %.16E > %s',number,filename2)
the output is:
a = 'filename1 number > filename2'
a is only string. Then when I type system('a') in my linux machine it runs properly and puts the content of filename1 with a change in the number inside filename2.

But in Ubuntu instead of 
'filename1 number > filename2'
I should put 
'./filename1 number > filename2'
I know that this "./" to execute the commands is not Ubuntu problem. It is from my weak linux knowledge that still I don't know why I should put ./ before all the files to execute them while in my linux machine I just type the file name!!! :( This is the third once that this "./" catches me! :(

---

### Post by geirha on 2008-12-02
There are two ways to execute a command in the shell.
1. Supply the path (either relative or absolute) to where the executable is. E.g
```

/bin/ls    # Abosolute path to the executable
./foo      # Relative path to the executable, with . being the current directory

```
2. Run the command without specifying the path. It will then search through the PATH variable.
```
$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
$ ls

```
In the above example, it will first look for /usr/local/sbin/ls, then /usr/local/bin/ls, then /usr/sbin/ls etc. until it finds it. Since ls is in /bin and /bin is in my PATH variable, it will eventually find it and execute it. If it doesn't find it, it will give you the error "command not found"

It is possible to add . (current directory) to the PATH variable, and that will allow you to execute files that are in the current directory, without prepending it with ./, but that is a security risk, and I'd recommend against it. Your other linux system probably has . in the PATH...?

---

### Post by y_kavaguchi on 2008-12-02
Thanks a million,

I understood now! Yes I looked to the .cshrc file in the other linux system and it has a . in the defined path!

Best regards,
Saeid.

---

