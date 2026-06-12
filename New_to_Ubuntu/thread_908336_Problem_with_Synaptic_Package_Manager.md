---
title: "Problem with Synaptic Package Manager"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by Slayeragb2 on 2008-09-02
Right, so in my Word Processing Class at school, I opened up my laptop and started looking around the site for anything that I might want for programming. After finding something, I opened up Synaptic Package Manger, when it gave me this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache-> open() failed, please report.

So, I went into the terminal and ran what it said, but it said I have to have superuser privileges.

How do I fix this problem?

---

### Post by LesFromWaldenVT on 2008-09-02
You could try using sudo:

sudo dpkg --configure -a

it will ask for the password. Give it your normal password and it should work.

Les

---

### Post by Slayeragb2 on 2008-09-02
Thanks, I have only had Ubuntu for about a month now, and the only time I get to get on the computer right now is at school.
What does the sudo command do?

---

### Post by Elfy on 2008-09-02
What you need to remember is that all of these things affect the system andd need to have superuser priveleges; I believe that it arises from the fact that on other distros you would be doing these tasks as root. So in consequence the warnings assume that you are already root and don't say that you need to have superuser privelege.

If and when you find yourself needing to do things in a root prompt in recovery mode you don't need to use sudo and dpkg --configure -a would work.

Sudo gives a command root rights, the first user is setup as such during installaton.

---

### Post by lapubell on 2008-09-02
sudo stands for Super User DO and then whatever command.  As linux is a multi user operating system, many of your day to day tasks do not need high level permissions to run.  This is one of the big differences between the Linux Super User and the Windows Adminsitrator.

When you are an administrator in Windows, you run all your software as that user, so if you get some spyware or virus when browsing the web as an Administrator, it can corrupt the whole system.  When browsing the web in Linux, you usually are doing this as your normal user, which doesn't have Super User permissions.  This way you can't accidently kill off your system.  So be careful using the sudo command, because you really can change ANYTHING on your computer with that command.

---

### Post by Camilia on 2008-09-07
Great thread!! I got the same response after halting download of acid lab.

---

