---
title: "Terminal authentication failure"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by brodiesel on 2008-10-29
So, I'm trying to install this package, and I'm told to go to terminal and input su, where i am prompted for a password. I know my password (I login every day) but every time i type it in, i am told that i have an "authentication failure."

any ideas?

---

### Post by wolfen69 on 2008-10-29
you need to type sudo instead. or sudo su.

---

### Post by brodiesel on 2008-10-29
i tried that and got this:

usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
b@b-laptop:~$ 

which to my command line retarded brain leaves me where i was.

?

---

### Post by wolfen69 on 2008-10-29
did you try sudo su?

---

### Post by brodiesel on 2008-10-29
now i'm even more confused. i tried 'sudo us' and first it said "enter password' and then before i could enter the password it switched to say command not found, and at that point i couldnt get it back to where it asked for my passowrd. here's how it looked:

b@b-laptop:~$ sudo us
[sudo] password for b: 
sudo: us: command not found
b@b-laptop:~$ sudo us
sudo: us: command not found


???

---

### Post by wolfen69 on 2008-10-29
sudo *su* **not** sudo *us*

---

### Post by jerome1232 on 2008-10-29
Ubuntu uses sudo (Super User do) to give a user temporary root privilages, generally you just preface your commands with sudo instead of using 'su' (Switch User) to switch to the root account.

The root account is locked by default in Ubuntu.

ie guide says:
su
apt-get install joespackage

you would do
sudo apt-get install joespackage

You can also use sudo -i to gain a root shell similar to using su.

---

### Post by brodiesel on 2008-10-29
This is making more sense, but not actually getting me close to my goal of installing java. Thanks for the helps, anyway. I was curious what the whole sudo thing meant anyway. I'll start a new thread for the java question.

---

### Post by AndyCooll on 2008-10-29
As I've mentioned in your other thread, you can install Java straight from the repos (System > Administration > Synaptic Package Manager). Then do a search for Java and choose either the OpenJDK version or the Sun version.

:cool:

---

