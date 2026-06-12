---
title: "Commands to optimize the system and ideal method to uninstall an application?"
date: 2015-01-29
forum: New to Ubuntu
---

### Post by garycheng12 on 2015-01-29
I am looking for commands that optimize the system safely but effectively. I did some googling and found some commands, but it seems that although everyone can agree on roughly what a certain command does (it does an expected action 99% of the cases), even experienced linux users misinterpret/disagree on the intricacies of the 1% of the cases whre the action does what is not so obvious/expected.

To uninstall a package cleanly, I would follow this process and train of thought:

-** sudo apt-get purge PackageA**                             //removes PackageA and config files that are not in Home, does not remove dependencies
- **sudo apt-get autoremove**                                           //removes all unused dependencies. By definition, isn't this 100% safe to run any time? Why would anyone want to keep redundant dependencies?
- manually track down any remaining relevant package files, which are only config files that are in Home (not deleted by purge)
- **sudo apt-get clean**                               //what does apt-get clean and apt-get autoclean do? I read the manual but it is different from what I've been told--I thought it clean removes all                  downloaded packages that were downloaded for installation and autoclean does the same thing except it doesn't delete the latest package downloaded. Why would any user would want to keep these downloaded packages after they installed them on their system unless they are tight on bandwidth/have no access to the internet.

What does this command do?

**dpkg -l | grep '^rc' | awk '{print $2}' | xargs dpkg --purge**

In the end, the system should be the same size down to the byte from before installation of PackageA to after uninstallation of PackageA (this is most likely not possible/practical, but just out of curiosity I want to know why it can't be done). 

Also, I would like to know more commands regarding optimization in the form of performance, storage, tideness, etc.

Thanks

---

### Post by kerry_s on 2015-01-29
i use a ~/.bash_aliases list.
my list:

# custom alias's
alias update='sudo apt-get update'
alias upgrade='sudo apt-get upgrade'
alias search='apt-cache search'
alias show='apt-cache show'
alias install='sudo apt-get install'
alias reinstall='sudo apt-get reinstall'
alias remove='sudo apt-get purge'
alias add='sudo dpkg -i'
alias clean='sudo apt-get autoremove'
alias fix='sudo apt-get -f install'

you can also use aptitude, i find it slower, but it has it's uses. you should at least know how to use it.

---

### Post by deadflowr on 2015-01-29
> What does this command do?


dpkg -l | grep '^rc' | awk '{print $2}' | xargs dpkg --purge



It'll spout out something about you don't have permission to run it.

That said to break it down the first part dpkg -l reads the list of installed packages, as read from the status file in /var/lib/dpkg

The second shows you all those package in rc status ( it means remove, and config-files, so remove config-files; you may probably be able to also call it residual config-files, since that is what they typically are), which you may have left over.(From the status file it'll read as deinstall ok config-files.

The third entry* awk '{print $2}'* tells the system to only print out the second field in which ever lines the other entries/commands have produced. In this case it outputs the package name since the dpkg -l command outputs the status first, then the package name second (rc is in the first field, and the package-name is in the second)

lastly, the  xargs tells to take the info from the output the previous command produced and to uses it with the next command: dpkg --purge.
if that makes any sense.
I'm sure I'm not explaining it well at all.

Of course, if using Ubuntu, it won't do anything since you'd need to be root or sudo.
If you wanted to run it, then add sudo before the last command " xargs sudo dpkg --purge"

---

### Post by Holger_Gehrke on 2015-01-29
> **garycheng12 said:**
> 

- **sudo apt-get autoremove**                                           //removes all unused dependencies. By definition, isn't this 100% safe to run any time? Why would anyone want to keep redundant dependencies?
]
Not redundant, but unused **as far as apt knows**. As someone who has on occasion compiled stuff from source, I can give you an example:
Run 'configure', find out I'm missing lib-xyz, install lib-xyz-dev (which gets me both the library as a dependency and the headers, which are what the compiler needs), compile, remove lib-xyz-dev which removes the headers but leaves the library alone. Now my compiled program runs, but apt doesn't know about it and think lib-xyz is an unused dependency. The solution to this is simple: either run 'aptitude unmarkauto lib-xyz' or mark it as manually installed in synaptic.

> **garycheng12 said:**
> 
- **sudo apt-get clean**                               //what does apt-get clean and apt-get autoclean do? I read the manual but it is different from what I've been told--I thought it clean removes all                  downloaded packages that were downloaded for installation and autoclean does the same thing except it doesn't delete the latest package downloaded. Why would any user would want to keep these downloaded packages after they installed them on their system unless they are tight on bandwidth/have no access to the internet.


The fact that these packages are in '/var/**cache**/apt/packages/' makes it kind of obvious: if you deinstall and reinstall something it doesn't need to get downloaded again.

Another reason to keep packages in cache: You are tight on HD-space **and** often don't have an internet connection. Keeping a big package in cache but uninstalled makes it possible to install the program when needed and remove it when not, all without connecting to the net.

---

### Post by garycheng12 on 2015-01-29
> **Holger_Gehrke said:**
> ]
Not redundant, but unused **as far as apt knows**. As someone who has on occasion compiled stuff from source, I can give you an example:
Run 'configure', find out I'm missing lib-xyz, install lib-xyz-dev (which gets me both the library as a dependency and the headers, which are what the compiler needs), compile, remove lib-xyz-dev which removes the headers but leaves the library alone. Now my compiled program runs, but apt doesn't know about it and think lib-xyz is an unused dependency. The solution to this is simple: either run 'aptitude unmarkauto lib-xyz' or mark it as manually installed in synaptic.



The fact that these packages are in '/var/**cache**/apt/packages/' makes it kind of obvious: if you deinstall and reinstall something it doesn't need to get downloaded again.

Another reason to keep packages in cache: You are tight on HD-space **and** often don't have an internet connection. Keeping a big package in cache but uninstalled makes it possible to install the program when needed and remove it when not, all without connecting to the net.

Nice, I like these answers.

---

