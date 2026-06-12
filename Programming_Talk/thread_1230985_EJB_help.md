---
title: "EJB help"
date: 2009-08-04
forum: Programming Talk
---

### Post by mthalis on 2009-08-04
I installed Java using ```
sudo apt-get install ..
``` and also run ```
sudo update-java-alternatives -s java-6-sun
``` this command.

Below shown my /etc/enviroment file 
```

PATH="/usr/lib/jvm/java-6-sun-1.6.0.14/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.14"
CLASSPATH="/usr/lib/jvm/java-6-sun-1.6.0.14/lib"

``` 

In that file JAVA_HOME,CLASSPATH and /usr/lib/jvm/java-6-sun-1.6.0.14/bin I manually set.

I wrote below script compile my Java files

```

#!/bin/sh
set CLASSPATH=.;%J2EE_HOME%\lib\j2ee.jar

javac -deprecation -d . vtcbean/*.java

```

Below error happen

```

ites@ites-desktop:~/Music/jwork/beans/ccount$ ./buildbean
: not found: 2: %J2EE_HOME%libj2ee.jar
vtcbean/Ccount.java:3: package javax.ejb does not exist
import javax.ejb.EJBObject;
                ^
vtcbean/Ccount.java:6: cannot find symbol
symbol: class EJBObject
public interface Ccount extends EJBObject {
                                ^
vtcbean/CcountBean.java:3: package javax.ejb does not exist
import javax.ejb.SessionBean;
                ^
vtcbean/CcountBean.java:4: package javax.ejb does not exist
import javax.ejb.SessionContext;
                ^
vtcbean/CcountBean.java:6: cannot find symbol
symbol: class SessionBean
public class CcountBean implements SessionBean {
                                   ^
vtcbean/CcountBean.java:12: cannot find symbol
symbol  : class SessionContext
location: class vtcbean.CcountBean
    public void setSessionContext(SessionContext context) {}
                                  ^
vtcbean/CcountHome.java:3: package javax.ejb does not exist
import javax.ejb.EJBHome;
                ^
vtcbean/CcountHome.java:4: package javax.ejb does not exist
import javax.ejb.CreateException;
                ^
vtcbean/CcountHome.java:7: cannot find symbol
symbol: class EJBHome
public interface CcountHome extends EJBHome {
                                    ^
vtcbean/CcountHome.java:8: cannot find symbol
symbol  : class CreateException
location: interface vtcbean.CcountHome
    public Ccount create() throws CreateException, RemoteException;
                                  ^
10 errors


```

I think it can't find **j2ee.jar** file, I search that file in my machine but couldn't find it. How can fix it. Please help me.

---

### Post by hoboy on 2009-08-04
this is your error
%J2EE_HOME%libj2ee.jar  it should be like %J2EE_HOME%lib/j2ee.jar

---

### Post by mthalis on 2009-08-04
This is my new script 
> 
#!/bin/sh
set CLASSPATH=.;%J2EE_HOME%/lib/j2ee.jar

