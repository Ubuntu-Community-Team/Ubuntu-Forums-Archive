---
title: "Preferred method of running a process as a specific user at startup."
date: 2015-08-27
forum: New to Ubuntu
---

### Post by martin-lee.cusick on 2015-08-27
Being fairly new to the Linux environment, and not having local resources to inquire on, I would like to ask what is the preferred method of starting a process at startup as a specific user on a Ubuntu 12.04 system. The reasoning for such a setup is that this machine(s) will be hosting an Input/Output Controller (IOC) in an industrial setting.  If the machine fails or restarts, this process must boot automatically..... everytime.
My internet searches have provided two such area's to perform this task:

```
/etc/rc.local
```

```
/etc/init.d/
```

I ask for the specific advantages and disadvantages of each approach. I'll add that some of these machines are clients and some are servers, but all need to run an IOC, and preferably in the same manner.
Within what ever method above is deemed to be the most appropriate, a bash shell script must be run as my specified user. It is my understanding all start up process are owned by root. So I question if this is the best practice:

```
sudo -u <user> start_ioc.sh
```

If this is the case, then I believe it is required to create a file under:

```
/etc/sudoers.d/
```

Using:

```
sudo visudo -f <filename>
```

Where within this file you assign the appropriate rights and paths to the user. Most of my searches has shown this as the proper format:

```
#<user or group> <host or IP>=(<user or group to run as>)NOPASSWD:<list of comma separated applications>
root ALL=(user)NOPASSWD:/usr/bin/start_ioc.sh
```

So for final additional information, the ultimate reason for this approach, which may also be flawed logic, is that the IOC process needs to have access to a network attached server (NAS). Allowing root access to the NAS is I believe a no-no, where the user can have the appropriate permissions assigned.

---

### Post by TheFu on 2015-08-27
You cannot run any gui programs until after the user logs into a GUI.

There is not "preferred" method for what you ask. There are multiple different ways to accomplish it, depending on the task, when it should start and how it was installed, and the skills of the support people.

Basically, it seems like a simple question, but any simple answer will make 500 assumptions which may NOT be true. Best to start by learning to be a Unix power user, IMHO. That will provide some of the needed background to better select the best method for your needs.

Any process can be started as any userid. You've probably only seen root used, because it is the most common.
Do not use sudo in any startup scripts. Use **su**.
Follow scripting best practices - especially the one about fully specifying all paths to all programs used. Before login, the environment is extremely lite. Do not trust the PATH, for example.

All the sudo stuff you have above just isn't needed. During startup, everything is running under root. Root doesn't need any help to change to a different userid - definitely doesn't need sudo.

How you should start this specific program?  There are probably 50 examples in /etc/init.d/ ... follow one that is simple and uses a different userid to run stuff.  **Make certain you support start, stop, status, and restart options.** Also be certain you don't try to start it too early after a reboot sequence.  Since it is client/server, it needs to wait until networking is up -right?  Do you need network storage up first - anything else up first?  It is usually safest to make it S99 and K99 in the specific rc.d directories.  You can use **update-rc.d** to make the symlinks, or just manually create the links if you like.

Probably a good idea to read up in a book about the init processing.  Also, with 14.04 and later, the things that we've used for 40 yrs are changing thanks to systemd.  It isn't all bad, but it is a change.  12.04 only has about 18 months of support left, so deploying on 14.04 now would get you to 2019.

---

### Post by martin-lee.cusick on 2015-08-31
Thank you for your post. 

I've passed on the idea for 14.04 and it was noted and approved, barring testing for a specific DAQ hardware. Being new and clueless to this, I appreciate your honest post. I will most likely stick to what has worked for 40 years for this, but be prepared to use systemd.

I will update what is used, and how well it works when the time comes.

---

