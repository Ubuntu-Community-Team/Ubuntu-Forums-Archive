---
title: "Ruby gems bundler install showes nothing"
date: 2015-04-12
forum: New to Ubuntu
---

### Post by Imtiaz_Dipto on 2015-04-12
i am trying to create ruby on rails environment in my Ubuntu 14.04 following this link -   [https://gorails.com/setup/ubuntu/14.04](https://gorails.com/setup/ubuntu/14.04)   but after ruby installing when i am trying to install gems bundle its  show me nothing... i am waiting for 2 - 3 hour for its massage its show  me nothing... then i am trying the command like this way - 

"gem install bundler -V" 

but i get the same result... no any massage. i need some help.. please any one help me..

---

### Post by TheFu on 2015-04-12
Are you using rvm or rbenv?
How much RAM does the system have?  I found gems to refuse to work with less than 1G of RAM.  I'm not using RoR anymore over that requirement. A trivial webapp shouldn't mandate the production server which may be replicated 1,000x require 1G of RAM for a support tool, IMHO.  My notes for setting up RoR for 12.04 are here: [http://blog.jdpfu.com/2012/07/18/ruby-on-rails-environment-on-ubuntu-12-04](http://blog.jdpfu.com/2012/07/18/ruby-on-rails-environment-on-ubuntu-12-04)

---

### Post by Imtiaz_Dipto on 2015-04-12
i am trying to use rbenv .. and my system have 4 GB RAM

---

### Post by TheFu on 2015-04-12
Those instructions say to run:```

echo "gem: --no-ri --no-rdoc" > ~/.gemrc
gem install bundler
```

Did that work or not?  Exactly (copy/paste) what is the output if it didn't work?

Or is the issue at a different place? Did ruby get installed correctly? does the version actually match what you expect and is it NOT the system ruby?

---

### Post by Imtiaz_Dipto on 2015-04-13
after runing this its dont give me any output...this the main problem it didn't give me any output. ruby was installed correctly.

---

### Post by TheFu on 2015-04-13
**ruby -v**?
Then **which gem**?

---

### Post by Imtiaz_Dipto on 2015-04-17
its show me ruby 2.2.1

---

### Post by TheFu on 2015-04-17
Sorry it wasn't clear - type "which ruby"
The path is important.

---

