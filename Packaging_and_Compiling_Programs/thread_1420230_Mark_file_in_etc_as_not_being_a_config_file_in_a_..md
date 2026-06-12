---
title: "Mark file in /etc as not being a config file in a .deb?"
date: 2010-03-02
forum: Packaging and Compiling Programs
---

### Post by SoftwareExplorer on 2010-03-02
I (somewhat) understand that /debain/conffiles list configuration files, and that files /etc are automatically considered configuration files. However, I need to put a script in /etc/profile.d/ and it needs to be removed when the package is removed the normal way. How can I set the script as not being a config file?

---

### Post by SoftwareExplorer on 2010-03-07
Bump. Should I just use the postrm script to remove the file?

---

### Post by SevenMachines on 2010-03-08
debian conffiles are files that wont be removed or replaced on upgrade by the dpkg system on upgrade and so on. They're specifically used to retain local changes. 
If you've a file that you want to put in etc/ that doesnt fit into this category I think putting it in the .install file is fine, or the rules file, whatever you prefer

---

### Post by SoftwareExplorer on 2010-03-08
> **SevenMachines said:**
> debian conffiles are files that wont be removed or replaced on upgrade by the dpkg system on upgrade and so on. They're specifically used to retain local changes. 

I get that part.
> **SevenMachines said:**
> 
If you've a file that you want to put in etc/ that doesn't fit into this category I think putting it in the .install file is fine, or the rules file, whatever you prefer
Could you elaborate on the .install file? I've never heard of it. Right now I install the file with the 'install' command in the rules, but the problem is that the file is not deleted when the package is removed. However, I want it to be removed when the package is removed. From my understanding, (please correct me if I'm wrong) the rules file has no control over how the package is removed.

---

### Post by SevenMachines on 2010-03-09
the .install file is used by debhelper to install/remove files. it looks like you're not using debhelper though.

files install using 'install' in the rules file should be removed automatically when the package is uninstalled. if its ok to post your packaging and maybe source that would be handy. I can't really guess whats going wrong to be honest. i take it your install line looks something like below or simlar-ish

install -D -m0640 $(CURDIR)/debian/something.conf  $(CURDIR)/debian/tmp/etc/profile.d/something.conf

---

### Post by SoftwareExplorer on 2010-03-09
The package I'm trying to do this with is the gtk2-module-rgba packages at
[[COLOR="DeepSkyBlue"]https://launchpad.net/~erik-b-andersen/+archive/rgba-gtk/+packages[/COLOR]]("https://launchpad.net/~erik-b-andersen/+archive/rgba-gtk/+packages")
Thanks.

---

### Post by SevenMachines on 2010-03-10
sadly the link for the source used fr that ppa package is broken for me so i cant really build it to check, looking at the diff though, nothing leaps out as wrong in the rules file so i can't really see whats going wrong if yours is the same

---

### Post by SoftwareExplorer on 2010-03-10
Ok I attached the orig.tar.gz, the diff.gz and the dsc(with .txt added to the name so it would upload). 
Is the missing orig.tar.gz something I could have done when I uploaded it to launchpad? I had the orig.tar.gz in the folder I was working in.

---

### Post by SevenMachines on 2010-03-11
ah, i see what you mean now /etc/profile.d/gtkrgba.sh isnt removed on -remove but only on --purge. sorry, i dont know if theres a way to make it automatically uninstall on remove (someone else might obviously).
 perhaps theres a better way to set the environmental variables you need, [debian policy on profile ]("http://www.debian.org/doc/debian-policy/ch-opersys.html#s9.9")may or may not help.

---

### Post by SoftwareExplorer on 2010-03-20
I looked at the debian policy and it didn't really help with how I needed to set varibles.
I just made a postrm that deletes the file. I think that will do the trick, but hopefully without any bad effects (what happens if a user purges my package and a file it's supposed to remove isn't there?)

Thanks for the help.

---

