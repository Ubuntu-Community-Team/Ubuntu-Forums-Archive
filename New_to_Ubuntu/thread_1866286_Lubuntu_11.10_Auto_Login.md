---
title: "Lubuntu 11.10 Auto Login"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by loj23 on 2011-10-21
How do I enable auto login for Lubuntu 11.10 ?
I tried to inspired from this thread [http://ubuntuforums.org/showthread.php?t=1864527&page=2](http://ubuntuforums.org/showthread.php?t=1864527&page=2) 
and set *lightdm.conf* file:
```

[SeatDefaults] 
user-session=[COLOR=Red]lubuntu[/COLOR] 
greeter-session=lightdm-gtk-greeter 
autologin-user=my_username 
autologin-user-timeout=0
```but it does not work.
After this I have still login screen and have to login manualy.

---

### Post by dingo on 2011-10-21
This worked for me to enable autologin on lubuntu 11.10 (from the wiki at: [https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides]("https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides"))

```
sudo nano /etc/lxdm/default.conf

```
and replace lines:

```
[base]
# autologin=dgod

```
to

```
[base]
autologin=dgod
```

replace dgod with your username

---

### Post by amjjawad on 2011-10-21
> **loj23 said:**
> How do I enable auto login for Lubuntu 11.10 ?
I tried to inspired from this thread [http://ubuntuforums.org/showthread.php?t=1864527&page=2](http://ubuntuforums.org/showthread.php?t=1864527&page=2) 
and set *lightdm.conf* file:
```

[SeatDefaults] 
user-session=[COLOR=Red]lubuntu[/COLOR] 
greeter-session=lightdm-gtk-greeter 
autologin-user=my_username 
autologin-user-timeout=0
```but it does not work.
After this I have still login screen and have to login manualy.

Hello and Welcome :)

Have you tired this: [https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_enable_automatic_logon_in_LXDM](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_enable_automatic_logon_in_LXDM)


Oh sorry, someone beat me to it :)

---

### Post by loj23 on 2011-10-23
> **dingo said:**
> This worked for me to enable autologin on lubuntu 11.10 (from the wiki at: [https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides))


Hi,
thank you. 
But this setting did not help me. 
Still same. I have to login manually.

---

### Post by amjjawad on 2011-10-23
> **loj23 said:**
> Hi,
thank you. 
But this setting did not help me. 
Still same. I have to login manually.

Just tested that on my second PC where Lubuntu 11.10 is installed and it did work.

Have you rebooted after changing the config file?

---

### Post by tranduyhung on 2012-01-04
My mistake, wrong thread

---

### Post by MacHaddock on 2012-02-22
> **dingo said:**
> This worked for me to enable autologin on lubuntu 11.10 (from the wiki at: [https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides]("https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides"))

```
sudo nano /etc/lxdm/default.conf

```
and replace lines:

```
[base]
# autologin=dgod

```
to

```
[base]
autologin=dgod
```

replace dgod with your username


When I did this I got something about not finding xsession and using fallbacksession instead. I changed back and I still have the fallback session!

---

