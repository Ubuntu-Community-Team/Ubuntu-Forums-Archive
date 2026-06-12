---
title: "facing the below error when trying to update or installl software"
date: 2013-05-01
forum: New to Ubuntu
---

### Post by izareif on 2013-05-01
mon 1.2.5-0ubuntu0.10.04.1   Something wicked happened resolving 'diriyahisa1:8080' (-5 - No address associated with hostname) Err [http://64.repository.backtrack-linux.org/](http://64.repository.backtrack-linux.org/) revolution/main libglib-perl 1:1.222-1   Something wicked happened resolving 'diriyahisa1:8080' (-5 - No address associated with hostname) Err [http://all.repository.backtrack-linux.org/](http://all.repository.backtrack-linux.org/) revolution/main unattended-upgrades 0.55ubuntu6   Something wicked happened resolving 'diriyahisa1:8080' (-5 - No address associated with hostname) Err [http://64.repository.backtrack-linux.org/](http://64.repository.backtrack-linux.org/) revolution/main libpango-perl 1.221-2   Something wicked happened resolving 'diriyahisa1:8080' (-5 - No address associated with hostname) Err [http://all.repository.backtrack-linux.org/](http://all.repository.backtrack-linux.org/) revolution/main python-software-properties 0.75.10.1   Something wicked happened resolving 'diriyahisa1:8080' (-5 - No address associated with hostname) Err [http://64.repository.backtrack-linux.org/](http://64.repository.backtrack-linux.org/) revolution/main libgtk2-perl 1:1.221-4ubuntu2   Something wicked happened resolving 'diriyahisa1:8080' (-5 - No address associated with hostname)

---

### Post by anejo on 2013-05-01
Usually the "Something wicked happened resolving..." is an indication that your DNS configuration is unable to resolve the address that it is trying to resolve
Are you behind a proxy maybe?
Maybe it is simply a case of checking your network connection settings, resetting it?
Then retry the "apt-get update"

---

### Post by izareif on 2013-05-01
Yes iam using proxy .. plz if pro from my dns can you help me how to configure it?
:confused:

---

### Post by izareif on 2013-05-02
101 view till now and no body can help me in this case ?

---

### Post by claracc on 2013-05-02
> **izareif said:**
> mon 1.2.5-0ubuntu0.10.04.1   Something wicked happened resolving 'diriyahisa1:8080' (-5 - No address associated with hostname) Err [http://64.repository.backtrack-linux.org/](http://64.repository.backtrack-linux.org/) revolution/main libglib-perl 1:1.222-1   Something wicked happened resolving 'diriyahisa1:8080' (-5 - No address associated with hostname) Err [http://all.repository.backtrack-linux.org/](http://all.repository.backtrack-linux.org/) revolution/main unattended-upgrades 0.55ubuntu6   Something wicked happened resolving 'diriyahisa1:8080' (-5 - No address associated with hostname) Err [http://64.repository.backtrack-linux.org/](http://64.repository.backtrack-linux.org/) revolution/main libpango-perl 1.221-2   Something wicked happened resolving 'diriyahisa1:8080' (-5 - No address associated with hostname) Err [http://all.repository.backtrack-linux.org/](http://all.repository.backtrack-linux.org/) revolution/main python-software-properties 0.75.10.1   Something wicked happened resolving 'diriyahisa1:8080' (-5 - No address associated with hostname) Err [http://64.repository.backtrack-linux.org/](http://64.repository.backtrack-linux.org/) revolution/main libgtk2-perl 1:1.221-4ubuntu2   Something wicked happened resolving 'diriyahisa1:8080' (-5 - No address associated with hostname)

You will have to disable the repositories [http://64.repository.backtrack-linux.org/](http://64.repository.backtrack-linux.org/), [http://all.repository.backtrack-linux.org](http://all.repository.backtrack-linux.org), when I click on them with browser it is shown a page full of 0s and 1s, no any software package. What for are them?, what ubuntu are you using?

Disable them in sources.list

---

