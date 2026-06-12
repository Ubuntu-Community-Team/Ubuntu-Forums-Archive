---
title: "FAQ: Where is my firewall?"
date: 2004-10-22
forum: Outdated Tutorials &amp; Tips
---

### Post by gecko on 2004-10-22
[size=6]Where is the Firewall?[/size]

**Dude, where is the firewall?**

Their is no firewall installed with Ubuntu!

**Holy Batman! Why doesn't Ubuntu come with a firewall?**

Layman's Terms
It does not need one. It does not have anything listening to the network.

Technical Term's
Since Ubuntu doesn't run any daemons that listen to the outside world by default (the postfix install only listens on localhost) there's no need for a default firewall. The rationale is that if a user's got a need for installing a world-facing daemon, they'll be aware that they should configure a firewall/ACL for it too.

Source - Ubuntu FAQ on website.

**Can I use a firewall?**

First up, do you have an Internet connection? For the home user, their is no need to install a firewall unless you are on the Internet. In fact, you cannot install the firewall unless you have a network connection of some type.

**I am not comfortable without a firewall, how do I get one?**

The simplest firewall to install is firestarter. With its wizard configuration it is a snap to setup. Click on Computer->System Configuration Menu->Synaptic Package Manager to start the installation. You have to re-configure the package manager to access additional software. Click Settings->Repositories and click on each one until you find the first entry with the settings...

Distribution:warty
Section(s):main restricted

Now add the word 'universe' to the Section(s) line. So it now reads

Distribution:warty
Section(s):main restricted universe

Click OK and now select Edit->Reload Packages List to refresh the list of packages. Click on Edit->Search and type firestarter then click OK to find the package. Click the box next to the package name and select "Mark For Installation". 

NB: Make sure to read the fine print before you install to ensure it is only installing one package. If you need to use proxy to access the outside world then refer to the HOWTO on proxies in this forum. Now the Apply button should be available on the main toolbar. Click this to install the package

Firestarter comes with a wizard and if you follow the defaults it should install easily. Do not use the **loopback** interface for the firewall. It must be something else, such as eth0 or ppp0. If you cannot choose any other interface then cancel the install and get assistance.

**Contribute!**
If you have more information on this topic then post a reply to this message! All contributions help! Any corrections then message the author's directly.

Gecko

---

### Post by wallijonn on 2004-10-31
I just posited a HOWTO: Standalone Firewall in the General Section.

Maybe a moderator can move my setting up Shorewall Firewall posit to here.

[http://www.ubuntuforums.org/showthread.php?t=2728](http://www.ubuntuforums.org/showthread.php?t=2728)

---

