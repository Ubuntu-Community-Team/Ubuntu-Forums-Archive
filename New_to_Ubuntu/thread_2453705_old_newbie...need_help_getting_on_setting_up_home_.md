---
title: "old newbie...need help getting on setting up home network"
date: 2020-11-15
forum: New to Ubuntu
---

### Post by Seadevil on 2020-11-15
I have two desktop computers:  PRIMARY AND SECONDARY. i am on primary and just installed Lubuntu 19. I am having problem accessing my home network and secondary computer.

i followed the instructions for setting up Samba and got to the end where he says:

> To access your network share

```
      sudo apt-get install smbclient
      # List all shares:
      smbclient -L //<HOST_IP_OR_NAME>/<folder_name> -U <user>
      # connect:
      smbclient //<HOST_IP_OR_NAME>/<folder_name> -U <user>
```

To access your network share use your username (<user_name>) and password through the path "smb://<HOST_IP_OR_NAME>/<folder_name>/" (Linux users) or "\\<HOST_IP_OR_NAME>\<folder_name>\" (Windows users). Note that "<folder_name>" value is passed in "[<folder_name>]", in other words, the share name you entered in "/etc/samba/smb.conf".

my secondary computer has Windows 7.  the path to my wife's desktop is \\Secondary\Users\Vickie\Desktop

when i enter it, i get this error message:   

```
\SECONDARYSecondary: Not enough '\' characters in service
Usage: smbclient [-?EgqBVNkPeC] [-?|--help] [--usage]
        [-R|--name-resolve=NAME-RESOLVE-ORDER] [-M|--message=HOST]
        [-I|--ip-address=IP] [-E|--stderr] [-L|--list=HOST]
        [-m|--max-protocol=LEVEL] [-T|--tar=<c|x>IXFqgbNan]
        [-D|--directory=DIR] [-c|--command=STRING] [-b|--send-buffer=BYTES]
        [-t|--timeout=SECONDS] [-p|--port=PORT] [-g|--grepable] [-q|--quiet]
        [-B|--browse] [-d|--debuglevel=DEBUGLEVEL]
        [-s|--configfile=CONFIGFILE] [-l|--log-basename=LOGFILEBASE]
        [-V|--version] [--option=name=value]
        [-O|--socket-options=SOCKETOPTIONS] [-n|--netbiosname=NETBIOSNAME]
        [-W|--workgroup=WORKGROUP] [-i|--scope=SCOPE] [-U|--user=USERNAME]
        [-N|--no-pass] [-k|--kerberos] [-A|--authentication-file=FILE]
        [-S|--signing=on|off|required] [-P|--machine-pass] [-e|--encrypt]
        [-C|--use-ccache] [--pw-nt-hash] service <password>
```

don't know what this wants or  what i should enter.

would appreciate some help.

thanks

---

### Post by TheFu on 2020-11-15
all ubuntu 19.xx versions are out of support and should not be used.  20.04 is the current LTS. New installs should load that release.
[https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)

Connecting win7 will be harder and harder as microsoft pushes for or secure defaults. They did that earlier this year.  The samba project similarly changed some defaults to improve security.

step 1 - load a supported verson of ubuntu.

 \\Secondary\Users\Vickie\Desktop --->  use forward / characters instead.

---

### Post by Seadevil on 2020-11-15
oh, my bad...i  installed Lubuntu 20.04

---

