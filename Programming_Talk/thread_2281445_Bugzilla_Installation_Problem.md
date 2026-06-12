---
title: "Bugzilla Installation Problem"
date: 2015-06-07
forum: Programming Talk
---

### Post by osama3 on 2015-06-07
In our company, we have Ubuntu server running in virtual environment. I wanted to install Bugzilla for our developers. Installation went smooth unrill I issued the command "./checksetup.pl" as the last step in installation. The command should run and asks for the password for the user "admin". Unforunatly it ran ends with "installation complete successfully" !!. I invoked the bugzilla with the browser and I tried to login as admin but I couldn't. I have to log in as admin to complete the configuration. I posted the request since a while (in other forum) so I need the answer ASAP. Thanks

---

### Post by ofnuts on 2015-06-07
See [https://www.bugzilla.org/docs/tip/en/html/api/checksetup.html](https://www.bugzilla.org/docs/tip/en/html/api/checksetup.html)

In particular the **--make-admin** and** --reset-password** options that let you define your own admin acccount.

---

