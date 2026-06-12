---
title: "extension problem"
date: 2012-05-31
forum: New to Ubuntu
---

### Post by navvirdi15 on 2012-05-31
I am using latest version of gnome .I have install some extension previously but I am not able to install extension now from extension.gnome.org
i am able to ON/OFF the previous install extension from the site. but the not installed extension do not response.

---

### Post by wilee-nilee on 2012-05-31
> **navvirdi15 said:**
> I am using latest version of gnome .I have install some extension previously but I am not able to install extension now from extension.gnome.org
i am able to ON/OFF the previous install extension from the site. but the not installed extension do not response.

Look for extensions in the software manager or synaptic if you have synaptic installed.

---

### Post by navvirdi15 on 2012-05-31
i have installed advanced setting software

---

### Post by navvirdi15 on 2012-05-31
i want  to install the software from the site ,but it is not happening

---

### Post by Enigmapond on 2012-05-31
What extensions are you talking about. Most can be installed from the software centre or even better, use synaptic to install. If you install from the site, they usually tell you it's better to install from the repos...but again...which extensions are you talking about?

---

### Post by navvirdi15 on 2012-05-31
[https://extensions.gnome.org/extension/322/quicklists/](https://extensions.gnome.org/extension/322/quicklists/)
[https://extensions.gnome.org/extension/105/panel-docklet/](https://extensions.gnome.org/extension/105/panel-docklet/)

---

### Post by tea for one on 2012-05-31
> **navvirdi15 said:**
> I am using latest version of gnome .I have install some extension previously but I am not able to install extension now from extension.gnome.org
i am able to ON/OFF the previous install extension from the site. but the not installed extension do not response.

Just to clarify, you are referring to this site:-

[https://extensions.gnome.org/](https://extensions.gnome.org/)

Within this site, if you click on "Installed extensions", does the site list your own extensions correctly?

---

### Post by tea for one on 2012-05-31
Another question - you have installed gnome-shell?

---

### Post by navvirdi15 on 2012-05-31
yes yes they show the installed extension
i have installed latest gnome shell 3.4

---

### Post by tea for one on 2012-05-31
I've just thought of another little detail - can you confirm that you are using Firefox because I have read that some browsers are incompatible with the gnome-extension site?

---

### Post by navvirdi15 on 2012-05-31
tried both chrome and firefox

---

### Post by tea for one on 2012-05-31
As I understand, your gnome-extensions were perfectly OK until recently so, I imagine, something has interfered somewhere?

Have you upgraded to 12.04 or did you do a fresh install?

Can you see your extensions in Home/.local/share/gnome-shell/extensions?

Has anything on your PC (software/hardware) changed since the extension were functioning OK?

I am at a bit of a loss as to why the site will not yet you install new extensions where previously it was OK?

---

### Post by navvirdi15 on 2012-05-31
yes i have upgraded to 12.04 

i can  see extensions in Home/.local/share/gnome-shell/extensions

---

### Post by tea for one on 2012-05-31
Did the extensions work before you upgraded and then cease working sometime after the upgrade?

When a LTS release is available, I back up my home directory and do a fresh install even though my home directory is on a separate partition. 

There are many threads on this forum discussing the unforeseen problems of upgrades and it is possible that you may have experienced a little latent difficulty somewhere?

If you have time and a spare capacity on your hard drive, the nuclear option is to start with a fresh install, re install gnome-shell, gnome tweak tool and your chosen extensions and see what happens. Make sure you _back up your home directory_ first.

I know that this is not an ideal solution but an Ubuntu install is now pretty quick. For example, I accidentally removed some dependencies for Kaffeine last week and it was quicker to reinstall from my back up iso (remastersys) rather than hunt down the packages and test that everything was OK.

Perhaps, somebody else can offer a suggestion or two?

Kind regards

---

### Post by navvirdi15 on 2012-05-31
thanx

---

### Post by cortman on 2012-05-31
I have yet to have the browser based extension install pages work with gnome shell 3.4. I can confirm that the instructions given [here]("http://www.noobslab.com/2012/04/install-gnome-shell-34-and-extensions.html") do work, and have worked for me multiple times.

---

### Post by ifoolb on 2012-06-19
Maybe proxy is the matter.I have the same issue and I find that system is manual proxy,so I set it no proxy,now the site works fine.

---

