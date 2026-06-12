---
title: "Cygwin Bash: kill command issues"
date: 2008-10-08
forum: Programming Talk
---

### Post by Silentwolf on 2008-10-08
Hi,
I'm a bit of a newbie, so please keep answers straight forward!
I'm trying to kill a particular process ID from a shell script.
Code = 
/bin/kill -f 1188

Error = 
illegal pid: 1188

I know that that process is there (am just testing with killing a notepad.exe process) and if I type the same command into the bash shell? then the command works and kills that process. Why won't it work in a *.sh script?

If you need more info let me know,

Thanks in advance,

---

### Post by Titan8990 on 2008-10-08
Did you remember to use a shebang:

#!/bin/bash


You are in flaky waters when trying to control windows with Cygwin. It does not function as a UNIX OS emulator like many (including myself) would like.

---

### Post by snova on 2008-10-08
I think the shebang must not be the problem because the "kill" program is giving the error, not the shell.

I don't know what might be causing the error except that Notepad doesn't have this particular PID anymore. After a PID gets used, it's typically never used again until you reboot. This is the case on Linux as I recall, but possibly not on Windows.

But I suggest the following instead of using PID's:

```
kill `pidof notepad`
# If that doesn't work, try:
kill `pidof notepad.exe`
```

"killall" is also an alternative, because then you don't have to deal with PID's. I don't know whether this is present on Cygwin, though I expect it probably is.

---

### Post by Silentwolf on 2008-10-09
Thanks for the replies so far. I think that there is something wrong with the way I'm doing my script... I'm also getting issues with finding files even if I think that the script should create the files in the first place. Though it is finding the first file I open...
I expect to find multiple processes with the same name, and I need to choose the most recent one to kill - which is why I don't have the luxury of using killall or kill 'pidof ...
Have been looking up how to write script files but am yet to find what is wrong with my code.
E.g of my code:

#! /bin/bash
#
#Paths to get commands from
PATH=/usr/bin:bin:C:\\WINNT\\system32;
#
echo "getting saved process id"
processid=$(cat notepadpid.txt)
echo $processid
#
echo "current notepad processes"
echo $(ps -W | grep notepad.exe)
#
echo "killing notepad"
/bin/kill -f $processid
echo $(ps -W | grep notepad.exe)
#
echo "starting notepad"
notepad.exe &
echo "find and save new notepad process id"
numberprocesses=($(ps -W | grep notepad.exe | wc -l))
ps -W | grep notepad.exe | cut -c6-10 > pid.txt
processid=($(cat pid.txt))
echo ${processid[${numberprocesses}-1]}
${processid[${numberprocesses}-1]} > notepadpid.txt
#Finished -> exit
exit 0

Debug script result:
bash-3.2$ bash notepadscript.sh
notepadscript.sh: line 4: $'\r': command not found
getting saved process id
2216
current notepad processes
2308 0 0 2308 ? 0 09:27:27 C:\WINNT\system32\notepad.exe 1224 0 0 1224 ? 0 09:30
:17 C:\WINNT\system32\notepad.exe 348 0 0 348 ? 0 09:44:22 c:\WINNT\system32\not
epad.exe 2216 0 0 2216 ? 0 10:02:59 C:\WINNT\system32\notepad.exe
killing notepad
kill: illegal pid: 2216
2308 0 0 2308 ? 0 09:27:27 C:\WINNT\system32\notepad.exe 1224 0 0 1224 ? 0 09:30
:17 C:\WINNT\system32\notepad.exe 348 0 0 348 ? 0 09:44:22 c:\WINNT\system32\not
epad.exe 2216 0 0 2216 ? 0 10:02:59 C:\WINNT\system32\notepad.exe
starting notepad
notepadscript.sh: line 18: $'\r': command not found
find and save new notepad process id
: No such file or directory1: pid.txt
-1")syntax error: operand expected (error token is "
-1")syntax error: operand expected (error token is "
: numeric argument required6: exit: 0

---

### Post by snova on 2008-10-09
The first thing I notice is that there shouldn't be a semicolon on line four. That's causing the first error.

I've no idea what to do, though. Shell scripting isn't one of my strengths.

---

### Post by Silentwolf on 2008-10-16
This is now solved.
It turned out to be due to editing the shell code in a Windows notepad which was adding Windows formatting to the shell when read in Bash. 
Thanks for your help.

---

