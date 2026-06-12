---
title: "PolicyKit"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by mmmmm_PIE on 2008-09-07
Hey!
My first day with Linux/Ubuntu, things have been going pretty well so far but I've run into my second major roadblock trying to understand PolicyKit. I'm attempting to configure hal, but the process fails when it finds 'PolicyKit is not explicitly disabled and no PolicyKit found'.

Google brings up a number of extensive guides, but they're rather unhelpful to a guy who doesn't even know what PolicyKit *is*.

Thanks in advance for any help!

Edit: For some reason, wrote network Manager in post, meant Hal

---

### Post by mmmmm_PIE on 2008-09-07
*Bump* (Is three hours an appropriate wait before bumping around here? Sorry if not...)

---

### Post by stevoo on 2008-09-07
well you maybe this can help out :)

[Link TO a Solution perhaps ?]("http://beginlinux.wordpress.com/2008/07/12/policykit-solutions-with-ubuntu-804/")

---

### Post by mmmmm_PIE on 2008-09-07
^Thanks, it looks like it possibly could be some help, but I'm having problems implementing.

The guide suggests running a number of commands of the syntax 'apt-get install -reinstall xxxxxxx'... but I have problems with the -reinstall, returning the error "E: command line option 'r' [from -reinstall] is not known".

I'm looking for a solution, but any help speeding up the process would be great.

---

### Post by chaanakya_chiraag on 2010-01-11
It's ```
sudo apt-get install --reinstall policykit
```
I think the person who posted made a mistake there and only put one dash.

---

