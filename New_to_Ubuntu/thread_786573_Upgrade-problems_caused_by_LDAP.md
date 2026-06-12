---
title: "Upgrade-problems caused by LDAP"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by ZippZapp on 2008-05-08
OS: Ubuntu Server 8.04 (Hardy Heron) /AMD64

LDAP PROBLEMS AFTER UPGRADE 7.10-->8.04
----------------------------------------

1) While (and after) upgrading to 8.04 I'm getting LDAP error messages while trying to install or upgrade many komponents:

Example: 

```
user@server:/etc/ldap$ sudo apt-get install php5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
php5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up slapd (2.4.7-6ubuntu4.1) ...
  Backing up /etc/ldap/slapd.conf in /var/backups/slapd-2.3.35-1ubuntu0.2... done.
  Upgrading BDB 'checkpoint' options... .
  Moving old database directories to /var/backups:
  Loading from /var/backups/slapd-2.3.35-1ubuntu0.2: 
  - directory dc=mynet,dc=lan... failed.

Loading the database from the LDIF dump failed with the following
error while running slapadd:
    /etc/ldap/slapd.conf: line 102: warning: no by clause(s) specified in access line.
    <access clause> ::= access to <what> [ by <who> [ <access> ] [ <control> ] ]+ 
    <what> ::= * | dn[.<dnstyle>=<DN>] [filter=<filter>] [attrs=<attrspec>]
    <attrspec> ::= <attrname> [val[/<matchingRule>][.<attrstyle>]=<value>] | <attrlist>
    <attrlist> ::= <attr> [ , <attrlist> ]
    <attr> ::= <attrname> | @<objectClass> | !<objectClass> | entry | children
    <who> ::= [ * | anonymous | users | self | dn[.<dnstyle>]=<DN> ]
        [ realanonymous | realusers | realself | realdn[.<dnstyle>]=<DN> ]
        [dnattr=<attrname>]
        [realdnattr=<attrname>]
        [group[/<objectclass>[/<attrname>]][.<style>]=<group>]
        [peername[.<peernamestyle>]=<peer>] [sockname[.<style>]=<name>]
        [domain[.<domainstyle>]=<domain>] [sockurl[.<style>]=<url>]
        [dynacl/<name>[/<options>][.<dynstyle>][=<pattern>]]
        [ssf=<n>] [transport_ssf=<n>] [tls_ssf=<n>] [sasl_ssf=<n>]
    <style> ::= exact | regex | base(Object)
    <dnstyle> ::= base(Object) | one(level) | sub(tree) | children | exact | regex
    <attrstyle> ::= exact | regex | base(Object) | one(level) | sub(tree) | children
    <peernamestyle> ::= exact | regex | ip | ipv6 | path
    <domainstyle> ::= exact | regex | base(Object) | sub(tree)
    <access> ::= [[real]self]{<level>|<priv>}
    <level> ::= none|disclose|auth|compare|search|read|{write|add|delete}|manage
    <priv> ::= {=|+|-}{0|d|x|c|s|r|{w|a|z}|m}+
    <control> ::= [ stop | continue | break ]
    dynacl:
        <name>=ACI      <pattern>=<attrname>
    
    slapadd: bad configuration file!
dpkg: error processing slapd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 slapd
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@server:/etc/ldap$ 
```

I am running SAMBA with a workgroup using Windows XP-home and Pro clients.

I have got the understanding that I should not use LDAP as long as I have XP/Home-clients, since they are not able to log into a domain. Have I got this right? (I do not have any desire to log into a domain either).  DHCP and SAMBA-shares (with security=user,  passdb backend = smbpasswd) seems to work OK.

2) Is there any reason why I shouldn't uninstall LDAP? Will uninstalling solv my problems? 

3) Any good reason for keeping LDAP? If so How do I get it work properly so it is not trashing system/software-upgrades and installations (And without excluding the XP-home-users)?


Any helpfull hints appreciated!

---

