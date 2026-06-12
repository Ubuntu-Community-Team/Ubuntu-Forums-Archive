---
title: "Preferable /etc/folder to set Path variable system wide?"
date: 2014-04-07
forum: New to Ubuntu
---

### Post by panorain on 2014-04-07
I have read a couple different pages on setting Environment variables.

/etc/profile is stated preferable on this page---> [http://www.cyberciti.biz/faq/ubuntu-linux-user-profile-bash-configuration/](http://www.cyberciti.biz/faq/ubuntu-linux-user-profile-bash-configuration/)

/etc/environment is stated on this page----> [http://2buntu.com/982/setting-environment-variables-in-linux-using-bash-shell-how-to/](http://2buntu.com/982/setting-environment-variables-in-linux-using-bash-shell-how-to/)

As being a beginner I know that the first works but the second has A sole PATH entry line right in it and looks to really be the proper ideal way to modify PATH at this point.

Any thoughts on this?

Thanks,

---

### Post by SeijiSensei on 2014-04-07
[https://help.ubuntu.com/community/EnvironmentVariables#System-wide_environment_variables](https://help.ubuntu.com/community/EnvironmentVariables#System-wide_environment_variables)

Changing /etc/environment seems to be the preferred option.

---

### Post by panorain on 2014-04-07
Thank you, would you happen to know if /etc/environment is the prefered option for most or all releases of Ubuntu.

Again thank you,

---

### Post by SeijiSensei on 2014-04-07
No, but you shouldn't be using any releases older than 12.04 LTS. I'd bet the same documentation applies to that release.

Your next choice should be 14.04 LTS after it is released later this month. Some people prefer to wait a couple of months after the release data for any late bug fixes.

---

### Post by panorain on 2014-04-07
Thank you for affirming the /etc/environment folder is the preferred option to set Path ----> system wide.

I appreciate your help. 

Thank you for your response and caring.

---

