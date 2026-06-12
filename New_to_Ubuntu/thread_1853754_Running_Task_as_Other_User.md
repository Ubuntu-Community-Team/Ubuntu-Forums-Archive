---
title: "Running Task as Other User"
date: 2011-10-02
forum: New to Ubuntu
---

### Post by CaffeineFreeless on 2011-10-02
I'm trying to automate a straightforward process that can only be done as root, so that certain regular users can do it.

I envision a single script that they run with a few arguments, and the system will take care of the rest.

What is the proper way to do this? (In terms of workflow and security) Should I have a root process polling directories, or is there some way to cause root to perform this action directly?

---

### Post by dave01945 on 2011-10-02
if you make the script with whatever commands you want in it then do these commands

```
sudo chown root scriptname
sudo chmod +x scriptname
sudo chmod u+s scriptname
```

the first command will set the scripts owner to root
the second will make it executable to everyone
and the third will add a setuid bit that means whoever starts the script it will run as root

--EDIT--

ignore that just found out the setuid bit doesn't work on shell scripts only binaries so that won't work unless you can right it in C

---

### Post by bodhi.zazen on 2011-10-02
> **dave01945 said:**
> and the third will add a setuid bit that means whoever starts the script it will run as root

--EDIT--

ignore that just found out the setuid bit doesn't work on shell scripts only binaries so that won't work unless you can right it in C

The preferred method is to simply call the script with sudo. You can configure sudo if needed to run the script without needing to enter a password.

---

