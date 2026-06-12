---
title: "How to install mysql 5.1 on ubuntu 8.04"
date: 2010-01-15
forum: Repositories &amp; Backports
---

### Post by mnish on 2010-01-15
I am a newbie and have to install mysql 5.1 on ubuntu 8.04. And I cannot find a reasonable tutorial that does this. Anybody able to help?

---

### Post by fahadysf on 2010-02-26
I found a very cool post for this [here]("http://permalink.gmane.org/gmane.comp.finance.mifos.devel/7709")

---

### Post by ffrr on 2010-02-26
fahadysf,

I chanced upon this thread with the same question and likely less experience than the OP. (S)He seems to have managed. I fail following your "very cool post". It isntructs me  to create a file "/etc/apt/sources.list.d/mysql.list" and I fail miserably with "no permission". So far I have managed to handle permission snags with "sudo". Not this time! Nothing doing! I can cd to the directory and even create the file with "touch". But I cannot write to it, despite an owner's write permission.

To my confusion  "su" rejects the password I successfully use with sudo and which is the same password I start the machine with. There is a root account. It has been set up when I installed Ubuntu. In retrospect isn't it strange I wasn't required to define a root password? Somesone has got to be able to login a root and that would normally be the person who installs the system--in my case the only one that uses the machine . . .

Thankful for any advice

Frederic

---

