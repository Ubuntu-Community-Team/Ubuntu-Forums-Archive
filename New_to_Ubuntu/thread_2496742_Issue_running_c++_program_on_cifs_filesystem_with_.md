---
title: "Issue running c++ program on cifs filesystem with kernel 6.5.0-26-generic"
date: 2024-04-10
forum: New to Ubuntu
---

### Post by oraclerzhang on 2024-04-10
Hello,
When I try to run a c++ script which is on a cifs mounted system I get an error message. This is on a Ubuntu 22.04----Linux  6.5.0-26-generic #26~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Tue Mar 12 10:22:43 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

T01$ ./test
-bash: ./test: Input/output error
Then I find the warning in the kernel log:
T01$ sudo tail -n 100 /var/log/syslog | grep -i warning
<4>1 2024-04-10T10:15:57.163826-07:00 T01 kernel - - - [25523.801864] WARNING: CPU: 12 PID: 42870 at fs/smb/client/file.c:3341 cifs_limit_bvec_subset.constprop.0+0x11a/0x190 [cifs]


Here is my c++ file: I have already give "+x" to my c++ script
#include <stdio.h>
#include <errno.h>
#include <string.h>
int main() {
    printf("Starting the program...\n");


    if (printf("Hello, World!\n") < 0) {
        // If printf returns a negative value, an error occurred
        perror("Error printing Hello, World");
        return 1;
    }


    printf("Program finished successfully.\n");
    return 0;
}

But my c++ script was running well in kernel 6.2.0-32, is there something bug or upgrade since kernel 6.5.0-*?
T02$ ./test
Starting the program...
Hello, World!
Program finished successfully.

T02$ uname -a
Linux T02 6.2.0-32-generic #32~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Fri Aug 18 10:40:13 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

With the latest kernel version 6.5.0-26, I'm only having trouble with the C++ file in my cifs mounted dir, getting input/output errors. But with kernel 6.2.0-32 the script is working perfectly fine.





I will appropriate with any response. 

