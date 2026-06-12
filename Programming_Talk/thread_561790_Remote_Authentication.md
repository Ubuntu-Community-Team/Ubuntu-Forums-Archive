---
title: "Remote Authentication"
date: 2007-09-28
forum: Programming Talk
---

### Post by shoaibi on 2007-09-28
I am developing a java application  which takes username and password from the user, and then authenticates it from the linux operating system.
How is that possible? i mean the authentication part?
is there a service/daemon that can perform user authentication on behalf of a request from a java application? if yes, can you provide details on how to use that?

---

### Post by amo-ej1 on 2007-09-28
Well when you say authentication in a Linux context, I immediately think 'PAM', when googling for Java and PAM I ended up at JPAM: [http://jpam.sourceforge.net/](http://jpam.sourceforge.net/) which bridges java to PAM.

The samples at: [http://jpam.sourceforge.net/samples.html](http://jpam.sourceforge.net/samples.html) seem straightforward, so I think this might actually be useful to you.

---

### Post by amo-ej1 on 2007-09-28
But I've seemed to 'missed' the remote part of your subject. So basicly you can't do authentication with Linux system X when you application runs on system Y (where X != Y). In that case you will need to have some sort of proxy application installed on the system that has access to the authentication source.

---

### Post by shoaibi on 2007-10-06
Okay, here is the problem.
I have downloaded JPAM 1.1 for Linux and installed as it was told in the INSTALL File and the Online Documentation.
But i had this problem that the $java_home/bin/x where x=client OR server didn't exist. So i created both folders and pasted the libjpam.so file there.

After that i ran my code(provided below), and it gave exceptions. I read the manual again, and it says, if the JPAM can't find files, it will seach in local fodler as well, so i made a copy in local folder as well. and ran the same code again but the same ClassNotFound Exception appeared.

I posted on JPAM Forums, but no one replied, so i am posting it here so that if anyone knows JPAM, i would request his help.


Here is the list of pam modules that i have installed:
```

pam_krb5-2.2.11-1
pam_smb-1.1.7-7.2.1
pam_pkcs11-0.5.3-23
pam-0.99.6.2-3.14.el5
pam_ccreds-3-5
pam_passwdqc-1.0.2-1.2.2
pam-devel-0.99.6.2-3.14.el5


```

Here is the code:
```

/*
 * Main.java
 *
 * Created on October 2, 2007, 12:09 PM
 *
 * To change this template, choose Tools | Template Manager
 * and open the template in the editor.
 */

package autenticate;
import net.sf.jpam.*;
/**
 *
 * @author shoaibi
 */
public class Main {
    
    /** Creates a new instance of Main */
    public Main() {
    }
    
    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        String user1Name = "test";
        String user1Credentials = "password";
        Pam mypam = new Pam(); //When i click the link in error, i get here.
        boolean authenticated = mypam.authenticateSuccessful(user1Name, user1Credentials);
        if(authenticated ==true)
        {
            System.out.println("Congrats\nYou have logged In");
            
        }
        else
            System.out.println("Sorry\nAuthentication Failed");
    }
    
}



```


Here is the Error:
```

Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/commons/logging/LogFactory
        at net.sf.jpam.Pam.<clinit>(Pam.java:38)
        at autenticate.Main.main(Main.java:28) //this points to the Pam object creation line
Java Result: 1

```


What could possibly go wrong?

I have JDK6u2 installed. and i set all classpaths and etc....

---

### Post by tenmillionmilesaway on 2007-10-06
From the JPam manual:
> 
3.2 Mandatory Java Dependencies
JPam requires commons-logging commons-logging is a very common dependency, and is therefore not
included in the distribution.
Jpam also requires JAAS. Originally introduced as an optional package (JAAS 1.0) to version 1.3 of the
Java 2 SDK, JAAS has now been integrated into the Java 2 SDK, version 1.4.

The problem is you dont have those jars on your classpath

Richard

---

### Post by shoaibi on 2007-10-07
The link given for common-logging in their documentation wasn't valid, besides they said that its a very common dependency, so i thought i would already have it, and then about JAAS, i have the JDK6u2, i think it is built in to it, isn't it?

---

### Post by shoaibi on 2007-10-07
Here is the list of my commons dependencies, which shows that i have a commons-logging dependency installed, haven't i?
```

xml-commons-resolver-1.1-1jpp.12
jakarta-commons-collections-3.1-6jpp.1
jakarta-commons-el-1.0-7jpp.1
jakarta-commons-discovery-0.3-4jpp.1
glibc-common-2.5-12
vim-common-7.0.109-3
sgml-common-0.6.3-18
xml-commons-apis-1.3.02-0.b2.7jpp.10
jakarta-commons-fileupload-1.0-6jpp.1
jakarta-commons-dbcp-1.2.1-7jpp.1
jakarta-commons-modeler-1.1-8jpp.1
tomcat5-common-lib-5.5.17-8jpp.2
samba-common-3.0.23c-2
xml-common-0.6.3-18
libibcommon-1.0.1-5.el5
jakarta-commons-codec-1.3-7jpp.2
jakarta-commons-logging-1.0.4-6jpp.1
jakarta-commons-digester-1.7-5jpp.1
jakarta-commons-pool-1.3-5jpp.1
jakarta-commons-validator-1.1.4-5jpp.1
jakarta-commons-daemon-1.0.1-6jpp.1
php-common-5.1.6-5.el5
xml-commons-1.3.02-0.b2.7jpp.10
jakarta-commons-httpclient-3.0-7jpp.1
jakarta-commons-beanutils-1.7.0-5jpp.1
jakarta-commons-launcher-0.9-6jpp.1

```

---

