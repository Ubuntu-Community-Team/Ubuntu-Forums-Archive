---
title: "Installing Zentyal on an existing live server"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by HeavenCore on 2013-02-05
Hi there

We have a VM hosted offsite that runs a live B2B website accessed 24/7 by hundreds of clients a week.

This server is running Ubuntu 11.10 (Server) with no GUI etc - our only access is SSH & so on.

Whilst this is fine and everything's working fine - we really need to arrange easier GUI access for simple tasks so I can delegate simple admin tasks to other people.

Up to now I’ve usually used Webmin with no major problems, but I seem to remember reading somewhere that Webmin is no longer supported by ubuntu. So then i came across eBox or to use its current name Zentyal.

Installing Zentyal looks easy enough if you’re doing it on a new VM / box - but what i can’t seem to find is documentation / information on installing it on a live Ubuntu server without breaking current services.

On our server we currently have the standard LAMP setup & this would need to remain online as much as possible during the Zentyal installation - is this even possible? Or would we need to create a new VM, install Zentyal on it then migrate htdocs and mysql databases over and do it that way?

I welcome your thoughts - i'm pretty much an MS person (IIS, SQL Server etc) & my Linux experience is a basic working knowledge at best so thought i'd ask before even attempting this.

Regards

Jordon

---

### Post by Cheesemill on 2013-02-05
Zentyal is based on Ubuntu 12.04, it isn't possible to install it on 11.10.

---

### Post by HeavenCore on 2013-02-05
I'm open to upgrading first :)

(just a simple case of running "do-release-upgrade" i think isnt it?)

---

### Post by Cheesemill on 2013-02-05
> **HeavenCore said:**
> I'm open to upgrading first :)

(just a simple case of running "do-release-upgrade" i think isnt it?)
Theoretically, yes.

But there is no way I would even consider doing that on a live server without having tried it first on your testing server (which should already have the exact same configuration as your live machine). There are any number of things that can go wrong during an upgrade, many of which can only be fixed with a fresh installation.

You do have to start planning your upgrade as a matter of urgency though, as support for 11.10 ends in 2 months.

Personally I would install 12.04 on a new VM and then migrate the services across one by one once you have done some proper testing.

---

### Post by HeavenCore on 2013-02-05
Hi there

As i say, this server is a VM (Virtual Machine running on a SAN / ESX Host) so rolling back in the event of problems is easy peasy.

To that end i've cloned the live VM and updated the clone to 12.10 - apart from having to re-install the SSL certificates etc it went smoothly and everything seems to be working.

Of course we'll leave the clone online with a handful of customers for testing (for a few days at least), if all goes well i'll then be ready to make the clone primary and get cracking on Zentyal.

I'll pop back when we're happy that the 12.10 VM is stable & look into the installation of Zentyal.

Regards

Jordon

---

### Post by Cheesemill on 2013-02-06
Why did you upgrade to 12.10?

Zentyal ***only*** works on 12.04.

---

