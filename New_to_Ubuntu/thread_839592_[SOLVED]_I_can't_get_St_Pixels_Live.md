---
title: "[SOLVED] I can't get St Pixels Live"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by sanderella on 2008-06-24
Does anyone go into St Pixels online church? I can't configure it to work on my Ubuntu box with Hardy. Previously, with 7.10 it worked flawlessly. This is the last remaining problem I have with Hardy, and I'd like to get it working. 
I have downloaded the installation program, StPixelsClient.jnlp. I have all the Java updates. When I try to open the installation program nothing happens, and it doesn't go through the installation process.:confused: Anyone able to help? Mark at St Pixels told me I have to configure my browser, but Firefox doesn't seem to want to be configured. boo hoo.#-o

---

### Post by jamesstansell on 2008-06-25
The JNLP configuration is actually done through the MIME settings. (Its official name is Java Webstart.)  There were some corrections made for Hardy, but I don't use any webstart apps so don't have any recent direct experience.

Hardy ships with the javaws implementation provided by the icedtea project, but it may not be 100% compatible with the Sun version.  Do you know which one you have installed?  If you type "javaws -version" at a command prompt what does it say?

You shouldn't actually need the browser, as a webstart app can be launched by using the javaws command.

---

### Post by sanderella on 2008-06-26
This is what I got. What does it mean? Thanks.

Usage:   javaws [-run-options] <jnlp file>
         javaws [-control-options]

control-options:
  -about                Shows a sample application.
  -viewer               Shows the trusted certificate viewer.

run-options:
  -basedir dir          Directory where the cache is kept.
  -arg arg              Adds an application argument before launching.
  -param name=value     Adds an applet parameter before launching.
  -property name=value  Sets a system property before launching.
  -update seconds       Update check if seconds since last checked.
  -license              Display the GPL license and exit.
  -verbose              Enable verbose output.
  -nosecurity           Disables the secure runtime environment.
  -noupdate             Disables checking for updates.
  -headless             Disables download window, other UIs.
  -strict               Enables strict checking of JNLP file format.
  -help                 Print this message and exit.

When I right-click on StPixelsClient.jnlp a menu appears saying 'Open with "OpenDKJava Web start"'. When I do, nothing happens.

---

### Post by sanderella on 2008-06-26
Hey, I did it! I did it! I did it!:) I got St Pixels working. I had to download and install Java6.:KS:KS:KS

---

