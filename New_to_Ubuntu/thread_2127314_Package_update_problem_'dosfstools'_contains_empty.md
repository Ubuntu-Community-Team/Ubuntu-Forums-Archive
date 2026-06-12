---
title: "Package update problem: 'dosfstools' contains empty filename"
date: 2013-03-19
forum: New to Ubuntu
---

### Post by Aerotype7 on 2013-03-19
When I attempt to perform a general update, or install some software, I get the following error:

(Reading database ... 75%dpkg: unrecoverable fatal error, aborting:
 files list file for package `dosfstools' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)


I have the Ubuntu standard set installed, which claims to contain dosfstools, and I can find the associated .list file, but I'm not sure how to go about fixing this. Can anyone shed light on this problem and a potential solution?

Thanks.

---

### Post by Aerotype7 on 2013-03-20
I haven't made any progress - any ideas? 

Alternatively, is there something I could do to make my question clearer? Or should I post in a different section?

---

### Post by ibjsb4 on 2013-03-20
Have you tried reinstalling it?

```
sudo apt-get install --reinstall dosfstools
```

---

### Post by Aerotype7 on 2013-03-20
Yes, gives an error:



Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 412 not upgraded.
Need to get 75.9 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main dosfstools amd64 3.0.12-1ubuntu1 [75.9 kB]
Fetched 75.9 kB in 0s (5,260 kB/s)    
(Reading database ... 75%dpkg: unrecoverable fatal error, aborting:
 files list file for package `dosfstools' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by ibjsb4 on 2013-03-20
Try 

```
sudo apt-get clean
sudo apt-get update
```

Im going by what I found here.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=contains+empty+filename&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=contains+empty+filename&sa=Search&cof=FORID:9)

[https://wiki.ubuntu.com/DebuggingInstallationIssues#files_list_file_missing_final_newline_.2BAC8_contains_empty_filename](https://wiki.ubuntu.com/DebuggingInstallationIssues#files_list_file_missing_final_newline_.2BAC8_contains_empty_filename)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=var%2Fcache%2Fapt%2Farchive&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=var%2Fcache%2Fapt%2Farchive&sa=Search&cof=FORID:9)

[https://answers.launchpad.net/ubuntu/+source/apt/+question/45974](https://answers.launchpad.net/ubuntu/+source/apt/+question/45974)

---

