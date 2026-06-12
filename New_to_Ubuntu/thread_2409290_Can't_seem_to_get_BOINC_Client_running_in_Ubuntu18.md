---
title: "Can't seem to get BOINC Client running in Ubuntu18.04"
date: 2018-12-31
forum: New to Ubuntu
---

### Post by taurus5482 on 2018-12-31
I have used the package supplied by Synaptic manager. Boinc Manager runs OK, but I have to start BOINC Client in a terminal and it comes up with 

john@RanchodL:~/Downloads/BOINC$ ./run_client ./boinc: /usr/lib/x86_64-linux-gnu/libcurl.so.4: version `CURL_OPENSSL_3' not found (required by ./boinc)
Can any one help?

Just like to run BOINC!

---

### Post by clementc on 2019-01-01
Hi [**[COLOR=#000000]taurus5482[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115185"),

It looks like your system is missing curl, please try installing libcurl3 using the following command in Terminal:

sudo apt-get install libcurl3

Please report back if this has helped resolve your issue.

---

