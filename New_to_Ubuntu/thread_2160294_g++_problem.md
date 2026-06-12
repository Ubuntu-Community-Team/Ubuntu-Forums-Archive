---
title: "g++ problem"
date: 2013-07-06
forum: New to Ubuntu
---

### Post by zDUle98 on 2013-07-06
Apparently I don't have g++ installed. I am running Ubuntu 13.04. When I try ```
sudo apt-get install g++
``` I get the following error message:

```
Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 g++ : Depends: g++-4.7 (>= 4.7.2-1~) but it is not going to be installed
```

What do you suggest me to do?

---

### Post by nemilar on 2013-07-06
What happens if you

```
apt-get install g++-4.7
```

?

---

### Post by zDUle98 on 2013-07-06
```
Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 g++-4.7 : Depends: gcc-4.7-base (= 4.7.2-22ubuntu5) but 4.7.3-1ubuntu1 is to be installed
           Depends: gcc-4.7 (= 4.7.2-22ubuntu5) but 4.7.3-1ubuntu1 is to be installed
           Depends: libstdc++6-4.7-dev (= 4.7.2-22ubuntu5) but it is not going to be installed
```

---

### Post by KARNVORbeefRAGE on 2013-07-06
Did you already install gcc? I realize that it is showing up as one of the dependencies to be installed, but does it work if you...
```
sudo apt-get install gcc
```
then...
```
sudo apt-get install g++
```

I appologize if this does nothing, but this was what I had to do.

---

### Post by zDUle98 on 2013-07-06
This is the output of the
```
sudo apt-get install gcc
```

```
Reading package lists...
Building dependency tree...
Reading state information...
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I can even compile c programs with gcc.

---

### Post by mc4man on 2013-07-06
could you run the below command, then post all that shows at the end - 
```
sudo apt-get update && apt-cache policy gcc-4.7 g++-4.7
```


Ex. from  here
> Reading package lists... Done
gcc-4.7:
  Installed: 4.7.3-1ubuntu1
  Candidate: 4.7.3-1ubuntu1
  Version table:
 *** 4.7.3-1ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main amd64 Packages
        100 /var/lib/dpkg/status
g++-4.7:
  Installed: 4.7.3-1ubuntu1
  Candidate: 4.7.3-1ubuntu1
  Version table:
 *** 4.7.3-1ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main amd64 Packages
        100 /var/lib/dpkg/status


---

### Post by zDUle98 on 2013-07-07
```

Reading package lists... Done
gcc-4.7:
  Installed: 4.7.3-1ubuntu1
  Candidate: 4.7.3-1ubuntu1
  Version table:
 *** 4.7.3-1ubuntu1 0
        100 /var/lib/dpkg/status
     4.7.2-22ubuntu5 0
        500 http://rs.archive.ubuntu.com/ubuntu/ raring/main amd64 Packages
g++-4.7:
  Installed: (none)
  Candidate: 4.7.2-22ubuntu5
  Version table:
     4.7.2-22ubuntu5 0
        500 http://rs.archive.ubuntu.com/ubuntu/ raring/main amd64 Packages

```

---

### Post by mc4man on 2013-07-07
The mirror you are using has not been updated so choose a different one.

Open up software sources, from terminal it's - 
```
software-properties-gtk
```
(on raring it may take about 10 sec to open, just wait

Then on main page choose another mirror to "Download from:" (I'd go with Main server for the moment, screen 1

While in software source also make sure under the Updates tab that the 1st. 2 are enabled  - screen 2

Then update your sources again (sudo apt-get update) & you should be fine 
(there may be a lot of other updates available, after installing g++ you could check

---

### Post by zDUle98 on 2013-07-07
Thanks. Everything works now :)

---

