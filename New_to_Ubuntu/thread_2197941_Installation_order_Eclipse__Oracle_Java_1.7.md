---
title: "Installation order Eclipse / Oracle Java 1.7"
date: 2014-01-06
forum: New to Ubuntu
---

### Post by guy.dillen on 2014-01-06
What is the correct installation order when I want Oracle 1.7 as my default java jdk version? I first installed Oracle java jdk 1.7 followed by Eclipse (using the Ubuntu Software Center) but obviously this installs also a version of openjdk - and makes this the default version?!

Thanks.

---

### Post by theDaveTheRave on 2014-01-06
you can tell eclipse which version of the jdk you want to use. It is however tucked away in one of the settings somewhere.... I forget exactly where.

Also openJDK is in fact more advanced than the oracle version, the only thing that you won't find in the openJDK is the JDBC/ODBC bridge.

If you read up on how openJDK and oracle are moving, there seems to be an agreement that the oracle JDK will follow the openJDK, so much so that most of the development seems to be occuring on the openJDK branch, with the potential that there will be only the openJDK at some point in the future. Notwithstanding the JDBC/ODBC connector that is only available from oracle... however if you use  [http://grepcode.com/](http://grepcode.com/) you can find all the code required to get your own personal version of the connector.

From what I can tell the only reason that the connector isn't in openJDK is a problem with the licence.

David

---

