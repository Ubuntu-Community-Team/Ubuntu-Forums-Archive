---
title: "Looking for Beta Testers!"
date: 2009-03-17
forum: Programming Talk
---

### Post by kavon89 on 2009-03-17
I have been developing a password manager called Cosis for some time, and now I need some public testers to give me feedback and to help me identify bugs and problems. 

I especially need people who run Mac OS X, Windows, Linux with KDE, or Solaris to look for any problems and try to break it as much as possible. ;)

[Download & View screenshots here!]("http://cosis.googlecode.com")

Description from my project page:

> In these days of heightened technology use, it is a struggle to keep track of every username and password that one uses. The possible solutions of using the same password repeatedly and putting sensitive data into ordinary text files are both hazards to security. The solution is Cosis, an account manager. The objective of Cosis is to provide a simple, easy, and secure way to store and retrieve account information for immediate and future use.

Some features of Cosis include:

    * Easy to use interface
    * Cross-platform compatibility, working on any system that has Java installed
    * Capable of supporting multiple users, ideal for shared computers
    * Data backup to prevent loss of information
    * Portable data files
    * Strong 128-bit AES encryption 

---

### Post by soltanis on 2009-03-17
Well for your first bug, your "outdated java version dialog" seems to not respond to clicking on the "Ok" button (or the close the damn window button, for that matter).

Steps to reproduce:

- Install JVM 1.5.
- Run java -jar Cosis.jar
- Observe window
- Attempt to close window via "Ok"
- Attempt to close window via "x" in the upper right hand corner
- Conclude something is wrong and kill -9 the app.

---

### Post by jimi_hendrix on 2009-03-17
i have not tried it but i like what i see...good work

---

### Post by kavon89 on 2009-03-17
> **soltanis said:**
> Well for your first bug, your "outdated java version dialog" seems to not respond to clicking on the "Ok" button (or the close the damn window button, for that matter).

Steps to reproduce:

- Install JVM 1.5.
- Run java -jar Cosis.jar
- Observe window
- Attempt to close window via "Ok"
- Attempt to close window via "x" in the upper right hand corner
- Conclude something is wrong and kill -9 the app.

Tried to reproduce this on a virtual install of Windows XP with Java 5 update 17 and I have no issues pressing OK or the X to close the window. Seems odd that this would even happen, this is the only code which would be executed if a user's Java doesn't meet my requirements:

```
double javaVersion = Double.valueOf(System.getProperty("java.specification.version"));
        if(javaVersion < 1.6) {
            JOptionPane.showMessageDialog(null, "Your system has an outdated version of the Java Runtime Environment (" + javaVersion + ").\n"
                    + "Please update your version to 1.6 or greater: www.java.com/getjava", "Outdated Java - " + Main.NAME, JOptionPane.INFORMATION_MESSAGE);
            System.exit(0);
        }
```

---

