---
title: "Debian packages"
date: 2011-04-07
forum: Packaging and Compiling Programs
---

### Post by nkae100 on 2011-04-07
Developers need to stop making Debian packages with dependencies.

There is nothing more infuriating than trying to install something from a Debian package on a computer that does not have internet access, only to find that it needs to download dependency packages for the install to work.

Windows developers MSI packages don't have this problem!

Windows developers own Debian Linux developers in this instance.

---

### Post by Cheesehead on 2011-04-07
Several tools already exist to ensure you have all the dependencies you need.
Try one. It will make your life much less frustrating.

Synaptic has this, and will even print it for you as part of it's 'create download script' feature.
The apt-zip and apt-on-cd packages were made for precisely this situation.
The kerryx website (and others) will also check dependencies for you.

(Long ago, i did a dist-upgrade of from 6.06 to 6.10 to an offline system manually without any of these tools. It took twelve boring hours. These tools make it very easy and fast)

---

### Post by MadCow108 on 2011-04-07
> **nkae100 said:**
> Windows developers own Debian Linux developers in this instance.

because they place every decency into one large file resulting in dozens of duplicated libraries of varying versions. This is a security nightmare ...
sometimes they just link everything in statically creating a humongous executable... (example would be the skype package for linux clearly created by windows developers! its 32 mb large, I do   not even want to know how much outdated stuff is packed into it ...)
To me this is the opposite of "owning"

as mentioned there are many tools to solve this offline problem
another possibility is apt-offline

---

### Post by JupiterV2 on 2011-04-08
> **nkae100 said:**
> ...

Windows developers MSI packages don't have this problem!

Windows developers own Debian Linux developers in this instance.

That's also because Windows installers are 2 or 3 or 10 times larger than a Debian package because they have to include non-WinAPI libraries in their installers. Debian packages simply contain the files necessary for the package and tell the packaging system what libraries it depends on. This allows, as others have stated, the user to have the most up-to-date, bug free, versions of a library installed without breaking the package. 

In Windows, each package has to maintain its own dependencies. Buggy, out of date, libraries are often shipped with installers which are in desperate need of an update but no update ever comes. Or, multiple versions of the same library exist on the same system, something which isn't, usually, necessary on a Debian based system.

Maybe you should consider that just because it's not what you're used to, doesn't mean its wrong. Maybe you should consider that perhaps Debian does dependency handling this way in order to preserve the health and security of your system, at the cost of requiring a connection to the internet at the time of installation.

---

