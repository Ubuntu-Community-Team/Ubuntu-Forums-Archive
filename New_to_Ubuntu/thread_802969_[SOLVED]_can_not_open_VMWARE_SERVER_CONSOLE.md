---
title: "[SOLVED] can not open VMWARE SERVER CONSOLE"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by rraj.be on 2008-05-21
I cant open vmware server console.

when i start it using my menu in task bar its displaying "starting vmware server console" and after few seconds it disappears and nothing happens.

what may be the problem

---

### Post by lazyart on 2008-05-21
What has changed since the last time you ran it?

Open up the console and type```
vmware
```.  The output there should give you a clue.

---

### Post by rraj.be on 2008-05-21
i have not yet started. this is the first attempt to start.

---

### Post by decoherence on 2008-05-21
Go to the menu Applications -> Accessories -> Terminal

There type 'vmware' (without quotes)

Copy/paste the results here or do a Google search on them.

Perhaps this thread will be helpful?

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

---

### Post by thewho? on 2008-05-21
You should be going to the terminal and typing this command:

vmware-server-console

It will leave the output in that terminal which will almost definetly show the error.  Did you compile it yourself, or did you use a package?

---

### Post by rraj.be on 2008-05-21
this is the result that i got when i typed vmware in terminal

```
raj@raj-dworkstation:~$ vmware-server-console
bash: vmware-server-console: command not found
raj@raj-dworkstation:~$ vmware               
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
```

---

### Post by decoherence on 2008-05-21
I'm only guessing here, but try putting this in the terminal.

```
sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0
```

You will be asked for your password the first time. Type it and press Enter -- it won't show anything on the screen.

These commands are from the link in my previous post. I had to do this to get VMWare working on my machine.

---

### Post by rraj.be on 2008-05-21
its displaying 

```
raj@raj-dworkstation:~$ sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1
cp: cannot create regular file `/usr/lib/vmware/lib/libgcc_s.so.1': No such file or directory

```

---

### Post by rraj.be on 2008-05-22
the required library are 

```
libcairo and libstdc++
```

---

### Post by decoherence on 2008-05-22
> **rraj.be said:**
> its displaying 

```
raj@raj-dworkstation:~$ sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1
cp: cannot create regular file `/usr/lib/vmware/lib/libgcc_s.so.1': No such file or directory

```

perhaps
```
sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware-server/lib/libgcc_s.so.1
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware-server/lib/libpng12.so.0
```

---

### Post by rraj.be on 2008-05-22
It worked.

But could you tell me whats the actual problem that caused this error.

please..

---

### Post by decoherence on 2008-05-23
glad it worked. this error, like many (most?) errors in the linux world, was caused by the program looking for a file in the wrong place. the commands you used copied the files to the expected place.

---

### Post by bey on 2009-10-27
Hi,

I have the same problem on Ubuntu 9.04 while opening VMware server console. The above solution didn't fix the problem. Any other solution?

Thanks,
Ben

---

