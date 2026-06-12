---
title: "I forgot to check the block to install 3rd party software"
date: 2021-10-21
forum: New to Ubuntu
---

### Post by Kusho on 2021-10-21
On installing Ubuntu 21.10 I did a clean install but I forgot to check the box to install 3rd party software.  Now my movies won't play.  I found the fix online but it no longer works.

[https://askubuntu.com/questions/290293/how-can-i-install-the-third-party-software-option-after-ive-skipped-it-in-the](https://askubuntu.com/questions/290293/how-can-i-install-the-third-party-software-option-after-ive-skipped-it-in-the)

it says to run 

sudo apt-get install ubuntu-restricted-extras

but when i run that it says

E: Unable to locate package ubuntu-restricted-extras

Please help.

---

### Post by deadflowr on 2021-10-21
In Software and Updates, enable the multiverse repository.
Then run an apt update to reload the sources.

---

### Post by ActionParsnip on 2021-10-21
[https://packages.ubuntu.com/impish/ubuntu-restricted-extras](https://packages.ubuntu.com/impish/ubuntu-restricted-extras)

That website shows the sources of all packages in the official repositories. As Deadflower states, it is in the multiverse repo which will need enabling then your sources rescanning to see the new packages. You can also do the same by editting /etc/apt/sources.list an uncommenting the lines that give you the multiverse repositories.

---

### Post by Kusho on 2021-10-21
Sorry for not trying that before I asked.  Yes simply doing an Software and Updates fixed it.  Ran the command again and downloading the package.
Thanks

---

### Post by ActionParsnip on 2021-10-21
Remember to mark as solved if the issue is sorted

---

### Post by deadflowr on 2021-10-21
> **Kusho said:**
> Sorry for not trying that before I asked.  Yes simply doing an Software and Updates fixed it.  Ran the command again and downloading the package.
Thanks

It's not something most users would even think to do as when you check the box in the installer the repos all get enabled.
But on a clean install without checking the box only the main (Canonical) and restricted (Proprietary) repositories are enabled.
Or at least that's been the historic case as I've seen it.
The universe (Community) repository may or may not be enabled by default. I'm not sure.
I know it is for all the various Desktop flavors such as Kubuntu or Lubuntu, since those have their packages in the universe,
and it would be kind of weird for users of those desktops to not have access to the Software they provide out of the box.
But the main Ubuntu desktop has all it's default packages in main, so it has no real need for universe to be enabled.

That said, if the solution worked, [please mark this thread as solved.]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

