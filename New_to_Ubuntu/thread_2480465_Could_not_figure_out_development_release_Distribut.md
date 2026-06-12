---
title: "Could not figure out development release: Distribution data outdated. Please check fo"
date: 2022-10-31
forum: New to Ubuntu
---

### Post by maketopsite on 2022-10-31
```
unattended-upgrade -v
Could not figure out development release: Distribution data outdated. Please check for an update for distro-info-data. See /usr/share/doc/distro-info-data/README.Debian for details.
Starting unattended upgrades script
Allowed origins are: o=Ubuntu,a=focal, o=Ubuntu,a=focal-security, o=UbuntuESMApps,a=focal-apps-security, o=UbuntuESM,a=focal-infra-security
Initial blacklist: 
Initial whitelist (not strict): 
No packages found that can be upgraded unattended and no pending auto-removals
```


Although I've added
```
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates main
```
into

[FONT=courier new]/etc/apt/sources.list[/FONT]

and made

```
apt-get autoclean
apt-get clean
apt clean
apt update && apt upgrade && apt full-upgrade
apt-get update && apt-get upgrade  && apt-get dist-upgrade && apt-get install -f
```

Is please necessary any other action ?

```

cat /etc/os-release 
NAME="Ubuntu"
VERSION="20.04.5 LTS (Focal Fossa)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 20.04.5 LTS"
VERSION_ID="20.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=focal
UBUNTU_CODENAME=focal
```

---

### Post by ActionParsnip on 2022-10-31
What is the output of:
```

dpkg -l | awk {'print $2'} | grep -i desktop

```
Thanks

---

### Post by maketopsite on 2022-10-31
> **ActionParsnip said:**
> What is the output of:
```

dpkg -l | awk {'print $2'} | grep -i desktop

```
Thanks

You are welcome.

```
# dpkg -l | awk {'print $2'} | grep -i desktop
budgie-desktop-environment
cinnamon-desktop-data
desktop-base
desktop-file-utils
gir1.2-freedesktop:amd64
gir1.2-gdesktopenums-3.0:amd64
gir1.2-gnomedesktop-3.0:amd64
gnome-desktop3-data
gsettings-desktop-schemas
kubuntu-settings-desktop
libgnome-desktop-3-19:amd64
libunity-scopes-json-def-desktop
mate-desktop-common
plasma-desktop
plasma-desktop-data
policykit-desktop-privileges
sound-theme-freedesktop
xdg-desktop-portal
xfdesktop4
xfdesktop4-data
```

---

### Post by MAFoElffen on 2022-10-31
> **maketopsite said:**
> ```
Although I've added
[CODE]deb [[COLOR=#ff0000]http://archive.ubuntu.com/ubuntu[/COLOR]]("http://archive.ubuntu.com/ubuntu") focal-updates main
```
into

[FONT=courier new]/etc/apt/sources.list[/FONT]

Because the URL is incomplete... Shouldn't it be(?)
```
deb  http://us.archive.ubuntu.com/ubuntu/ focal-updates main
```
And so forth...

---

### Post by cg2v on 2022-11-01
This is [COLOR=#333333]LP[/COLOR][#1993667]("https://launchpad.net/bugs/1993667"), which will be fixed by distro-info-data 0.52ubuntu0.2 once that is fully released.

---

### Post by maketopsite on 2022-11-02
> **MAFoElffen said:**
> Because the URL is incomplete... Shouldn't it be(?)
```
deb  http://us.archive.ubuntu.com/ubuntu/ focal-updates main
```
And so forth...

I'm sorry I don't know. I've used URL recommended in documentation: [FONT=courier new]/usr/share/doc/distro-info-data/README.Debian[/FONT]

---

### Post by maketopsite on 2022-11-02
> **cg2v said:**
> This is [COLOR=#333333]LP[/COLOR][#1993667]("https://launchpad.net/bugs/1993667"), which will be fixed by distro-info-data 0.52ubuntu0.2 once that is fully released.

well thank you.

---

### Post by maketopsite on 2022-11-11
> **cg2v said:**
> This is [COLOR=#333333]LP[/COLOR][#1993667]("https://launchpad.net/bugs/1993667"), which will be fixed by distro-info-data 0.52ubuntu0.2 once that is fully released.

Solved, thank you.

---

