---
title: "I have Ubuntu Pro and i am not geting any updates because of esm"
date: 2023-08-24
forum: New to Ubuntu
---

### Post by scag on 2023-08-24
[https://portal.support.canonical.com/selfservice/s/article/Creating-a-local-apt-repository-of-the-ESM-and-FIPS-Repositories-for-Ubuntu](https://portal.support.canonical.com/selfservice/s/article/Creating-a-local-apt-repository-of-the-ESM-and-FIPS-Repositories-for-Ubuntu)  im trying hard to under stand what i did wrong but i think there is no way to fix just a fresh reinstall

---

### Post by scag on 2023-08-24
yea i am going to keep research because i half to find the problem and find a solution to the problem then just giving up yup hears what i did wrong  500 http://<IP_ADDR_OR_FQDN_APT_MIRROR>/ubuntu/ <RELEASE>-infra-updates/main amd64 Packages
     origin <IP_ADDR_OR_FQDN_APT_MIRROR>
 500 http://<IP_ADDR_OR_FQDN_APT_MIRROR>/ubuntu/ <RELEASE>-infra-security/main amd64 Packages
     origin <IP_ADDR_OR_FQDN_APT_MIRROR>

---

### Post by MAFoElffen on 2023-08-24
What is the output of these:
```

pro status
grep . /etc/apt/sources.list.d/ubuntu-esm-*.list

```
Please post the output with CODE Tags.

---

