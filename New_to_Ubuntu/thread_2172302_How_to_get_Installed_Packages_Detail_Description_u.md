---
title: "How to get Installed Packages Detail Description using cmd in 12.04"
date: 2013-09-04
forum: New to Ubuntu
---

### Post by Harmeet_Singh on 2013-09-04
i want to get detail description of all installed and packages and also want installed packages is device into groups like in synaptic manager. how to achive this using command in ubuntu or another way. i fount some commands for find installed packages and detail description but how to finds packages groups ? the commands are as 
below : 

$dpkg --get-selections > install.txt

$ dpkg --print-avail mongodb-10gen

---

### Post by ian-weisser on 2013-09-04
You really want thousands of package descriptions?
Why? Do you plan to use them for something, or are you merely browsing?


One simple way to get a package description is to use the command **apt-cache show <packagename>** and look for the Description field. For group, look in the Section field.

To get all the installed packages, you would obviously need to script the command into your solution.

For example, the "hello" package is in the devel section:
```
$ apt-cache show hello | grep Section:
Section: devel
```

---

### Post by bluefrog on 2013-09-04
cat /var/lib/dpkg/status
dpkg -l will list what is available on your system as well
dpkg -p zip will give info about zip package

---

### Post by oldfred on 2013-09-04
If you want the list of default applications and versions you can go the the local mirror you use to download from and manifests for the flavor you download.
       Look for manifests for version:
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

If you want a list to reinstall you just want package names.

 dpkg --get-selections > ~/my-packages

      
 List with explanations of programs, not for reinstall
dpkg -l > ~/installed_programs.txt


 Top level only - no depends (not for reinstall)
sudo apt-get install aptitude
aptitude --disable-columns -F '%p' search '~i!~M!~R(~i)' > toplevel 

But if you want all the details I think you have to run a script as suggested by ian-weisser above.

---

