---
title: "Trying to upgrade from 14.0 to 16"
date: 2016-08-20
forum: New to Ubuntu
---

### Post by danielhk1 on 2016-08-20
Dear all

Got the error message when run 

root# do-release-upgrade
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 113, in <module>
    print(_("Checking for a new Ubuntu release"))
UnicodeEncodeError: 'ascii' codec can't encode characters in position 0-6: ordinal not in range(128)

Would you please tell me how to solve this?
Thanks

Daniel

---

### Post by RobGoss on 2016-08-20
> **danielhk1 said:**
> Dear all

Got the error message when run 

root# do-release-upgrade
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 113, in <module>
    print(_("Checking for a new Ubuntu release"))
UnicodeEncodeError: 'ascii' codec can't encode characters in position 0-6: ordinal not in range(128)

Would you please tell me how to solve this?
Thanks

Daniel


Are you adding sudo at the beginning of that command?

```
 [COLOR=#111111][FONT=Consolas]sudo do-release-upgrade[/FONT][/COLOR]
```

I find it better to do a **fresh installation** coming from I'm assuming you mean **14.04 to 16.04**, it will save you a lot of time and heartache, what ever data you feel is important just do a backup and go for it..

---

### Post by pauljw on 2016-08-20
root# do-release-upgrade

This line indicates that you've made unrecommended mods to your 14.04 system and makes one wonder what else you've done that isn't recommended.  You can't do these things and then expect a utility that anticipates an unmolested environment to be able to do its job properly.

---

### Post by danielhk1 on 2016-08-22
> **pauljw said:**
> root# do-release-upgrade

This line indicates that you've made unrecommended mods to your 14.04 system and makes one wonder what else you've done that isn't recommended.  You can't do these things and then expect a utility that anticipates an unmolested environment to be able to do its job properly.

HI Paul

Thanks for your response, i don't know what do you mean by mod? I don't think i have specifically mod the system
To get to root simply a sudo -i can do it

---

### Post by danielhk1 on 2016-08-22
> **RobGoss said:**
> Are you adding sudo are the beginning of that command?

```
 [COLOR=#111111][FONT=Consolas]sudo do-release-upgrade[/FONT][/COLOR]
```

I find it better to do a **fresh installation** coming from I'm assuming you mean **14.04 to 16.04**, it will save you a lot of time and heartache, what ever data you feel is important just do a backup and go for it..

The result is same for both [COLOR=#111111][FONT=Consolas]do-release-upgrade under [/FONT][/COLOR]root and [COLOR=#111111][FONT=Consolas]sudo do-release-upgrade under non root

I have also tried to do fresh install under virtualbox , but it gives me a corrupted screen which i cannot install. I didn't have this problem with 14.04.[/FONT][/COLOR]

---

### Post by oldos2er on 2016-08-23
> **RobGoss said:**
> Are you adding sudo are the beginning of that command?

```
 [COLOR=#111111][FONT=Consolas]sudo do-release-upgrade[/FONT][/COLOR]
```

Not necessary.

---

### Post by yetimon_64 on 2016-08-23
From a bit of googling on this question ... OP what language does your system use ? If anything other than USA english try switching to USA English and then fully updating the system with ...
 ```
sudo apt-get update && sudo apt-get dist-upgrade
```If any problems show up, please post them back here in [noparse]```

```[/noparse]tags for readability before attempting the release upgrade. You should fix any current problems *_before_* attempting the release upgrade.

If the updating works without a problem then try the command
```
[COLOR=#111111][FONT=Consolas]sudo do-release-upgrade[/FONT][/COLOR]
```

It appears from my reading that having a language setting other than English has caused other users problems like yours when doing a release upgrade. Ensuring the system is fully up to date with no errors showing is also recommended from other past threads. 

Hope this works for you, cheers, yeti.

---

### Post by RobGoss on 2016-08-23
I see more and more people having so much trouble trying to upgrade from **14.04** to **16.04 **including my self. I think it has something to do with skipping distributions in between maybe sone key compointentsand software are left out that's needed to move on to 16.04. After I did a **fresh installation** of 16.04 I never look back it;s been good ever sense

---

### Post by yetimon_64 on 2016-08-23
> **RobGoss said:**
> ...After I did a **fresh installation** of 16.04 I never look back it;s been good ever sense
Yes. I must admit to always doing a fresh installation, in fact I dual boot 14.04 and 16.04 off different partitions of the same drive. I never do the release upgrade because of such error reports. 

I just noted when doing research some interesting past posts where the system language setting has caused that particular error the OP posted when a release upgrade was tried. It will be interesting to note if the OP uses another system language set, other than English, if so there may be an easy fix by changing to USA English going by some older threads posting that particular error.

---

### Post by danielhk1 on 2016-08-24
> **yetimon_64 said:**
> Yes. I must admit to always doing a fresh installation, in fact I dual boot 14.04 and 16.04 off different partitions of the same drive. I never do the release upgrade because of such error reports. 

I just noted when doing research some interesting past posts where the system language setting has caused that particular error the OP posted when a release upgrade was tried. It will be interesting to note if the OP uses another system language set, other than English, if so there may be an easy fix by changing to USA English going by some older threads posting that particular error.

Hi Yetimon,

I appericate your response! 

Yes, my system use zh_tw as system language.
After vi /etc/default/locale and change it to en_us, it solved the problem.

Thank you!

Daniel

---

### Post by pauljw on 2016-08-24
> **danielhk1 said:**
> HI Paul

Thanks for your response, i don't know what do you mean by mod? I don't think i have specifically mod the system
To get to root simply a sudo -i can do it

You are so right, I apologize.  I totally spaced that out and envisioned you having created a root account and using it had gotten yourself into something that was creating problems for you.

Paul

---

