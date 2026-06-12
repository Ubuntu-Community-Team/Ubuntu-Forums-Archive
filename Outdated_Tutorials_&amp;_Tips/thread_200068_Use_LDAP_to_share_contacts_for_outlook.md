---
title: "Use LDAP to share contacts for outlook"
date: 2006-06-19
forum: Outdated Tutorials &amp; Tips
---

### Post by fizgig on 2006-06-19
For starters, I'm not an administrator or a programmer or a linux expert.  The method below might not be the best but it did work for me.  As people suggest changes to make it better, I'll update this first post accordingly.  Hope it helps you out....

1.  Install ldap:  [B]apt-get install slapd
[/B](I think this installs all the dependencies.  I'll add more here later if it's not the case)
2.  Edit the slapd.conf file in /etc/ldap.  What follows is my file:
> # Schema and objectClass definitions
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema

# Schema check allows for forcing entries to
# match schemas for their objectClasses's
schemacheck     on

# Where the pid file is put. The init.d script
# will not stop the server if you change this.
pidfile         /var/run/slapd/slapd.pid

# List of arguments that were passed to the server
argsfile        /var/run/slapd.args

# Read slapd.conf(5) for possible values
loglevel        296

# Where the dynamically loaded modules are stored
modulepath    /usr/lib/ldap
moduleload    back_bdb

backend        bdb
checkpoint 512 30

database        bdb

# The base of your directory in database #1
suffix          "dc=companyname,dc=com"

rootdn    "cn=Manager,dc=companyname,dc=com"
rootpw "secret"

# Where the database file are physically stored for database #1
directory       "/var/lib/ldap"

# Indexing options for database #1
index           objectClass eq
index           cn    pres,eq

mode    0600

# Save the time that the entry gets modified, for database #1
lastmod         on

access to *
    by * read

access to dn.base="" by * read

access to *
        by dn="cn=admin,dc=localdomain" write
        by * read


Note that security is pretty low.  If you want to write to the directory, you send the root user (cn=Manager,dc=companyname,dc=com) and password (secret) in clear text over the network - no big deal for me yet but there are methods 
around for more secure authorization.

3.  Start the slapd daemon: [B]/etc/init.d/slapd start
[/B]4.  We need to get the initial structure into it.  Make a text file that has the following in it called build.ldif
> dn: dc=companyname,dc=com
dc: companyname
objectClass: dcObject
objectClass: organizationalUnit
ou: Companyname Dot Com

dn: ou=employees,dc=companyname,dc=com
ou: employees
objectClass: organizationalUnit


5.  Get that into the database: [B]slapadd -v -l build.ldif
[/B]6.  Now let's add some people.  I like to use GUI's.  Since I use XP at work (long story) I like this free client: [http://ldaptool.sourceforge.net/](http://ldaptool.sourceforge.net/)  There are linux versions as well and I might add the info for those later but the settings will be similar....
7.  Install the client and for the settings, use the following values:
Server:  ip address of ldap server (or host name if possible)
Servertype: OpenLdap
Port: 389
Root DN: dc=companyname,dc=com
User Name: cn=Manager,dc=companyname,dc=com
Password: password from slapd.conf file next to rootpw
Say OK to connect.
8.  Right-click ou=employees and select "Add Entry"
9.  For object class, select inetOrgPerson (hit "i" twice)
10. For DN, enter **cn=John Smith** (or whatever) hit OK.
11. In the new right-hand pane, right-click sn, select "Add" enter the last name for the person (**Smith**)
12. I want to have the mobile number and email address.  According to [this page]("http://www.openldap.org/faq/data/cache/294.html"), that maps to mobile and mail respectively. So, let's add those attributes.
13.  In the right-hand pane, at the very top, right-click that long bold line and select "Add".  Scroll to "mobile" and select it.  Do the same for "mail".
14.  Right click each new attribute in the tree, select "Add" and add the value for each in whatever format you want.
15.  Let's save it.  Right-click the long bold line again and select "Save".
16.  Now just set up your email client to point at your ldap server.  The only setting that is tricky is the base dn.  It should read something like: **ou=employees,dc=yourcompany,dc=com **also the port should be **389**
17.  In outlook, to make your directory server the first in line to check against, go to tools->options and select address book.  
18.  In the new window, select "Tools -> Options"
19.  Select your directory server and hit the up arrow to make it the top server. 
20.  Now, when you type in a partial name that's in the directory, hit CTRL-K to get a list of the people that match it in your directory.

Voila!

---

### Post by frenchn00b on 2010-01-15
Hello, I have a problem at step 5:
slapadd -v -l build.ldif

it gives:

```
# slapadd -v -l build.ldif
/etc/ldap/slapd.conf: line 9: unknown directive <schemacheck> outside backend info and database definitions.
slapadd: bad configuration file!

```

:( Any ideas how to make it?

---

### Post by mistamidget on 2011-03-28
If you cut and pasted the example you need to add a blank line at the bottom to terminate the dn
So there should be 10 lines in the ldif file

---

