---
title: "Evolution  cannot get Gmail contacts"
date: 2015-06-08
forum: New to Ubuntu
---

### Post by anbu-s on 2015-06-08
Evolution was working fine with gmail contacts showing up when i type in an email to name. But lately, evolution doesnt get any gmail contacts at all.
When i click on gmail contacts it shows this error

Detailed error message: Unable to connect to 'Contacts': The requested resource was not found: [https://developers.google.com/accounts/docs/AuthForInstalledApps](https://developers.google.com/accounts/docs/AuthForInstalledApps)

Googling this doesn't help much other than some forums says its something google has changed recently. How do i fix this for evolution now?

I'm on evolution 3.12.9

Thanks

---

### Post by Vladlenin5000 on 2015-06-08
I don't use Evolution myself. I do know lots of people using it and some have Gmail accounts. Never heard of any issue.
Perhaps you need to update Evolution. It should be 3.12.11 by now in 15.04.

---

### Post by anbu-s on 2015-06-08
> **Vladlenin5000 said:**
> I don't use Evolution myself. I do know lots of people using it and some have Gmail accounts. Never heard of any issue.
Perhaps you need to update Evolution. It should be 3.12.11 by now in 15.04.

Thanks.
How do I upgrade to the latest version of evolution?

---

### Post by Vladlenin5000 on 2015-06-08
I should be updated with regular system updates. What Ubuntu version (I mean release) are you running?

---

### Post by anbu-s on 2015-06-08
> **Vladlenin5000 said:**
> I should be updated with regular system updates. What Ubuntu version (I mean release) are you running?

I'm on 
Ubuntu 14.04.2 LTS
Gnome 3.12.2

System updates gives me an error message saying "failed to download repository information"

Details of error msg:

```
W:Failed to fetch cdrom://Ubuntu-GNOME 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)/dists/trusty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu-GNOME 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)/dists/trusty/multiverse/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu-GNOME 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)/dists/trusty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu-GNOME 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)/dists/trusty/universe/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu-GNOME 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)/dists/trusty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu-GNOME 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)/dists/trusty/multiverse/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu-GNOME 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)/dists/trusty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu-GNOME 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)/dists/trusty/universe/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by Vladlenin5000 on 2015-06-08
> **anbu-s said:**
> I'm on 
Ubuntu 14.04.2 LTS
Gnome 3.12.2

System updates gives me an error message saying "failed to download repository information"

Which repository/ies? Please post the results if *sudo apt-get update* (Go advanced, click the # and paste inside).

---

### Post by anbu-s on 2015-06-08
> **Vladlenin5000 said:**
> Which repository/ies? Please post the results if *sudo apt-get update* (Go advanced, click the # and paste inside).


Here are the results :

```
W: Failed to fetch cdrom://Ubuntu-GNOME 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)/dists/trusty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu-GNOME 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)/dists/trusty/multiverse/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu-GNOME 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)/dists/trusty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu-GNOME 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)/dists/trusty/universe/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu-GNOME 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)/dists/trusty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu-GNOME 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)/dists/trusty/multiverse/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu-GNOME 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)/dists/trusty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu-GNOME 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)/dists/trusty/universe/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by anbu-s on 2015-06-08
I unchecked the CD-rom option under the software updates - now there is no error.
But no software updates either. I still have evolution 3.12.9

---

### Post by wildmanne39 on 2015-06-08
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by anbu-s on 2015-06-09
> **Wild Man said:**
> Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

I'll do that in the future - thanks for pointing out

Any solution to my problem? its been a struggle with evolution not having any of my gmail contacts. Its impossible to send emails now from my laptop anymore.

---

### Post by deadflowr on 2015-06-10
How do you have evolution 3.12.X on trusty when the version for trusty only is at 3.10.X ?
Package Reference here: [http://packages.ubuntu.com/search?keywords=evolution](http://packages.ubuntu.com/search?keywords=evolution)

Are you really running a newer Ubuntu version, like 14.10 (utopic)?
Or did you add a gnome ppa, maybe?

---

### Post by tornadof3 on 2015-06-10
I suspect Google may have changed the way they handle requests to access contact lists. I use Evolution (from standard repos) on Ubuntu 15.04 and contacts were working fine until about last week. I get the same error message. However, at work I Thunderbird with the plugin for google contacts and that has recently stopped too

---

### Post by anbu-s on 2015-06-10
So its broken recently then. No solutions from anyone?

---

### Post by anbu-s on 2015-06-12
Not sure what happened. There was some system updates. Nothing i saw related to evolution. But now I get all gmail contacts.. So I guess there was a fix!!

---

### Post by Adam_Kleiner on 2015-06-13
Someone correct me if I'm wrong, but I don't believe Evolution automatically grabs your contacts for you. You'll likely have to manually export them from Gmail and import into Evolution.

To get your contacts from Gmail:
[https://support.google.com/mail/answer/24911?hl=en](https://support.google.com/mail/answer/24911?hl=en)

---

