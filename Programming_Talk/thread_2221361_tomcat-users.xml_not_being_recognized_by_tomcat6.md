---
title: "tomcat-users.xml not being recognized by tomcat6"
date: 2014-05-01
forum: Programming Talk
---

### Post by awclemen on 2014-05-01
Hello Forum-folks,

Well, I'm at my wits end.  I'm trying to get to the manager/html page, but I keep running into the the 401 Unauthorized error.  I'm running tomcat 6.0.35 on 12.04.4 LTS.

Here's the tomcat-users.xml file:

```

<?xml version='1.0' encoding='utf-8'?>
<tomcat-users>
  <role rolename="tomcat"/>
  <role rolename="role1"/>
  <role rolename="manager-gui"/>
  <user username="tomcat" password="tomcat" roles="manager-gui"/>
  <user username="both" password="tomcat" roles="tomcat,role1"/>
  <user username="role1" password="tomcat" roles="role1"/>
</tomcat-users>

```

The server:8080 page of the site says to use the "manager" role, but the documentation and the 401 error page say to use the "manager-gui" role.  Neither work.  Here's the important parts of the server.xml file:

```

    <!-- Editable user database that can also be used by
         UserDatabaseRealm to authenticate users
    -->
    <Resource name="UserDatabase" auth="Container"
              type="org.apache.catalina.UserDatabase"
              description="User database that can be updated and saved"
              factory="org.apache.catalina.users.MemoryUserDatabaseFactory"
              pathname="/etc/tomcat6/tomcat-users.xml" />

      <!-- This Realm uses the UserDatabase configured in the global JNDI
           resources under the key "UserDatabase".  Any edits
           that are performed against this UserDatabase are immediately
           available for use by the Realm.  -->
      <Realm className="org.apache.catalina.realm.UserDatabaseRealm"
             resourceName="UserDatabase"/>


```

I had to edit the Resource tag's pathname parameter from "conf/tomcat-users.xml" to "/etc/tomcat6/tomcat-users.xml".  The "conf/tomcat-users.xml" file does not exist when I do a find over the whole server:

```
root@SERVERNAME:/etc/tomcat6# find / -name "tomcat-users.xml"
/etc/tomcat6/tomcat-users.xml

```

I have restarted tomcat6 EVERY time I change a configuration file:

```
service tomcat6 restart
```

and restarted the browser every time.  I can't find anything in the logs about any errors.  Is there anyway to turn on a debug feature to see where Tomcat is looking for the credentials?

Any ideas are welcome.  Thanks in advance for any help.

--FRB

---

### Post by Habitual on 2014-05-02
my /etc/tomcat6/tomcat-users.xml shows this entry:
It is the only edit I made to allow my "SomeAdmin" user to access the Manager.
And this blurb is NOT from an Ubuntu install (not that it matters)...
```
<tomcat-users>
<!--
  <role rolename="tomcat"/>
  <role rolename="role1"/>
  <user username="tomcat" password="tomcat" roles="tomcat"/>
  <user username="both" password="tomcat" roles="tomcat,role1"/>
  <user username="role1" password="tomcat" roles="role1"/>
-->

<!-- The host manager webapp is restricted to users with role "admin" -->
<!--<user name="tomcat" password="password" roles="admin" />-->
<!-- [COLOR=#ff0000]The manager webapp is restricted to users with role "**manager**[/COLOR]" -->
 <user name="SomeAdmin" password="AdminPassword" roles="manager" />
</tomcat-users>
```

Save, bounce and check.
Hope that helps.

---

### Post by awclemen on 2014-05-15
Thanks for your help Habitual, but I found what my problem was.  I had two Realms for security in my server.xml - In my old version of JBoss I was able to use multiple Realms, but maybe not Tomcat?  I'm probably missing something in my set up.  Thanks again for your help!

---

