---
title: "Running eclipse with sudo - best practice?"
date: 2007-04-08
forum: Programming Talk
---

### Post by rstoya05-lx on 2007-04-08
Hi, 
Eclipse crashes consistently for me when validating a web.xml file and trying to bring up the Sun license agreement dialog for caching the XSD. I've also confirmed if I start Eclipse with sudo it works fine. So is it a good idea (or advisable) to run Eclipse with sudo?

I've developed on Windows in the past where Eclipse, Java, Tomcat are installed in a local directory (a.k.a. C:\ drive). In Ubuntu I used the Synaptic Package Manager to install it for all users but that seems to require root privileges in some cases. 

It doesn't seem right to have to use root privileges to start Eclipse. Or for that matter to be able to deploy web application projects to Tomcat. I am new to Ubuntu and would appreciate some advice. 

Thanks!

---

### Post by cobray on 2007-04-08
You should not run eclipse as root.

What probably happened is you ran eclipse as root and one of the config files was written to disk with root permission.
When you try to run it as non-root, you get this funky problem.

You need to reinstall eclipse.

I had this problem in the past with tomcat.  Reinistalling tomcat fixed the problem for me.

---

### Post by cobray on 2007-04-08
I forgot to mention I had alot of problems with the eclipse install from synaptic.

What I did was downloaded the eclipse sdk 3.2.2 from eclipse.org and untarred the file into my home directory.

Everything works great.

---

### Post by rstoya05-lx on 2007-04-08
> You should not run eclipse as root.

Yes, I feel the same way. Now I downloaded Eclipse 3.2.2 as well and unpacked it directly into my home directory. I suppose since I'm the only user on this machine it probably doesn't matter if the install is in a shared area or not. Or does it?

> What probably happened is you ran eclipse as root and one of the config files was written to disk with root permission. When you try to run it as non-root, you get this funky problem.

Actually, I get this problem even if I install all 3 (eclipse, tomcat, java) locally. Do you use the Web Tools Platform at all? The crash occurs when it tries to bring up a license dialog for caching the web.xml schema. I should probably post a message on the WTP forums.

> I had this problem in the past with tomcat. Re-inistalling tomcat fixed the problem for me.

I will try that. Thanks for your suggestions!

I would love to hear from more people using Eclipse and the Web Tools Platform, more specifically about whether they use the package manager or install locally. In theory if I use the package manager to install my development tools should I be able to run them without root privileges?

Thanks,
Rossen

---

### Post by rstoya05-lx on 2007-04-08
Well, I would still love to hear from others on the questions I posed above but I wanted to post some information on the Eclipse crash since I managed to get around it.

The crash was due to a problem with the SWT browser widget under Linux. It occurred in /usr/lib/firefox/components/libdocshell.so:

```
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0x8394442f, pid=17306, tid=3085403824
#
# Java VM: Java HotSpot(TM) Server VM (1.5.0_08-b03 mixed mode)
# Problematic frame:
# C  [libdocshell.so+0x42f]  _Z17AppendUTF8toUTF16RK19nsACString_internalR18nsAString_internal+0x42f
#

```

This thread from the Eclipse archives refers to the same issue:
[http://dev.eclipse.org/newslists/news.eclipse.platform.swt/msg33865.html](http://dev.eclipse.org/newslists/news.eclipse.platform.swt/msg33865.html)

The only difference is for me the issue happened when Eclipse tries to cache the web.xml schema file and brings up a license agreement dialog. The thread above indicates the issue is fixed in Eclipse 3.3 (not an official release at this time). However, I got around the issue by disabling the caching of the XSD from inside Eclipse:

Window > Preferences > Internet > Cache > Disable Caching

regards,
Rossen

---

### Post by DC@DR on 2007-04-09
I've been using Eclipse 3.2.2 + WTP in Ubuntu for a while and haven't experienced any crashes yet like that. I agree that installing Eclipse manually is much more stable than via Synaptic. But I will keep in mind about your issue's fix, and hopefully when Eclipse 3.3 (Europa) arrives, it will come with more features and stability :-)

---

### Post by rstoya05-lx on 2007-04-10
Hi, thanks for your reply. 

Do you experience any crashes at all? I'm just curious to hear if it has been running stable for others. So far I got past one more that was caused by insufficient PermGen space. 

This is described here: 
[http://tassos.blogentis.net/2006/06/08/eclipse-and-permgen-space](http://tassos.blogentis.net/2006/06/08/eclipse-and-permgen-space)

Also, I am running with a dual-core CPU and Ubuntu 6.10.

---

### Post by theToolman on 2008-03-21
Hey I have the same issue:

Gutsy kubuntu clean install, package managed eclipse 3.2.2, updated (using internal update) to have WTP.  Opening a web.xml using the WTP xml editor opens the licence dialog then crashes.  other XML files open fine.

The workaround listed above works for me too. (disabling caching)  I have never run eclipse as root, so this isn't the cause of problem in my case.

---

