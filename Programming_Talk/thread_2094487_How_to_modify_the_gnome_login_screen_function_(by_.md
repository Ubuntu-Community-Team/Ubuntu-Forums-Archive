---
title: "How to modify the gnome login screen function (by code)"
date: 2012-12-13
forum: Programming Talk
---

### Post by dqvn on 2012-12-13
Dear all,

I'm a programmer in Linux environment. I just have a requirement that requires me to build a new login function for Ubuntu 12.10 (quantal)

The requirement is:
- Supporting the Ubuntu users outside company (more than 1000 PCs worldwide) could be authenticated with our system through their username/password. I have a system that run as web-services and allow users giving input of their username/password then we will return yes if trust and no in other cases.  

- The Ubuntu user after that could login the system by their account from our company.

The problem here:
- We can't use the current account management system in Ubuntu 12.10 because we have more than 1000 users and continues to increase more and more. Thus it is impossible to create 1000+ account in one Ubuntu OS.
- I tried the solution of LDAP client but it is take too much time for outside company users. -> just run good inside building (company) through Lan-wire (intranet). then this solution is impossible for outside PCs. 

My proposal is:
- Modify the current login service of gnome (gdm) in Ubuntu 12.10 by source code and rewrite the login services of Ubuntu to connect into our web-services and allow users login if the on-line account management service returns  true/yes and restrict them if the web-services return false/no. Then, we will use (one) default account of Ubuntu to login. In other sides, the login screen shows the restricted message until users input correctly.

However, I don't know where is the source code of gnome login screen? how can I get it from ubuntu.org. Or do we have any better solutions for my  problem.

Thanks and best regards,
Quang Nguyen

---

