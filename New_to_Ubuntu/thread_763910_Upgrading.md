---
title: "Upgrading"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by NewToLinuxAIR on 2008-04-23
Hi

Does anyone know how to upgrade Ubuntu 6 to Ubuntu 7 and then to 8 without creating a new installation or un-installing and then reinstalling the new version?

I have Ubuntu 6 for 64bit machines, and would like to upgrade in the same way you can with Microsoft. Further, I am completely new to Linux and would like someone guidance. Can anyone help me?

Thanks

---

### Post by Oldsoldier2003 on 2008-04-23
> **NewToLinuxAIR said:**
> Hi

Does anyone know how to upgrade Ubuntu 6 to Ubuntu 7 and then to 8 without creating a new installation or un-installing and then reinstalling the new version?

I have Ubuntu 6 for 64bit machines, and would like to upgrade in the same way you can with Microsoft. Further, I am completely new to Linux and would like someone guidance. Can anyone help me?

Thanks

if you are using 6.06 LTS you will be able to do a direct upgrade to 8.04 LTS. first. make sure you have one of the desktop metapackages installed. (ubuntu-desktop, kubuntu-desktop or xubuntu-desktop)

then:
```

sudo aptitude update
sudo aptitude upgrade
sudo aptitude dist-upgrade
```


to make sure you are completely updated.then

```
sudo aptitude install update-manager-core
sudo do-release-upgrade -d
```

if you wait until Hardy is officially released the last command will be

```
sudo do-release-upgrade
```

you wont need the -d

Hope this helps.

---

### Post by bawilson2 on 2008-04-23
Here's a guide on upgrading to Hardy.

[https://help.ubuntu.com/community/HardyUpgrades]("https://help.ubuntu.com/community/HardyUpgrades")

---

### Post by SunnyRabbiera on 2008-04-23
well its possible to do but not recommended to upgrade ubuntu without reinstalling anything.
But in your case its probably safer to do a fresh install of hardy, there is supposed to be a way to easily update from dapper to hardy but I am unsure on how unstable it will make your system.

as for guidance, what parts do you need help on?

---

### Post by phidia on 2008-04-23
I also believe there is a gui way to do this.
If you open up the Update Manager 
(from the top menu in Gnome, System>Administration>Update Manager)
with an active internet connection if a more recent version of Ubuntu is available it will give you the option to upgrade to that.

I believe the gui method uses the same commands as the CLI way.
I have done several disto-upgrades on 64 bit systems too and they worked fine-no problems.

When there are problems I suspect it's because there were packages installed not using the package manager.

---

### Post by SunnyRabbiera on 2008-04-23
> **phidia said:**
> I also believe there is a gui way to do this.
If you open up the Update Manager 
(from the top menu in Gnome, System>Administration>Update Manager)
with an active internet connection if a more recent version of Ubuntu is available it will give you the option to upgrade to that.

Right, but he must not do it until hardy is ready.
when the time comes it will appear on its own.

---

### Post by phidia on 2008-04-23
> **SunnyRabbiera said:**
> Right, but he must not do it until hardy is ready.
when the time comes it will appear on its own.

Absolutely!

The OP was asking about upgrading from 6 to 7 also.

---

