---
title: "How to fix installed version is higher than the latest version"
date: 2011-11-08
forum: New to Ubuntu
---

### Post by whchaz1027 on 2011-11-08
Hi Geeks,

Due to firefox branding and force to downgrade my firefox to 3.5. Now, every time I make an upgrade in synaptic, I have to use force version in order to get the latest. My question is how can I fix this?

Thanks in advanced,
whchaz1027

---

### Post by pawanh on 2011-11-20
> **whchaz1027 said:**
> Hi Geeks,

Due to firefox branding and force to downgrade my firefox to 3.5. Now, every time I make an upgrade in synaptic, I have to use force version in order to get the latest. My question is how can I fix this?

Thanks in advanced,
whchaz1027
I'm not quite sure what you mean, but I think you'd be better off installing the version in the repositories. So remove your current version and install the latest one from synaptic.

---

### Post by beew on 2011-11-20
I think Mozilla no longer supports FF3.5 so it is a security risk to go online with it.

But to your general question, if you want to prevent a package from being upgraded for legitimate reasons,--it is not in your present case,--simply lock the version in synaptic: highlight the package and go to packages > lock version. Again you should definitely upgrade your FF.

---

### Post by whchaz1027 on 2011-11-20
> **beew said:**
> I think Mozilla no longer supports FF3.5 so it is a security risk to go online with it.

But to your general question, if you want to prevent a package from being upgraded for legitimate reasons,--it is not in your present case,--simply lock the version in synaptic: highlight the package and go to packages > lock version. Again you should definitely upgrade your FF.

Yes, I'm already using FF 7.0.1. I don't want to lock its version. I mean the latest version is always 3.6.10 even if there is a new version of it. Pls. see this [http://img534.imageshack.us/img534/9865/ffbrandingproblem.png](http://img534.imageshack.us/img534/9865/ffbrandingproblem.png)

Thanks to your replies Sir.

---

### Post by pawanh on 2011-11-22
You're using Maverick. The latest version of Firefox for it is indeed 3.6.10. That's because Maverick is not the current version of Ubuntu. It supports the older version of Fx. However, if you want the latest version of Fx every time, add Fx's official ppa to your repository.

Enter the following in a terminal
```
gksu add-apt-repository ppa:mozillateam/firefox-stable
```

Then update your repository. You should then see the latest Fx version in Synaptic.

---

### Post by whchaz1027 on 2011-11-22
> **pawanh said:**
> You're using Maverick. The latest version of Firefox for it is indeed 3.6.10. That's because Maverick is not the current version of Ubuntu. It supports the older version of Fx. However, if you want the latest version of Fx every time, add Fx's official ppa to your repository.

Enter the following in a terminal
```
gksu add-apt-repository ppa:mozillateam/firefox-stable
```Then update your repository. You should then see the latest Fx version in Synaptic.


I am using Natty and I already have that ppa. Regarding with the latest version, there's no problem with it, I could still have one when it is availabale. My problem is that I have to use force version in order for me to install that latest version. I want to remove Fx 3.6 from the choices and instead, only the latest version would just appear on that drop down list.

Thank you by the way...

---

### Post by pawanh on 2011-11-22
> **whchaz1027 said:**
> I am using Natty and I already have that ppa. Regarding with the latest version, there's no problem with it, I could still have one when it is availabale. My problem is that I have to use force version in order for me to install that latest version. I want to remove Fx 3.6 from the choices and instead, only the latest version would just appear on that drop down list.

Thank you by the way...
I wonder why it is showing you the maverick version then :D
I wish I could have helped you better

---

### Post by lovinglinux on 2011-11-24
> **whchaz1027 said:**
> I am using Natty and I already have that ppa. Regarding with the latest version, there's no problem with it, I could still have one when it is availabale. My problem is that I have to use force version in order for me to install that latest version. I want to remove Fx 3.6 from the choices and instead, only the latest version would just appear on that drop down list.

Thank you by the way...

Remove all firefox versions using Synaptic and install firefox again.

---

### Post by whchaz1027 on 2011-11-25
> **lovinglinux said:**
> Remove all firefox versions using Synaptic and install firefox again.


I guess, that's not a good idea. I think my problem here is the firefox branding thing...Anyway, thanks for the suggestion.

---

