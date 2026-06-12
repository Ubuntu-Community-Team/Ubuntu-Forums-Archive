---
title: "Problrm with installing torque on 12,04"
date: 2012-06-10
forum: New to Ubuntu
---

### Post by hodgesse on 2012-06-10
Hi

I'm trying to install torque on 12.04

First I tried by downloading the tarball.  That didn't work.

Then I tried to use sudo apt-get install torque*

Here is the output;

 sudo apt-get install torque*
[sudo] password for erin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libtorque2' for regex 'torque*'
Note, selecting 'torque-server' for regex 'torque*'
Note, selecting 'libtorque-dev' for regex 'torque*'
Note, selecting 'torque-scheduler' for regex 'torque*'
Note, selecting 'torque' for regex 'torque*'
Note, selecting 'torque-client' for regex 'torque*'
Note, selecting 'torque-common' for regex 'torque*'
Note, selecting 'libtorque2-dev' for regex 'torque*'
Note, selecting 'torque-client-x11' for regex 'torque*'
Note, selecting 'torque-gui' for regex 'torque*'
Note, selecting 'torque-mom' for regex 'torque*'
Note, selecting 'torque-pam' for regex 'torque*'
Note, selecting 'slurm-llnl-torque' for regex 'torque*'
Note, selecting 'libtorque2-dev' instead of 'libtorque-dev'
libtorque2 is already the newest version.
libtorque2 set to manually installed.
torque-client is already the newest version.
torque-client set to manually installed.
torque-common is already the newest version.
torque-common set to manually installed.
torque-scheduler is already the newest version.
torque-scheduler set to manually installed.
torque-server is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 slurm-llnl-torque : Conflicts: torque-client
                     Conflicts: torque-client-x11 but 2.4.16+dfsg-1build1 is to be installed
 torque-client-x11 : Conflicts: torque-client
E: Unable to correct problems, you have held broken packages.
erin@ubuntu:~$ 

Any suggestions would be much appreciated.

Thanks,
Erin

---

### Post by hodgesse on 2012-06-11
This gives the solution:

[http://ubuntuforums.org/showthread.php?t=289767](http://ubuntuforums.org/showthread.php?t=289767)

---

### Post by remekk on 2012-07-06
Does it really solve the problem?

I have spent a lot of time trying to install Torque on Ubuntu 12.04, but unsuccessfully.
I have tried to install it from the software center, and also using the source files downloaded from the Torque website, and there is always a different problem... for instance, when trying to install version 4.1.0, I get the following error message when running the script configure:
```
configure: error: TORQUE needs libxml2-devel in order to build
```although libxml2-dev is installed on my machine.

Did anybody manage to install Torque on Ubuntu 12.04 and could help me?

Thank you very much in advance!

---

### Post by Noluigi on 2012-09-24
I have this same problem, is there a solution?

---

### Post by PMarecki on 2012-10-28
... had the same problem with Torque 4.1.2; 

First apply the patches from: [http://www.clusterresources.com/bugzilla/show_bug.cgi?id=210](http://www.clusterresources.com/bugzilla/show_bug.cgi?id=210)

and run `autoconf`; these still fail to produce the correct `sed` line in final `configure` file (for me), which you may edit manually to be of the final form

xmlLib=`xml2-config --libs | sed 's/-L[^[:space:]]* //g;s/-l//'`
echo "Current output of the script: $xmlLib" 

[echo should report `xml2`]
Afterwards `configure` runs smoothly to the end.

---

