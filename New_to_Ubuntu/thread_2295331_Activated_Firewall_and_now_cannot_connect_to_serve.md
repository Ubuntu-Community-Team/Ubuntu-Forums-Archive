---
title: "Activated Firewall and now cannot connect to server"
date: 2015-09-17
forum: New to Ubuntu
---

### Post by faisal6 on 2015-09-17
This my first experience with Ubuntu. I bought an un managed dedicated  server; activated the firewall; opened only port 80 for Tomcat and forgot to open the port for remote desktop connection.
Now both Putty and Remote Desktop Connection cannot connect: connection refused message I get.

Is there any way I can manage to get beyond the firewall and configure it?

Regards

---

### Post by QIII on 2015-09-17
If there were a nice, easy way to get around a firewall, firewalls would not be of much use.  Any discussion of hacking a firewall would be shut down here on the UF and might result in the issuance of infractions.

Do you have a control panel to get to it?  Can you make firewall changes via the CP?  Who is the provider?  Can the provider re-image the server?

---

### Post by Dragonbite on 2015-09-17
How did you activate the firewall, over SSH?

If you can get the firewall turned off then you can fix things but without access to the firewall or any other settings you can fix it, but the question becomes whether you have access to the machine or not.

If the machine is accessible you will be able to log into the server itself and make changes that way.

Good luck!

---

### Post by sandyd on 2015-09-17
> **faisal6 said:**
> This my first experience with Ubuntu. I bought an un managed dedicated  server; activated the firewall; opened only port 80 for Tomcat and forgot to open the port for remote desktop connection.
Now both Putty and Remote Desktop Connection cannot connect: connection refused message I get.

Is there any way I can manage to get beyond the firewall and configure it?

Regards

Few options now that you have locked yourself out:
[LIST=1]
[*] Get out-of-band access, some servers have a out of band access unit that allows you to access the server as if you had connected a keyboard/mouse/screen to it. Some datacenters have their own out-of-band access mechanisms.
Some names that go with brands:
HP: iLO
Dell: iDRAC
Supermicro: IPMI
* Side Note: Lots of these out of band management utilities are _insecure_ and have insecure firmware and/or default passwords. Some even require ancient versions of java; keep them disconnected from the internet until you need to use.

[*]2. Get datacenter to connect a KVM-over-IP unit, it is similar to an out-of-band access unit, and simulate you connecting a keyboard/mouse/screen to the server. You can then access your server's console directly via a URL that the datacenter provides.

[*]3. Ask datacenter support to run the command to unblock your firewall.
[/LIST]

---

### Post by faisal6 on 2015-09-18
I do have KVM-over-IP  access to the server but for some reasons Java applet doesn't work when I try to view the server console:

I get this Java error: 

com.sun.deploy.net.FailedDownloadException: Unable to load resource: [https://xxx.xx.xx.xx/cgi_bin/javaRKVM.jnlp](https://xxx.xx.xx.xx/cgi_bin/javaRKVM.jnlp)
    at com.sun.deploy.net.DownloadEngine.actionDownload(Unknown Source)
    at com.sun.deploy.net.DownloadEngine.downloadResource(Unknown Source)
    at com.sun.deploy.cache.ResourceProviderImpl.getResource(Unknown Source)
    at com.sun.deploy.cache.ResourceProviderImpl.getResource(Unknown Source)
    at com.sun.javaws.Launcher.updateFinalLaunchDesc(Unknown Source)
    at com.sun.javaws.Launcher.prepareToLaunch(Unknown Source)
    at com.sun.javaws.Launcher.prepareToLaunch(Unknown Source)
    at com.sun.javaws.Launcher.launch(Unknown Source)
    at com.sun.javaws.Main.launchApp(Unknown Source)
    at com.sun.javaws.Main.continueInSecureThread(Unknown Source)
    at com.sun.javaws.Main.access$000(Unknown Source)
    at com.sun.javaws.Main$1.run(Unknown Source)
    at java.lang.Thread.run(Unknown Source)

The guys don't want to help in anyway, saying it's an un managed server and I have to  fix it.

---

### Post by sandyd on 2015-09-23
As I mentioned above, your JRE may be too new. 
Try downgrading to JRE 1.6 and see what happens.
You may want to do this in a virtual machine if you don't want to mess up your installation.

---

### Post by SeijiSensei on 2015-09-24
Linode lets you access the virtual machine's console directly from its web dashboard.  It's a lifesaver if you accidentally lock yourself out via SSH. Does your provider offer a similar option?

---

