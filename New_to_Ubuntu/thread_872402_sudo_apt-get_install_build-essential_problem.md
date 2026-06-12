---
title: "sudo apt-get install build-essential problem"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by scuba123 on 2008-07-27
Hello everybody,

I have a question regarding to apt-get. I ran "sudo apt-get install build-essential" and received the following messages:
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
apt-get: relocation error: /usr/lib/libapt-pkg-libc6.7-6.so.4.6: symbol _ZSt16__ostream_insertIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_PKS3_i, version GLIBCXX_3.4.9 not defined in file libstdc++.so.6 with link time reference

Do you know what they are and how to be able to run "sudo apt-get install build-essential"? Please help. Thank you.

Regards,

Scuba123

---

### Post by tamoneya on 2008-07-27
did you run sudo apt-get update before hand.  Seems like something is just out of sync.

---

### Post by scuba123 on 2008-07-28
Hello Tamoneya,

I ran this command "sudo apt-get update" before I ran" sudo apt-get install build-essential".
If now I run "sudo apt-get update", I receive the following:
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
apt-get: relocation error: apt-get: symbol _ZSt16__ostream_insertIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_PKS3_i, version GLIBCXX_3.4.9 not defined in file libstdc++.so.6 with link time reference

-------------------------------------
Actually, I installed the newest version of g++ before and it worked. However I was trying to make a program running and got some errors. According to the developer, he said that he used an older version of g++, which was 4.0.1. After that I searched around ubuntu forum and found out this link: [ftp://ftp.gnu.org/pub/gnu/gcc/](ftp://ftp.gnu.org/pub/gnu/gcc/).

I then went ahead configured and installed the older version. And I got my machine installed with g++ version 4.0.1. However due to some circumstances, I have to help debugging the program, then I installed "ddd". Once I ran it, I received this error message: 
ddd: /usr/local/lib/libstdc++.so.6: no version information available (required by ddd)
ddd: /usr/local/lib/libstdc++.so.6: no version information available (required by ddd)
ddd: Symbol `_XmStrings' has different size in shared object, consider re-linking

Since I am tired of this kind error message, I was thinking to reinstall the newest version of g++ by using "sudo apt-get install build-essential" and I got the above error messages. This is cronology of my problem. I am sorry that I didn't post the whole information in the first place.

Please help. Thank you very much.

Regards,

scuba123

---

### Post by scuba123 on 2008-07-28
Anybody? Please help. Thanks in advance.

---

### Post by eightmillion on 2008-07-28
Try this...
> sudo ln -s /usr/lib/libstdc++.so.6 /usr/local/lib/
Then try an update.

---

### Post by scuba123 on 2008-07-28
Hi Eightmillion,

Thank you for your response. I have tried with command: sudo ln -s /usr/lib/libstdc++.so.6 /usr/local/lib/ 

I received the following:
ln: creating symbolic link `/usr/local/lib/libstdc++.so.6': File exists

I still can't run "sudo apt-get update". I got the same error message listed on the previous reply. Could you let me know another approach? Thank you very much.

Regards,

scuba123

---

### Post by Joeb454 on 2008-07-28
Hmmm, not sure if it'll do anything, but it's worth trying ```
sudo apt-get install -f
``` and possibly ```
sudo dpkg --configure -a
``` to try and fix any broken packages/missing dependencies :)

---

### Post by scuba123 on 2008-07-28
Hello Joeb454,

Thanks for your response. I tried with "sudo apt-get install -f" and then "sudo dpkg --configure -a". It still gives me the same error message after I run "sudo apt-get update". The following is the error messages:

apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
apt-get: relocation error: apt-get: symbol _ZSt16__ostream_insertIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_PKS3_i, version GLIBCXX_3.4.9 not defined in file libstdc++.so.6 with link time reference
/usr/lib/apt/methods/http: relocation error: /usr/lib/libapt-pkg-libc6.7-6.so.4.6: symbol _ZSt16__ostream_insertIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_PKS3_i, version GLIBCXX_3.4.9 not defined in file libstdc++.so.6 with link time reference

Please help. Thanks in advance.

Regards,

scuba123

---

