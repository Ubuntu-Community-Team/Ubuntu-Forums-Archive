---
title: "[SOLVED] Java Plugin Help"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by Promaster91 on 2008-06-05
I have the jre, java plugin and jdk (I code in java) installed on my ubuntu computer. When I try to view an applet in Firefox 2, I get an error message saying that I have to install the jre. However I have the jre installed.
```

stefan@stefan-laptop:~$ java -version
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Server VM (build 1.6.0-b09, mixed mode)
stefan@stefan-laptop:~$ 

```
I have no idea what is going on. I can run and compile .java files, it is just the applets in the web browsers that I can't run. Can somebody help me? Thanks in advance.

---

### Post by iaculallad on 2008-06-05
Open your Firefox browser and type this at the address bar: **about:plugins** (about.colon.plugins) to see if jre is installed for Firefox.

---

### Post by Promaster91 on 2008-06-05
No. The only one I see is flash. I installed the java plugin through add/remove. Should I install it a different way?

---

### Post by jamesstansell on 2008-06-06
> **Promaster91 said:**
> No. The only one I see is flash. I installed the java plugin through add/remove. Should I install it a different way?

If you are comfortable with manual configuration and using the command line, you should be able to add a symbolic link (ln -s) to the plugin in your ~/.mozilla/plugins/ directory to get it to work.  The link to use would depend on which plugin you have.  (Remember to remove the link when it's no longer needed.)

Which plugin package do you have installed?  Based on the java version you showed I assume it is icedtea-gcjwebplugin.  But what I typed below probably applies more to the sun-java6-plugin package.

You may be running into a known bug with packaging related to the Firefox 2 browser.  If you use Firefox 3 it should be able to see the plugin.  One of the java packages is being tested and should show up in the hardy-updates repository soon (maybe next week?)

If you want to take some manual steps there would be several options, including one in the bug report.  Sorry, I don't have the reference handy, and am short on time to look it up right now.

---

### Post by NilsE on 2008-06-06
I did not get satisfactory results until I removed all Java packages and installed sun-java 6.  It then showed up in plugins and started working.

The bottom line is gcj and open versions are still in development and can be problematic.

---

### Post by Promaster91 on 2008-06-17
Ok, I fixed it by uninstalling firefox and removing .mozilla from my home folder. Thanks for your help.

---

