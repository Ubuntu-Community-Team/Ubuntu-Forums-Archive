---
title: "Help with adding an AD group to sudoers file on Ubuntu server 22.04 joined to AD"
date: 2024-04-23
forum: New to Ubuntu
---

### Post by fandreani on 2024-04-23
Hello everyone,on my Ubuntu Server 22.04 joined to my AD server via SSSD I'm unable to add an Active Directory group to the sudo group. In the sudoers file, I added the group to the /etc/sudoers file and it looks like this:


#Allow members of group sudo to execute any command
%sudo ALL=(ALL:ALL) ALL 
%digital-tech-staff-sambaserver-L3-test-Admin-L@mydomain-name.it ALL=(ALL) ALL


Users can connect correctly via SSH, but when they run the "sudo su" command, the ubuntu server responds with "username@domain.it is not in the sudoers file. This incident will be reported."


To temporarily solve the issue, I manually added EACH member of the AD group with the command "sudo usermod -aG sudo username." Fortunately, the group was small, but I will have the problem with groups with many more members.
 Can someone please give me some ideas on how to solve this? Thanks in advance.

---

### Post by MAFoElffen on 2024-04-23
Please post raw format and commands within Code Tags. I edited the quote so it is easier to read there. Look at what I highlighted in red...
> **fandreani said:**
> 
```

#Allow members of group sudo to execute any command
%sudo ALL=(ALL:ALL) ALL 
%digital-tech-staff-sambaserver-L3-test-Admin-L[COLOR=#ff0000]@mydomain-name.it[/COLOR] ALL=(ALL) ALL

```

Do not specify the domain name after group name. Just the group name, like this:
```

%digital-tech-staff-sambaserver-L3-test-Admin-L ALL=(ALL) ALL

```
That's a Windows thing that doesn't cross-over to Linux. Linux see's all that text as literal, and says, that (whole text) is not the "group name" I see...

---

