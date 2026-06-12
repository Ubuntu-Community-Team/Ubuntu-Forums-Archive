---
title: "can't install subclipse"
date: 2009-11-01
forum: Programming Talk
---

### Post by giants_fan on 2009-11-01
Hi,

I just installed Ubuntu 9.10 (fresh install) and installed Eclipse 3.5.1 (via apt-get).  Then, when I tried to install Subclipse (v 1.6), I get a rather odd error message:

"The artifact file for osgi.bundle,org.eclipse.ant.ui,3.4.1.v20090901_r351 was not found."

And the install fails.  Anybody have any ideas?

Thanks!

---

### Post by januzi on 2009-11-01
Is this eclipse - 3.5.1-0ubuntu6 or eclipse - 3.5.1-0ubuntu7 ?

---

### Post by giants_fan on 2009-11-01
How do i tell?

To install, I did "apt-get install eclipse".  The synaptic package manager tells me that the installed version I have "3.5.1+repack~1-0ubuntu1".

---

### Post by collinp on 2009-11-01
```
apt-cache policy eclipse
``` should give you the version number.

---

### Post by giants_fan on 2009-11-01
Yeah, it's the same version that I noted earlier...

[FONT="Courier New"]
eclipse:
  Installed: (none)
  Candidate: 3.5.1+repack~1-0ubuntu1
  Version table:
     3.5.1+repack~1-0ubuntu1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages

[/FONT]

---

### Post by brownbat on 2009-11-02
I can't install subclipse either. I get a bunch of errors, "dependency" style errors. The eclipse forums are not much help, so I hope someone will have a suggestion here.

---

### Post by Can+~ on 2009-11-02
Sounds like a problem with the repository version. Maybe install the version on the website, and add then do it with that? I have all my current setup on eclipse (Eclipse from site + CDT + Pydev + Subclipse) on Jaunty without a trouble.

---

### Post by nwoetzel on 2009-11-02
> **brownbat said:**
> I can't install subclipse either. I get a bunch of errors, "dependency" style errors. The eclipse forums are not much help, so I hope someone will have a suggestion here.

I had a similar problem. It turns out, that the eclipse version from the repository does not come with the ganymede update site.
So just add
[http://download.eclipse.org/releases/ganymede/](http://download.eclipse.org/releases/ganymede/)
to your "Available software sites" in preferences->Install/Update, or when calling "install new software". When installing subclipse now, eclipse should be able to find all dependencies on the ganymede update site.

---

### Post by bostonaholic on 2009-11-03
> **nwoetzel said:**
> I had a similar problem. It turns out, that the eclipse version from the repository does not come with the ganymede update site.
So just add
[http://download.eclipse.org/releases/ganymede/](http://download.eclipse.org/releases/ganymede/)
to your "Available software sites" in preferences->Install/Update, or when calling "install new software". When installing subclipse now, eclipse should be able to find all dependencies on the ganymede update site.

Thank you, this fixed my particular issue.  I just upgraded to [COLOR="Orange"]Karmic[/COLOR] and I guess Eclipse was upgraded with it.  Anyway, when I tried to install Subclipse 1.6, the "Finish" button was not clickable after agreeing to the license agreement to install Subclipse.  After adding the Ganymede update site, the "Finish" button was enabled and it seems as though Subclipse is installing successfully.

Thanks again, I wish I could give you 'thanks' like we used to...

EDIT:  I just noticed when Eclipse was restarting that I'm now running Galileo, not Ganymede.  I updated my update site to reflect Galileo.  Looks like Sublipse works fine even though I used Ganymede when installing Subclipse.

---

### Post by sdemills on 2010-01-25
You would not believe how much and for how long I have struggled trying to figure out why, after the Review Licenses panel, the FINISH button was never enabled.

Thank you for this excellent advice which fixed the problem and enabled me to complete the installation of Subclipse.

Kind Regards
Steve
:P

---

### Post by nicklong on 2010-01-31
Thank you for this advice - I have been searching all over for a resolution to installing subclipse.

I am posting this reply because this problem also occurs for the Galileo version of Eclipse (which is the Karmic Koala 9.10 repository version of Eclipse installed by Synaptic Program Manager).  By adding [http://download.eclipse.org/releases/galileo/](http://download.eclipse.org/releases/galileo/) as a remote site in the Eclipse software install wizard the problem is solved.

Best Wishes,
Nick

---

### Post by bartonski on 2010-03-31
> **sdemills said:**
> You would not believe how much and for how long I have struggled trying to figure out why, after the Review Licenses panel, the FINISH button was never enabled.

Thank you for this excellent advice which fixed the problem and enabled me to complete the installation of Subclipse.

Kind Regards
Steve
:P

This fits my sentiments word for word.

Cheers!

---

### Post by rsxrsx on 2010-10-17
[FONT=Verdana]I used: [https://help.ubuntu.com/community/EclipseSubversion](https://help.ubuntu.com/community/EclipseSubversion).
Remote site: "http://subclipse.tigris.or[/FONT]g/update"

---

### Post by nldquy on 2011-03-16
> **nwoetzel said:**
> I had a similar problem. It turns out, that the eclipse version from the repository does not come with the ganymede update site.
So just add
[http://download.eclipse.org/releases/ganymede/](http://download.eclipse.org/releases/ganymede/)
to your "Available software sites" in preferences->Install/Update, or when calling "install new software". When installing subclipse now, eclipse should be able to find all dependencies on the ganymede update site.

worked like a charm. Thank you very much :guitar:

---

### Post by ihadanny on 2011-09-17
> **nwoetzel said:**
> I had a similar problem. It turns out, that the eclipse version from the repository does not come with the ganymede update site.
So just add
[http://download.eclipse.org/releases/ganymede/](http://download.eclipse.org/releases/ganymede/)
to your "Available software sites" in preferences->Install/Update, or when calling "install new software". When installing subclipse now, eclipse should be able to find all dependencies on the ganymede update site.

I'm having the same problem on natty, trying to install subclipse 1.6 on helios. I added "http://download.eclipse.org/eclipse/updates/3.6" to my available software sites, but it didn't do the trick... :confused:

---

### Post by ihadanny on 2011-09-17
Big oops. I only added "http://download.eclipse.org/eclipse/updates/3.6", I should have also added "http://download.eclipse.org/releases/helios/", which fixes everything as advertised. Thanks guys!

---

