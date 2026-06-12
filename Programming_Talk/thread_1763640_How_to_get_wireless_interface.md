---
title: "How to get wireless interface?"
date: 2011-05-20
forum: Programming Talk
---

### Post by hakermania on 2011-05-20
ifconfig displays a lot of information, but im making a program and I was possible to take the current interface through the command
```
airmon-ng
``` and some string editing.

Unfortunately the above command is very slow, it does approximately 2 seconds to execute and my program hangs.

Is there any secure way to take the current interface through ifconfig?
Or is the interface written somewhere specifically like the hostname does? (/etc/hostname)

Please mention that my program requires root permissions to run, so there is no problem with executing command requiring su permissions.

Thanks in advance for any replies!

---

### Post by hakermania on 2011-05-20
Well, I found my own way, but I cannot be sure that it will always work...
```

ifconfig > tmp;
a=0; 
while read line; do
a=$(expr $a + 1);
if [ $a -eq 18 ]; then
b=${line%% *};
fi;
done < tmp
rm tmp
echo "'$b'"
```This will output 'wlan0' in my case but I cannot be sure that always and in every PC the interface is being outputed in the 18th line of $(ifconfig)!!!
But if it does, then please post here that this works for you too...

---

### Post by dwhitney67 on 2011-05-20
See if the contents of /proc/net/wireless can be used.  On my two dissimilar Ubuntu systems, the third line contains the information you require.
```

Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22
  **eth1**: 0000    5.  -54.  -57.       0    159      0   2309      0        0

```
Check you system to see if in lieu of eth1, you have wlan0.

P.S.  I just checked an RHEL virtual machine that does not have a wireless interface.  There was _no_ third line in the output.

---

### Post by hakermania on 2011-05-21
the /proc/net/wireless file doesn't include the wlan0 string in my case :/
I let the pc searching for files containing the word wlan0 and nothing interesting was found :/

---

### Post by hakermania on 2011-05-22
What about the  /proc/net/dev file? My interface appears on the 3rd line.....What about yours people out there?

the /prov/net/arp says it clear, but i'm still not sure....

---

### Post by slavik on 2011-05-22
```
iwconfig 2>&1 | grep IEEE | awk '{print $1}'
```

---

### Post by hakermania on 2011-05-22
> **slavik said:**
> ```
iwconfig 2>&1 | grep IEEE | awk '{print $1}'
```
I wasn't aware of the command 'iwconfig'.
How do you guarantee that this is going to work at everybody running ubuntu-like OS and being in a laptop?

---

### Post by slavik on 2011-05-23
```

slavik@home-main:~$ dpkg -S iwconfig
wireless-tools: /usr/share/man/cs/man8/iwconfig.8.gz
wireless-tools: /usr/share/man/fr.UTF-8/man8/iwconfig.8.gz
wireless-tools: /usr/share/man/man8/iwconfig.8.gz
wireless-tools: /usr/share/man/fr.ISO8859-1/man8/iwconfig.8.gz
wireless-tools: /sbin/iwconfig
slavik@home-main:~$ apt-cache showpkg wireless-tools 
Package: wireless-tools
Versions: 
30~pre9-3ubuntu6 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
                  MD5: 34c7dc532552aa22b7a3e5860d0000e7


Reverse Depends: 
  kubuntu-desktop,wireless-tools
  broadcom-sta-source,wireless-tools
  broadcom-sta-common,wireless-tools
  atmel-firmware,wireless-tools
  xubuntu-desktop,wireless-tools
  wifi-radar,wireless-tools
  wicd-daemon,wireless-tools
  whereami,wireless-tools
  ubuntustudio-desktop,wireless-tools
  ubuntu-sugar-remix,wireless-tools
  ubuntu-chinese-desktop,wireless-tools
  network-config,wireless-tools
  lubuntu-desktop,wireless-tools
  laptop-mode-tools,wireless-tools
  kismet,wireless-tools
  brdesktop-common,wireless-tools
  aircrack-ng,wireless-tools
  ubuntu-desktop,wireless-tools
  pm-utils,wireless-tools
  pcmciautils,wireless-tools
  linux-wlan-ng,wireless-tools
  kubuntu-desktop,wireless-tools
  acpi-support,wireless-tools
Dependencies: 
30~pre9-3ubuntu6 - libc6 (2 2.7) libiw30 (2 30~pre1) 
Provides: 
30~pre9-3ubuntu6 - 
Reverse Provides: 
slavik@home-main:~$ 

```

Unless you remove (or modify) one of the -desktop packages (depends on the version of ubuntu you are using), dpkg is supposed to guarantee that it _WILL_ be there and available.

---

### Post by hakermania on 2011-05-23
I don't say that the iwconfig command won't be available but is can I take for granted that it will show the default interface on every pc?

---

### Post by slavik on 2011-05-24
there is no such thing as "the default interface"

---

### Post by hakermania on 2011-05-24
What I need is the most secure way to get the wireless interface that the system uses to connect to the internet.
You proposed a solution  that it works for me, but that's not the point. I myself have already found more than 9 ways to take this interface, but none of them is secure, because they didn't work in all situations. So, what I search for is the most secure way. So, I'm asking how do you know that your solution is the most secure way. I think you got me now..

Thx again :)

---

### Post by slavik on 2011-05-25
you are basing this solution on an assumption, which is _STUPID_ ... but!

```

DEFAULT_IFACE=$(netstat -rn | grep '^0\.0\.0\.0' | awk '{print $8}')
if [[ ${DEFAULT_IFACE} == $(iwconfig 2>&1 | grep IEEE | grep ${DEFAULT_IFACE} | awk '{print $1}' ) ]]; then
  echo ${DEFAULT_IFACE} "appears to be the default wireless interface used for all routing if there is nothing stricter defined."
fi

```

Did I mention, this solution is stupid? Take a guess why. (Hint: It has to do with what the internet really is, but you have to really understand that.)

---

### Post by slavik on 2011-05-25
you are basing this solution on an assumption, which is _STUPID_ ... but!

```

DEFAULT_IFACE=$(netstat -rn | grep '^0\.0\.0\.0' | awk '{print $8}')
if [[ ${DEFAULT_IFACE} == $(iwconfig 2>&1 | grep IEEE | grep ${DEFAULT_IFACE} | awk '{print $1}' ) ]]; then
  echo ${DEFAULT_IFACE} "appears to be the default wireless interface used for all routing if there is nothing stricter defined."
fi

```

Did I mention, this solution is stupid? Take a guess why. (Hint: It has to do with what the internet really is, but you have to really understand that.)

---

### Post by hakermania on 2011-05-25
:roll::roll::roll::roll:


Well, I don't know what to reply because I didn't get what the assumption is (I trust ubuntuforums for their solutions and you, as you are from the staff)....

And the code you posted above I am not sure it will work (because I've already tested it in several PCs and not all have an IP there, at the output of netstat -rn)

---

### Post by slavik on 2011-05-25
the internet is a giant network of computers. when you have 3 interfaces on it, they can be used to route to different subnets. if you connect to a network via VPN, you can get a ton more routes (where I work, there are like 20 subnets added), adding in that you might want end up using dns server inside the vpn, all of your traffic might end up going through there.

what do those PCs show when you run netstat -rn? can you also show output of iwconfig for those?

EDIT: You do realize that the code I posted so far was meant to give you ideas, right?

---

