---
title: "update-manager problem"
date: 2013-10-18
forum: New to Ubuntu
---

### Post by MadMonkey1966 on 2013-10-18
Update Manager tells me...The package information was last updated 12 days ago. Press 'Check'...etc....

When i do, i get...

Failed to download repository information

Check your Internet connection.

W:Failed to fetch [http://packages.medibuntu.org/dists/precise/Release.gpg](http://packages.medibuntu.org/dists/precise/Release.gpg)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, E:Some index files failed to download. They have been ignored, or old ones used instead.

No idea what it all means as i am no Ubntu expert by any means. All i know is i have an internet connect as i am here now lol...

Any help would be greatly appreciated.

Many Thanks

---

### Post by grahammechanical on 2013-10-18
You have in your software sources a repository that no longer exists. You need to remove that medibuntu repository. If you set Update Manager to check for updates daily you would have been getting those error messages every day. You most likely have Update Manager set for checking for updates every two weeks. This is not the problem. You should still be able to update but you will get those error messages until you take medibuntu out of your software sources.

[http://www.medibuntu.org/](http://www.medibuntu.org/)

Regards.

---

### Post by MadMonkey1966 on 2013-10-18
Thanks for the reply Graham...

I hav gone into Synaptic Package Manager and removed the 2 Medibuntu entries in there (what every they were)

BUT i am still getting the same problem, have i missed something ? as i say, i am no expert when it come to stuff like this lol

Cheers :)

---

### Post by ibjsb4 on 2013-10-18
Check "Software Sources" for Medibuntu.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

### Post by MadMonkey1966 on 2013-10-18
Yay,,,great stuff ibjsb4

There were 2 entries in there as you said, deleted and all is back to normal.

Many Thanks for your time :P\\:D/

---

### Post by handydoug on 2013-10-19
Thanks grahammechanical, removing the 2 Medibuntu entries from "Software Sources" worked for me exactly

---

### Post by handydoug on 2013-10-19
Thanks to ibjsb4, too.

---

### Post by Mike Krall on 2013-10-20
Same problem and same solution... thank you...

Mike

---

