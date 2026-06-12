---
title: "[SOLVED] j2me with netbeans"
date: 2008-12-19
forum: Programming Talk
---

### Post by leg on 2008-12-19
Have recently installed netbeans and have now installed the mobility plugin and the mobile development toolkit plugin. Every time I try to create a new mobile project I get the message "No j2me compatible platform is installed in the ide ...". What have I done wrong.

---

### Post by cl333r on 2008-12-19
If you installed the plugin(s) check whether the Java ME platform is listed under Tools->Java platforms along with the other platforms, like on the screenshot.

---

### Post by drubin on 2008-12-19
> **leg said:**
> Have recently installed netbeans and have now installed the mobility plugin and the mobile development toolkit plugin. Every time I try to create a new mobile project I get the message "No j2me compatible platform is installed in the ide ...". What have I done wrong.

Have you installed the [WTK]("http://java.sun.com/products/sjwtoolkit/download.html")

---

### Post by leg on 2008-12-20
> **cl333r said:**
> If you installed the plugin(s) check whether the Java ME platform is listed under Tools->Java platforms along with the other platforms, like on the screenshot.
No it isn't listed like that I only  have the jdk 1.6 platform listed there.

> **drubin said:**
> Have you installed the [WTK]("http://java.sun.com/products/sjwtoolkit/download.html")
Now this is something I suspected might be the case. Are you saying that the toolkit plugin within NetBeans is a wrapper for the actual WTK?

---

### Post by drubin on 2008-12-20
> **leg said:**
> No it isn't listed like that I only  have the jdk 1.6 platform listed there.


Now this is something I suspected might be the case. Are you saying that the toolkit plugin within NetBeans is a wrapper for the actual WTK?

YES :)

With out the WTK you wont be able to compile for mobile and the mobile platforms... Netbeans is just the GUI for this

---

### Post by leg on 2008-12-20
Thanks Drubin downloading now!

---

### Post by drubin on 2008-12-22
> **leg said:**
> Thanks Drubin downloading now!

Let us know if this solved your issue :)

---

### Post by leg on 2008-12-28
> **drubin said:**
> Let us know if this solved your issue :)Yes it did thanks.

---

### Post by BrianB2 on 2010-06-06
In the past I've used the standalone netbeans installer from the sun/oracle web site. I recently did a clean install of lucid and noticed the universe repository has a package called "netbeans" (version 6.8-0ubuntu5) and decided to install this deb instead.

The installation process detected that I already had the "sun-java6-jdk" package installed and correctly configured this as my netbeans default j2se platform.

However, I couldn't find a deb package corresponding to the j2me wireless toolkit. I downloaded the standalone installer from [http://java.sun.com/products/sjwtoolkit/download.html]("http://java.sun.com/products/sjwtoolkit/download.html") (2.5.2_01 for CLDC), chmoded to permit execution and ran it as sudo because I wanted to install it for global use. This installer couldn't find my java installation, so I had to point it to "/usr/lib/jvm/java-6-sun/bin".

All the help I could find referred to old versions of netbeans and the dialogues no longer exist. Here's how I integrated the wtk into the lucid netbeans package...

1. tools -> plugins:- mark the "Mobility" plugin for installation. Permit netbeans to shutdown and restart.
2. tools -> Java Platforms:- click the "Add Platform" button. Select "Java ME MIDP Platform Emulator" and navigate the file chooser dialog to the directory where you installed the toolkit (e.g. /opt/WTK2.5.2). The toolkit attributes are displayed and you click next and then finish.

If you redisplay your java platforms, the j2me toolkit is listed above the j2se one.

---

### Post by BrianB2 on 2010-06-23
When I tried to run or debug my midlet I found I needed an internal web server to run the kvm. I went to the available plugins and installed "java web applications", which gave me a choice, and I took the default of Glassfish-v3. I then went through the dialogue to download it and accept the license agreement.

After restarting netbeans (all this as sudo so the installs go to system-wide locations): tools -> servers -> add server -> choose glassfish in its downloaded directory and configure it. Choose a master password. In order to run the web server as a normal user, chmod go+r the ~~/domains/Glassfish_v3/master_password file. (It isn't a bad idea to do the same for ~~/domains/Glassfish_v3/config/ and its files, too.)

Beware!! DON'T ever get tempted to check the netbeans base IDE plugin setting to look for updates! There are some incompatibilities between the path expectations of the updates and the directory structure used by the ubuntu package. If you take any of these base IDE updates you will probably trash all your hard work and might not even be able to clean the system up for a fresh install. You have been warned!

---

