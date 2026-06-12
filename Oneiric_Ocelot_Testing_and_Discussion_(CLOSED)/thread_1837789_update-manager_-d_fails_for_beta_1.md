---
title: "update-manager -d fails for beta 1"
date: 2011-09-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by wgarcia on 2011-09-02
I tried to upgrade to 11.10 beta 1 with "update-manager -d" and it fails at the "calculating the changes" step. I filed a bug:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/839417](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/839417)

The message that I got is:


```
An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug using the command 'ubuntu-bug update-manager' in a terminal.
```

---

### Post by ventrical on 2011-09-02
> **wgarcia said:**
> I tried to upgrade to 11.10 beta 1 with "update-manager -d" and it fails at the "calculating the changes" step. I filed a bug:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/839417](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/839417)

The message that I got is:


```
An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug using the command 'ubuntu-bug update-manager' in a terminal.
```


I clicked on the 'Update Manager icon right in Unity and it worked like a charm. That <update> fixes the Ubuntu Software Center bug and you can then download synaptic from the Ubuntu Software Center.

---

### Post by dino99 on 2011-09-02
you got the answer:

This can be caused by:
 * Upgrading to a pre-release version of Ubuntu

dont use that command before final release, simply change sources.list distro (deactivate third party repo like ppa) then update.

---

### Post by wgarcia on 2011-09-02
dino99, is that right? Changing sources.list to maverick (and disabling all third party sources) and then running

sudo apt-get update
sudo apt-get upgrade

will upgrade the system fully from 11.04 to 11.10 Beta 1 (at this stage)? 

It seems that through "update-manger -d" a lot of things are done, like eliminating obsolete packages, downloading and installing the versions corresponding to 11.10 (this part I can see is done by the commands above), cleaning the old packages... Will all this be done with the simple procedure you propose or will I end up with a partially upgraded system?

---

### Post by seeker5528 on 2011-09-02
If you use apt-get or Synaptic, there will be more manual labor for you dealing with obsolete packages and what not.

Using apt-get or Synaptic also means you have more opportunities to allow/disallow different things to be installed or removed or hold off upgrading some group of packages until they are all synced up with compatible versions.

If you do use update manager it's best to try it in the evening when packages are more likely to be in sync.

Which time zone is best to judge when "evening" is a whole other question. :P

The reliability of the mirror you are using is also a factor.

Later, Seeker

---

### Post by wgarcia on 2011-09-05
> **seeker5528 said:**
> If you use apt-get or Synaptic, there will be more manual labor for you dealing with obsolete packages and what not.


Do you have a full list of commands that will complete the upgrade by eliminating obsolete packages and all the other things "update-manager" does?

---

### Post by wgarcia on 2011-09-05
I could finally overcome this error message. The key lies in looking at last lines of the file:

/var/log/dist-upgrade/apt.log

There I could see that the culprit of the unmet dependencies was "gcc-4.4". Uninstalling this package make the error go away. 

As soon as I finish the upgrade I will reinstall it (or reinstall build-essential which installs the last version of gcc).

---

### Post by thijsemans on 2011-09-28
Removal of gcc-4.4 worked for me too.

---

### Post by glenstewart on 2011-10-09
gcc-4.4 isn't the only package causing this problem.  On my system, it was both gcc and nspluginwrapper.

So as above, you can sudo apt-get remove nspluginwrapper
...to solve the problem.

---

