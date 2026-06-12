---
title: "Help with distcc not connecting to helpers"
date: 2011-05-02
forum: Packaging and Compiling Programs
---

### Post by Helios747 on 2011-05-02
Hello, I'm using Ubuntu 11.04 64 bit (dual core) and was setting up distcc on it to connect to my server running Ubuntu 10.10 server 64 bit (triple-core)

Both systems are using distcc from the repos.

Both systems are using GCC/G++ 4.4 and distcc has been configured to use those versions.

in the distcc hosts list each machine has the other machine's IP address in the list.

This is the distcc manager (that the right phrase? The machine that's sending off the jobs) config file

```
  GNU nano 2.2.6                                     File: /etc/default/distcc                                                                                

# Defaults for distcc initscript
# sourced by /etc/init.d/distcc

#
# should distcc be started on boot?
#
# STARTDISTCC="true"

STARTDISTCC="true"

#
# Which networks/hosts should be allowed to connect to the daemon?
# You can list multiple hosts/networks separated by spaces.
# Networks have to be in CIDR notation, f.e. 192.168.1.0/24
# Hosts are represented by a single IP Adress
#
# ALLOWEDNETS="127.0.0.1"

ALLOWEDNETS="192.168.2.0/24"

#
# Which interface should distccd listen on?
# You can specify a single interface, identified by it's IP address, here.
#
# LISTENER="127.0.0.1"

LISTENER="192.168.2.10"

#
# You can specify a (positive) nice level for the distcc process here
#
# NICE="10"

NICE="10"

#
# You can specify a maximum number of jobs, the server will accept concurrently
#
# JOBS=""

JOBS="2"

#
# Enable Zeroconf support?
# If enabled, distccd will register via mDNS/DNS-SD.
# It can then automatically be found by zeroconf enabled distcc clients
# without the need of a manually configured host list.
#
# ZEROCONF="true"

ZEROCONF="false"

```the distcc starter's IP is 192.168.2.10

the distcc helper's IP is 192.168.2.5

but whatever I 'make CC='distcc' CCXX='distcc'' anything I get

```
distcc[2499] (dcc_build_somewhere) Warning: failed to distribute, running locally instead
```
I double checked that each system has distccd running via init.d.


Help!

---

### Post by stefanadelbert on 2011-05-29
I'm having a similar problem. I'm running a build on my laptop (192.168.100.103) and I'm expecting distcc to include my mediacentre machine (192.168.100.11) in a distributed build. 

Both machines are running latest repo distcc:

```
~/.distcc$ distcc --version
distcc 3.1 x86_64-pc-linux-gnu
  (protocols 1, 2 and 3) (default port 3632)
  built Apr 19 2011 15:03:23
```

Both machines have the same config file /etc/default/distcc:

```
STARTDISTCC="true"
ALLOWEDNETS="192.168.100.0/24"
LISTENER="127.0.0.1"
NICE="10"
JOBS=""
ZEROCONF="true"
```

/etc/distcc/hosts on the laptop (client) looks like this:

```
+zeroconf
```

Distcc knows about both the client and the server. From the client:

```
~/.distcc/zeroconf$ distcc --show-hosts
192.168.100.11:3632/8
192.168.100.103:3632/8

```

Avahi sees the server machine:

```
~/.distcc/zeroconf$ avahi-browse _distcc._tcp -rtkv
Server version: avahi 0.6.30; Host name: stefan-laptop.local
E Ifce Prot Name                                          Type                 Domain
+   eth0 IPv4 distcc@mediacentre                            _distcc._tcp         local
=   eth0 IPv4 distcc@mediacentre                            _distcc._tcp         local
   hostname = [mediacentre.local]
   address = [192.168.100.11]
   port = [3632]
   txt = ["cc_machine=x86_64-linux-gnu" "cc_version=4.5.2" "gnuhost=x86_64-pc-linux-gnu" "distcc=3.1" "cpus=2" "txtvers=1"]
: Cache exhausted
: All for now

```

Both machines are very similar - 64bit, gcc 4.5.2, same distcc.

When I run a build, I get these error messages in the log file:

```
distcc[7405] (dcc_parse_hosts) Warning: /home/stefan/.distcc/zeroconf/hosts contained no hosts; can't distribute work
distcc[7405] (dcc_zeroconf_add_hosts) CRITICAL! failed to parse host file.
distcc[7405] (dcc_build_somewhere) Warning: failed to distribute, running locally instead
```

This is what the generated hosts file (/home/stefan/.distcc/zeroconf/hosts) looks like:

```
192.168.100.11:3632/8
```

I have specifically turned off ipv6 in the avahi-daemon.conf to avoid a similar error I was getting earlier.

If I run the build and monitor it with distccmon-gnome only the localhost jobs run, the others show as blocked.

Any hints?

---

### Post by Helios747 on 2011-05-30
Hi,

Heh, I forgot to say that I solved the problem. This might help others too.

It seems that there's some bug with distcc/avahi that causes this problem.

Take out "+zeroconf" out of the global hosts file (/etc/distcc/hosts) and things should work as expected.

---

### Post by stefanadelbert on 2011-05-30
Nice! I'll give this a go once I'm home this evening.

I suppose that it's a good idea to disable zeroconf on all servers too, i.e.

[/etc/default/distcc]
```
ZEROCONF="false"
```

This should make sure that distccd is NOT started on the servers with the "--zerconf" command line parameter.

Any other tips while we're on the topic?

---

### Post by Helios747 on 2011-05-30
Probably wouldn't hurt. :)


A little tip I picked up off of another site

you can see proof that distcc is shooting off jobs by using this command

```
netstat -n 1 | grep ip.of.helper.computer

```

and make sure you're setting the -j (job) flag in make so you're actually running more than one job! heh. you probably already know that though. -j should equal the number of cores working on the compile + 1, right?

---

### Post by stefanadelbert on 2011-05-31
> **Helios747 said:**
> -j should equal the number of cores working on the compile + 1, right?

That's right, as far as I know.

Unfortunately I'm still getting the job attempts blocked and the jobs are just being run locally, even after disabling zeroconf on the server and removing "+zerconf" from /etc/distcc/hosts.

Things are looking good in the log file though - I'm not seeing errors. But distccmon-gnome shows "Blocked". I'll keep going and see what I find.

---

### Post by Helios747 on 2011-05-31
Are you using ufw/firestarter?

Do you have iptables configured?

What does that netstat command in my previous post show?

---

