---
title: "HOWTO: Automatically block SSHD/PROFTPD Attacker"
date: 2005-11-07
forum: Outdated Tutorials &amp; Tips
---

### Post by pinoyskull on 2005-11-07
Have you checked your auth.log?

Does it contain entries similar to these?
```

Nov  4 18:40:28 localhost sshd[12424]: User root from cassyopaya.de not allowed because not listed in AllowUsers
Nov  4 18:40:28 localhost sshd[12424]: error: Could not get shadow information for NOUSER
Nov  4 18:40:28 localhost sshd[12424]: Failed password for invalid user root from 85.214.16.171 port 45975 ssh2
Nov  4 18:40:30 localhost sshd[12429]: User root from cassyopaya.de not allowed because not listed in AllowUsers
Nov  4 18:40:30 localhost sshd[12429]: error: Could not get shadow information for NOUSER
Nov  4 18:40:30 localhost sshd[12429]: Failed password for invalid user root from 85.214.16.171 port 46204 ssh2
Nov  4 18:40:33 localhost sshd[12431]: User root from cassyopaya.de not allowed because not listed in AllowUsers
Nov  4 18:40:33 localhost sshd[12431]: error: Could not get shadow information for NOUSER
Nov  4 18:40:33 localhost sshd[12431]: Failed password for invalid user root from 85.214.16.171 port 46404 ssh2
Nov  4 18:40:36 localhost sshd[12434]: User root from cassyopaya.de not allowed because not listed in AllowUsers
Nov  4 18:40:36 localhost sshd[12434]: error: Could not get shadow information for NOUSER
Nov  4 18:40:36 localhost sshd[12434]: Failed password for invalid user root from 85.214.16.171 port 46607 ssh2
Nov  4 18:40:39 localhost sshd[12436]: User root from cassyopaya.de not allowed because not listed in AllowUsers
Nov  4 18:40:39 localhost sshd[12436]: error: Could not get shadow information for NOUSER
Nov  4 18:40:39 localhost sshd[12436]: Failed password for invalid user root from 85.214.16.171 port 46794 ssh2
Nov  4 18:40:41 localhost sshd[12441]: User root from cassyopaya.de not allowed because not listed in AllowUsers
Nov  4 18:40:41 localhost sshd[12441]: error: Could not get shadow information for NOUSER
Nov  4 18:40:41 localhost sshd[12441]: Failed password for invalid user root from 85.214.16.171 port 47006 ssh2
Nov  4 18:40:44 localhost sshd[12443]: User root from cassyopaya.de not allowed because not listed in AllowUsers
Nov  4 18:40:44 localhost sshd[12443]: error: Could not get shadow information for NOUSER
Nov  4 18:40:44 localhost sshd[12443]: Failed password for invalid user root from 85.214.16.171 port 47194 ssh2
Nov  4 18:40:47 localhost sshd[12446]: User root from cassyopaya.de not allowed because not listed in AllowUsers
Nov  4 18:40:47 localhost sshd[12446]: error: Could not get shadow information for NOUSER
Nov  4 18:40:47 localhost sshd[12446]: Failed password for invalid user root from 85.214.16.171 port 47402 ssh2
Nov  4 18:40:50 localhost sshd[12451]: User root from cassyopaya.de not allowed because not listed in AllowUsers
Nov  4 18:40:50 localhost sshd[12451]: error: Could not get shadow information for NOUSER

```

You can automatically block these attackers using BLOCKHOSTS ([http://freshmeat.net/redir/blockhosts/58025/url_homepage/blockhosts](http://freshmeat.net/redir/blockhosts/58025/url_homepage/blockhosts))

**INSTALLATION**

1.) Install Dependencies
```

apt-get install python-egenix-mxtools python2.4-dev

```

2.) Download Blockhosts source
```

wget http://www.aczoom.com/tools/blockhosts/BlockHosts-1.0.3.tar.gz

```

3.) Extract it to a temporary directory
```

tar xzvf BlockHosts-1.0.3.tar.gz

```

4.) Install it
```

cd BlockHosts-1.0.3
python setup.py install --force

```

**CONFIGURATION**

1.) Edit /etc/blockhosts.cfg, search for
```

#"LOGFILES": ( "/var/log/auth.og", ),

```
and uncomment it
```

"LOGFILES": ( "/var/log/auth.log", ),

```

2.) Edit /etc/hosts.allow, it should contain entries similar to these
```

sshd, proftpd, in.proftpd: ALL: spawn (/usr/bin/blockhosts.py --verbose --echo "%c-%s" >> /var/log/blockhosts.log 2>&1 )& : allow

# permanent whitelist addresses - these should always be allowed access

# permanent blacklist addresses - these should always be denied access

ALL: 10.  : deny
ALL: 192. : deny
ALL: 172. : deny

# ----------------------------------------
# next section is the blockhosts section - it will add/delete entries in
# between the two marker lines (#---- BlockHosts Additions)

#---- BlockHosts Additions
#---- BlockHosts Additions

```

3.) DONE

Note: blockhosts.py will automatically executed everytime sshd/proftpd service is called

---

