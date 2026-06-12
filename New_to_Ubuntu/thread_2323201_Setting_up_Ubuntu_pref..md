---
title: "Setting up Ubuntu pref."
date: 2016-05-03
forum: New to Ubuntu
---

### Post by UtnubuLap on 2016-05-03
Hey!

Haven't used Ubuntu ,or Linux in general for a few years. (So I have no clue what I am talking about.) Just installed Ubuntu 16.04 LTS on a spare laptop I have. Went well, but I have a few questions.




First thing I did was to update, I searched for "Software Updater" in dash and ran it, everything went straight forward.

However after when I did:
sudo apt-get update
sudo apt-get upgrade

It seemed that "Software Updater" had not updated everything.

**Question 1**: What terminal commands are equivilant to the "Software Updater"?
**Question 2**: How do I navigate to "Software Updater" without going via searching?
**Question 3**: What is the prefered method of updating Ubuntu? (Software Updater vs sudo apt-get upgrate/upgrade vs sudo apt-get upgrate/dist-upgrade)



System updated, I went exploring:

I noticed that "System Settings - Secruity & Privacy - Search" is toggled to "OFF", which should prevent online search results. (Amazon, etc) Great! However I downloaded and installed "Unity Tweak Tool" and navigated to "Unity Tweak Tool - Search" and noticed "Show "More Suggestions"" ticked, which displays "If enabled, show applications available for download in the Dash" if mouse is hovered over.

**Question 4**: Isn't the "OFF" supposed to prevent all online searches? Not just "Search online sources", which is unticked in "Unity Tweak Tool".

Let me know if I am missing something, I believe this should be unticked due to "OFF" being toggled.

(I tried searching for "VLC" and "VideoLAN" but got no results, so it might not be effective, even if the box is ticked. I am assuming it searches "Ubuntu Software" for "applications available for download". Regardless I will disable it, if I need some application I won't search for it in dash, but in "Ubuntu Software".)



I had the extras option ticked when I installed, for .mp3, etc. Can't recall exactly what it was named, but since the "Software Updater" seemed to differ from terminal, I decided to try:

sudo apt-get install ubuntu-restricted-extras

It went on for a minute installing.

**Question 5**: Was the full package not installed upon installing Ubuntu? Only parts of it?


Thanks!

---

### Post by mcduck on 2016-05-03
1: They should all do the same thing. However Software Updates follows your settings for how often updates should be presented to the user, so it might not display non-security updates unless you specifically tell it to check for updates. I don't think it does automatic check every time you open the program. Apart from that, it's equivalent of "sudo apt-get upgrade".

2: pin it into your launcher, start from terminal, or just wait for it to pop up on it's own (either because of important security updates, or based on the update settings you have for non-critical updates). I suppose intended way is that you wouldn't usually launch it yourself.

3. Which ever you prefer yourself. They all are just interfaces for exactly the same package management system (however keep in mind that *apt-get dist-upgrade* is slightly more powerful, as it's also able to uninstall packages to deal with dependencies. Sometimes it's required, but if you run it, make sure to actually check the changes it suggests before continuing). I personally prefer using "sudo apt update && sudo apt upgrade", just because updatinfg stuff from CLI is same process I do  on the servers and other things I manage, might as well do it the same way on every system. And the *apt* command has some nice eyecandy compared to *apt-get* ;)

4. The package manager knows what packages and versions are available in the repositories (that's how your updates work, for example), so suggesting a program to install doesn't require online search. It's local information. ;) You are right though that it's not listing every package available, as that would probably yield way too many useless results for desktop users, so it's using a subset of common desktop packages instead. I'm not quite sure how they are selected, I would have assumed VLC to be in the list...

5. I'm not sure about this one, maybe the option you get during install isn't exactly the same as the ubuntu-restricted-extras? It probably installs *some* proprietary drivers and common codecs etc, while I believe ubuntu-restricted-extras has quite a lot of stuff...

---

### Post by howefield on 2016-05-03
For number 5, you'd have ttf-mscorefonts-installer and unrar at the very least, possibly more that wouldn't be installed initially but is included with ubuntu-restricted-extras.

---

### Post by grahammechanical on 2016-05-03
> It seemed that "Software Updater" had not updated everything.

What was the actual message? "packages held back?" If that is the case then that is normal. Those packages are held back for a reason and the reason maybe that they are dependent on other packages that are not yet ready to go into the normal archive channel. These held back packages show up in Software Updater. They are listed but not checked to be downloaded & installed.

Be careful when using dist-upgrade.

> apt-get dist-upgrade 

The same as the above, except add the  "smart upgrade" checkbox. It tells APT to use "smart" conflict  resolution system, and it will attempt to upgrade the most 
important  packages at the expense of less important ones if necessary.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

It can break things sometimes. It is rare that it does break something but you never know until it happens.

> Isn't the "OFF" supposed to prevent all online searches?

If it meant that you would not be able to update/upgrade the system or to install any more applications. To do those two things we need to search the Ubuntu software repositories or archives. How can that be done if the appropriate utilities are not allowed to go online and search for what we are asking for? Likewise, when we go to Additional Drivers to change to another proprietary video driver the utility has to search online for the appropriate video driver, download it and install it. So, do not be surprised if you see internet activity if you do any of these things.

> Was the full package not installed upon installing Ubuntu? Only parts of it?

It is not one package but many and if we do not tick to accept a Microsoft End User Licence Agreement (EULA) then Microsoft true type core fonts will not get installed as part of the deal. Then later when we install Ubuntu Restricted Extras there is still one part of the Extras that is not installed. Perhaps all the Extras get re-installed.

Ubuntu 16.04 comes with some new (to us) Apt commands.

```
apt update = apt-get update
apt upgrade = apt-get upgrade
apt full-upgrade = apt-get dist-upgrade
```

Regards.

---

### Post by UtnubuLap on 2016-05-22
Thanks! Appreciate the help!

---

