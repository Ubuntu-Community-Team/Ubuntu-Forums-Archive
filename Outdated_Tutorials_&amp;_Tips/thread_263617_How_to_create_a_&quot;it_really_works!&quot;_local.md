---
title: "How to create a &quot;it really works!&quot; local repository of packages"
date: 2006-09-23
forum: Outdated Tutorials &amp; Tips
---

### Post by jamadagni on 2006-09-23
You have a collection of deb packages that you trust, archived into a directory (preferably somewhere under your home directory). You would like to create a local repository from these packages (where they are situated).

Here are the steps to follow:

[list=1]
[*]Download the attached script. Preferably remove the txt extension (which I appended only for UbuntuForums to accept the file as an attachment).

[*]Add the executable attribute to the file. You can do this by chmod +x <filename> on the command line or using your favourite file manager.

[*]Put this script in the directory which contains your archived deb packages.

[*]Edit the script using your favourite text editor to change the text "My local Ubuntu Dapper repository" to what you desire **but do not change anything else!**

[*]Now run this script from the terminal at its directory.

[*]If you see any warning messages about packages being repeated, you may want to delete the superfluous packages.

[*]You will most probably see a warning about packages missing from an "override file" followed by a list of packages. You may safely ignore this.

[*]If you get an error message about a failed signing because no secret key was available, use gpg --gen-key or KGpg Ctrl+N to create a new key pair and then execute the command: ```
gpg -bao Release.gpg Release
```

[*]Now export the public key corresponding to the private key used to sign the repo: ```
gpg --export -a "*Your Name*" > public.key
``` replacing Your Name (the quotes should remain) by the name you used to create the key.

[*]Import this public key to apt's list of trusted signatures by: ```
apt-key add public.key
```

[*]Follow the instructions given by the script regarding the /etc/apt/sources.list file. You will need administrator privileges to edit the apt sources.list file.

[*]Run sudo apt-get update or do the equivalent from Synaptic or Adept.

[*]If you do not get any error messages, then your repository should be attached and available!
[/list]

If you have any suggestions for improvement of this script, please post them here. Of course, bug reports are welcome too!

Finally, I should add a few words about:

**Unsigned repositories:** 

While executing the script, you may ignore the error message about the failed signing and skip the gpg -bao command, but your repository will be an unsigned one, and hence be untrusted by apt. This means that if the same package lies on an unsigned repository and a signed one, apt will prefer retrieving the package from the signed repository. This further means that apt may download many megabytes of packages from a remote (on the internet) repository though the same package is available in your local (on your computer) repository.

Of course, even if a repository is signed, if the key has not been imported to apt's trusted keys list using apt-key add, then it is as bad as unsigned. Hence it is important to sign the Release file using a gpg key, and also to import it to apt's trusted keys list.

**Credits:** I have learnt this procedure from many sources. I thank them all.

---

### Post by blueprats on 2010-05-14
Hey,
Thanks for the above information, it is really a good guide to set local repository. Also the script is awesome I liked it. I followed the complete procedure, but unfortunately I am still getting the unmet dependency error while installing any package. By the way thanks for your work.

---

### Post by jamadagni on 2010-05-17
Hello there! I'm glad my howto was of help. I have updated the scripts quite a lot since I wrote this howto almost four years ago and I will see when I can upload them (I'm browsing away from home) -- in the meanwhile it would help if you could outline the exact steps you followed by which you got the error.

---

