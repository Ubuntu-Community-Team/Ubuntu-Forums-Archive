---
title: "squid ldap_auth"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by redmorning on 2008-06-27
i confiugured a proxy server (squid 2.6.STABLE14) on a machine (with ubuntu gutsy 7.10) and it has two ethernet cards,one of them for the wan and the other one is for lan (university lan).From my home i can use my proxy server very well (cache,acl...).the second thing that i want to do is to reach the ldap server in university but i can't.

here is the on of the output about the subtree of ldapserver
```

bim@bimproxy:~$ ldapsearch -x -b dc=gsu,dc=edu -h proxyserver uid=myusername
# extended LDIF
#
# LDAPv3
# base <dc=gsu,dc=edu> with scope subtree
# filter: uid=myusername
# requesting: ALL
#

# search reference
ref: ldap://gsu.edu/CN=Configuration,DC=gsu,DC=edu

# search result
search: 2
result: 0 Success

# numResponses: 2
# numReferences: 1

```

as you see i will check the entry of the users which will pass through my proxy to reach internet with dc=gsu,dc=edu

here is my problem : before i make changes in squid.conf about auth_param basic program i need to control if my proxy can reach ldap server and make control of the username and password.i tried some codes:
```

/usr/lib/squid/ldap_auth -ZZ -b "dc=gsu,dc=edu" -h 10.99.1.1

/usr/lib/squid/ldap_auth -b "dc=gsu,dc=edu" -f "uid=%s" -h 10.99.1.1

 /usr/lib/squid/ldap_auth -P -R -b "dc=gsu,dc=edu" -D "dc=gsu,dc=edu" -w "secretsquidpassword" -f "uid=%s)" -h 10.99.1.1


```
after them i enter my username and password with a blank space and results are err , err success or 
squid_ldap_auth: WARNING, could not bind to binddn 'Invalid credentials'
ERR Invalid credentials etc..


i learn about the parameters but not enough.can anyone help me about this subject.?

thank you.

---

### Post by redmorning on 2008-06-27
anybody ?

---

### Post by redmorning on 2008-06-29
nobody?  
(:
there must be somebody who know stuff about this issue,i will be thankful for your helps..

---

