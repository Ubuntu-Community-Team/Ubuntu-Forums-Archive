---
title: "HowTo: Create LDAP server for shared Address Book in Thunderbird"
date: 2006-10-05
forum: Outdated Tutorials &amp; Tips
---

### Post by NobodySpecial on 2006-10-05
Do you envy Lotus Notes users with their shared Address Book, but want to use only open-source software?  Then this HowTo may be for you!  We will set up an LDAP server to host an Address Book for users to access via Mozilla Thunderbird.

This was installed on Ubuntu Dapper 6.06 from the Server CD with the LAMP option.  Standard desktop install should work, but hasn't been tested.

Also required: You MUST have a "fully qualified domain name" pointing to your server (i.e. can't just point to 192.168.1.2 or other network number, at least not for SSL data).  To do this, you go to dyndns.org (or similar website) and register a domain such as "KewlLdapServer.homedns.org" and set your router to forward port 389 traffic to your server computer (and later will change to port 636 when SSL set up).

First install OpenLDAP:
```
sudo apt-get install slapd
```
Set a password:
```
slappasswd
```
The system will return a hash.  As an example:
> {SSHA}Afaw3o8asdAWEfksj
Now we define a schema to match T'Bird's requirements:
```
sudo nano /etc/ldap/schema/mozillaorgperson.schema
```
You can use Gedit instead of Nano if in desktop mode.

Copy/paste the following:```

#
# mozillaOrgPerson schema v. 0.6.3
#

# req. core
# req. cosine
# req. inetorgperson

# attribute defs

attributetype ( 1.3.6.1.4.1.13769.2.1.1 
        NAME ( 'mozillaNickname' ) 
        SUP name )

attributetype ( 1.3.6.1.4.1.13769.2.1.2 
        NAME ( 'mozillaUseHtmlMail' ) 
        SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 
        SINGLE-VALUE )

attributetype ( 1.3.6.1.4.1.13769.2.1.3
        NAME 'mozillaSecondEmail' 
        EQUALITY caseIgnoreIA5Match
        SUBSTR caseIgnoreIA5SubstringsMatch
        SYNTAX 1.3.6.1.4.1.1466.115.121.1.26{256} )

attributetype ( 1.3.6.1.4.1.13769.2.1.4
        NAME 'mozillaHomeLocalityName' 
        EQUALITY caseIgnoreMatch
        SUBSTR caseIgnoreSubstringsMatch
        SYNTAX 1.3.6.1.4.1.1466.115.121.1.15{128} )

attributetype ( 1.3.6.1.4.1.13769.2.1.5 
        NAME 'mozillaPostalAddress2'
        EQUALITY caseIgnoreListMatch
        SUBSTR caseIgnoreListSubstringsMatch
        SYNTAX 1.3.6.1.4.1.1466.115.121.1.41 )

attributetype ( 1.3.6.1.4.1.13769.2.1.6 
        NAME 'mozillaHomePostalAddress2'
        EQUALITY caseIgnoreListMatch
        SUBSTR caseIgnoreListSubstringsMatch
        SYNTAX 1.3.6.1.4.1.1466.115.121.1.41 )

attributetype ( 1.3.6.1.4.1.13769.2.1.7 
        NAME ( 'mozillaHomeState' ) SUP name )

attributetype ( 1.3.6.1.4.1.13769.2.1.8 
        NAME 'mozillaHomePostalCode'
        EQUALITY caseIgnoreMatch
        SUBSTR caseIgnoreSubstringsMatch
        SYNTAX 1.3.6.1.4.1.1466.115.121.1.15{40} )

attributetype ( 1.3.6.1.4.1.13769.2.1.9 
        NAME ( 'mozillaHomeCountryName' ) 
        SUP name SINGLE-VALUE )

attributetype ( 1.3.6.1.4.1.13769.2.1.10
        NAME ( 'mozillaHomeFriendlyCountryName' )
        EQUALITY caseIgnoreMatch
        SUBSTR caseIgnoreSubstringsMatch
        SYNTAX 1.3.6.1.4.1.1466.115.121.1.15 )

attributetype ( 1.3.6.1.4.1.13769.2.1.11
        NAME ( 'mozillaHomeUrl' )
        EQUALITY caseIgnoreIA5Match
        SUBSTR caseIgnoreIA5SubstringsMatch
        SYNTAX 1.3.6.1.4.1.1466.115.121.1.26{256} )

attributetype ( 1.3.6.1.4.1.13769.2.1.12
        NAME ( 'mozillaWorkUrl' )
        EQUALITY caseIgnoreIA5Match
        SUBSTR caseIgnoreIA5SubstringsMatch
        SYNTAX 1.3.6.1.4.1.1466.115.121.1.26{256} )

# un-comment for all LDAP server NOT supporting SYNTAX 2.16.840.1.113730.3.7.1
attributetype ( 1.3.6.1.4.1.13769.2.1.13
        NAME ( 'nsAIMid' )
        DESC 'AOL Instant Messenger (AIM) Identity'
        EQUALITY telephoneNumberMatch
        SUBSTR telephoneNumberSubstringsMatch
        SYNTAX 1.3.6.1.4.1.1466.115.121.1.50 )

attributetype ( 1.3.6.1.4.1.13769.2.1.14 NAME ( 'mozillaHomeStreet' )
        EQUALITY caseIgnoreMatch
        SUBSTR caseIgnoreSubstringsMatch
        SYNTAX 1.3.6.1.4.1.1466.115.121.1.15{128} )

# un-comment for Netscape 6.x and all other LDAP server supporting SYNTAX 2.16.840.1.113730.3.7.1
# attributeTypes ( 2.16.840.1.113730.3.1.2013
#       NAME ( 'nsAIMid' )
#       DESC 'AOL Instant Messenger (AIM) Identity'
#       SYNTAX 2.16.840.1.113730.3.7.1 )

attributetype ( 1.3.6.1.4.1.13769.2.1.96
        NAME ( 'mozillaCustom1' )
        SYNTAX 1.3.6.1.4.1.1466.115.121.1.15
        SINGLE-VALUE )

attributetype ( 1.3.6.1.4.1.13769.2.1.97
        NAME ( 'mozillaCustom2' )
        SYNTAX 1.3.6.1.4.1.1466.115.121.1.15
        SINGLE-VALUE )

attributetype ( 1.3.6.1.4.1.13769.2.1.98
        NAME ( 'mozillaCustom3' )
        SYNTAX 1.3.6.1.4.1.1466.115.121.1.15
        SINGLE-VALUE )

attributetype ( 1.3.6.1.4.1.13769.2.1.99
        NAME ( 'mozillaCustom4' )
        SYNTAX 1.3.6.1.4.1.1466.115.121.1.15
        SINGLE-VALUE )
 
# defined in "A Summary of the X.500(96) User Schema for use with LDAPv3" - RFC 2256
#
# attributetype ( 2.5.4.6 NAME ( 'c' 'countryName' )
#       DESC 'RFC2256: ISO-3166 country 2-letter code'
#       SUP name SINGLE-VALUE )

# defined in "The COSINE and Internet X.500 Schema" - RFC 1274
#
# attributetype ( 0.9.2342.19200300.100.1.43
#       NAME ( 'co' 'friendlyCountryName' )
#       DESC 'RFC1274: friendly country name'
#       EQUALITY caseIgnoreMatch
#       SUBSTR caseIgnoreSubstringsMatch
#       SYNTAX 1.3.6.1.4.1.1466.115.121.1.15 )


# objectClass defs 

objectclass ( 1.3.6.1.4.1.13769.2.2.1 
        NAME 'mozillaOrgPerson' 
        SUP top 
        AUXILIARY 
        MAY ( 
        sn $ 
        givenName $ 
        cn $ 
        mozillaNickname $ 
        title $ 
        telephoneNumber $ 
        facsimileTelephoneNumber $ 
        mobile $ 
        pager $ 
        homePhone $ 
        street $ 
        postalCode $ 
        mozillaPostalAddress2 $ 
        mozillaHomeStreet $ 
        mozillaHomePostalAddress2 $ 
        l $ 
        mozillaHomeLocalityName $ 
        st $ 
        mozillaHomeState $ 
        mozillaHomePostalCode $ 
        c $ 
        mozillaHomeCountryName $ 
        co $ 
        mozillaHomeFriendlyCountryName $  
        ou $ 
        o $ 
        mail $ 
        mozillaSecondEmail $ 
        mozillaUseHtmlMail $ 
        nsAIMid $ 
        mozillaHomeUrl $ 
        mozillaWorkUrl $ 
        description $ 
        mozillaCustom1 $ 
        mozillaCustom2 $ 
        mozillaCustom3 $ 
        mozillaCustom4 ) ) 

# not part of the official Mozilla schema but read by Mozilla: 'departmentNumber' and 'postOfficeBox'
# 

```
LDAP uses slapd as a daemon.  Edit the config file:
```
sudo nano /etc/ldap/slapd.conf
```
Find the following line:
> include /etc/ldap/schema/nis.schema
Change it to:
```
include /etc/ldap/schema/mozillaorgperson.schema
```
Find the line under datbase #1 that starts with "suffix" and change to:
```
suffix          "dc=homedns,dc=org"
```
You can use any two other names you want instead, such as "dc=example,dc=com" or whatever.

Find the line under datbase #1 that starts with "directory" and change to:
```
directory       "/var/lib/ldap"
```

Someplace in this area under database #1, add the following two lines:
```
rootdn          "cn=admin,dc=homedns,dc=org"
rootpw          {SSHA}Afaw3o8asdAWEfksj
```
You can use a different root user other than "admin" and also change the "dc=homedns,dc=org" to whatever you used under the "suffix" line.  Of course you will enter whatever {SSHA} hash you were specifically given after the "slappasswd" command.

Save and exit your editor.

Restart the server daemon:
```
sudo /etc/init.d/slapd restart
```

At this point if you get an error message, it usually means you did something wrong in the configuration file, so go over it again.

If no errors came back at you, erase any prior data:
```
sudo rm -rf /var/lib/ldap/*
```

Next make an initialization file:
```
nano ~/init.ldif
```
Add this code:
```
dn: dc=homedns,dc=org
objectClass: top
objectClass: dcObject
objectClass: organizationalUnit
dc: homedns
ou: Kewl LDAP Server HomeDNS

dn: ou=personal,dc=homedns,dc=org
objectClass: top
objectClass: organizationalUnit
ou: personal
description: Personal Addressbook

```
Again, change the "dc=homedns,dc=org" to whatever you entered previously.

Create a template file:
```
nano ~/template.ldif
```
Add this code:
```
dn: cn=Sam Smith,ou=personal,dc=homedns,dc=org
objectclass: top
objectclass: person
objectclass: organizationalPerson
objectclass: inetOrgPerson
objectclass: mozillaOrgPerson
givenName: Sam
sn: Smith
cn: Sam Smith
mail: email@here.com
mozillaSecondEmail: .
mozillaNickname: .
homePhone: .
telephoneNumber: .
facsimileTelephoneNumber: .
pager: .
mobile: .
mozillaHomeStreet: .
mozillaHomeLocalityName: .
mozillaHomeState: .
mozillaHomePostalCode: .
mozillaHomeCountryName: .
mozillaHomeUrl: .
title: JobTitle
ou: BusinessDept
o: BusinessOrganization
street: BusinessStreet
l: BusinessCity
st: BusinessState
postalCode: BusinessZip
c: BusinessCountry
mozillaWorkUrl: .
mozillaCustom1: .
mozillaCustom2: .
mozillaCustom3: .
mozillaCustom4: .

```
Some points about the template:
1. Change "Sam Smith" to a relevent name.  Note that the full name "Sam Smith" is twice above (lines 1 and 9) and "Sam" is on line 7 and "Smith" is on line 8.  All these names must match as shown in the template above for this to work right.
2. As always, change the "dc=homedns,dc=org" to whatever you decided on.
3. Each line has a definition followed by a colon then some data.  The data line must not be blank.  I have inserted a period for these lines.  For several of the lines I have put desciptors, just so it is clear what they contain.  You can change these to periods, too.

Add the initiatlization file to the LDAP database:
```
sudo slapadd -v -l init.ldif
```
If you have an error here, try to reset the server and do the rm command again: sudo slapadd -v -l init.ldif, then sudo rm -rf /var/lib/ldap/*, then try the code again.

Add the template file data:
```
sudo slapadd -v -l template.ldif
```
Again, if you get an error here, try to restart again and troubleshoot until the system accepts the command without error.

Restart the server daemon for it to load the new data:
```
sudo /etc/init.d/slapd restart
```

Now to try to access via Thunderbird.  This is tested with the standard repository "mozilla-thunderbird", currently at version 1.5.0.7.  Click on "Address Book" then File -> New -> LDAP Directory.  Hostname is "KewlLdapServer.homedns.org" (substitute your actual server), Base DN is "dc=homedns,dc=org" (or whatever you used) and port is default 389.  Be sure your router is passing all port 389 data to your server's internal IP address.

Now left-click the new addressbook, type Control-F, then try to search for your name.  Hint: To bring up all addresses in the list, search the e-maill address field for "@".

If it finds the name you entered, great.  If not, exit T'Bird and load again.  If it fails again, go back through the above and troubleshoot.  You might want to use Luma to troubleshoot (see below).

If all went well up to this point you are ready to secure your server with SSL.

You may have to install OpenSSL:
```
sudo apt-get install openssl
```

Create an SSL certificate:
```
openssl req -x509 -days 3650 -newkey rsa:2048 -nodes -keyout ldap_key.pem -keyform PEM -out ldap_crt.pem -outform PEM
```
You can put anything here you want, except the "common name" **MUST** match your "fully qualified domain name" such as "KewlLdapServer.homedns.org".

Copy the certificate files to their proper folders:
```
sudo cp ldap_crt.pem /etc/ssl/certs
sudo cp ldap_key.pem /etc/ssl/private
```

Re-edit the config file:
```
sudo nano /etc/ldap/slapd.conf
```
Uncomment the ssl lines, rename to:
```
TLSCertificateFile      /etc/ssl/certs/ldap_crt.pem
TLSCertificateKeyFile   /etc/ssl/private/ldap_key.pem
```

Ask the server to listen for SSL:
```
sudo nano /etc/default/slapd
```
Find the "SLAPD_SERVICES" line and change to:
```
SLAPD_SERVICES="ldaps:///"
```
Now go back to your router and change the forwarded port from 389 to 636.

Restart the server daemon to run with the new config:
```
sudo /etc/init.d/slapd restart
```

Close and restart T'Bird.  Edit your LDAP Addressbook (right-click -> properties) and check "use secure connection (SSL)" and it should change the port to 636.  Close and restart T'Bird then try to search for your data as before.

At this point you should have a working LDAP Addressbook server with a whopping ONE entry.  Now comes the hard part: adding other entries and editing them.  It turns out that Mozilla Thunderbird presently will not let you edit any LDAP entries (it is hoped that feature may be added some day).  So the basic way to build up your entries is to enter them one at a time after editing the template and executing the "slapadd" command above.  This works fine for those of us with a couple dozen entries.  If you have in the hundreds, you will have to write some sort of script to automate this.

How do you edit entries?  There is an ubntu package "ldap-utils" that runs from the command line, but a GUI solution is available: Luma.

The Dapper repository version of Luma is old, and the newer one worked out some bugs, so we will compile from source.  Please note that this is installed on a client computer, not the server.

Note: Luma in Edgy / Feisty is more current than Dapper and works great, so you can install directly via apt-get or Synaptic and skip the steps to compile from source.

Go to [http://luma.sourceforge.net]("http://luma.sourceforge.net") and download the latest version (currently "luma-2.3.tar.bz2") and untar to a directory.

Install dependencies:
```
sudo apt-get install qt3-dev-tools python2.4-dev python2.4-qt3 python2.4-ldap python2.4-samba
```
Run the install script:
```
./install.py --prefix=/usr/local
```
You should now be able to Alt-F2 and enter "luma".

Set it up with plugins for Addressbook and Browser.  Set up server with SSL, uncheck "anonymous bind", select simple authentication, Bind as "cn=admin,dc=homedns,dc=org" (or whatever you had chosen above), password you had entered above, and select "Use base DN's provided by server".

Under Luma "Addressbook" plugin you can browse the names and change the lines where a period is present.  The other blank lines do not match our schema and should be left alone.  Disappointingly, only a few basic options can be edited here.

To edit the other options, choose Luma "Browser" plugin and now all options can be edited.

BIG thanks to Nathan Wills and his tutorial at [http://applications.linux.com/article.pl?sid=05/05/18/1248224]("http://applications.linux.com/article.pl?sid=05/05/18/1248224")

---

### Post by keeb on 2006-12-04
Thank you very much, this helped tremendously for understanding LDAP and SSL authentication!

---

### Post by NobodySpecial on 2006-12-04
Thanks for the feedback! I'm glad my efforts helped somebody.  So many wonderful people have contributed things to these forums that have helped me  tremendously and I'm glad I can give something back to this community.

---

### Post by jdpipe on 2006-12-15
Still working my way through this HOWTO, however though I would note that LUMA is now in the Ubuntu Repository (at least as of Ubuntu 6.10)

---

### Post by jdpipe on 2006-12-15
Great, it's all working. A useful HOWTO -- thanks.

BTW, I found a nicer GUI for creating address book entries. It's called 'directoryassistant' and its in the Ubuntu repositories.

Cheers
JP

--- EDIT: I had trouble using 'directoryassistant' over an encrypted connection. So maybe Luma is better after all.

---

### Post by Pitt Stains on 2007-05-02
This may be a stupid question, but is there a way to set up a computer on a local network as an LDAP server?  I realize that users won't be able to use the shared address books if they are not in the office, but I don't think that will be a problem in this case.

I have a very simple office setup, where the users work on PCs and Macs and an Ubuntu box acts as a file server.  Email clients are Thunderbird and Outlook, though I'm trying to phase out Outlook.  There is no domain controller or anything like that.

If this is not possible and/or an alternate solution is better, I'm all ears!

Thanks!

---

### Post by NobodySpecial on 2007-05-02
jdpipe - you are right, Luma in the present Edgy / Feisty repositories works fine, don't need to install from source.

Pitt Stains - if you follow this how-to on a server, you will have it set up for everyone in the office to access.  And if you follow it through, you will see that you can access your address book outside the office, from anywhere in the world that you have internet connectivity and a Thunderbird client.

---

### Post by Pitt Stains on 2007-05-03
> **NobodySpecial said:**
> Pitt Stains - if you follow this how-to on a server, you will have it set up for everyone in the office to access.  And if you follow it through, you will see that you can access your address book outside the office, from anywhere in the world that you have internet connectivity and a Thunderbird client.

Thanks.  I see the instructions want me to open up ports 389 and 636 to the world, which I'm not sure I'm ready to do.  Too scary.  I think I'll try to set this up as a local domain, which will suit our needs for now.  For that, I think I can skip the "fully qualified domain name" bit, which I believe would require a static IP address (not sure whether my ISP offers that).

If the need arises I can set up the same thing on the Ubuntu box that will be our web server (in the process of migrating servers), which I'd feel better about (for some reason) than exposing our office network.

I do have a second question... not everyone in the office uses Thunderbird.  I see a lot of the attribute names have a "mozilla" prefix.  Is it not possible to create a schema that would work for TBird as well as Outlook?  I am trying to move people over to TBird, but some are more resistant than others.

Thanks for taking the time to answer.
-Pitt

---

### Post by NobodySpecial on 2007-05-03
Pitt Stains - The 389 port is just initial to test, you end up with only 636 "open to the world" and of course your router points it to only one computer, running Linux, thus minimal security risk (i.e. only risk if that port is also used for something less secure, or risk of a vulnerability in slapd arises).

Your ISP doesn't have to give you a static IP address - just get one from [www.dyndns.org](www.dyndns.org) and configure your router for it (most routers can handle this).

I don't think there is any way to make it work for Evolution as well, because it would require a different schema.

---

### Post by silly.agent on 2007-05-08
Hi there. First of all, thank you for this great howto.
I have followed all the steps but for some (probably idiotic) reason I cannot get T'Bird to load the data from the LDAP server. Could you take a look at my settings and give me some hints?
Thanks a lot.

sa

Settings:


Domain name:   ldap.servername.org
(-> DNS record for ldap.servername.org poiting to static server ip)
Router:        forwarding all 389 traffic to local server ip


---
File:          init.ldif

dn: dc=servername,dc=org
objectClass: top
objectClass: dcObject
objectClass: organizationalUnit
dc: servername
ou: LDAP Server ServerName

dn: ou=personal,dc=servername,dc=org
objectClass: top
objectClass: organizationalUnit
ou: personal
description: Personal Addressbook


---
File:          template.ldif

dn: cn=Sam Smith,ou=personal,dc=servername,dc=org
objectclass: top
objectclass: person
objectclass: organizationalPerson
objectclass: inetOrgPerson
objectclass: mozillaOrgPerson
givenName: Sam
sn: Smith
cn: Sam Smith
mail: [email]email@here.com[/email]
mozillaSecondEmail: .
mozillaNickname: .
homePhone: .
telephoneNumber: .
facsimileTelephoneNumber: .
pager: .
mobile: .
mozillaHomeStreet: .
mozillaHomeLocalityName: .
mozillaHomeState: .
mozillaHomePostalCode: .
mozillaHomeCountryName: .
mozillaHomeUrl: .
title: JobTitle
ou: BusinessDept
o: BusinessOrganization
street: BusinessStreet
l: BusinessCity
st: BusinessState
postalCode: BusinessZip
c: BusinessCountry
mozillaWorkUrl: .
mozillaCustom1: .
mozillaCustom2: .
mozillaCustom3: .
mozillaCustom4: .


---
T'Bird LDAP settings:

Name:          LDAP Server
Hostname:      ldap.servername.org
Base DN:       ldap,dc=servername,dc=org
Port number:   389
Bind DN:       <empty>

---

### Post by NobodySpecial on 2007-05-08
silly.agent - hard to say what is wrong as there are many variables, but try this one change:

```
Base DN: dc=servername,dc=org
```

When it works, Thunderbird won't show you a list.  You have to do a search for a name, or simply for "@".

---

### Post by silly.agent on 2007-05-08
Thanks for your reply.
I tried your suggestion but didn't work.

I didn't mention earlier that I change the target location of the db (also changed permissions to openldap : openldap)

```
directory       "/var/lib/ldap/mozilla/db"
```

Also noticed that after wiping out the db with

```
sudo rm -rf /var/lib/ldap/mozilla/db/*
```

when I do a search

```
ldapsearch -x -b '' -s base '(objectclass=*)' namingContexts
```

I get the following output:

```

# extended LDIF
#
# LDAPv3
# base <> with scope baseObject
# filter: (objectclass=*)
# requesting: namingContexts 
#

#
dn:
namingContexts: dc=servername,dc=org

# search result
search: 2
result: 0 Success

# numResponses: 2
# numEntries: 1

```

Then, after adding data:

```

sudo slapadd -v -l init.ldif
sudo slapadd -v -l template.ldif

```

and restarting server

```

sudo /etc/init.d/slapd restart
ldapsearch -x -b '' -s base '(objectclass=*)' namingContexts

```

I get the following error message:

```

ldap_bind: Can't contact LDAP server (-1)

```

Any ideas?
Thanks again.

---

### Post by silly.agent on 2007-05-08
Still no white smoke. 

I managed to solve this problem though:

```
ldap_bind: Can't contact LDAP server (-1)
```

looks like it was the byproduct of running slapd manually without adding the "-u openldap" parameter, consequently the db files were not owned anymore by openldap : openldap but by root : root instead.

Now running

```
ldapsearch -x -b '' -s base '(objectclass=*)' namingContexts
```

generates the following output:

```

# extended LDIF
#
# LDAPv3
# base <> with scope baseObject
# filter: (objectclass=*)
# requesting: namingContexts 
#

#
dn:
namingContexts: dc=servername,dc=org

# search result
search: 2
result: 0 Success

# numResponses: 2
# numEntries: 1

```


Unfortunately, T'Bird still cannot retrieve the single entry from the LDAP server.
These are the db file permissions:

```

ls -l /var/lib/ldap/mozilla/db/

-rw------- 1 openldap openldap    2048 2007-05-08 19:59 alock
-rw------- 1 openldap openldap    8192 2007-05-08 16:55 __db.001
-rw------- 1 openldap openldap 2629632 2007-05-08 16:55 __db.002
-rw------- 1 openldap openldap   98304 2007-05-08 16:55 __db.003
-rw------- 1 openldap openldap  565248 2007-05-08 16:55 __db.004
-rw------- 1 openldap openldap   24576 2007-05-08 16:55 __db.005
-rw------- 1 openldap openldap      96 2007-05-08 16:55 DB_CONFIG
-rw------- 1 openldap openldap    8192 2007-05-08 19:59 dn2id.bdb
-rw------- 1 openldap openldap   32768 2007-05-08 19:59 id2entry.bdb
-rw------- 1 openldap openldap   58149 2007-05-08 19:59 log.0000000001
-rw------- 1 openldap openldap    8192 2007-05-08 19:59 objectClass.bdb

```

Any suggestions anyone?

---

### Post by silly.agent on 2007-05-09
More baby steps.

I managed to connect locally (LAN ip) and retrieve data from the LDAP server.
Attempts to connect to ldap.servername.org have failed (most likely a firewall/router problem, I will look into that later on)

In the meantime, I tried to get the TLS part going but after restarting the LDAP server I get the following syslog output:

```

main: TLS init def ctx failed: -1
slapd stopped.
connections_destroy: nothing to destroy

```

looks like a problem with the certificates :-(
any suggestions?
thanks

---

### Post by NobodySpecial on 2007-05-09
silly.agent - I don't think the certificates work unless you connect via the FQDN (e.g. ldap.servername.org).

---

### Post by Ashaman074 on 2007-05-29
Thanks for writing a good HOWTO.  I am fairly new to all of this, and was able to get this working without much difficulty.

I must admit though, that now having it set up and running I feel a bit like I have wasted my time.  I thought that Thunderbird would be able to edit and add LDAP entries which would have been great; the fact that it cannot seems odd to me.  

Making it worse, I am not sure how to even go about doing so.  Obviously, the template can be used - but what if I want to delete an entry?  How can that be accomplished?

Luma sounded like a reasonable option, but after installing it  I gather it is for a graphical Linux installation (as opposed to server-based)?  Or possibly a linux based workstation?  I couldn't find any documentation or information about it on the website.

Is there another option for windows based machines, Thunderbird, and a linux LDAP server?

Any tips would be appreciated; my plan was to switch everyone to Thunderbird for use with LDAP, but this is a bit of a snag!

---

### Post by NobodySpecial on 2007-05-29
Ashaman074 - Your post is like the gameshow Jeopardy.  You just posted the answer.  Now I will give you the question!
> Why don't more people move from Windows to Linux?
And you gave a fantastic answer - congratulations!

Of course, I say this with much sarcasm.  Linux has made huge leaps in the past couple years, but one place it really lags is in competing with the MS Exchange Server.  This method of LDAP and editing with Luma is clunky at best.  It works quite well for my small household, but is not up to par for even a small office, in my view.

Hopefully an Open Source project such as [Zimbra]("http://www.zimbra.com") will soon change that.

---

### Post by Ashaman074 on 2007-05-30
Heheh, well thanks for the reply.  If nothing else, I figure some of these projects are good learning experiences.

Actually, I have looked at zimbra before and was shocked at what all it can do - I guess that is why I was surprised that sharing an address book via LDAP had limitations.

Is there a way to delete entries at least?  It wouldn't really be what I had hoped for, but it would at least allow me to provide an up-to-date address book for everyone - and that would be of some benefit :)

---

### Post by gentgeen on 2007-07-09
> **Ashaman074 said:**
> 

Making it worse, I am not sure how to even go about doing so.  Obviously, the template can be used - but what if I want to delete an entry?  How can that be accomplished?

Luma sounded like a reasonable option, but after installing it  I gather it is for a graphical Linux installation (as opposed to server-based)?  Or possibly a linux based workstation?  I couldn't find any documentation or information about it on the website.


If you are looking for a command-line option, I would suggest looking at **ldapdelete**  Do a "**man ldapdelete**" before you tried it though.

If you would prefer a more GUI-approach, try some of the web based ones out there.  There are lots.  You can put that on your server, then it will not matter what OS you are on.

---

### Post by mick8985 on 2007-08-08
> **NobodySpecial said:**
> Pitt Stains - The 389 port is just initial to test, you end up with only 636 "open to the world" and of course your router points it to only one computer, running Linux, thus minimal security risk (i.e. only risk if that port is also used for something less secure, or risk of a vulnerability in slapd arises).

Your ISP doesn't have to give you a static IP address - just get one from [www.dyndns.org](www.dyndns.org) and configure your router for it (most routers can handle this).

I don't think there is any way to make it work for Evolution as well, because it would require a different schema.

This can be done for evolution. The schema is probably already sitting there on your system.

```
michael@michael-desktop:~$ sudo cp /usr/share/evolution-data-server-1.10/evolutionperson.schema /etc/ldap/schema/

```
open up /etc/ldap/slapd.conf in a text editor and add this line to the includes
```
include         /etc/ldap/schema/evolutionperson.schema

```

---

### Post by smahomad on 2007-10-03
WOW! I got it working on first attempt!
Great HOW-TO ! Many many thanks !


Now a suggestion for a great folow-up action :-)

We now have our thunderbird addressbooks full of entries, so the question now is, how do we move those entries into the LDAP repository ?

I tried exporting the address book into ldif file (under windows), copied the stuff over to the Linux box (via WinSCP), tried the slapadd command, but I got parse errors on the very last line of the file... and not a single entry got fed into the repository...

Any ideas on how to move the stuff from the various Thunderbird address books (different users across a micro-company) and consolidate them into LDAP?

Many thanks in advance

---

### Post by NobodySpecial on 2007-10-03
smahomad - I wish I knew how, but the only way I know to put in names and addresses is the tedious method described in the how-to.

---

### Post by smahomad on 2007-10-04
I found this, I'll try it.. see if it helps

[http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/476224](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/476224)

Update:
I tried this, but it didn't seem to work

the slapadd command outputs a parse error on the blank lines...

I created a mailing list on TB to contain a subset of my local address book contacts, then I exported that mailing list to an LDIF file
fixed with the above script (which also meda some funny output) but managed to create an output file

I tried adding that fixed LDIF file into the LDAP repository and got parse errors on the blank lines between each entry...

---

### Post by xIke on 2007-10-17
Gack, this worked for me right up until the SSL step.  Adding 
```
**/etc/ldap/slapd.conf**
TLSCertificateFile      /etc/ssl/certs/ldap_crt.pem
TLSCertificateKeyFile   /etc/ssl/private/ldap_key.pem

**/etc/default/slapd**
SLAPD_SERVICES="ldaps:///"
```
keep it from starting up.  It complains: 
```
Stopping OpenLDAP: slapd.
Starting OpenLDAP: slapd - failed.
The operation failed but no output was produced. For hints on what went
wrong please refer to the system's logfiles (e.g. /var/log/syslog) or
try running the daemon in Debug mode like via "slapd -d 16383" (warning:
this will create copious output).

Below, you can find the command line options used by this script to 
run slapd and slurpd. Do not forget to specify those options if you
want to look to debugging output:
  slapd -h 'ldaps:///' -g openldap -u openldap 

```

Any advice?

---

### Post by xIke on 2007-10-18
Also for me, removing "include         /etc/ldap/schema/nis.schema" makes it fail to start up, because it's missing shadow among other things.  Not sure if this has been changed since the thread was originally posted.

---

### Post by dsegarra on 2007-12-05
I am trying to setup OpenLDAP for testing purposes. No qualified domain in place. If so, what should my ldap.conf contain for HOST and URI??? BASE???..that part I get lost. Also, how would I know which port is my LDAP running??? is this 389 by default??..thanks




d

---

### Post by borobudur on 2008-02-18
Don't know if this thread is still updated.

I don't get the ssl connection encrypted. I get this error message:
```
ldap_bind: Can't contact LDAP server (-1)
        additional info: error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed

```Can anyone help me please?

---

### Post by borobudur on 2008-02-18
I solved my problem with this: [INDENT][COLOR=Blue]*                 If you instead get the error message:                 ldap_bind: Can't contact LDAP server (81): additional              info: error:14090086:SSL              routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify              failed                 , your ldapsearch was compiled with settings                 that instruct it to always try to verify the server's                 certificate. Adding [SIZE=3]**[I]TLS_REQCERT never***[/SIZE] to                 the ldap.conf used by ldapsearch (for Red                 Hat-derived Linuxes, this file is located in                 /etc/openldap) will solve this problem.[/I][/COLOR]
[/INDENT]Found it here: [http://www.cendio.com/support/tag/LDAP-auth.html](http://www.cendio.com/support/tag/LDAP-auth.html)

---

### Post by dave_abrahams on 2008-04-03
I've set up LDAP with Kerberos according to the following guides:

[https://help.ubuntu.com/community/OpenLDAPServer#head-b5966b4f7e707477050f4a959c585874bbf33771](https://help.ubuntu.com/community/OpenLDAPServer#head-b5966b4f7e707477050f4a959c585874bbf33771)
[https://help.ubuntu.com/community/SingleSignOn](https://help.ubuntu.com/community/SingleSignOn)

Now, the first link specifies security changes to slapd.conf that are incompatible with your advice to edit out the use of the NIS schema.  I'm wondering, since I am actually using kerberos, whether any of that is necessary.  Obviously, I don't know much about these technologies yet and I'm trying to learn as I go along so if anyone could explain the interactions here I would be very grateful.

---

### Post by cjwilber on 2008-04-18
> **NobodySpecial said:**
> smahomad - I wish I knew how, but the only way I know to put in names and addresses is the tedious method described in the how-to.

I had a similar quandary, so I wrote a simple web based app for adding, editing, and deleting data. I have based it on the LDAP schema for Thunderbird, but tried to make it flexible so that other attributes can be used instead.
If anyone is interested, I could let them have a look at this, and then share it with a wider audience if they thought it useful.

I've put a couple of attachments of screenshots. Basically, there is a front screen which allows you to search for addresses, including wildcards.
That returns a list with minimal information presented - name, email, phone number, monile number
You can select one of these entries to view more details, and you can also choose to edit the entry
It is also possible to create new entries from the front screen.

It's probably a bit kludgy, but might help someone.

---

### Post by Robvdl on 2008-06-07
Also for me, removing "include /etc/ldap/schema/nis.schema" makes it fail to start up, and leaving it in, Thunderbird doesn't seem to work at all with the LDAP server.

Could this guide please be updated to work on Hardy? I think that may be the problem.

Also, what if your domain is domain.co.nz instead of domain.com

do you use:

dc=domain,dc=co,dc=nz

or:

dc=domain,dc=co.nz

??

---

### Post by dannyboy1121 on 2008-07-04
I think the bit that says "Thunderbird currently does not allow editing of ldap" should be highlighted and put in bold as a header. Reading bugzilla on this is painful.

---

### Post by Gouki on 2008-07-30
Just a few heads up ...

**1st** - Regarding the management of data present on the LDAP server via the clients (email clients). 

As far as I know, only Evolution is capable of reading and writing. Other clients like Outlook, Outlook Express and Thunderbird are only allowed to read.

**2nd** - To manage the information one has in the LDAP server, I recommend installing phpldapadmin, which is packaged and available in the repositories:

```
gouki@stacker:~$ sudo apt-cache search phpldapadmin
phpldapadmin - web based interface for administering LDAP servers
```

I'm sure that, with *phpldapadmin* installed, managing your address book will be allot easier.

---

### Post by dannyboy1121 on 2008-09-03
> **Gouki said:**
> Just a few heads up ...

**1st** - Regarding the management of data present on the LDAP server via the clients (email clients). 

As far as I know, only Evolution is capable of reading and writing. Other clients like Outlook, Outlook Express and Thunderbird are only allowed to read.

**2nd** - To manage the information one has in the LDAP server, I recommend installing phpldapadmin, which is packaged and available in the repositories:

```
gouki@stacker:~$ sudo apt-cache search phpldapadmin
phpldapadmin - web based interface for administering LDAP servers
```

I'm sure that, with *phpldapadmin* installed, managing your address book will be allot easier.

Agreed - phpLDAPadmin is fantastic. Web based which means that you can manage it from pretty much any computer. Recommended. :)

---

### Post by RichardCL on 2009-03-05
I'm getting an error trying to
```
sudo slapadd -v -l /root/init.ldif
```

I get the output

```
slapadd: line 1: database (dc=nodomain) not configured to hold "dc=homedns,dc=org"
slapadd: line 1: database (dc=nodomain) not configured to hold "dc=homedns,dc=org"

```

Any ideas?

---

### Post by nilsja on 2009-04-18
i get the same error
```
slapadd: line 1: database (dc=nodomain) not configured to hold "dc=homedns,dc=org"
```any ideas?

---

### Post by Tony Newton on 2009-11-13
Well, after bashing my head against this particular brick wall for almost three weeks now, im ready to call it quits with Linux.

Ive been using Ubuntu as a LAMP server for 2 years now and actually found it to be stable and relaibale. However recently I wanted to create an LDAP server so i could have shared address books for the company.  "Should be simple enough" I thought.

Well here we are three weeks later, and as i said, im ready to call it a day with Linux. I have been unable to find a single guide that tells me how to set this frigging thing up in a coherent way that actually a) makes sense and B) is current.

And before anyone tells me the RTFM - I have. Ive also read this and many other "how to " guides that supposedly tell people how to set up slapd.  A lot of them are for previous versions of open ldap so just confuse the issue, most of them dont explain what or why to do stuff, and none of them work.

I for one cannot afford to spend this much time scouring the net for little nuggets of wisdom that may (but usually dont..) help me.  Im also fed up with the attitude of many so called linux "experts" who seem to take great pleasure in answering perfectly reasonable questions with a patronising and "im so clever and you are stupid" attitude. If you were so clever you'd be able to help me (or the thousands of others who also shared this frustration over the past few years) but you havnt. So thanks for nothing.

Some people have been very pleasant and helpfull, to them I extend huge thanks, but I now have a very good understanding of why Linux isnt gaining popularity.

Its far to complicated and fickle to setup and install stuff. The documentation is usually of a very poor standard and believe me there is a TON of it out there, much of it incorrect or out of date which makes filtering the rubbish tiresome and unproductive.

I have a large investment in Linux stuff at the moment, so I am about to advertise for a linux specialist to help us. They will have 1 week. If at the end of that week we still have no luck Im going to solve my open ldap problem by spending a truckload of cash to get Microsoft products.  Not at all what i want to do, but in a commercial environment, i simply cannot afford to shag about with this any longer.

Shame really, but i think untill the Linux community gets its act together and collectivly stops acting like a bunch of spoiled kids in an exclusive club that you have to be "in the know" to join and participate in, start concentrating on developing user centric tools that work in a coherent way and are easy to setup and configure rather than pfaffing about getting all excited about yet another piece of desktop eye candy, I think it will just fade away.  And that would be a crime.

---

### Post by proddy on 2009-11-16
@Tony Newton - know how you feel. I've been struggling getting LDAP & phpldapadmin working on my system to discover both are not compatible with Ubuntu 9.10 Karmic Koala without a shed loads of tweaking.

---

### Post by Kropotkin on 2009-11-19
First, thanks for a great how-to.

I'm seeing an error importing the schema:

```

$ sudo slapadd -v -l init.ldif
/usr/local/etc/openldap/schema/mozillaorgperson.schema: line 173 objectclass: AttributeType not found: "sn"
slapadd: bad configuration file!
```

As far as I can see, the problem seems to be here:

```

objectclass ( 1.3.6.1.4.1.13769.2.2.1 
        NAME 'mozillaOrgPerson' 
        SUP top 
        AUXILIARY 
        MAY ( 
        **sn** $ 
        givenName $ 
        cn $ 
        mozillaNickname $ 
```

Any ideas what is going wrong here?

I am running server version **openldap-server-2.3.43** under FreeBSD; accessing it from Ubuntu and Fedora clients.

Thanks.

---

### Post by abishur on 2009-11-22
@Tony and Proddy LDAP and phpLDAP admin work wonderfully on 9.10, I've made a guide on getting LDAP set up and authenticating windows users to it [here]("http://ubuntuforums.org/showthread.php?t=1330637").  If you're having problems accessing LDAP with phpLDAPadmin (getting an error message like   [FONT=&quot]“E_STRICT: Declaration of AJAXTREE::draw_dn()….) then the problem is actually in the latest version of php and not 9.10's fault.

To fix that problem edit your AJAXTree.php file ([/FONT]  [FONT=&quot]/usr/share/phpldapadmin/lib/AJAXTree.php) and on the 16th line find where it says "$level=0" and change it to "$level"  then phpLDAPadmin will work just fine.  (I'm guessing that this is your problem proddy since all you said was a vague "something" isn't working with phpldapamin and ldap)
[/FONT]

---

### Post by MidSpeck on 2009-12-14
> **Tony Newton said:**
> ...start concentrating on developing user centric tools that work in a coherent way and are easy to setup and configure...

Tony, I agree with you on this point.  "Linux" will not take off completely until it is able to provide "user centric tools".

That being said, you are talking about a server-side program here, and those are not always required to be the most "user" friendly, since it is generally understood that a computer-savvy individual will be doing the set up.

I also understand what you mean about those with the "I'm better than you" attitudes.  I've run across plenty of those in my day.

I know you posted a month ago, I just saw it today and luckily have some experience with OpenLDAP on Ubuntu.  What issues are you having?  Error messages?

---

### Post by Xi0N on 2011-02-17
Reviving an obsolete thread..... i am trying to do this... configure a ldap server to use it with thunderbird, but the problem is that this tuto is obsolete, and the config files have either been moved or do not exist....
Can anyone point out a bit how o do it nowadays?
I really need this utility.... seems pretty useful...

If anyone can help..... thanks!!!

---

### Post by barinov2000 on 2011-04-07
> **Xi0N said:**
> Reviving an obsolete thread..... 
If anyone can help..... thanks!!!
Anyone at all? :-k

---

