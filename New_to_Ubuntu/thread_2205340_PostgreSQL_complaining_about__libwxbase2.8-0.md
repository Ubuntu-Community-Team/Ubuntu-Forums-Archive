---
title: "PostgreSQL complaining about  libwxbase2.8-0"
date: 2014-02-13
forum: New to Ubuntu
---

### Post by robertzito on 2014-02-13
I am at a loss here!! I attempted to upgrade my  PostgreSQL 9.1.11 on x86_64-unknown-linux-gnu, I did everything step by step from postgreswiki ([https://wiki.postgresql.org/wiki/Apt](https://wiki.postgresql.org/wiki/Apt)). When I attempt to run sudo apt-get install postgresql-9.3 pgadmin3 I get the error below. When I look at my package manage it shows that both postgres 9.1 and 9.3 are installed. But when I select the version from postgresql it still comes back 9.1. Now postgres does not show a repository for saucy so I used trusty. Also I know libwxbase2.8-0 is installed...

Is the msg below telling me that I need a lib from trusty?
Why does my package manger show both postgresql 9.1 & 9.3 installed?

Sorry for all the questions and appreciate the assistance!!!

pgadmin3 : 
Depends: libwxbase2.8-0 (>= 2.8.12.1+dfsg) but 2.8.12.1-14ubuntu1.1 is to be installed
Depends: libwxgtk2.8-0 (>= 2.8.12.1+dfsg) but 2.8.12.1-14ubuntu1.1 is to be installed

---

### Post by robertzito on 2014-02-13
Here is the entire msg I get, I gave up unless someone knows some sort of trick, man what a pain in the a@@, it says below that 9.3 is installed but Select version has it @ PostgreSQL 9.1.11 on x86_64-unknown-linux-gnu, compiled by gcc (Ubuntu/Linaro 4.8.2-12ubuntu2) 4.8.2, 64-bit

 

sudo apt-get install postgresql-9.3 pgadmin3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
postgresql-9.3 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 pgadmin3 : Depends: libwxbase2.8-0 (>= 2.8.12.1+dfsg) but 2.8.12.1-14ubuntu1.1 is to be installed
            Depends: libwxgtk2.8-0 (>= 2.8.12.1+dfsg) but 2.8.12.1-14ubuntu1.1 is to be installed
            Recommends: pgagent but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

And if I attempt to put back pgadmin from the the Software Center I now get:

The following packages have unmet dependencies:


pgadmin3: Depends: pgadmin3-data (= 1.18.1-2~11.git0747a08.pgdg14.04+1) but 1.18.1-2~11.git0747a08.pgdg14.04+1 is to be installed
          Depends: libc6 (>= 2.14) but 2.17-93ubuntu4 is to be installed
          Depends: libgcc1 (>= 1:4.1.1) but 1:4.8.1-10ubuntu9 is to be installed
          Depends: libpq5 (>= 8.4~) but 9.3.2-2~195.bzr436.pgdg14.04+1 is to be installed
          Depends: libstdc++6 (>= 4.4.0) but 4.8.1-10ubuntu9 is to be installed
          Depends: libwxbase2.8-0 (>= 2.8.12.1+dfsg) but 2.8.12.1-14ubuntu1.1 is to be installed
          Depends: libwxgtk2.8-0 (>= 2.8.12.1+dfsg) but 2.8.12.1-14ubuntu1.1 is to be installed
          Depends: libxml2 (>= 2.7.4) but 2.9.1+dfsg1-3ubuntu2 is to be installed
          Depends: zlib1g (>= 1:1.1.4) but 1:1.2.8.dfsg-1ubuntu1 is to be installed

---

### Post by SeijiSensei on 2014-02-13
I'm guessing you tried to install 9.3 from a third-party repository like PGDG?

What you are seeing are version conflicts in the required libraries.

If it were me, and I really wanted 9.3, I'd compile it from [source]("http://www.postgresql.org/ftp/source/v9.3.2/").  That way you know everything will hang together properly.

Unless there are specific features in 9.3 that you need to use, there is no reason to upgrade.  Upgrading just because a new version is available rather undermines the notion of controlled repositories with reviewed software.  This is especially true for server software like PostgreSQL where stability is more important than freshness.  Just for comparison, the current version of PostgreSQL shipping with RedHat/CentOS machines is 8.4.  All major distribution providers "backport" security fixes into their supported versions, so you needn't worry about having some security hole from an earlier version.

---

### Post by robertzito on 2014-02-13
I want to use to_json feature in 9.2 and greater, do I have to remove everything like 9.1 and 9.3 and start from scratch?

---

### Post by SeijiSensei on 2014-02-13
That would be my suggestion unless you take the compile-it-yourself route.  Then everything will be installed under /usr/local/pgsql and can be run independently alongside the current server.

In this case, I'd edit postgresql.conf to bind the new server to a different TCP port, say 55432.  Then you can have both the current and the new server running on the same machine while you test things out.

---

### Post by SeijiSensei on 2014-02-13
I discovered tonight when I install Postgres on my Ubuntu 14.04 desktop that it comes with PG 9.3.2.  The official release of 14.04 won't happen until April, but then it will become the new LTS version.

If this is a production machine that needs to be stable and reliable, then I wouldn't suggest this approach.  But if it's just to work on some stuff in development, you could give 14.04 a try.  If you don't have a machine available, consider installing [VirtualBox]("http://www.virtualbox.org/") on a desktop machine, then creating a virtual machine and installing the [14.04 server version]("http://cdimage.ubuntu.com/ubuntu-server/daily/current/").

---

