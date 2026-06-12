---
title: "stdin for child process in bash script"
date: 2013-12-06
forum: Programming Talk
---

### Post by pavel-pazin on 2013-12-06
Hi everyone, 
I've some problems with bash-script.

I want to write bash script which reads from file some strings, calls some "cli" tool and inputs strings into cli-tool. Like some user enter it manually.

For example, we should start cli-tool, and input some commands:

User input manually:
#cli_tool
<cli_tool>: command1
some_output1
<cli_tool>: command2
some_output2
...
<cli_tool>: exit
#

I want to store these commands to file "command_to_cli_tool" and just run script which read commands and enters to tool

I tried to do something like this:

exec 6<&0
exec < command_to_cli_tool
read cmd1;
read cmd2;
exec 0<&6 6<&-

(
   /bin/cli_tool
   echo cmd1 > &0;
   echo cmd2 > &0;
)

But it seems smth wrong with pipes... 

Could any one give me some advice how I can write cmd1 to stdin for child process?

---

### Post by Lars Noodén on 2013-12-06
Normally you would use redirects to have your program read from a file.

```

cmnd1 < somefile;
cmnd2 < someotherfile;

```

---

