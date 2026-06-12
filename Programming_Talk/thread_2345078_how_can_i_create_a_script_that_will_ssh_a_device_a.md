---
title: "how can i create a script that will ssh a device and type some commands?"
date: 2016-11-30
forum: Programming Talk
---

### Post by ggabak on 2016-11-30
Hi Guys,
this is the scenario:
ubuntu pc and I have 10 wireless devices that I need to check their firmware version.
I would like to create a script that it will ask me IP, after I enter it, I hit enter then it will show me the version of the firmware.

this is what i do.

ssh admin@10.0.0.10
admin
admin
show device

The wireless box I use it is not a linux box it has it's commands.

thank you in advance for your help

---

### Post by TheFu on 2016-12-01
Welcome to the forums.

Teaching to fish ... I'd put the IPs into a text file and run the script as batch reading it, 1 line at a time.  Many different ways to accomplish this. 
[https://www.cyberciti.biz/faq/unix-linux-execute-command-using-ssh/](https://www.cyberciti.biz/faq/unix-linux-execute-command-using-ssh/)  

I'd specify the full-path-to-any-programs in the script. Never trust the PATH.

BTW, ssh can accept a password on the command line, if ssh-keys aren't setup.  BTW, I'd setup keys immediately and disable remote admin access using a password.

[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html) might be helpful too. "beginning bash scripting" is the search. There are lots of others.

If the remote systems aren't any sort of Unix, then I'd use **expect**. [http://www.admin-magazine.com/Articles/Automating-with-Expect-Scripts](http://www.admin-magazine.com/Articles/Automating-with-Expect-Scripts)

It is always best to learn by doing.

---

