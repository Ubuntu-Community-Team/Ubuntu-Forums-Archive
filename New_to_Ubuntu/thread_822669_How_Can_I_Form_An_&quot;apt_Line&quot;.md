---
title: "How Can I Form An &quot;apt Line&quot;?"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by hodad on 2008-06-08
I need to add a software source.  When I go to System-Admin-Software Sources I need to "enter a complete APT"  line. However, the format of this is not the same as the URL's I am used to entering (such as [http://www.etc](http://www.etc)).  I've been through scads of answers in the forums, but none of them make sense.  I know that the sources are located in the file /etc/apt/sources.li , and I know how to use "gedit" to add a line , but HOW DO I CONSTRUCT AN APT LINE FOR A PARTICULAR URL that I want to allow downloads from??

For instance, I simply want to download FireFTP from a mozilla site, but it doesn't work because Synaptic can't find it.  Obviously, I need to add a "APT line" for this site under software sources, either from the command line or thru "system- admin-software sources", but I can't seem to find anything that simply explains HOW TO CONSTRUCT AN APT LINE FOR A PARTICULAR SOURCE (!*&^%).  

SOrry about the frustration, but this is one of those times where a simple little problem leads to HOURS of fruitless searching for a simple answer.  Any help would be GREATLY appreciated!!!

Thanks!](*,)](*,)

---

### Post by Happy_Man on 2008-06-08
I'm confused. Could you please provide a more detailed summary of your situation?

Yes, sources.list features a different syntax than normal http addresses, but don't worry, if an installation calls for adding one, they will give you the exact line you need.

---

### Post by mikewhatever on 2008-06-08
Consult this guide [http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/).

---

### Post by niteshifter on 2008-06-08
Hi,

I think you're making adding FireFTP much harder than it needs to be. That, and a google try of site:mozilla.org FireFTP gives nothing (meaning it's not available as a simple file download from anywhere in mozilla.org).

Firefox has a built-in mechanism for add-ons and externsions: In FireFox, click on Tools, then click Add-ons. In the dialog that appears, click on Get Extensions. This takes you to the addons.mozilla.org site (and will match your system language). There you can search for FireFTP (or any other), then download it and install it, from there.

---

