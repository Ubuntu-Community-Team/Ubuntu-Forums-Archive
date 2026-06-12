---
title: "IBM Websphere 7 install issue"
date: 2013-04-11
forum: New to Ubuntu
---

### Post by Arturo Martinez on 2013-04-11
Ok, hi everyone!
First of all, thanks for your time and support.

I know, that I should search through IBM's support web, or through all the internet, but I'm completely freezed with this issue.
I'm trying to install IBM Websphere 7 on Ubuntu 12.10.

I've updated all the OS and APP (*sudo apt-get install && sudo apt-get update*) [**ok**]
I've re-linked the shell from DASH to BASH [**ok**]
I've set the path where it's suppose to be the browser (Firefox) launcher. (*export BROWSER=/usr/bin/firefox*) [**ok**]
Then, whenever I run _launchpad.sh_ file it says I don't have [COLOR=#ff0000]any supported BROWSER[/COLOR].
I thought that this should be something related with my Firefox version, then I came to an IBM's page that explains that with "under no logical circunstances" some Firefox version are not supported, so I have to "update" the _browser.sh_ configuration file, adding "**Firefox\ X[0-9].*) return 0;;*" text to that script. I have to add support for versions 1[0-9] and 2[0-9]. [**ok**]

Now, whenever I run _launchpad.sh_ file, the Firefox browser opens (as expected) but the same #|@#|@€|@#~|@#~|@#~| error cames again: [COLOR=#ff0000]no supported browser[/COLOR].

Any help out there?

---

