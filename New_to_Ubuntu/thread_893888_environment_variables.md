---
title: "environment variables"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by boblemur on 2008-08-18
hey all, im looking for a way that i can change environment variables from the commandline, that are valid until i shutdown.

ie:

at boot

```
/etc/environment
```

reads:

```
# what eva path may be
PATH="......."
# my variable location
location="0" 

```

im looking for a way so that i can change location via the terminal to be anything i want, i have sudo access so i can change anything i want and i dont mind it asking for my pw.

is there a way to make changes to these variables? because my aim is to write a program that will apply my proxy and hosts depending on where i am(worked out from my ip address). but i need some way of having location globally available and also editable.

thanks in advance

---

### Post by freak42 on 2008-08-18
you can edit ~/.bashrc to add paths to your (or better bash's environment)
like this:

```
export PATH=$PATH:/whereever/the/path/should/go
```

you can check your current path on the command line like:
```
echo $PATH
```


of course you can also export on the commandline and not in the .bashrc file, however then the added path will not be retained across restarts.

hth

---

### Post by boblemur on 2008-08-18
this is not quite what im looking for.

i wanted to be able to globally change location, the other environment variable, but export simply changes it for that bash session and all of its child processes

---

### Post by Vivaldi Gloria on 2008-08-18
See

[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)

---

