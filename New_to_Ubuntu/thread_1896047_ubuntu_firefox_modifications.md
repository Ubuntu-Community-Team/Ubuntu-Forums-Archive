---
title: "ubuntu firefox modifications?"
date: 2011-12-16
forum: New to Ubuntu
---

### Post by Matrix01 on 2011-12-16
what does ubuntu firefox modification in add ons do?

---

### Post by ankspo71 on 2011-12-16
Hi,
That would be the package 'xul-ext-ubufox', or formerly ubufox

In Ubuntu 11.10's terminal, 'apt-cache show xul-ext-ubufox' says this:
> Description-en: Ubuntu-specific configuration defaults and apt support for Firefox
 Adds Ubuntu-specific modifications to Firefox.
 .
 Integrates the browser with Ubuntu to:
  * Enable searching for missing plugins from Ubuntu software catalog
  * Add the following options to the Help menu
    - Get help on-line
    - Help translating Firefox
    - Ubuntu Release Notes
  * Set homepage to Ubuntu Start Page
  * Display a restart notification after upgrading Firefox
  * Add ask.com to the search engines.
 .
 You can uninstall this if you prefer to use a pristine Firefox install.
Enhances: firefox


[COLOR="Gray"]Also, I believe it disables firefox's own updating feature.[/COLOR] <-- nope I was wrong about that part. :rolleyes:

---

