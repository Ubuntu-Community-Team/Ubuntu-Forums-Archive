---
title: "[SOLVED] JAVA_HOME and tomcat problem"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by bump_ on 2008-07-02
Hello,

I am having a problem with tomcat. I installed tomcat5.5 from the repositories. When I try to run the startup.sh or shutdown.sh scripts as root, I get an error:

```
bump@bump-laptop:/usr/share/tomcat5.5/bin$ sudo ./startup.sh 
Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program

bump@bump-laptop:/usr/share/tomcat5.5/bin$ sudo ./shutdown.sh 
Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program

```

I have set JAVA_HOME in both .bashrc and /etc/environment to:

```

JAVA_HOME=/usr/lib/jvm/java-6-openjdk/

```
but the I still get the same errors.

Curiously, when I run either scripts as a normal user, it starts up and goes until a permission denied error is thrown.

```

bump@bump-laptop:/usr/share/tomcat5.5/bin$ ./startup.sh 
Using CATALINA_BASE:   /usr/share/tomcat5.5
Using CATALINA_HOME:   /usr/share/tomcat5.5
Using CATALINA_TMPDIR: /usr/share/tomcat5.5/temp
Using JRE_HOME:       /usr/lib/jvm/java-6-openjdk/
touch: cannot touch `/usr/share/tomcat5.5/logs/catalina.out': Permission denied
./catalina.sh: 348: cannot create /usr/share/tomcat5.5/logs/catalina.out: Permission denied


```

Does this indicate root doesn't see the environment variables?

---

### Post by bump_ on 2008-07-02
After an hour or two working on this, I've found a solution.

For some reason, it does not work when i type

```
sudo ./startup.sh
```

I get the aforementioned error. 

but for some reason when i do:

```

sudo -s
./startup.sh

```

It works.

Could someone explain the difference between using sudo and running as root?

---

### Post by Jeff250 on 2008-07-02
**sudo** by default resets your environment variables.  **sudo -s** runs your default shell, so this is equivalent to running **sudo bash**.  So even though your environment was reset when running **sudo -s**, **.bashrc** was read in after it was reset when **sudo** launches **bash** with root privileges, so any environment settings in **.bashrc** were restored.  Note that **sudo -E** prevents your environment from being reset.

**sudo** resets your environment by default for security; for example, if it did not reset the environment, since many programs use environment variables to determine how they will behave, a malicious program executed as a normal user could manipulate environment variables in a way such that when you go to run a program with sudo, it reads in malicious environment variables and does something malicious.  In other words, programs executed as normal users could have ways of manipulating how programs run as root if the environment is not reset by sudo.

---

### Post by bab1 on 2008-07-02
I would add that sudo (based on su) can be used to switch users to OTHER than root.  su = switch user.  Most use it to run root commands.  I'll bet that is why it has all the various switches. ;-)

---

### Post by bump_ on 2008-07-02
Thanks for that. I wish I knew that earlier. sudo -E looks useful in this case.

---

### Post by bab1 on 2008-07-02
Ahhhh bump_, that's what the man pages are for.  ;-)

---

