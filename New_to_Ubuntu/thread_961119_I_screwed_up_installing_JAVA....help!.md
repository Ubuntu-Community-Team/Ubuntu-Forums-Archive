---
title: "I screwed up installing JAVA....help!"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by GoBlue! on 2008-10-28
Total newbie here...just installed Ubuntu 8.04 yesterday, and have never used Linux before.  Although, I grew up on MS-DOS, so dealing with a command line isn't foreign.

Anyway, I was surfing in Firefox and downloaded Java from java.com: jre-6u10-linux-i586.bin.  It downloaded to the desktop, and I was able to execute the install.  But, I guess I assumed that it would automatically install to a directory apart from my home directory.  I guess that's what I get for blindly hitting "Install" on so many Windows apps over the past decade.

So I now have a "jre1.6.0_10" folder sitting on my desktop.  I've also now seen that I could've just done this using the Synaptic Package Manager and saved myself a bunch of trouble, right?  Well, how do I just trash this folder so I can start over?  I'm so used to having to "uninstall" programs properly, that I don't want to just dump the folder in the trashcan without a little handholding.

Thanks for your patience,
Jim

---

### Post by bumanie on 2008-10-28
If you have installed it successfully, the best way to get rid of it is to > sudo aptitude purge <exact package name>You will find the majority of software needed is in synaptic, which can be installed via the synaptic GUI or command line in terminal.

---

### Post by The Cog on 2008-10-28
You can safely delete the directory from your desktop. If you want to install that version specifically, executing the install as root (sudo ./whateverItsCalled.bin) gives you the power to install it into /opt whish is where it prefers to go.

However, if you just want a general java and you're not that picky about the exact version, you are probably better off installing the version that comes in the package manager. The packages you want are probably sun-java6-jre and sun-java6-plugin. You can install these with synaptic (System->Administration->Synaptic) or from the command line:
**sudo aptitude install sun-java6-jre sun-java6-plugin**

---

### Post by Zzl1xndd on 2008-10-28
Also just installing the Ubuntu Restricted Extras from the Add/remove or Synaptic will install Java, Flash and more other things new users want.

If you go through Add/remove make sure you select all available  applications from the drop down before searching for Ubuntu Restricted Extras.

---

### Post by GoBlue! on 2008-10-28
> **tweakedenigma said:**
> Also just installing the Ubuntu Restricted Extras from the Add/remove or Synaptic will install Java, Flash and more other things new users want.

If you go through Add/remove make sure you select all available  applications from the drop down before searching for Ubuntu Restricted Extras.

Perfect!  I dumped the previous folder in the trash and installed the Restricted Extras.  I appreciate the help.

Jim

---

