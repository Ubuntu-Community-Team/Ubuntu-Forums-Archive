---
title: "cannot connect to X server"
date: 2012-11-16
forum: Programming Talk
---

### Post by binglim on 2012-11-16
I use OpenCV 2.4.3 with Eclipse (plugin CDT) in Ubuntu 12.10. 
I am sure the code is fine and I can build the project successfully, 
but when I ran the project, there is an error ":cannot connect to X server". 
Could you please help me on this? 
Thanks a lot!

---

### Post by dwhitney67 on 2012-11-16
Have you tried the following:  [http://lmgtfy.com/?q=%22%3Acannot+connect+to+X+server%22](http://lmgtfy.com/?q=%22%3Acannot+connect+to+X+server%22)

As for your exact problem, you will need to insert a quarter into my crystal ball to give you an approximate answer to solve the dilemma you are facing.

---

### Post by aknet on 2013-02-07
Did you find any solution binglim?
How it's fixed?

---

### Post by carabas on 2013-04-30
I had the same problem. The problem was that the console my application got started in didn't know the DISPLAY environment variable.

SOLUTION: Open the "run configurations" dialog, choose your application, switch to tab "environment", and add a variable DISPLAY set to ":0" 
(which is the equivalent of environment variable  DISPLAY=":0" in your shell)

---

