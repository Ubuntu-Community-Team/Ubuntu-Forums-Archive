---
title: "error in adding ldap ldif file"
date: 2017-11-14
forum: New to Ubuntu
---

### Post by sanko50 on 2017-11-14
my ldap admin DN is :  [COLOR=#000000][FONT=Verdana]* cn=admin,dc=nodomain*[/FONT][/COLOR]



I'm trying  to add a ldif file as per below command


[COLOR=#000000][FONT=Verdana]$sudo ldapadd -D "cn=admin,dc=nodomain" -w password@123 -f /home/tintin/ldif

[/FONT][/COLOR][COLOR=#ff0000][FONT=Verdana]adding new entry "dc=example,dc=com"[/FONT]
[FONT=Verdana]ldap_add: Server is unwilling to perform (53)[/FONT]
[FONT=Verdana]additional info: no global superior knowledge[/FONT][/COLOR]


ldif  file content :
-----------------------
dn: dc=example,dc=com
dc: example
description: My wonderful company 
objectClass: dcObject
objectClass: organization
o: Example, Inc.

dn: ou=people, dc=example,dc=com
ou: people
description: All people in organisation
objectclass: organizationalunit


dn: cn=Robert Smith,ou=people,dc=example,dc=com
objectclass: inetOrgPerson
cn: Robert Smith
cn: Robert J Smith
cn: bob  smith
sn: smith
uid: rjsmith
userpassword: rJsmitH
carlicense: HISCAR 123
homephone: 555-111-2222
mail: [EMAIL="r.smith@example.com"]r.smith@example.com[/EMAIL]
mail: [EMAIL="rsmith@example.com"]rsmith@example.com[/EMAIL]
mail: [EMAIL="bob.smith@example.com"]bob.smith@example.com[/EMAIL]
description: swell guy
ou: Human Resources


whats the issue here ? How to  resolve it ?

---