[COLOR=#000000][FONT=&quot]ProblemType: Bug[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]DistroRelease: [/FONT][/COLOR]Ubuntu 22.04.4 LTS
[COLOR=#000000][FONT=&quot]Package: [/FONT][/COLOR]linux-image-6.5.0-26-generic                                                             
[COLOR=#000000][FONT=&quot]ProcVersionSign[/FONT][/COLOR][COLOR=#000000][FONT=&quot]ature: Ubuntu [/FONT][/COLOR]6.5.0-26.26~22.04.1   
[COLOR=#000000][FONT=&quot]Uname: Linux 6.5.0-26-generic x86_64[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Architecture: amd64[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]CurrentDesktop: GNOME[/FONT][/COLOR]

---

### Post by TheFu on 2024-04-12
**There's no such thing as a C++ script.  You need to compile and link the C++ to make a program before it will run anything.**

CIFS mounts only get Unix-style permissions from the mount options.  Extensions mean nothing on Unix systems.  The file permissions control access and whether it can be executed.  Check the permissions for the resulting program, assuming is it located on CIFS.  BTW, all sorts of Unix build tools will complain about files being stored on CIFS storage.  You should use either NFS or local, native, Unix/Linux file systems for programming work.  If a program doesn't have execute permissions, it won't run.

CIFS needs to be mounted as a real file system, not just clicked as a GUI program might do.  Check that the **pwd** is set to an expected thing.

And you do understand that **chmod** and **chown** [COLOR="#FF0000"]_don't work_[/COLOR] on NTFS, exFAT, FAT32 nor CIFS/Samba storage at all, right?

---

### Post by oraclerzhang on 2024-04-12
Hello, TheFu
Thank you for your support.
[COLOR=#0D0D0D][FONT=Söhne]Here are my test results with different Ubuntu 22.04 kernel versions:[/FONT][/COLOR]
---------------------------------------------------------------------------
1:  **Kernel 6.5.0-26 --- got Input/Output error, and **[COLOR=#0D0D0D][FONT=Söhne]**I noticed there's an extra module called 'netfs' compared to kernel 6.2.0-32**.[/FONT][/COLOR]
oracler@T01:~/codehome$ uname -r
6.5.0-26-generic
oracler@T01:~/codehome$ ls -l
total 17
drwx------ 2 oracler domain users    0 Feb 21 10:32 '$RECYCLE.BIN'
-rwx------ 1 oracler domain users  282 Feb 21 10:31  desktop.ini
-rwx------ 1 oracler domain users  358 Apr  5 11:42  hello.c
-rwx------ 1 oracler domain users   14 Apr  9 12:22  test_file.txt
-rwx------ 1 oracler domain users    0 Feb  8 10:05  testing
-rwx------ 1 oracler domain users 1584 Apr  8 13:52  testing.c
-rwx------ 1 oracler domain users  452 Apr  8 13:38  test.py
oracler@T01:~/codehome$ g++ -o test hello.c
oracler@T01:~/codehome$ ./test
-bash: ./test: Input/output error
oracler@T01:~/codehome$ cat hello.c
#include <stdio.h>
#include <errno.h>
#include <string.h>
int main() {
    printf("Starting the program...\n");


    if (printf("Hello, World!\n") < 0) {
        // If printf returns a negative value, an error occurred
        perror("Error printing Hello, World");
        return 1;
    }


    printf("Program finished successfully.\n");
    return 0;
}

oracler@T01:~/codehome$ lsmod | grep -i cifs
cifs                 1417216  3
cifs_arc4              12288  1 cifs
cifs_md4               12288  1 cifs
fscache               389120  2 cifs,nfs
[B]netfs                  61440  3 cifs,fscache,nfs


[/B]

---------------------------------------------------------------------------
2.** Kernel 6.2.0-32 ---- going well without any problems.**
oracler@T02:~/codehome$ uname -r
6.2.0-32-generic
oracler@T02:~/codehome$ ls -l
total 33
drwx------ 2 oracler domain users     0 Feb 21 10:32 '$RECYCLE.BIN'
-rwx------ 1 oracler domain users   282 Feb 21 10:31  desktop.ini
-rwx------ 1 oracler domain users   358 Apr  5 11:42  hello.c
-rwx------ 1 oracler domain users 16048 Apr 12 10:02  test
-rwx------ 1 oracler domain users    14 Apr  9 12:22  test_file.txt
-rwx------ 1 oracler domain users     0 Feb  8 10:05  testing
-rwx------ 1 oracler domain users  1584 Apr  8 13:52  testing.c
-rwx------ 1oracler domain users   452 Apr  8 13:38  test.py
oracler@T02:~/codehome$ g++ -o test1 hello.c
oracler@T02:~/codehome$ ./test1
Starting the program...
Hello, World!
Program finished successfully.
oracler@T02:~/codehome$ cat hello.c
#include <stdio.h>
#include <errno.h>
#include <string.h>
int main() {
    printf("Starting the program...\n");


    if (printf("Hello, World!\n") < 0) {
        // If printf returns a negative value, an error occurred
        perror("Error printing Hello, World");
        return 1;
    }


    printf("Program finished successfully.\n");
    return 0;
}

oracler@T02:~/codehome$ lsmod | grep -i cifs
cifs                 1384448  3
cifs_arc4              16384  1 cifs
cifs_md4               16384  1 cifs
fscache               385024  2 cifs,nfs


I will appreciate any response.

---

### Post by TheFu on 2024-04-12
Please, please, please, wrap terminal and code with forum code-tags so indentation is maintained. Too hard to read otherwise and nobody here is being paid.  Don't make it hard for people to help you or learn from what you are doing.

[Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) explains.
Basically, use the "advanced editor" and use the '#' button on the header there like you were using Bold or Quote tags.

BTW, you've lost me completely on the lsmod output.  I don't see the relevance.  **df -Th .** is how I'd check the file system and mount for the **pwd**.

And a .c file will be compiled as C code, not C++.  If you want to force C++ compilation, use .C or .cc or .cxx, or .cpp as the extension.  However, for a program this trivial, all that forcing CPP to be used does is add bloat.  The only thing I see in the code that isn't normal C is the // for comments. I suppose gcc/g++ decided not to bother about that error ... or perhaps support was added to a later C version that I used decades ago.  The last time I wrote any new C code was in the 1990s.

I don't have any CIFS storage here anymore and I don't have any kernels newer than, ... 5.15.x.  I'm all about stability", not "new".

---

### Post by oraclerzhang on 2024-04-12
Hi TheFu,
Thank you for you support.
I just went through the kernel release: [https://discourse.ubuntu.com/t/jammy-jellyfish-release-notes/24668#heading--official-flavours](https://discourse.ubuntu.com/t/jammy-jellyfish-release-notes/24668#heading--official-flavours)
and run: [COLOR=#C4C7C5][FONT=&quot]sudo sysctl -w kernel.task_delayacct=1  
My problem is fixed.

[/FONT][/COLOR]

---

### Post by oraclerzhang on 2024-04-12
Hi TheFu,
[COLOR=#0D0D0D][FONT=Söhne]Sorry, I'm feeling drained. I ran my code on an NFS mount mistakenly which I thought I fixed issue, but our CIFS mount from Netapp is a no-go for changes, and the client wants the latest kernel. It's driving me crazy! I haven't touched anything on the Netapp site or the CIFS mount options. I just upgraded the kernel from 6.2.0-32 to 6.5.0-26, and now I'm getting this error. I also found another guy facing the same issue as me.-- [/FONT][/COLOR][Bug #2052835 &#8220;Error running program on cifs filesystem&#8221; : Bugs : linux-signed-hwe-6.5 package : Ubuntu (launchpad.net)]("https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-6.5/+bug/2052835")

---

### Post by MAFoElffen on 2024-04-15
Sort of & then again, not the same. You are running compiled C++, and he is running a Bash Script. Right? Same kernel, and from a CIFS mount, but with different animals.

Quoted from ilmarix:
> 
     mounting with
 -o cache=loose
 seems to circumvent the issue for me.
This is probably not safe if multiple machines are accessing the same files.

                  

Did you try that?

---

### Post by oraclerzhang on 2024-04-15
Hi MAFoElffen,
I just tried cache=loose, it worked. thanks a lot.

---

### Post by MAFoElffen on 2024-04-16
So this is working now?

If so, when we open a thread, we (the person who started it) are responsible to mark it as "Solved".

At the "Thread Tools" link at the upper right of the first page of the thread, there is a link "in it" to mark it as Solved.

---

### Post by oraclerzhang on 2024-04-19
Yes, It is working now, thanks again.

---

