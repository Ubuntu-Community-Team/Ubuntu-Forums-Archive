---
title: "Set permanent environment variable for a user"
date: 2012-01-06
forum: New to Ubuntu
---

### Post by Scarlet Sphere on 2012-01-06
Hi, 

I am trying to set an environment variable for a user but I am not sure how to. 
I read from [here]("https://help.ubuntu.com/community/EnvironmentVariables#Persistent environment variables")
> Environment variable settings that should affect just a particular user (rather then the system as a whole) should be set into:

~/.pam_environment - This file is specifically meant for setting a user's environment. It is not a script file, but rather consists of assignment expressions, one per line.
Note: Using .pam_environment requires a re-login in order to initialize the variables. Restarting just the terminal is not sufficient to be able to use the variables.

If you are using KDE, see the KDE User-base page on this topic.

Not recommended:

~/.profile - This is probably the best file for placing environment variable assignments, since it gets executed automatically by the DisplayManager during the start-up process desktop session as well as by the login shell when one logs-in from the textual console.
~/.bash_profile or ~./bash_login - If one of these file exist, bash executes it rather then "~/.profile" when it is started as a login shell. (Bash will prefer "~/.bash_profile" to "~/.bash_login"). However, these files won't influence a graphical session by default.
~/.bashrc - Because of the way Ubuntu currently sets up the various script files by default, this may be the easiest place to set variables in. The default configuration nearly guarantees that this file will be executed in each and every invocation of bash as well as while logging in to the graphical environment. However, performance-wise this may not be the best thing to do since it will cause values to be unnecessarily set many times.

Does that mean I just have to add the following line to either of the files?
```
export ABC=/home/user/abc
```

---

### Post by jtarin on 2012-01-06
What variable are you wanting to set?

---

### Post by Scarlet Sphere on 2012-01-08
I want to set a variable which I can retrieve by using System.getenv()

I tried just entering the export command in a terminal and then run the System.getenv() but it doesn't seem to retrieve anything. I really need help on this :confused:

---

