---
title: "Add a Host File"
date: 2013-10-11
forum: New to Ubuntu
---

### Post by Stephen_Revere on 2013-10-11
I'm being told that I need to add a host file. The host file is [COLOR=#1F497D][FONT=Calibri]199.XXX.XXX.22  [/FONT][/COLOR][build-www.10mag.com]("http://build-www.10mag.com/"). They're giving me instructions for WPC and Mac. How do I do that in Ubuntu?

---

### Post by Stephen_Revere on 2013-10-11
This is what I've tried so far, and it didn't work:

steve@steve-Inspiron-3421:~$ sudo hostname 199.XXX.XXX.40 build-www.10mag.com
[sudo] password for steve: 
Usage: hostname [-v] [-b] {hostname|-F file}         set host name (from file)
       hostname [-v] [-d|-f|-s|-a|-i|-y|-A|-I]             display formatted name
       hostname [-v]                                 display host name


       {yp,nis,}domainname [-v] {nisdomain|-F file}  set NIS domain name (from file)
       {yp,nis,}domainname [-v]                      display NIS domain name


       dnsdomainname [-v]                            display dns domain name


       hostname -V|--version|-h|--help               print info and exit


Program name:
       {yp,nis,}domainname=hostname -y
       dnsdomainname=hostname -d


Program options:
    -s, --short            short host name
    -a, --alias            alias names
    -i, --ip-address       addresses for the host name
    -I, --all-ip-addresses all addresses for the host
    -f, --fqdn, --long     long host name (FQDN)
    -A, --all-fqdns        all long host names (FQDNs)
    -d, --domain           DNS domain name
    -y, --yp, --nis        NIS/YP domain name
    -b, --boot             set default hostname if none available
    -F, --file             read host name or NIS domain name from given file


Description:
   This command can get or set the host name or the NIS domain name. You can
   also get the DNS domain or the FQDN (fully qualified domain name).
   Unless you are using bind or NIS for host lookups you can change the
   FQDN (Fully Qualified Domain Name) and the DNS domain name (which is
   part of the FQDN) in the /etc/hosts file.

---

### Post by steeldriver on 2013-10-11
Told by whom? what are you trying to do exactly?

---

### Post by vasa1 on 2013-10-11
> **steeldriver said:**
> Told by whom? what are you trying to do exactly?
My suspicion is that this is some sort of advertising for the site mentioned.

---

### Post by JKyleOKC on 2013-10-11
You already have a "hosts" file, at /etc/hosts. This file provides translation between URL names and IP address numbers and is created automatically when you install the system. Its purpose is to add translations for addresses that are not included in the public DNS system, such as "localhost." You can add more entries to it but must use a command such as "gksudo gedit /etc/hosts" to do so since it's a protected system file. However be very cautious about doing so, since this is a very simple way of allowing malware into your system if you don't know exactly what's at the IP address being added!

---

### Post by Stephen_Revere on 2013-10-11
We're building a new site and they tell me I need to do this to view the site.

---

### Post by Stephen_Revere on 2013-10-11
> **JKyleOKC said:**
> You already have a "hosts" file, at /etc/hosts. This file provides translation between URL names and IP address numbers and is created automatically when you install the system. Its purpose is to add translations for addresses that are not included in the public DNS system, such as "localhost." You can add more entries to it but must use a command such as "gksudo gedit /etc/hosts" to do so since it's a protected system file. However be very cautious about doing so, since this is a very simple way of allowing malware into your system if you don't know exactly what's at the IP address being added!

That's it! Thanks for the coaching Jim. I added the host file and we're good to go. Much appreciated.

---

### Post by JKyleOKC on 2013-10-13
You're quite welcome! Glad to help out. Mark the thread as "SOLVED" as shown by the link in my sig below, please.

---