### Post by fandreani on 2024-04-26
Hi, thank you for the reply, I tried your solution but I get the same result [COLOR=#000000] (user@domain.it is not in sudoers)[/COLOR]

---

### Post by MAFoElffen on 2024-04-26
Please post the results of these, posting the output within CODE Tags:
```

sudo grep -v -e '#\|^$' /etc/sudoers
sudo grep -v -e '#\|^$' /etc/sudoers.d/*

```
And had you rebooted the server since the edit do that the edit could apply in the current environment?

---

### Post by fandreani on 2024-04-29
Hi,thanks again for the reply, here the results from the commands
Results for **sudo grep -v -e '#\|^$' /etc/sudoers**
```
fandreani@domain.it@sambaserver-l3-test:~$ sudo grep -v -e '#\|^$' /etc/sudoersDefaults    env_reset
Defaults    mail_badpass
Defaults    secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"
Defaults    use_pty
root    ALL=(ALL:ALL) ALL
%admin ALL=(ALL) ALL
%IT-Tech-Staff-Linux-Servers-L    ALL=(ALL)   ALL
%sudo    ALL=(ALL:ALL) ALL
%digital-tech-staff-sambaserver-L3-test-Admin-L   ALL=(ALL)    ALL
%IT-Tech-Staff-A-G    ALL=(ALL)   ALL
@includedir /etc/sudoers.d
```
the other command **sudo grep -v -e '#\|^$' /etc/sudoers.d/*** , displays nothing and yes I have rebooted the server

---

### Post by MAFoElffen on 2024-04-29
> **fandreani said:**
> 
```

%IT-Tech-Staff-Linux-Servers-L    ALL=(ALL)   ALL
%digital-tech-staff-sambaserver-L3-test-Admin-L   ALL=(ALL)    ALL
%IT-Tech-Staff-A-G    ALL=(ALL)   ALL

```

Lets see how those groups show up as(?)
```

getent group | grep -E 'IT-Tech-Staff-Linux-Servers-L|digital-tech-staff-sambaserver-L3-test-Admin-L|IT-Tech-Staff-A-G'

```
Then modify from that output...

---

### Post by ActionParsnip on 2024-04-29
If you run:
```

visudo -c

```
Does the file check as OK? If you also run:
```

id foo

```
(Change 'foo' for the actual username here). Do you see the names and IDs from you domain

---

### Post by fandreani on 2024-04-30
> **MAFoElffen said:**
> Lets see how those groups show up as(?)
```

getent group | grep -E 'IT-Tech-Staff-Linux-Servers-L|digital-tech-staff-sambaserver-L3-test-Admin-L|IT-Tech-Staff-A-G'

```
Then modify from that output...

Hi, I tried but this command shows nothing in the output

**EDIT:** I noticed that any user in our domain from others AD groups not specified in the sudoers file can authenticate via SSH but cannot execute commands because they are not listed in the sudoers file.
 Could there be something else we're overlooking?

---

### Post by fandreani on 2024-04-30
Hi, here the result for **#visudo -c**

```
fandreani@domain.it@sambaserver-l3-test:~$ sudo visudo -c/etc/sudoers: parsed OK
/etc/sudoers.d/README: parsed OK
```

and here the result of command **#id [EMAIL="fandreania@domain.it"]fandreania@domain.it[/EMAIL]** ,which is a member of the AD group [B]%[COLOR=#E8E6E3][FONT=&amp]IT-Tech-Staff-Linux-Servers-L
[/FONT][/COLOR][/B]```
[COLOR=#000000]fandreani@domain.it@sambaserver-l3-test:~$ id fandreania@domain.it[/COLOR][B][COLOR=#E8E6E3][FONT=&amp]
[/FONT][/COLOR][/B]
[COLOR=#000000]uid=952401222(fandreania@domain.it) gid=952400513(s-1-5-21-2495866372-2476539352-2360203011-513@domain.it) groups=952400513(s-1-5-21-2495866372-2476539352-2360203011-513@domain.it),952400572(s-1-5-21-2495866372-2476539352-2360203011-572@domain.it),952401374(s-1-5-21-2495866372-2476539352-2360203011-1374@domain.it),952401194(s-1-5-21-2495866372-2476539352-2360203011-1194@domain.it),952401193(s-1-5-21-2495866372-2476539352-2360203011-1193@domain.it),952401214(s-1-5-21-2495866372-2476539352-2360203011-1214@domain.it),952401156(s-1-5-21-2495866372-2476539352-2360203011-1156@domain.it),952403109(s-1-5-21-2495866372-2476539352-2360203011-3109@domain.it),952400512(s-1-5-21-2495866372-2476539352-2360203011-512@domain.it),952401179(s-1-5-21-2495866372-2476539352-2360203011-1179@domain.it),952401579(s-1-5-21-2495866372-2476539352-2360203011-1579@domain.it),952401524(s-1-5-21-2495866372-2476539352-2360203011-1524@domain.it)[/COLOR]
```[B][COLOR=#E8E6E3][FONT=&amp]
[/FONT][/COLOR][/B]I'm a bit confused from this output,  I didn't think there were numbers but rather names of the groups from AD.

---

### Post by MAFoElffen on 2024-05-01
I have a few things to try (one at a time.):
```

%SMB\\digital-tech-staff-sambaserver-L3-test-Admin-L ALL=(ALL) ALL
%digital-tech-staff-sambaserver-L3-test-Admin-L@DOMAIN.IT ALL=(ALL) ALL
%DOMAIN.IT\\digital-tech-staff-sambaserver-L3-test-Admin-L ALL=(ALL:ALL) ALL

```

---

### Post by fandreani on 2024-05-02
Hi, thanks for the reply,I tried all the three solutions provided without good results, still the message "xx@domain.it is not in the sudoers..."
Do you think the **sssd.conf** or **krb5.conf** files or something similar could be helpful to you?
I didn't handle the integration with AD myself,probably a colleague did a misconfiguration.
I'm not very experienced, just guessing, so feel free to correct me.

---

### Post by MAFoElffen on 2024-05-03
Yes please...

---

### Post by fandreani on 2024-05-06
Hi, this is the **sssd.conf file**
```
 [sssd]domains = domain.it
config_file_version = 2
services = nss, pam


[domain/domain.it]
default_shell = /bin/bash
krb5_store_password_if_offline = True
cache_credentials = True
krb5_realm = domain.it
realmd_tags = manages-system joined-with-adcli 
id_provider = ad
ldap_sasl_authid = SAMBASERVER-L3-$
fallback_homedir = /home/%u@%d
ad_domain = domain.it
use_fully_qualified_names = True
ldap_id_mapping = True
access_provider = ad
ad_gpo_access_control = permissive
```

and this is **krb5.conf**```
  [libdefaults]default_realm = DOMAIN.IT
    rdns=false
# The following krb5.conf variables are only for MIT Kerberos.
    kdc_timesync = 1
    ccache_type = 4
    forwardable = true
    proxiable = true


# The following encryption type specification will be used by MIT Kerberos
# if uncommented.  In general, the defaults in the MIT Kerberos code are
# correct and overriding these specifications only serves to disable new
# encryption types as they are added, creating interoperability problems.
#
# The only time when you might need to uncomment these lines and change
# the enctypes is if you have local software that will break on ticket
# caches containing ticket encryption types it doesn't know about (such as
# old versions of Sun Java).


#    default_tgs_enctypes = des3-hmac-sha1
#    default_tkt_enctypes = des3-hmac-sha1
#    permitted_enctypes = des3-hmac-sha1


# The following libdefaults parameters are only for Heimdal Kerberos.
    fcc-mit-ticketflags = true
udp_preference_limit = 0


[realms]
    ATHENA.MIT.EDU = {
        kdc = kerberos.mit.edu
        kdc = kerberos-1.mit.edu
        kdc = kerberos-2.mit.edu:88
        admin_server = kerberos.mit.edu
        default_domain = mit.edu
    }
    ZONE.MIT.EDU = {
        kdc = casio.mit.edu
        kdc = seiko.mit.edu
        admin_server = casio.mit.edu
    }
    CSAIL.MIT.EDU = {
        admin_server = kerberos.csail.mit.edu
        default_domain = csail.mit.edu
    }
    IHTFP.ORG = {
        kdc = kerberos.ihtfp.org
        admin_server = kerberos.ihtfp.org
    }
    1TS.ORG = {
        kdc = kerberos.1ts.org
        admin_server = kerberos.1ts.org
    }
    ANDREW.CMU.EDU = {
        admin_server = kerberos.andrew.cmu.edu
        default_domain = andrew.cmu.edu
    }
        CS.CMU.EDU = {
                kdc = kerberos-1.srv.cs.cmu.edu
                kdc = kerberos-2.srv.cs.cmu.edu
                kdc = kerberos-3.srv.cs.cmu.edu
                admin_server = kerberos.cs.cmu.edu
        }
    DEMENTIA.ORG = {
        kdc = kerberos.dementix.org
        kdc = kerberos2.dementix.org
        admin_server = kerberos.dementix.org
    }
    stanford.edu = {
        kdc = krb5auth1.stanford.edu
        kdc = krb5auth2.stanford.edu
        kdc = krb5auth3.stanford.edu
        master_kdc = krb5auth1.stanford.edu
        admin_server = krb5-admin.stanford.edu
        default_domain = stanford.edu
    }
        UTORONTO.CA = {
                kdc = kerberos1.utoronto.ca
                kdc = kerberos2.utoronto.ca
                kdc = kerberos3.utoronto.ca
                admin_server = kerberos1.utoronto.ca
                default_domain = utoronto.ca
    }


[domain_realm]
    .mit.edu = ATHENA.MIT.EDU
    mit.edu = ATHENA.MIT.EDU
    .media.mit.edu = MEDIA-LAB.MIT.EDU
    media.mit.edu = MEDIA-LAB.MIT.EDU
    .csail.mit.edu = CSAIL.MIT.EDU
    csail.mit.edu = CSAIL.MIT.EDU
    .whoi.edu = ATHENA.MIT.EDU
    whoi.edu = ATHENA.MIT.EDU
    .stanford.edu = stanford.edu
    .slac.stanford.edu = SLAC.STANFORD.EDU
        .toronto.edu = UTORONTO.CA
        .utoronto.ca = UTORONTO.CA 
```

---

### Post by achyachy007 on 2024-07-22
I have tried using quotation marks and it works

"%group-name"  ALL=(ALL:ALL) ALL

---

