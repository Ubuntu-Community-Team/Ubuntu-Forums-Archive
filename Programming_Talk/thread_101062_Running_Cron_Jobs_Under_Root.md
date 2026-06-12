---
title: "Running Cron Jobs Under Root"
date: 2005-12-09
forum: Programming Talk
---

### Post by capi on 2005-12-09
I'm writing a bash script that will download and compile the latest snapshot of a program I'm working on. Now, it's a fairly simple script, but I have two questions on it. First I'd like to make it a cron job that executes at say midnight. My problem is I'm not sure how to get it to run under root(so it can compile), would giving it root permisions do that? Second, I'm using checkinstall when I'm building it, and it comes up with a prompt asking y or n. How do I respond to that in a bash script? just write a line after it with a y? Heres a pseudo-version of the script.

```

wget <url>
cd <pak>
./configure
make
checkinstall -D make install
y

```

I don't know how well that will run, and I probably need to mess with the wget line so the script knows where to cd to(can you even cd in a bash script?). Sorry I'm sounding like an idiot. I can probably figure out the rest of it, but the first two have me a little confused.

---

### Post by amohanty on 2005-12-09
Heres my suggestion:

1. Create a dummy user, with shell /bin/false (i think thats what nologin is in Ubuntu)
2. login as that user:
> su - <username>
3. Put it into that users crontab
> crontab -e
4. Setup sudo so that the user can only run checkinstall as su and to run checkinstall it will not require a password. I dont remember the sudoers syntax offhand so cant tell you, but its in the manual.

Also you dont need to cd to remember old folders, Look at the following commands:
> 
pushd
popd

HTH

---

### Post by cwaldbieser on 2005-12-09
[QUOTE=capi]I'm writing a bash script that will download and compile the latest snapshot of a program I'm working on. Now, it's a fairly simple script, but I have two questions on it. First I'd like to make it a cron job that executes at say midnight. My problem is I'm not sure how to get it to run under root(so it can compile), would giving it root permisions do that? Second, I'm using checkinstall when I'm building it, and it comes up with a prompt asking y or n. How do I respond to that in a bash script? just write a line after it with a y? Heres a pseudo-version of the script.

```

wget <url>
cd <pak>
./configure
make
checkinstall -D make install
y

```

I don't know how well that will run, and I probably need to mess with the wget line so the script knows where to cd to(can you even cd in a bash script?). Sorry I'm sounding like an idiot. I can probably figure out the rest of it, but the first two have me a little confused.[/QUOTE]

For the y/n part, I think you can just pipe the output of the "yes" command to the checkinstall command:
```

yes | checkinstall -D make install

```

---

