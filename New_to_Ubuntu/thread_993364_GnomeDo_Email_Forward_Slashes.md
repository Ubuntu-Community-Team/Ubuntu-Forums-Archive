---
title: "GnomeDo Email Forward Slashes"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by wandman on 2008-11-25
I'm using the Gmail contacts plugin with GnomeDo and Evolution is set as my default mail client. When I type in an email address evolution opens and preceeds the address with three forward slashes so in the "To" field it says ///name@example. This means that emails don't send.

Is there a fix for this? Have I discovered a bug?

---

### Post by mustaghattack on 2009-02-02
I have the same problem.

---

### Post by jonolumb on 2009-02-14
I am having the same problem too! Anybody know how to fix this?

---

### Post by adaniels on 2009-03-01
It's a bug. I'm also waiting for a fix. It looks like we have to wait until jaunty which will be released at the end of april.

[https://bugs.launchpad.net/do-plugins/+bug/304533](https://bugs.launchpad.net/do-plugins/+bug/304533)

----

A dirty workaround:
  echo 'thunderbird $(echo "$1" | sed s/mailto:\\/*/mailto:/)' > /tmp/mailto-fix && chmod +x /tmp/mailto-fix

Open 'prefered applications' and for mail reader, set custom command:
  /tmp/mailto-fix %s

---

### Post by commonplace on 2009-03-07
> **adaniels said:**
> A dirty workaround:
  echo 'thunderbird $(echo "$1" | sed s/mailto:\\/*/mailto:/)' > /tmp/mailto-fix && chmod +x /tmp/mailto-fix

Open 'prefered applications' and for mail reader, set custom command:
  /tmp/mailto-fix %s


Any idea how I would get this to open up a new e-mail in Google Apps (Gmail for my domain)?

These are the instructions I followed: [http://do.davebsd.com/wiki/index.php?title=GMail_Contacts_Plugin]("http://do.davebsd.com/wiki/index.php?title=GMail_Contacts_Plugin") and it 'works' but it does the three slashes thing (///name@domain.com).

Any ideas? :)  Thanks!

/Kevin

---

