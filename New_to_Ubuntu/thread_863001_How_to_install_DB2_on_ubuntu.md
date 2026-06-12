---
title: "How to install DB2 on ubuntu"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by alexband on 2008-07-18
I read the helps from IBM site.
Here is the thing.
I got a warning said I need to set the DISPLAY env variable, because I need to change to root to install DB2. When I use other username I can start the GUI panel but it won't install. 
So how can I set the env variable?
Does DB2 support to install on ubuntu?

---

### Post by overdrank on 2008-07-18
> **alexband said:**
> I read the helps from IBM site.
Here is the thing.
I got a warning said I need to set the DISPLAY env variable, because I need to change to root to install DB2. When I use other username I can start the GUI panel but it won't install. 
So how can I set the env variable?
Does DB2 support to install on ubuntu?

HI and you may look here
[http://www.ubuntu.com/partners/ibm/db2](http://www.ubuntu.com/partners/ibm/db2)
and 
[http://www.uboontu.com/results.htm?cx=002072379199720138921%3A9m-bgfzutzq&cof=FORID%3A10&q=DB2&sa.x=60&sa.y=25&sa=Search#1306](http://www.uboontu.com/results.htm?cx=002072379199720138921%3A9m-bgfzutzq&cof=FORID%3A10&q=DB2&sa.x=60&sa.y=25&sa=Search#1306)

---

### Post by phantomjoker on 2008-07-18
Ok - go to your terminal and enter ```
env
``` 

that gives you your environment readout. Also ```
env --help
``` gives you 'help' with the env code

Also on your env readout - your DISPLAY should read

> DISPLAY=:0.0

does this help?

---

### Post by agasamapetilon on 2008-10-07
Hi! I want to install a free version of DB2 v9.5 but when I try to run the db2setup I got the following error:

```
DBI1190I db2setup is preparing the DB2 Setup wizard which will guide
      you through the program setup process. Please wait.

The DISPLAY variable is not set properly. Ensure that the DISPLAY variable is set properly and that permissions are set properly to open windows on the display specified, then rerun the command.
```

I tried to run also as I read in some forums but nothing appears to work for me.

```
xclock &
```

When I echo the DISPLAY the output shows nothing. Any help will be much appreciated by you guys, thanks!

---