javac -deprecation -d . vtcbean/*.java


but same error happen

> 
ites@ites-desktop:~/Music/jwork/beans/ccount$ ./buildbean 
: not found: 2: %J2EE_HOME%/lib/j2ee.jar
vtcbean/Ccount.java:3: package javax.ejb does not exist
import javax.ejb.EJBObject;
                ^
vtcbean/Ccount.java:6: cannot find symbol
symbol: class EJBObject
public interface Ccount extends EJBObject {
                                ^
vtcbean/CcountBean.java:3: package javax.ejb does not exist
import javax.ejb.SessionBean;
                ^
vtcbean/CcountBean.java:4: package javax.ejb does not exist
import javax.ejb.SessionContext;
                ^
vtcbean/CcountBean.java:6: cannot find symbol
symbol: class SessionBean
public class CcountBean implements SessionBean {
                                   ^
vtcbean/CcountBean.java:12: cannot find symbol
symbol  : class SessionContext
location: class vtcbean.CcountBean
    public void setSessionContext(SessionContext context) {}
                                  ^
vtcbean/CcountHome.java:3: package javax.ejb does not exist
import javax.ejb.EJBHome;
                ^
vtcbean/CcountHome.java:4: package javax.ejb does not exist
import javax.ejb.CreateException;
                ^
vtcbean/CcountHome.java:7: cannot find symbol
symbol: class EJBHome
public interface CcountHome extends EJBHome {
                                    ^
vtcbean/CcountHome.java:8: cannot find symbol
symbol  : class CreateException
location: interface vtcbean.CcountHome
    public Ccount create() throws CreateException, RemoteException;
                                  ^
10 errors



I think missing **j2ee.jar** how can I fix it? please help me

---

### Post by hoboy on 2009-08-04
> **mthalis said:**
> This is my new script 


but same error happen



I think missing **j2ee.jar** how can I fix it? please help me

This  ;%J2EE_HOME%\  should point to an j2ee home
you can downlaod it from here

[http://java.sun.com/javaee/downloads/index.jsp?userOsIndex=1&userOsId=linux&userOsName=Linux](http://java.sun.com/javaee/downloads/index.jsp?userOsIndex=1&userOsId=linux&userOsName=Linux)

---

### Post by mthalis on 2009-08-04
Can I install it using **apt-get install**?

Note : I installed netbeans 6.7

---

### Post by hoboy on 2009-08-04
> **mthalis said:**
> Can I install it using **apt-get install**?

Note : I installed netbeans 6.7

Nop. ok are you using Netbeans ? if so what type of project you have created ?

If you have problem of getting j2ee.jar  and you are using NetBeans just create java EE project/EJB Module then expend Glssfish/ then get javaee.jar that shuod do the trick

---

### Post by mthalis on 2009-08-04
I'm beginer for EJB, then I don't want use netbeans I created Java files using text editor and  want to compile and run it.

**Ccount.java**
```

package vtcbean;
import javax.ejb.EJBObject;
import java.rmi.RemoteException;

public interface Ccount extends EJBObject {
    public int characters(String str) throws RemoteException;
    public int upper(String str) throws RemoteException;
    public int lower(String str) throws RemoteException;
    public int spaces(String str) throws RemoteException;

}

```

**CcountBean.java**
```

package vtcbean;

import javax.ejb.SessionBean;
import javax.ejb.SessionContext;


public class CcountBean implements SessionBean {
    public void ejbActivate() {}
    public void ejbPassivate() {}
    public void ejbCreate() {}
    public void ejbPostCreate() {}
    public void ejbRemove() {}

    public void setSessionContext(SessionContext context) {}

    public int characters(String str) { 
        return(str.length());
    }

    public int upper(String str) { 
        int count = 0;
        for(int i=0; i<str.length(); i++) {
           if(Character.isUpperCase(str.charAt(i)))
               count++;
        }
        return(count);
    }

    public int lower(String str) { 
        int count = 0;
        for(int i=0; i<str.length(); i++) {
           if(Character.isLowerCase(str.charAt(i)))
               count++;
        }
        return(count);
    }

    public int spaces(String str) { 
        int count = 0;
        for(int i=0; i<str.length(); i++) {
           if(Character.isWhitespace(str.charAt(i)))
               count++;
        }
        return(count);
    }
}


```

**CcountHome.java**
```

package vtcbean;

import javax.ejb.EJBHome;
import javax.ejb.CreateException;
import java.rmi.RemoteException;


public interface CcountHome extends EJBHome {
    public Ccount create() throws CreateException, RemoteException;

}


```

META-INF folder contain **ejb-jar.xml**

```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE ejb-jar PUBLIC '-//Sun Microsystems, Inc.
//DTD Entereprise JavaBeans 2.0//EN'
'http://java.sun.com/dtd/ejb-jar_2_0.dtd'>


<ejb-jar>
    <display-name>Ejb1</display-name>
    <enterprise-beans>
        <session>
            <display-name>CcountBean</display-name>
            <ejb-name>CcountBean</ejb-name>
            <home>vtcbean.CcountHome</home>
            <remote>vtcbean.Ccount</remote>
            <ejb-class>vtcvean.CcountBean</ejb-class>
            <session-type>Stateless</session-type>
            <transaction-type>Bean</transaction-type>
            <security-identity>
                <description></description>
                <use-caller-identity></use-caller-identity>
            </security-identity>
        </session>
    </enterprise-beans>
</ejb-jar>


```
Again how can I compile it....

---

### Post by jespdj on 2009-08-04
> **mthalis said:**
> ```

#!/bin/sh
set CLASSPATH=.;%J2EE_HOME%\lib\j2ee.jar

javac -deprecation -d . vtcbean/*.java

```
This looks like it's written for Windows. It works differently on Unix-like operating systems:

```
#!/bin/sh
set CLASSPATH=.:$J2EE_HOME/lib/j2ee.jar

javac -deprecation -d . vtcbean/*.java
```
Note:
[LIST]
[*]Use ':' instead of ';' to separate path entries.
[*]Use '$...' instead of '%...%' to get the value of an environment variable.
[*]Use '/' instead of '\' in paths.
[/LIST]

---

### Post by mthalis on 2009-08-04
I installed j2ee and set $J2EE_HOME

below show my /etc/environment
> 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
J2EE_HOME="/home/ites/SDK"

I configured my script also

> 
#!/bin/sh
set CLASSPATH=.:$J2EE_HOME/lib/j2ee.jar
javac -deprecation -d . vtcbean/*.java


but same error happen

> 
ites@ites-desktop:~/Music/jwork/beans/ccount$ ./buildbean 
vtcbean/Ccount.java:3: package javax.ejb does not exist
import javax.ejb.EJBObject;
                ^
vtcbean/Ccount.java:6: cannot find symbol
symbol: class EJBObject
public interface Ccount extends EJBObject {
                                ^
vtcbean/CcountBean.java:3: package javax.ejb does not exist
import javax.ejb.SessionBean;
                ^
vtcbean/CcountBean.java:4: package javax.ejb does not exist
import javax.ejb.SessionContext;
                ^
vtcbean/CcountBean.java:6: cannot find symbol
symbol: class SessionBean
public class CcountBean implements SessionBean {
                                   ^
vtcbean/CcountBean.java:12: cannot find symbol
symbol  : class SessionContext
location: class vtcbean.CcountBean
    public void setSessionContext(SessionContext context) {}
                                  ^
vtcbean/CcountHome.java:3: package javax.ejb does not exist
import javax.ejb.EJBHome;
                ^
vtcbean/CcountHome.java:4: package javax.ejb does not exist
import javax.ejb.CreateException;
                ^
vtcbean/CcountHome.java:7: cannot find symbol
symbol: class EJBHome
public interface CcountHome extends EJBHome {
                                    ^
vtcbean/CcountHome.java:8: cannot find symbol
symbol  : class CreateException
location: interface vtcbean.CcountHome
    public Ccount create() throws CreateException, RemoteException;
                                  ^
10 errors
ites@ites-desktop:~/Music/jwork/beans/ccount$ 



How can I fixed it?

---

### Post by jespdj on 2009-08-06
Are you sure that $J2EE_HOME is set correctly and that the CLASSPATH really points to the right place? Try this:
```
javac -deprecation -cp .:/home/ites/SDK/lib/j2ee.jar -d . vtcbean/*.java
```
Check if j2ee.jar is indeed present in the directory /home/ites/SDK/lib.

---

