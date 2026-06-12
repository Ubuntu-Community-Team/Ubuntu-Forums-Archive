---
title: "How can I get all the debs from a repository"
date: 2021-04-09
forum: New to Ubuntu
---

### Post by ryanclaw on 2021-04-09
Hello guys,

Pretty new user here. I'm working on a project where I wanted to understand more about it but will run it from here just in case somebody already got a crack on it. I wanted to have a local repository in our environment due to bandwidth restrictions. Now I'm reading some howto online but not quite exactly what we wanted to achieve

End goal will be the following 
1. Have a local repository rsynced from official ubuntu repo BUT only ubuntu bionic, bionic-updates, bionic-backsports will be pulled down also synced nightly
2. In the repo I wanted to exclude irrelevant packages e.g. gnome, kde, x11 for the local repository to be leaner, cleaner - also space saver
3. I wanted to use rsync  for this one 

any suggestion will be greatly appreaciated

---

### Post by TheFu on 2021-04-09
It is unlikely that any site would need ALL the packages in a repo and all the updates daily.
Might I strongly suggest using **apt-cacher-ng** instead?  This way, only actually requested packages get pulled and once they are local, they won't be pulled over the internet unless there is an update. [https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)
I've been using this for about a decade.  It is for all Debian-based systems.  Across about 20 systems where, we only use about 4G in our apt-cacher-ng cache. Very efficient and nearly runs itself, including periodic maintenance.

If you want to be a mirror, there are tools for that.  Many Universities with computer/EE departments will have a mirror.  I've never looked into it.

---

### Post by ActionParsnip on 2021-04-09
+1 for apt cacher. Especially if you are running lots of Ubuntu systems on a network. Saves them all calling out to the Web for updates. Also makes minimal ISO installs very appealing as it can install over the LAN very quickly

---

### Post by ryanclaw on 2021-04-09
@TheFU

apt-cacher-ng actually make sense we only have about 30 systems running on Bionic and several Xenial - I haven't dig into the link but I'm guessing with your experience using this - it works like all of your endpoint got sources.list (official) and pass through apt-cacher-ng and cache it for the rest of the machine this is a neat feature. Will it also cache non official repo e.g. ppa repo? I think though you can't pinned versions - if newer version is available from the sources the endpoint it will get newer packages and apt-cacher-ng will update it's cache alongside dropping older packages?

---

### Post by ryanclaw on 2021-04-09
@ActionParsnip

Thank you - also thinking how can I utilize it with staging - production instances. like I wanted to update all staging machines at certain time - after baking the applied updates for couple of weeks and good I will move it to  production to update.

---

### Post by TheFu on 2021-04-09
> **ryanclaw said:**
> @TheFU

apt-cacher-ng actually make sense we only have about 30 systems running on Bionic and several Xenial - I haven't dig into the link but I'm guessing with your experience using this - it works like all of your endpoint got sources.list (official) and pass through apt-cacher-ng and cache it for the rest of the machine this is a neat feature. Will it also cache non official repo e.g. ppa repo? I think though you can't pinned versions - if newer version is available from the sources the endpoint it will get newer packages and apt-cacher-ng will update it's cache alongside dropping older packages?

Support for 16.04 ends this month, so move off that ASAP!  Or pay Canonical for ESM for each of those systems.
There is 1 line added to each client node APT config. /etc/apt/apt.conf.d/02proxy
```
Acquire::http { Proxy "http://istar:3142"; };
```

As more and more repos move to HTTPS, there's a small config change needs on the apt-cacher-ng to proxy https stuff too. How strict that is is up to your regex-fu.

PPA or any repo doesn't matter.

pinning is still handled on each client using apt-mark.
Don't ask me how it knows when to remove out of date packages, but it does. Perhaps it looks at atime? There are many config options. A few MB doesn't matter to me.  People running in a completely air-gapped environment would need a different solution. I think the package update task still hits the real repos/PPAs from each machine.  Maybe there's a way to have apt-cacher-ng cache that daily too, but I don't know.

---

### Post by ActionParsnip on 2021-04-10
Ah the apt cacher doesn't manage the updates or which servers update etc. I'd use ansible for that. You could have a script for updating all dev boxes that runs apt update apt upgrade on certain hosts, or, if you want to be lazy just put the root SSH key from your central server on every server and use a bash loop to run the commands. Same deal. Something like
```

for i in `cat /opt/evservers.txt` do; ssh root@$I /usr/bin/fullupgrade; done

```
Or something like that. I'm sure there is a prettier way but something like that will fly. 
You get the idea

---

### Post by TheFu on 2021-04-10
> **ActionParsnip said:**
> Ah the apt cacher doesn't manage the updates or which servers update etc. I'd use ansible for that. You could have a script for updating all dev boxes that runs apt update apt upgrade on certain hosts, or, if you want to be lazy just put the root SSH key from your central server on every server and use a bash loop to run the commands. Same deal. Something like
```

for i in `cat /opt/evservers.txt` do; ssh root@$I /usr/bin/fullupgrade; done

```
Or something like that. I'm sure there is a prettier way but something like that will fly. 
You get the idea

Don't use root.  Remote root isn't a good idea.

Setup a random "deploy" userid and have it in the sudoers with the ability to run apt-get commands without any password needed. Of course, lock down where that deploy4028 userid can ssh in from on all the client machines.  This will be needed for ansible too.  

Plus, it is handy to have a script that shuts down systems only if they need to be rebooted, but in the correct order, to minimize apparent downtime to the external clients.

---

### Post by ActionParsnip on 2021-04-10
Lots of options but yeah. You get the idea.

---

### Post by ryanclaw on 2021-04-12
@TheFu @ActionParship

Thanks so much for your input. Just a quick update on my progress was that I have install reprepro and did all of those signing keys shebang. so the plan now

1. I have rsynced the whole repor /ubuntu/pool and just the "pool" directory and exclude the rest
2. I have a cron job just to rsync the /ubuntu/pool everyday just so I can repo is updated if anything new from my source
3. I'm creating/researching on a script that will
a. find *.deb from ubuntu/pool > to a file
b. results from the above will be feed to reprepro
c. reprepro will sign all of the deb and added it to its DB
4. Client will only have on sources.list entry which is my reprepro machine
5. I will take a look for the apt mark for pinning
6. Thinking of client to use something like unattended-upgrade - again still in reading mode

Thanks

---

