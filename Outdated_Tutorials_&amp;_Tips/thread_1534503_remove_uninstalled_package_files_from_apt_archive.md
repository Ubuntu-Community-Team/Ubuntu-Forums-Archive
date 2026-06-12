---
title: "remove uninstalled package files from apt archive"
date: 2010-07-19
forum: Outdated Tutorials &amp; Tips
---

### Post by richcocoa on 2010-07-19
Hello...
This is my first forum post, but it is something I found quite useful: saving ***only the installed*** .debs in the apt archive/cache without too much hassle so that you are left with a lean archive, but which houses all your installed software.

**NOTE**: THIS TUTORIAL WILL REMOVE ALL PACKAGE FILES (.DEBS) FROM /var/cache/apt/archives/ WHICH ARE NOT INSTALLED. PROCEED IF YOU ARE SURE THIS IS WHAT YOU WANT. AND IT WORKED PERFECTLY FINE FOR ME WHEN I DID EVERYTHING BELOW, AND IT USUALLY SHOULD WORK FINE FOR YOU TOO IF EVERYTHING IS FOLLOWED PROPERLY. STILL KEEP A BACKUP OF IMPORTANT STUFF. AND IF IT BREAKS SOMETHING, PLEASE DO LEAVE A COMMENT BELOW.

Now the steps:

1.Open Software Sources in **Ubuntu Main Menu**->**System**->**Administration**->**Software Sources**. It will ask you for your password. Key it in.

Then do the following:

On the **Ubuntu Software** tab, deselect everything (but keep in mind which ones were selected, usually everything except Source code. We will later revert it to its earlier state).

Next on the **Other Software** tab, deselect everything (again make a note of everything that was selected. It is needed. Usually everything except **[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) partner (Source Code)** is unchecked).

[IMG]http://lh3.ggpht.com/_LsUlkZ3DmcQ/TESzauiIkXI/AAAAAAAAAEI/qcaNcugA6SY/s800/Screenshot-Ubuntu%20Forums%20-%20Post%20New%20Thread%20-%20Google%20Chrome.png[/IMG][IMG]http://lh6.ggpht.com/_LsUlkZ3DmcQ/TESzadM0LAI/AAAAAAAAAEA/n80GtS1GtEU/s800/Screenshot-Software%20Sources.png[/IMG][IMG]http://lh3.ggpht.com/_LsUlkZ3DmcQ/TESzaTtVh0I/AAAAAAAAAEE/Wb4lZORy7UQ/s800/Screenshot-Software%20Sources-1.png[/IMG]

Now close Software Sources. It will ask to Reload state information. Accept it, and wait for it to finish.

2.We also need to add a single line of code to the file /etc/apt/apt.conf

Ubuntu 10.04 doesn't have the apt.conf file, so we create one and add the code. And if you already have it, I think it should still work. But just in case something goes wrong, keep a backup copy of the original, if yours had one in it already. Then proceed:

First open a terminal, then type:

```
gksu gedit /etc/apt/apt.conf
```

Then type into the gedit window

```
APT::Clean-Installed "off";
```

**NOTE**: When I did the following, I had to restart. It said: 'Unable to get a lock' or something of that sort. A restart should work, if you have hiccups at this stage.

3.Then again in a terminal type 

```
sudo apt-get autoremove
```

It removes all orphaned packages, ie. the packages that don't satisfy dependencies of anything else, and usually it is safe to remove these.

Key in your password, and say yes whenever it prompts you to.

Then again in the terminal type:

```
sudo apt-get autoclean
```

This command removes all those packages from cache that are not downloadable from the internet (that is why we unselected all software sources, so that none could be downloadable:)), but it will keep the installed packages intact in the cache (and this is why we added that line in apt.conf:))

And you are done!!:D
This should remove all those package files in your /var/cache/apt/archives/ which are not installed. So you have a leaner archive but with a backup of all package files that you have currently installed.

Now as a final step, reselect all those things you had unselected in the Software Sources, under the Ubuntu Software, and Other Software tabs in step 1.

Cheers:popcorn:
Do let me know if the Tutorial could be bettered, and your experiences too.

---

