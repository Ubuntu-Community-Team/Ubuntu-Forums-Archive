---
title: "Eclipse SDK 3.2 from repository missing feature"
date: 2008-12-01
forum: Programming Talk
---

### Post by hardmath on 2008-12-01
I'm aware that the repository versions of Eclipse are not the latest and greatest, but this seems to me an actual bug.  Before posting to Launchpad I wanted some feedback...

Installing package eclipse from the repository rolls up packages:

eclipse-jdt
eclipse-pde
eclipse-platform
eclipse-rcp

For the sake of completeness, even though the description says "dummy package for transition to eclipse," I installed package eclipse-sdk from the repository as well.

The IDE comes up, but I'm concerned by what I see when I drill down into Help > Software Updates > Manage Configuration, in the nested features view I see a red blemish on Eclipse Project SDK 3.2.2... under Eclipse, and a red blemish nested under that on Eclipse Java Development Tools 3.2.2....

Pulling up the Show Properties dialog for that item, it tells me:

```
Status

The feature is not configured properly.

Reason:


Plug-in "org.eclipse.jdt.junit4.runtime" version "0.0.0" referenced by this feature is missing.

```

My impression is that packages junit and junit4 are installed with eclipse-jdt.  In any case the Synaptics Package Manager says they are installed.

So my hypothesis is that the library containing the required plug-in is probably on my machine (Hardy Heron), but is not being found because either my LIB or CLASSPATH environment variables are not correctly set.


TIA, hardmath

---

### Post by SeanHodges on 2008-12-02
I believe this will change as the new Java stack in Debian/Ubuntu is rolled out and Eclipse is upgraded. JUnit does not work with GCJ, which is the default version of Java on Ubuntu as of 8.10. 

This is an existing bug on the topic: [https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/67862](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/67862)

And here is a hacked version from another user, I can't recommend this because I haven't used it: [http://ubuntuforums.org/showthread.php?t=465242](http://ubuntuforums.org/showthread.php?t=465242)

I would recommend you subscribe to the bug above, and download the latest copy of Eclipse from the official website until the repository version is brought up-to-speed.

Also, if you haven't already, subscribe to this bug: [https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/123064](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/123064) to increase it's visibility and get any news on progress.

---

### Post by hardmath on 2008-12-02
Thanks, Sean.  I'm now subscribed to that bug.

However "Launchpad janitor" writes near the current end of that thread:

> This bug was fixed in the package eclipse - 3.2.2-5ubuntu1


Synaptics Package Manager tells me that the version I have installed from the repository is eclipse 3.2.2-5ubuntu2.

Moreover the forum thread here:

[_[Unable to get jUnit 4 to work in eclipse]_]("http://ubuntuforums.org/showthread.php?t=343029")

seems to point to copying missing jUnit4 files into the /usr/lib/eclipse/plugins directory.  I verified that those files are already present from my install.

So, taking a look at the "hack" that you couldn't personally recommend, comments there suggest a permissions problem with the jUnit4 files.  I'm going to look into that...

regards, hardmath

---

