---
title: "Problem with IBM Java 5 and Firefox 3"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by koriba on 2008-07-04
Hi!

I have to configure developer environment with Eclipse and IBM WAS CE 1.1. WAS needs IBM's Java 5.0, that I am using. Now, I have problem with running Java applets on new FF 3. I use Ubuntu 8.04 on VM. I have removed FF3-beta5 and installed full FF3 from Mozilla. Of course I have created symbolic link to libjavaplugin_ojigtk2.so. The web browser is aware of Java plug-in however it still does not run Java applets. Please help me solve this problem.

Thank you in advance.
koriba

---

### Post by ZabiGG on 2008-07-04
If your system is 64-bit, java applets are not supported. You will need to install the iced-tea java web plugin for them to work. Another option is to install 32-bit Firefox. There's a guide [here]("http://ubuntuforums.org/showthread.php?t=202537")

If your system is not 64-bit, I'm afraid I'll need more details.

Hope this helps,

Z.

---

### Post by jamesstansell on 2008-07-04
I'm not familiar with the libjavaplugin_ojigtk2.so library.  Is it from the IBM JDK?  If so, do you really need to use IBM's plugin in firefox?

---

