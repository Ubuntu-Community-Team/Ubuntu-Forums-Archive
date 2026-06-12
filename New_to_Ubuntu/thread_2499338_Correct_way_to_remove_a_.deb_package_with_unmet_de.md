---
title: "Correct way to remove a .deb package with unmet dependencies"
date: 2024-07-23
forum: New to Ubuntu
---

### Post by nightnome on 2024-07-23
I've tried to install a .deb package with dpkg -i command, but have some unmet dependencies and can't be installed. But this action has affected apt, and each time that i want to install any program with apt i can't because i've a package with unmet dependencies.

Apt recommends to me run "apt --fix-broken install" that install all the .deb package dependencies. But "apt --fix-broken install" download and install missing packages and install the package that i was trying to install with dpkg . I don't want install anything, i just want the system forget/remove that package. I've tried 'dpkg -r package' and 'apt remove package' but since the package isn´t installed i can't do that.

Is there any way to do that?

---

### Post by ActionParsnip on 2024-07-23
try:
```

sudo apt-get -f install

```
it'll either meet deps or uninstall the "bad" deb

---

### Post by nightnome on 2024-07-23
Same as &#8220;apt --fix-broken install&#8221;, it asks me to install the dependencies and the package.

Is there no way to get it to forget the package? Clean up all necessary files/configs and leave it as if I never put dpkg -i package.deb

---

### Post by &amp;KyT$0P# on 2024-07-23
What package?  What version of the package?
Where did you get this package?
What Ubuntu version are you using?

Does this work? -
```
sudo dpkg -P package
```

---

### Post by nightnome on 2024-07-23
> **halogen2 said:**
> What package?  What version of the package?
libpkcs11-dnie_1.6.8_amd64.deb (dirvers/tool for spanish ID reader)
> **halogen2 said:**
> Where did you get this package?
From spanish national police website: [https://www.dnielectronico.es/PortalDNIe/PRF1_Cons02.action?pag=REF_1110&id_menu=66](https://www.dnielectronico.es/PortalDNIe/PRF1_Cons02.action?pag=REF_1110&id_menu=66)
> **halogen2 said:**
> What Ubuntu version are you using?
KUbuntu 24.04

> **halogen2 said:**
> Does this work? - Yes that works. In fact now I realize that dpkg -r would have also worked if I had used it with the correct package name, because I was using libpkcs11-dnie_1.6.8_amd64 instead of libpkcs11-dnie. #-o [B]

Thank you very much for your help.[/B]

---

### Post by ActionParsnip on 2024-07-23
If this is solved then please mark as solved

---

