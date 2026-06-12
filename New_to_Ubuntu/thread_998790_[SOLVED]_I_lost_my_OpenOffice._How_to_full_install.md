---
title: "[SOLVED] I lost my OpenOffice. How to full install it?"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by Kosimo on 2008-12-01
Maybe I did something...
Anyway I don't have OpenOffice anymore.

It is enough to do:  ```
sudo apt-get install openoffice
``` ?

Thanks!

---

### Post by Kosimo on 2008-12-01
Ok I know now that openoffice package doesn't exist :P

So, what's the command for fully install openoffice? :P

---

### Post by stephanvaningen on 2008-12-01
```
sudo apt-get install openoffice.org
```

---

### Post by Kosimo on 2008-12-01
> **stephanvaningen said:**
> ```
sudo apt-get install openoffice.org
```

Good, that's the right one ;)

Anyway I get this error:

```
sudo apt-get install openoffice.org
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openoffice.org: Depends: openoffice.org-writer but it is not going to be installed
                  Depends: openoffice.org-calc but it is not going to be installed
                  Depends: openoffice.org-impress but it is not going to be installed
                  Depends: openoffice.org-draw but it is not going to be installed
                  Depends: openoffice.org-math but it is not going to be installed
                  Depends: openoffice.org-base but it is not going to be installed
                  Depends: openoffice.org-report-builder-bin but it is not going to be installed
E: Broken packages

```



Any help?

Thank you!

---

### Post by Kosimo on 2008-12-01
If it helps I must say that I did install OpenOffice 3.0 by adding launchpad repos

---

### Post by SunnyRabbiera on 2008-12-01
> **Kosimo said:**
> If it helps I must say that I did install OpenOffice 3.0 by adding launchpad repos

I would just take out the open office 3 repo if you really dont need windows 2007/8 doccuments.
Revert to open office 2, there really isnt much in open office 3 woth of note except maybe better speed and .docx support but open office 2 should be fine enough too.

---

### Post by Kosimo on 2008-12-01
> **SunnyRabbiera said:**
> I would just take out the open office 3 repo if you really dont need windows 2007/8 doccuments.
Revert to open office 2, there really isnt much in open office 3 woth of note except maybe better speed and .docx support but open office 2 should be fine enough too.

Yes, this is exactly what I want, but the big question is... How? :)

---

### Post by SunnyRabbiera on 2008-12-01
well make sure that all open office 3 packages are removed, use synaptic or command line or whatever to remove open office 3.
then take the open office 3 repository out of the lists and reinstall open office 2.

---

### Post by zika on 2008-12-01
I was in a same situation on 27.11.08. I waited until today for launchpad-repos to get back on-line. But in a forum thread I read that they will not and, instead, OO3 will apper in JJ. In the meantime I tried several places and several .deb files to reinstall OO3 with no {luck, success,...} Finally today I wrote ```
 $sudo apt-get remove openoffice*.*
``` and installed native OO2.4 via Applications->Add/Remove OpenOffice.org Suite and I'm at peace until JJ. Since I write everything in TeX and OO is just for crossover tasks and to accomodate my (let's say) customers (statistical analysis) I am OK. You can try.
(In one of these forums a gyu attacked all of us that were inpatient by saying that an application is always a part of OS. I do not completely agree with him but now I am a bit closer ... Nevertheless, I learned a lot from tinkering with this these several days (27.11. to 01.12) :wink:

---

### Post by Kosimo on 2008-12-01
> **SunnyRabbiera said:**
> well make sure that all open office 3 packages are removed, use synaptic or command line or whatever to remove open office 3.
then take the open office 3 repository out of the lists and reinstall open office 2.

How can I make sure all OpenOffice 3 packages are removed?
Is this the reason I still can't install openoffice.org using official repos?

---

### Post by SunnyRabbiera on 2008-12-01
> **Kosimo said:**
> How can I make sure all OpenOffice 3 packages are removed?
Is this the reason I still can't install openoffice.org using official repos?

the command above should work.

---

### Post by Kosimo on 2008-12-01
> **zika said:**
> I was in a same situation on 27.11.08. I waited until today for launchpad-repos to get back on-line. But in a forum thread I read that they will not and, instead, OO3 will apper in JJ. In the meantime I tried several places and several .deb files to reinstall OO3 with no {luck, success,...} Finally today I wrote ```
 $sudo apt-get remove openoffice*.*
``` and installed native OO2.4 via Applications->Add/Remove OpenOffice.org Suite and I'm at peace until JJ. Since I write everything in TeX and OO is just for crossover tasks and to accomodate my (let's say) customers (statistical analysis) I am OK. You can try.
(In one of these forums a gyu attacked all of us that were inpatient by saying that an application is always a part of OS. I do not completely agree with him but now I am a bit closer ... Nevertheless, I learned a lot from tinkering with this these several days (27.11. to 01.12) :wink:

That worked perfectly for me. Thanks! Actually I really don't need OpenOffice 3, so after removing everything I am now installing 2.6 from official repos.
I'll wait to JJ ;)

Thank you!

---

