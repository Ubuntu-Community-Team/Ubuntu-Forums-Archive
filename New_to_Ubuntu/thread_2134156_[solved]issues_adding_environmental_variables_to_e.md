---
title: "[solved]issues adding environmental variables to /etc/environmental"
date: 2013-04-10
forum: New to Ubuntu
---

### Post by santiagorf on 2013-04-10
Hi all,
I'd like to create a script that adds some environmental variables from a file "variables" to /etc/environment

The file "variables" is of the form

```
#!/bin/sh
export ROOT=/opt/drivers
export ROOT2=$ROOT/S56
....
```

My idea was to add the "variables" file to /etc/environmental 

```
sudo sh -c "cat  variables  >> /etc/environment"
```

The problem with this approach is that if I ```
echo $ROOT2
``` I get 
```
$ROOT/S56
```
rather than the expected
```
/opt/drivers/S56
```

However, if from the terminal I run ```
source variables
``` then if I ```
echo $ROOT2
``` I get the expected result
```
/opt/drivers/S56
```


How can I solve this issue?

I could manually change the "variables" file to 
```
#!/bin/sh
export ROOT=/opt/drivers
export ROOT2=${ROOT}/S56
```
....

but the "variables" file might change in the future and is not me who creates it, so I need a more "automatic solution".

Any help would be much appreciated!

---

### Post by schragge on 2013-04-10
I guess */etc/environment* just doesn't get sourced by any shell script on Ubuntu anymore. On Debian, it's still sourced from */etc/init.d/kbd*, but Ubuntu uses upstart. Try ```
grep /etc/environment /etc/init/*.conf
``` Previously, it was used for locale settings and got sourced from */etc/init/mountall.conf*. But it's deprecated in that role nowadays and */etc/default/locale* gets sourced by [/etc/init/mountall.conf]("http://bazaar.launchpad.net/%7Eubuntu-branches/ubuntu/raring/mountall/raring/view/head:/conf/mountall.conf") instead.

*/etc/environment* still gets evaluated by PAM module [pam_env(8)]("http://manpages.ubuntu.com/manpages/precise/en/man8/pam_env.8.html"), but it's a C program that expects variables in */etc/environment* to be simple *KEY=VALUE* pairs on separate lines.

[uhelp]community/EnvironmentVariables#System-wide_environment_variables[/uhelp] recommends placing your system-wide environment variables in */etc/profile.d/envvar.sh*

Also see [this thread]("http://www.mail-archive.com/debian-devel@lists.debian.org/msg286048.html") on debian-devel and manual page for [pam_env.conf(5)]("http://manpages.ubuntu.com/manpages/precise/en/man5/pam_env.conf.5.html").

---

### Post by santiagorf on 2013-04-11
Thanks. That seemed to solve the problem!!

---

