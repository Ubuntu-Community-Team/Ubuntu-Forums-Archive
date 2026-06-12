---
title: "Are &quot;recommended&quot; packages recommended?"
date: 2015-02-19
forum: New to Ubuntu
---

### Post by garycheng12 on 2015-02-19
I found it strange that sudo apt-get install <package-name>automatically installs not only dependencies (which obviously make sense), but recommended packages as well. You must specify that recommended packages are not to be installed with --no-install-recommends. 

Why isn't it the other way around, where apt-get install installs only the dependencies and you have to specify that you want recommended packages? Is it really the case that the majority of the people will actually need most of the recommended packages alongside the package they installed? 

Would the average user encounter any problems if --no-install-recommends added every time they did a apt-get install <package-name>? For example, if a user added a --no-install-recommends but found that he actually needed the recommended package, would he know that he is missing a recommended package (he could be just thinking that the package he installed is limited in tools rather than knowing a recommended package extends the functionality of the installed package that is not installed) and what the recommended package that is missing is so that he can install it?

---

### Post by grahammechanical on 2015-02-19
What you suggest would add complexity for the user, new or not, who justs wants to update the OS and install or remove applications in a simple way without needing to understand the relationships between different libraries. We want things to work and we want to be able to do that easily and simply. This is an underlying founding principle of Ubuntu.

> Depends
This declares an absolute dependency. A package will not be configured unless all of the packages listed in its Depends field have been correctly configured (unless there is a circular dependency as described above).
The Depends field should be used if the depended-on package is required for the depending package to provide a significant amount of functionality.
The Depends field should also be used if the postinst or prerm scripts require the depended-on package to be unpacked or configured in order to run. In the case of postinst configure, the depended-on packages will be unpacked and configured first. (If both packages are involved in a dependency loop, this might not work as expected; see the explanation a few paragraphs back.) In the case of prerm or other postinst actions, the package dependencies will normally be at least unpacked, but they may be only "Half-Installed" if a previous upgrade of the dependency failed.
Finally, the Depends field should be used if the depended-on package is needed by the postrm script to fully clean up after the package removal. There is no guarantee that package dependencies will be available when postrm is run, but the depended-on package is more likely to be available if the package declares a dependency (particularly in the case of postrm remove). The postrm script must gracefully skip actions that require a dependency if that dependency isn't available. 


>  [COLOR=#000000][FONT=Times New Roman]Recommends
[/FONT][/COLOR]
This declares a strong, but not absolute, dependency.
The Recommends field should list packages that would be found together with this one in all but unusual installations.[COLOR=#222222][FONT=Verdana]

[/FONT][/COLOR]
> Suggests
This is used to declare that one package may be more useful with one or more others. Using this field tells the packaging system and the user that the listed packages are related to this one and can perhaps enhance its usefulness, but that installing this one without them is perfectly reasonable.

Enhances
This field is similar to Suggests but works in the opposite direction. It is used to declare that a package can enhance the functionality of another package.

Pre-Depends
This field is like Depends, except that it also forces dpkg to complete installation of the packages named before even starting the installation of the package which declares the pre-dependency, as follows:
When a package declaring a pre-dependency is about to be *unpacked* the pre-dependency can be satisfied if the depended-on package is either fully configured, *or even if* the depended-on package(s) are only in the "Unpacked" or the "Half-Configured" state, provided that they have been configured correctly at some point in the past (and not removed or partially removed since). In this case, both the previously-configured and currently "Unpacked" or "Half-Configured" versions must satisfy any version clause in the Pre-Depends field.
When the package declaring a pre-dependency is about to be *configured*, the pre-dependency will be treated as a normal Depends. It will be considered satisfied only if the depended-on package has been correctly configured. However, unlike with Depends, Pre-Depends does not permit circular dependencies to be broken. If a circular dependency is encountered while attempting to honor Pre-Depends, the installation will be aborted.

Pre-Depends are also required if the preinst script depends on the named package. It is best to avoid this situation if possible.

Pre-Depends should be used sparingly, preferably only by packages whose premature upgrade or installation would hamper the ability of the system to continue with any upgrade that might be in progress.
You should not specify a Pre-Depends entry for a package before this has been discussed on the debian-devel mailing list and a consensus about doing that has been reached. See [Dependencies, Section 3.5]("https://www.debian.org/doc/debian-policy/ch-binary.html#s-dependencies").
[COLOR=#222222][FONT=Verdana]
Actually Ubuntu uses the Debian package management system. And it is up to the author of the software to comply with the Debian method. If installation and configuration of some piece of software fails it could be that the author has failed in packaging his software in some way. It should not be left to the user to fix things.
[/FONT][/COLOR][URL="https://www.debian.org/doc/debian-policy/ch-relationships.html"]
https://www.debian.org/doc/debian-policy/ch-relationships.html[/URL]

Regards

---

### Post by vasa1 on 2015-02-19
I like```
sudo apt-get install --no-install-recommends package_name
```I think SPM can be configured that way too.

---

### Post by ajgreeny on 2015-02-22
I personally almost always use the default of synaptic, which is to include recommended packages with the installation of anything; the only time I might not do so is when I am adding some package for a specific action which I know does not need all the recommends.

---

### Post by jacobpratt909 on 2015-02-22
Shouldn't you be able to "opt-out" of this in settings? As the original forum poster said "Why isn't it the other way around, where apt-get install installs only  the dependencies and you have to specify that you want recommended  packages?" you would be able to just press a checkbox to opt out of recommended packages, making it easier for new users to get the packages, and experienced users to opt out of it altogether and not have to insert "--no-install-recommends" every time?

-Wyz

---

### Post by v3.xx on 2015-02-22
> Shouldn't you be able to "opt-out" of this in settings?

There is one way.

[ATTACH=CONFIG]260165[/ATTACH]

---

### Post by jacobpratt909 on 2015-02-22
> **v3.xx said:**
> There is one way.

[ATTACH=CONFIG]260165[/ATTACH]

There we go :D

---

### Post by mc4man on 2015-02-22
I just leave as is, as noted one can add the option on cli,  thru synaptic or probably an alias

If you really wanted to turn off by default then this would likely suffice
```
sudo touch /etc/apt/apt.conf.d/apt.conf
```
```
sudo nano  /etc/apt/apt.conf.d/apt.conf
```
insert this line, save file
```

APT::Install-Recommends "false";
```

---

