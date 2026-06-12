---
title: "Error: Opening the cache"
date: 2018-08-11
forum: New to Ubuntu
---

### Post by angel-cake on 2018-08-11
Hello, i am new to ubuntu, therefore new to this forum as well (please don't trash me if i'm doing something wrong in this forum, just tell me and i'll fix my mistakes).
I want to install a virtual machine, but this message appears:
E:Malformed entry 1 in list file /etc/apt/sources.list.d/google-chrome.list (component), E:The list of sources could not be read.
As i mention before, i am new to ubuntu so i really don't know what this means and how i can fix it. 
if somebody decides to help me it will be very much appreciated. :KS

---

### Post by &amp;KyT$0P# on 2018-08-11
Please post the output from running this command in Terminal -
```
cat /etc/apt/sources.list.d/google-chrome.list
```

---

### Post by DuckHook on 2018-08-11
Welcome to the forums, arlet2407.

The message is telling you that your configuration file for the Chrome repository has a mistake in it which prevents the installation process (called apt) from scanning through your repositories and running any further. You need to correct the "malformed" entry, which is the first one (entry 1). Sometimes, the error message can be misleading, so don't expect an exact diagnosis of the problem from the contents of the error message.

When asking for help, it us useful to include as much background as you can:

[LIST=1]
[*]What version and flavour are you running?
[*]We can guess that you added the Chrome repo to your system, but what else?
[*]How are you trying to install your VM?
[*]Which VM are you installing?
[*]Did you do the usual:```
sudo apt update && sudo apt full-upgrade
```…prior to trying to install the VM?
[*]Open a terminal a post back to this thread the results of:```
cat /etc/apt/sources.list.d/google-chrome.list
```Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.
[/LIST]

---

### Post by angel-cake on 2018-08-11
hi halogen2, this is what appeared:
deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/stable](http://dl.google.com/linux/chrome/deb/stable) main

what does this mean? Sorry for bothering and thank you for your interest :o)

---

### Post by angel-cake on 2018-08-11
hi, this is what appeared:
```
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/stable main
```

what does this mean? Sorry for bothering and thank you for your interest :eek:)

i have the Xenial version, excuse my ignorance but what do you mean by flavour? and i am trying to download the oracle virtualbox... and no, i didn't do the usual...
Sorry for putting this reply twice, thanks for the advice DuckHook :)

---

### Post by deadflowr on 2018-08-12
The stable needs to be alone like
```
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
```

> what does this mean? 
There are four parts to a source list entry
1)deb is the type of archive; deb means it's the binary archive type, as oppose the deb-src which are the source file archive types.
2) the repository url, this is the link to the archive
2) the distribution; this is release version of the archive. In chrome it can be stable or beta or unstable. In Ubuntu it's the name of the release you use, like xenial or bionic.
4)the component. This is the precise area of the archives the packages would be in; it might main or something like non-free, or as with Ubuntu perhaps universe or restricted.

(The [arch=amd64] is a debian source.list usage to force the entry to only look for the amd64 packages from this particular archives, otherwise The system would look for all arch types that your system has listings for (Typically you have two amd64(these are 64-bit packages) and i386 (these are 32-bit packages)
(Fwiw, Google chrome dropped 32-bit versions some time ago, so it now has to force the arch=amd64 structure as the apt package manager kept failing when they remove the 32-bit packages.)

References here:
[https://wiki.debian.org/SourcesList]("https://wiki.debian.org/SourcesList")
[https://wiki.debian.org/Multiarch/HOWTO#Setting_up_apt_sources]("https://wiki.debian.org/Multiarch/HOWTO#Setting_up_apt_sources")

All that aside, you need to edit the entry.
(This needs to be done as root, unfortunately Ubuntu does not make it easy to do so.)

i think an easy solution is to overwrite the current entry and replace it with a quick one-liner
like so
```
sudo echo "deb[arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" > /etc/apt/sources.list.d/google-chrome.list
sudo apt update
```
and run the apt update to check if it worked.

Hope it helps (or works)

---

### Post by Impavidus on 2018-08-12
> **deadflowr said:**
> 
i think an easy solution is to overwrite the current entry and replace it with a quick one-liner
like so

...


You missed the space between deb and [arch=amd64] and the output redirect isn't going to work, as that makes the shell, not echo, attempt to write to the root-writable file. Better make it```
echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" | sudo tee /etc/apt/sources.list.d/google-chrome.list
sudo apt update
```

And thanks for the links. They help me solve another thread.

---

### Post by angel-cake on 2018-08-12
thank you very much for taking your time and explain :), and thanks for the links, deadflwr!

---

### Post by angel-cake on 2018-08-12
THANKS, IMPAVIDUS, IT IS FIXED!!!!!! thank you for taking your time also for helping me :), now how do i marked this as solved?

---

### Post by Impavidus on 2018-08-12
Click "Thread tools" (near the top of the page), then "Mark as solved".

---

### Post by oldrocker99 on 2018-08-12
Bear in mind that, as long as you search for the same problem, the only stupid question, especially here, the one that doesn't get asked. The Ubuntu community (and, in fact, the whole Linux community) loves to answer n00b questions. We **ALL** were n00bs ourselves at the beginning.

---

### Post by angel-cake on 2018-08-12
Thank you very much.

---

### Post by angel-cake on 2018-08-12
Yeah, i will keep that in mind, thanks :KS

---

### Post by wildmanne39 on 2018-08-12
Hello arlet2407, please do not create duplicate posts, you can include messages to more the one person in a post by typing @ then there username.

Thanks

---

### Post by angel-cake on 2018-08-13
oh, ok, thanks

---

