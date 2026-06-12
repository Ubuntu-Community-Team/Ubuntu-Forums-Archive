---
title: "How do I manage multi user, multi system passwords?"
date: 2016-06-01
forum: New to Ubuntu
---

### Post by Joe_Willmann on 2016-06-01
I want to build a network with several Ubuntu servers for development purposes.  I want any user to be able to lo on to any machine and have everything just work.

I also want to support thin client machines.  How do you configure thin clients so that they access some centralized user/password server for authentication purposes?

Is ldap the right tool?  And if so how do you configure Ubuntu to use ldap data base to authenticate users?

---

### Post by HermanAB on 2016-06-02
Google "linux nfs home" and "linux ldap howto".

---

### Post by Joe_Willmann on 2016-06-02
Thanks, that led me to what I needed to learn
Key points:
mfs [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
setting up LDAP server [URL="https://help.ubuntu.com/community/OpenLDAPServer"]https://help.ubuntu.com/community/OpenLDAPServer
[/URL]setting up LDAP clients [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)

Then the meet of the matter [https://help.ubuntu.com/community/SingleSignOn](https://help.ubuntu.com/community/SingleSignOn)
That was the key!

I just didn't know what to look for.

---

### Post by Tadaen_Sylvermane on 2016-06-05
Look into ltsp for the thin clients as well.

---

