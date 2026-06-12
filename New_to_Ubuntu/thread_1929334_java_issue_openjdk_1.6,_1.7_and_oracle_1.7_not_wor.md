---
title: "java issue: openjdk 1.6, 1.7 and oracle 1.7 not working correctly"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by jlinoff on 2012-02-21
Hi:

I am having a problem with javaws running a JNLP file on Ubuntu 11.10. It works just fine on windows 7 but I would really prefer to use Ubuntu if possible.

The JNLP file starts up a java app that is an IPMI/BMC viewer that connects to a host  on my network from firefox 10. It uses the javaws plugin. The main java app comes up with no problem but when I select one of the menu options (Media -> Virtual Media Wizard) which should pop up a dialogue window it just hangs. Other menu options seem to work, including other dialogues.

The java app is "Redirection Viewer" Version 1.38 from AMI.

I have tried openjdk 1.6, openjdk 1.7 and oracle jdk 1.7. I completely uninstalled each the previous one before trying the new one and verified the versions using "java -version" and "javac -version".

I verified that all ports are open using ufw. Now I am at my wits end and I am hoping that someone might have a suggestion about how to debug this problem.

I noticed two interesting differences between openjdk and oracle jdk:

1. openjdk 1.6 and 1.7 were really slow compared to oracle jdk 1.7
2. openjdk 1.6 and 1.7 failed to terminate background jobs intermittently whereas oracle jdk 1.7 seemed to correctly terminate the background jobs.

I really need this to work because I am trying to flash firmware (LSI SAS2008 HBA to I/T mode) on a filer on my system (SuperMicro SBB 6036ST) using IPMI because it has no USB ports or DVD slots. 

Thanks.

---

