---
title: "Broken packages after upgrading to 15.04"
date: 2016-01-29
forum: New to Ubuntu
---

### Post by theprograme on 2016-01-29
I upgraded last night from 14.04 to 15.04 and when I tried to log in I got the message  "failed to start session." After running apt-get install -f I got the following message:

Correcting dependencies failed.
The following packages have unmet dependencies:

Ubuntu-desktop: depends: (ubuntu-session, unity-control-center, unity-settings-daemon) but it is not installed.

Recommends: cheese, empathy, libreoffice(calc,gnome,ogltrans,pdfimport,writer), nautilus-share,remmina, Whitwell, totem, xul-ext-webaccounts, but it is not installed.

Error,  pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
Unable to correct dependencies.

When running sudo apt-get update, I get the following:

Unknown Multi-Arch type 'no' for package 'compiz-core, compiz-gnome.'
You may want to run apt-get update to correct these problems


How do I fix this?

Running on Asus S550CM

---

### Post by Bashing-om on 2016-01-29
theprograme; Welcome to the forum ..

As you:
> 
I upgraded last night from 14.04 to 15.04


Release 15.04 also goes End_OF_Life in a few days and will no longer have support, we need to get hot on this and get you up to 15.10.

And a big ouch ! Failed release-upgrade. these things can happen - generally to be honest due to operator error.
Did the release-upgrade complete ?
Show us what the sources are now by posting back - between code tags - the outputs of terminal commands:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

Then we most assuredly need to know the status of the package manager; Post back the complete results of:
```

sudo apt update
sudo apt upgrade

```
to give us a notion of what action(s) to take .

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]it is fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

