---
title: "Fully functional LDAPS client deployment on Ubuntu Server 9.1"
date: 2010-06-23
forum: Outdated Tutorials &amp; Tips
---

### Post by mathlaura on 2010-06-23
I spent many hours and the use of a plethora of somewhat-contradictory tutorials and webpages to achieve a functional LDAP-integrated login using LDAP over ssl (ldaps://) on Ubuntu server 9.1.  Now that I've gotten it right, I'd like to share for the benefit of future hapless LDAP-setter-uppers who like me are looking to get ldaps functional.  

This is not going to cover setting up openldap, but tutorials can be found many other places, and I have found them to all be generally in agreement and functional.  This tutorial assumes that you have a functional LDAP server which is configured for SSL and listening on port 636.

*Log into your soon-to-be LDAP client.  You will need to install nss-ldap
    sudo apt-get install libnss-ldap

After the usual prompts about how much additional disk space will be used, you will enter the pseudo-gui setup screen.  
    Please enter the URI of the LDAP server to use
        ldaps://<your server name or IP>/    
    Please enter the distinguished name of the LDAP search base.
        dc=yourserver,dc=example,dc=com
    LDAP version to use    
        This should generally be 3
    Make local root Database admin:
        I have configured this for no.  You will need to know your own information for a privileged LDAP user if you wish to use yes.  This is only necessary if you would like to use linux user commands to modify LDAP entries.
    Does the LDAP database require login?
        This is also generally no.  
    An explanation of the various crypt options
    Local crypt to use when changing passwords:
        Select exop

If you make any mistakes during this process, or need to change anything, it is possible to make changes via the various .conf files, but you can also use sudo dpkg-reconfigure ldap-auth-config to get the screen prompts again.

(I have also automated this process using debconf-utils seed files.  I can expound on this if people are interested.  For my purpose, I have scripted this process to configure LDAPS authentication on hundreds of servers.)

You will need to configure 3 configuration files now: /etc/nsswitch.conf, /etc/ldap.conf, /etc/ldap/ldap.conf 

    sudo vi /etc/nsswitch.conf (Or of course your preferred text editor)
    You will want to change the following lines:

        passwd:         compat
        group:           compat
        shadow:         compat

    to
        passwd:         files ldap
        group:           files ldap
        shadow:         files ldap

    Save these changes.  (I also found that compat ldap rather than files ldap was successful.)

    check /etc/ldap.conf with your preferred text editor, and ensure that it contains the following lines:

        base dc=yourserver,dc=example,dc=com
        uri ldaps://<your server name or IP>/
        
    and ensure that there is NO line which is not commented out which starts with "host"
    These settings should have been set correctly by the prompts at the time of installing libnss-ldap

    Now you will need to copy the certificate from your openldap server to the client.  Make sure that you copy the certificate which is referenced in your openldap configuration (slapd.conf) as "TLSCACertificateFile    yourcert.pem".  I copied this to /etc/ldap/certs, but you can put it anywhere as long as you know where it is on the client machine.

    Now, use your favorite text editor to open /etc/ldap/ldap.conf and edit it to have the following lines:

        BASE    dc=yourserver,dc=example,dc=com
        URI     ldaps://<your server name or IP>/
        TLS_CACERT /etc/ldap/certs/yourcert.pem
        TLS_REQCERT never

Other tutorials I have found suggest allowing RLS_REQCERT, but this broke my LDAPS setup and led to a lot of headaches looking for the problem.

Save, and you should have a functional LDAPS installation.  Type
       
    getent passwd

and you should see a listing of your LDAP users.

If you would like to make an LDAP user a sudoer for the client, you can use
    adduser ldapusername admin

---

