---
title: "Adept/synaptic won't install anything"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by bjones89 on 2008-05-07
I'm running hardy heron, just installed about 2 days ago

So whenever I enter synaptic or adept, the majority of the packages displayed are grayed out and won't allow me to download them. I wouldn't have assumed this to be a problem, but it is a ton of packages- almost everything that I don't already have- which wasn't the case several hours ago.

Not only that, but I can't install amarok. I took amarok off of my system today, only to realize it doesn't want to come back. oddly though, it isn't grayed out like everything else, the check box simply won't click in adept, and synaptic gives me the following error message:

"Could not mark all packages for installation or upgrade

The following package has unresolved dependencies. Make sure all required repositories are added and enabled in the preferences

'amarok:

Package amarok has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list'"

---

### Post by ramjet_1953 on 2008-05-08
Have you enabled the additional repositories?

TO do this, simply open Synaptic package manager and click on [COLOR="Blue"]Settings>Repositories.
[/COLOR]
When the window opens, simply click all of the boxes, except Source Code.

Regards,
Roger :)

---

### Post by quelx on 2008-05-08
is synaptic prompting you for your password? (i.e. are you running it as su?)

have you tried the console/terminal/command line?

open a terminal window
```
sudo apt-get install amarok
```

---

### Post by bjones89 on 2008-05-08
Thank you Ramjet, that fixed it!

---

