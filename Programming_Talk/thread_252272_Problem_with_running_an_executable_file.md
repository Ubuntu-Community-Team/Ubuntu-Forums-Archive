---
title: "Problem with running an executable file"
date: 2006-09-06
forum: Programming Talk
---

### Post by sshahir on 2006-09-06
I am new in Linux environment, and I am trying to compile and run C programs through gcc compiler, and I face a problem with running an executable output file. 

I have compiled a very simple &#8220;C program&#8221; by using &#8220;gcc HelloWorld.c -o test.out&#8221; 

The result is an executable file &#8220;test.out&#8221;, but when I try to execute the file, I cannot.

>test.out <enter>

I appreciate for any comment regarding How to run the executable file. 

Thanks,
Shahed

---

### Post by cstudent on 2006-09-06
./test.out

---

### Post by croak77 on 2006-09-06
Or copy to /usr/bin or /usr/local/bin

---

### Post by sshahir on 2006-09-06
I got it. Thanks a lot.

Regards,
Shahed

---

### Post by ifokkema on 2006-09-07
The reason for this is that the current directory you're in, is not in the PATH environment variable.

Also, I recommend you don't put your files in /usr/bin, but in ~/bin, unless they're meant for general usage among more than one user. You can add ~/bin to your path by editing your ~/.bash_profile or ~/.bashrc. ~/.bash_profile has it preconfigured, you just need to uncomment it.

---

