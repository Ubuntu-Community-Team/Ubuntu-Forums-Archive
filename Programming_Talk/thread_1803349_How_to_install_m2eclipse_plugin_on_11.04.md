---
title: "How to install m2eclipse plugin on 11.04?"
date: 2011-07-13
forum: Programming Talk
---

### Post by filmil on 2011-07-13
Using 11.04, stock Eclipse Galileo 3.5.2.

There seems to be no m2eclipse package available in repos.  Trying to install via the Eclipse update site dies with an error.  What can I do, short of installing my own Eclipse distro?

Cannot complete the install because one or more required items could not be found.
  Software being installed: m2e - Maven Integration for Eclipse 1.0.0.20110607-2117 (org.eclipse.m2e.feature.feature.group 1.0.0.20110607-2117)
  Missing requirement: m2e Marketplace 1.0.0.20110607-2117 (org.eclipse.m2e.discovery 1.0.0.20110607-2117) requires 'bundle org.eclipse.equinox.p2.operations 0.0.0' but it could not be found
  Cannot satisfy dependency:
    From: m2e - Maven Integration for Eclipse 1.0.0.20110607-2117 (org.eclipse.m2e.feature.feature.group 1.0.0.20110607-2117)
    To: org.eclipse.m2e.discovery [1.0.0.20110607-2117]

---

### Post by joelpet on 2011-07-15
I think I managed to install m2eclipse in Ubuntu 11.04 using stock Eclipse Galileo 3.5.2 through the following update site:

[http://m2eclipse.sonatype.org/sites/m2e](http://m2eclipse.sonatype.org/sites/m2e)

---

### Post by OpenMinded on 2011-08-18
> **joelpet said:**
> I think I managed to install m2eclipse in Ubuntu 11.04 using stock Eclipse Galileo 3.5.2 through the following update site:

[http://m2eclipse.sonatype.org/sites/m2e](http://m2eclipse.sonatype.org/sites/m2e)

thanks, that worked.
The m2eclipse site is pretty bad then.
How official is this URL?

---

### Post by joelpet on 2011-08-20
> **OpenMinded said:**
> How official is this URL?

I found it at their old project web site: [http://m2eclipse.sonatype.org/installing-m2eclipse.html](http://m2eclipse.sonatype.org/installing-m2eclipse.html).

---

### Post by ihadanny on 2011-09-26
> **joelpet said:**
> I think I managed to install m2eclipse in Ubuntu 11.04 using stock Eclipse Galileo 3.5.2 through the following update site:

[http://m2eclipse.sonatype.org/sites/m2e](http://m2eclipse.sonatype.org/sites/m2e)

wow, great. life-saver.

---

### Post by farshad on 2012-03-28
> **joelpet said:**
> I think I managed to install m2eclipse in Ubuntu 11.04 using stock Eclipse Galileo 3.5.2 through the following update site:

[http://m2eclipse.sonatype.org/sites/m2e](http://m2eclipse.sonatype.org/sites/m2e)

Hello,

I just wanted to install [m2eclipse]("http://m2eclipse.sonatype.org/sites/m2e") and went to the address, however I saw lots of files in there. I'm quite new in Linux, could you please let me know, how should I install these files? Should I download all the files one by one? What is the installation process? PLEASE

Thank you

---

### Post by r-senior on 2012-03-28
You install from inside Eclipse, not by downloading files externally. You need to add the URL as an update site and it will list the available packages.

Go to Help | Install Software and add the update site there. It's pretty straightforward.

---

