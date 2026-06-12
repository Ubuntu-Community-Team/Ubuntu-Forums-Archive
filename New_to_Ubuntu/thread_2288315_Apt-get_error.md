---
title: "Apt-get error?"
date: 2015-07-26
forum: New to Ubuntu
---

### Post by remmas-sido on 2015-07-26
Hello guys
Today, I run into a strange problem when I typed "sudo apt-get update && sudo apt-get upgrade"  at the end I get this error "E: Some index files failed to download. They have been ignored, or the old ones used instead." 
Anyone get an idea why this happened?
Thanks.

---

### Post by grahammechanical on 2015-07-26
Yes.

You have repositories in your list of software sources that are now longer accessible. The apt-get commands would have also given you information about those repositories. As apt-get update seeks to connect with the repositories it will report "Hit" or "Ign" = Ignore. And then apt-get upgrade will present a list of the repositories that have been ignored or replaced by others and then print that message.

Regards.

---

### Post by dino99 on 2015-07-26
it can also be some server(s) down for maintenace or else; simply retry later :p

---

