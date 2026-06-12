---
title: "Can't create config file (/usr/local/etc/no-ip2.conf)  : Error"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by billaboy on 2012-04-21
Can't create config file (/usr/local/etc/no-ip2.conf)...


Help...

it shows the error permission denied...

why is so..??
why is that file not created...
I tried making file by my own..
it created but don't know what content it should contain..

code :
noip2 -C


Output :


Auto configuration for Linux client of no-ip.com.

Can't create config file (/usr/local/etc/no-ip2.conf)
Permission denied
Re-run noip, adding '-c configfilename' as a parameter.
akshay@akshay:~$ noip2 -i
noip2: option requires an argument -- 'i'

USAGE: noip2 [ -C [ -F][ -Y][ -U #min]
	[ -u username][ -p password][ -x progname]]
	[ -c file][ -d][ -D pid][ -i addr][ -S][ -M][ -h]

Version Linux-2.1.9
Options: -C               create configuration data
         -F               force NAT off
         -Y               select all hosts/groups
         -U minutes       set update interval
         -u username      use supplied username
         -p password      use supplied password
         -x executable    use supplied executable
         -c config_file   use alternate data path
         -d               increase debug verbosity
         -D processID     toggle debug flag for PID
         -i IPaddress     use supplied address
         -I interface     use supplied interface
         -S               show configuration data
         -M               permit multiple instances
         -K processID     terminate instance PID
         -z               activate shm dump code
         -h               help (this text)

---

### Post by bodhi.zazen on 2012-04-21
You need to use sudo

```
sudo noip2 -C
```

See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

