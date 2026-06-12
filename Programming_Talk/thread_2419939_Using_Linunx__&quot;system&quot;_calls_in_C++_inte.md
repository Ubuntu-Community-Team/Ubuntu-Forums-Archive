---
title: "Using Linunx  &quot;system&quot; calls in C++ interactively"
date: 2019-05-27
forum: Programming Talk
---

### Post by anneranch on 2019-05-27
I am seeking help in figuring out how to use “system” calls from within C++ code.  
 My goal is to utilize Linux “command”  bluetoothctl.
 It is my understanding  bluetoothctl is based on “bluez” package and it is now part of the Linux kernel.  
 
 
 I have successfully implemented simple system call to test retrieve  “bluetoothctl help “. 
 
 
 ```
[COLOR=#642880][FONT=Monospace][SIZE=2]**system**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Monospace][SIZE=2]([/SIZE][/FONT][/COLOR][COLOR=#2a00ff][FONT=Monospace][SIZE=2]"[/SIZE][/FONT][/COLOR][COLOR=#2a00ff][FONT=Monospace][SIZE=2]_bluetoothctl_[/SIZE][/FONT][/COLOR][COLOR=#2a00ff][FONT=Monospace][SIZE=2] help | [/SIZE][/FONT][/COLOR][COLOR=#2a00ff][FONT=Monospace][SIZE=2]_tee_[/SIZE][/FONT][/COLOR][COLOR=#2a00ff][FONT=Monospace][SIZE=2] /[/SIZE][/FONT][/COLOR][COLOR=#2a00ff][FONT=Monospace][SIZE=2]_tmp_[/SIZE][/FONT][/COLOR][COLOR=#2a00ff][FONT=Monospace][SIZE=2]/A_test_file.txt >&2"[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Monospace][SIZE=2]);[/SIZE][/FONT][/COLOR]


``` 
 
 [COLOR=#000000][FONT=Monospace][SIZE=2]Works as expected. [/SIZE][/FONT][/COLOR] 
 
 
 
 
 [COLOR=#000000][FONT=Monospace][SIZE=2]I am having issues replicating the following output from “terminal”:[/SIZE][/FONT][/COLOR]
 
 
 
 
 
 
 j```
im@jim-desktop:~$ bluetoothctl

 Agent registered
 [bluetooth]#  
 
 

``` 
 
 
 
 Here is my first attempt to run similar code from C++




 
 
 ```
[COLOR=#000000]  [FONT=Monospace][SIZE=2]cout << [/SIZE][/FONT][/COLOR][COLOR=#2a00ff][FONT=Monospace][SIZE=2]"[/SIZE][/FONT][/COLOR][COLOR=#2a00ff][FONT=Monospace][SIZE=2]_bluetoothctl_[/SIZE][/FONT][/COLOR][COLOR=#2a00ff][FONT=Monospace][SIZE=2] "[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Monospace][SIZE=2] << [/SIZE][/FONT][/COLOR][COLOR=#642880][FONT=Monospace][SIZE=2]**endl**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Monospace][SIZE=2]; [/SIZE][/FONT][/COLOR][COLOR=#3f7f5f][FONT=Monospace][SIZE=2]// just to see the prompt[/SIZE][/FONT][/COLOR]

 [LEFT][COLOR=#642880][FONT=Monospace][SIZE=2]**system**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Monospace][SIZE=2]([/SIZE][/FONT][/COLOR][COLOR=#2a00ff][FONT=Monospace][SIZE=2]"[/SIZE][/FONT][/COLOR][COLOR=#2a00ff][FONT=Monospace][SIZE=2]_bluetoothctl_[/SIZE][/FONT][/COLOR][COLOR=#2a00ff][FONT=Monospace][SIZE=2] | [/SIZE][/FONT][/COLOR][COLOR=#2a00ff][FONT=Monospace][SIZE=2]_tee_[/SIZE][/FONT][/COLOR][COLOR=#2a00ff][FONT=Monospace][SIZE=2] /[/SIZE][/FONT][/COLOR][COLOR=#2a00ff][FONT=Monospace][SIZE=2]_tmp_[/SIZE][/FONT][/COLOR][COLOR=#2a00ff][FONT=Monospace][SIZE=2]/A_test_file.txt >&2"[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Monospace][SIZE=2] );         [/SIZE][/FONT][/COLOR][COLOR=#3f7f5f][FONT=Monospace][SIZE=2]// expecting "Agent registered " [/SIZE][/FONT][/COLOR][COLOR=#3f7f5f][FONT=Monospace][SIZE=2]and [/SIZE][/FONT][/COLOR][COLOR=#3f7f5f][FONT=Monospace][SIZE=2][bluetooth]#  [/SIZE][/FONT][/COLOR][COLOR=#3f7f5f][FONT=Monospace][SIZE=2]prompt on next line [/SIZE][/FONT][/COLOR] [/LEFT]
 [LEFT]
 [/LEFT]

```

The “output” from  “[COLOR=#2a00ff][FONT=Monospace][SIZE=2]"[/SIZE][/FONT][/COLOR][COLOR=#2a00ff][FONT=Monospace][SIZE=2]_bluetoothctl_[/SIZE][/FONT][/COLOR][COLOR=#2a00ff][FONT=Monospace][SIZE=2]"[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Monospace][SIZE=2]command is only [/SIZE][/FONT][/COLOR] 
 
 
 [COLOR=#000000][FONT=Monospace][SIZE=2]A[/SIZE][/FONT][/COLOR][COLOR=#3f7f5f][FONT=Monospace][SIZE=2]gent registered[/SIZE][/FONT][/COLOR]
 
 
 [COLOR=#3f7f5f][FONT=Monospace][SIZE=2]both in  [/SIZE][/FONT][/COLOR][COLOR=#2a00ff][FONT=Monospace][SIZE=2]A_test_file.txt and stdout [/SIZE][/FONT][/COLOR][COLOR=#2a00ff][FONT=Monospace][SIZE=2]as expected , but no [/SIZE][/FONT][/COLOR][COLOR=#3f7f5f][FONT=Monospace][SIZE=2][bluetooth]#  [/SIZE][/FONT][/COLOR][COLOR=#3f7f5f][FONT=Monospace][SIZE=2]prompt[/SIZE][/FONT][/COLOR]
 
 
 [LEFT]
 [/LEFT]
 [LEFT]This call is different from the  [COLOR=#2a00ff][FONT=Monospace][SIZE=2]_bluetoothctl _[/SIZE][/FONT][/COLOR][COLOR=#2a00ff][FONT=Monospace][SIZE=2]_help” - it actually receives response from the  “_[/SIZE][/FONT][/COLOR][COLOR=#2a00ff][FONT=Monospace][SIZE=2]_bluetoothctl”  _[/SIZE][/FONT][/COLOR][COLOR=#2a00ff][FONT=Monospace][SIZE=2]_and then a prompt._[/SIZE][/FONT][/COLOR]
[/LEFT]
 [LEFT]
 [/LEFT]
 I would guess the system call “return” needs to be more than the actual first line output.  
 Perhaps “file descriptor” ?  
 I do not know how to modify the system call to be more useful / interactive.  

 Any help would be appreciated.

---

### Post by oldos2er on 2019-05-27
Moved to Programming Talk.

---

### Post by TheFu on 2019-05-28
Part of the confusion is that a system call isn't the same as using the system() function.  With access to C-bindings, I'd use the bluetooth libraries on the system directly, not call an external program from C/C++.  If I just needed to ensure a daemon was running, then I'd script that outside my code, in a shell script.

For how to use the specific bluetoothctl command, I'd read the manpage for it.  I purge all bluetooth stuff from my systems due to security considerations, so cannot try anything out. Sorry.

---

