---
title: "Timed telnet sessions?"
date: 2005-12-02
forum: Programming Talk
---

### Post by Burke on 2005-12-02
I am writing a C++ program to check the status of several servers. I am using exec("telnet google.com 443 > temp.asc"); (as an example) to check the status. I plan to have the program analyze this file, then send me mail if the server isn't running. My issue, though, is how should I go about terminating the telnet session? I figure any useful errors will show themselves within the first second or two.  Is there any command line trick to run a program for x seconds, then terminate? (There should be :))  If not, how could I go about terminating the session through exec() or otherwise?  

...or is telnet even the way I should be approaching this problem?

Thanks a million for your help.

(Sorry if this is a double post, I had some cookie issues)

---

### Post by cwaldbieser on 2005-12-03
[QUOTE=Burke]I am writing a C++ program to check the status of several servers. I am using exec("telnet google.com 443 > temp.asc"); (as an example) to check the status. I plan to have the program analyze this file, then send me mail if the server isn't running. My issue, though, is how should I go about terminating the telnet session? I figure any useful errors will show themselves within the first second or two.  Is there any command line trick to run a program for x seconds, then terminate? (There should be :))  If not, how could I go about terminating the session through exec() or otherwise?  

...or is telnet even the way I should be approaching this problem?

Thanks a million for your help.

(Sorry if this is a double post, I had some cookie issues)[/QUOTE]

There are different ways to approach the problem.  You could try using netcat (nc).  Since you are connecting to port 443 in your example, I'm guessing they are secure web servers?  In that case, you could use curl to do something like:
```

$ curl https://www.google.com

```
You can set the timeout to be whatever you want, and you could just examine the output to determine if you got the HTML you were expecting.

I would generally consider this sort of thing easier to do from a script, but you could open a raw TCP socket and send an HTTP GET command and see if you got a response.  That could be done without having to exec another process.

---

