---
title: "Bash &quot;HERE documents &quot; help"
date: 2012-03-01
forum: Programming Talk
---

### Post by woodson2 on 2012-03-01
I'm trying to enter a block of text into an existing configuration file for OpenLDAP so the setup can be fully scripted.

The text below is what I want to enter into slapd.conf and this all works well and good, however as you probably know this will place the text at the end of the file. What I'd like to know is how can I choose where in an existing file I want to place the text or is this beyond the scope of HERE documents?

```
cat >> slapd.conf << "EOF"
access to attrs=userPassword
        by self write
        by anonymous auth
        by dn.base="cn=root,dc=abclott,dc=lott" write
        by group.base="cn=infrastructure,ou=GTECH,ou=groups,dc=abclott,dc=lott" write
        by dn.base="uid=ldapmgr,ou=people,dc=abclott,dc=lott" write
        by * none

access to dn.children="ou=people,dc=abclott,dc=lott"
        by dn.base="cn=root,dc=abclott,dc=lott" write
        by dn.base="cn=bind,dc=abclott,dc=lott" read
        by users read
        by * none

access to dn.children="ou=groups,dc=abclott,dc=lott"
        by dn.base="cn=root,dc=abclott,dc=lott" write
        by dn.base="cn=bind,dc=abclott,dc=lott" read
        by users read
        by * none

access to dn.children="ou=servers,dc=abclott,dc=lott"
        by dn.base="cn=root,dc=abclott,dc=lott" write
        by group.base="cn=infrastructure,ou=GTECH,ou=groups,dc=abclott,dc=lott" write
        by dn.base="cn=bind,dc=abclott,dc=lott" read
        by users read
        by * none

access to dn.subtree="ou=SUDOers,dc=abclott,dc=lott"
        by dn.base="cn=root,dc=abclott,dc=lott" write
        by dn.base="cn=bind,dc=abclott,dc=lott" read
        by users read
        by * none

access to *
        by dn.base="cn=root,dc=abclott,dc=lott" write
        by dn.base="cn=bind,dc=abclott,dc=lott" search
        by * none
EOF
```

---

### Post by diesch on 2012-03-02
With here docs you are using just the normal output redirection of the shell. So you can only replace a file with the content of the here doc or append the content to an existing file.

[m4](http://manpages.ubuntu.com/manpages/oneiric/en/man1/m4.1posix.html) may be a solution for you.

---

### Post by ofnuts on 2012-03-02
> **woodson2 said:**
> I'm trying to enter a block of text into an existing configuration file for OpenLDAP so the setup can be fully scripted.

The text below is what I want to enter into slapd.conf and this all works well and good, however as you probably know this will place the text at the end of the file. What I'd like to know is how can I choose where in an existing file I want to place the text or is this beyond the scope of HERE documents?

You won't avoid using some form of marker in the file to indicate where the new input should be inserted. Beside the macro processor above, there are ways to tell sed or awk to print a file up to, or starting from, a given pattern and use that to bracket your new input. 

A low-tech solution can also be to use "grep -n" to find the line number of the marker and then use it with wc -l/head/tail to extract  the relevant parts.

---

### Post by Khayyam on 2012-03-03
That "choice" is a line? If so ...

The contents of 'edit.ldif' are inserted at line 8 of input.ldif and the output collected in output.ldif

```
awk '{print} NR==8 {while (getline < "edit.ldif") print}' input.ldif > output.ldif
```

You know you can use 'ldapadd' or 'ldapmodify' for this kind of thing right?

HTH ... khay

---

