---
title: "send&quot; command ends up with &quot;syntax error&quot;"
date: 2012-12-03
forum: New to Ubuntu
---

### Post by socialusr on 2012-12-03
Hi Everybody,

I am brand new to this forum and want some help related to below script:
----------------------------------------
#!/usr/bin/expect
#set timeout 2
spawn monitorcli
send "\r"
send "show smth\r"
sleep 1;
send "delete smth\r"
interact
----------------------------------------
Everything works fine until it comes to command:
send "delete smth\r"

Output of this command is incorrect:
------------------
# e smth
syntax error
------------------

It doesn't execute the whole command "delete smth" but just "e smth"

What shall i change/do in order to get complete command executed?
For command "show smth" the output is correct.

---

### Post by steeldriver on 2012-12-03
Hello and welcome

I don't use 'expect' very often - and I don't know what your 'monitorcli' remote command looks like - so I'm only guessing here but it would seem like the 'send "delete smth\r" gets sent before the remote session is ready for input and so the remote shell 'eats' the first few characters

Can you not use a true 'expect-send' pair instead of just sleeping? i.e. 'expect' the monitorcli prompt character(s) (whatever they are) and only *then* send the delete command?

---

