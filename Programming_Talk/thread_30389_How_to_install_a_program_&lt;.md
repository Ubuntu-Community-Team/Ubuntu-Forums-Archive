---
title: "How to install a program? :&lt;"
date: 2005-04-28
forum: Programming Talk
---

### Post by -`Orb!t@l´- on 2005-04-28
I'm sorry for a stupid question like this but i download ubuntu and i don't know anything about linux :x. The ubuntu version is x86.

Firefox is version 0.9.0 and xchat 2.0.8 so i wanna update these 2 versions and find out how i can install a program :<. Thx for the help.

---

### Post by ubuntu-geek on 2005-04-28
Hello, If you are running Warty I suggest you load the backports into your sources.list you can find more information here > [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) or you can upgrade to the Hoary release to get new programs.

You can also use synaptic to install software that can be found in your system menus.

---

### Post by -`Orb!t@l´- on 2005-04-28
how can i check if i'm running warty?
whats warty anyway  :?

---

### Post by DJ_Max on 2005-04-28
[QUOTE=-`Orb!t@l´-]how can i check if i'm running warty?
whats warty anyway  :?[/QUOTE]
 It's the codename for Ubuntu 4.10.

---

### Post by -`Orb!t@l´- on 2005-04-29
and is the difference between ubuntu x86 (the version i got)
and the new one big?

and can i update to the new one if i want to?

and how do you check which version you got? :x

---

### Post by blaaat on 2005-04-30
[QUOTE=-`Orb!t@l´-]and is the difference between ubuntu x86 (the version i got)
and the new one big?

and can i update to the new one if i want to?

and how do you check which version you got? :x[/QUOTE]

Yes, you [can update](http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes).

[quote=http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes]

Through Synaptic Package Manager

   1.

      Open up Synaptic Package Manager
   2.

      Change your repositories to look for Hoary
          *

            From:

         ```
URI: http://archive.ubuntu.com/ubuntu/
         Distribution: warty
         Sections: main restricted
```

            To:

         ```
http://archive.ubuntu.com/ubuntu/
         Distribution: hoary
         Sections:  main restricted
```

   3.

      Reload sources
   4.

      Mark All Upgrades
[/quote]

edit: as for your version: Does firefox start with a page saying > Welcome to Ubuntu Linux 5.04: The Hoary Hedgehog Release? If it doesn't you probably have 4.10 (assuming you downloaded an official ISO)

---

### Post by TravisNewman on 2005-04-30
x86 isn't your version, its the architecture that it was built for. All IBM compatibles (computers that can run Windows) are x86. PPC is Apple macintosh, AMD64 is a specialized build for the new 64 bit amd processors, though AMD64 can run the x86 version as well

---

