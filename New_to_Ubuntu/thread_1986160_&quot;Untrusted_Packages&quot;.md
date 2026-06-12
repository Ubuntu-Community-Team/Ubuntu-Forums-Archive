---
title: "&quot;Untrusted Packages&quot;"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by lile001 on 2012-05-24
I have installed MEdibuntu stuff, so that I could use the cd and DVD drive properly.  Now when I do an update, I get an error message ```
"Requires installation of untrusted packages: 
The Action would require installation of packages from not authenticated sources  
Details
apport-hooks-medibuntu libavcodec-extra-53 
libavutil-extra-51 mencoder mplayer
```

Which looks like a bunch of medibuntu stuff to me.  What should I do?  Updtate manager GUI will not allow these to be installed, so I have been unchecking them to let the update proceed as a temporary measure, but that obviously isn't the right way to solve this problem.

---

### Post by raja.genupula on 2012-05-24
try to do the same thing with the terminal , then it will ask you as YES/NO . by giving YES/Y you can get them to install on your PC . 
all the best .

give a try with GUI way , make sure that all your universal PPA at software sources are enabled  .

---

### Post by lile001 on 2012-06-01
> **raja.genupula said:**
> try to do the same thing with the terminal , then it will ask you as YES/NO . by giving YES/Y you can get them to install on your PC . 
all the best .

give a try with GUI way , make sure that all your universal PPA at software sources are enabled  .

Thanks!  .... but slow down a little - most of that stuff I don't really know how to do.  How does one update using the terminal?   What is a universal PPA?

---

### Post by gettinoriginal on 2012-06-01
May I suggest you try the below link to make sure you have the applicable repositories installed.  It also has links to using the teriminal.  Using the "Search" bar will also help you learn your way around Ubuntu.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

P.S.  No such thing as a dumb question  :)

---

### Post by lile001 on 2012-06-01
> **gettinoriginal said:**
> 

P.S.  No such thing as a dumb question  :)

If you say that, you must not have looked at many of my posts! :p

Ok, looked into the link you provided, and found the easy way, "Software Sources" under the edit tab of Ubuntu Software Center.  No point in trying the hard way first!  

Under this, I find I have this source chekced: 

Medibuntu - Ubuntu 12.04 "Precise pangolin" ([http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free)

So it looks like Medibuntu is allowed as a software source.  Why am I getting the error message that Medibuntu is untrusted?  

Meanwhile, the hard way, looking at /etc/apt/sources.list, I cannot find any mention of medibuntu in this file.  

Following the plot [here]("https://help.ubuntu.com/community/Repositories/Ubuntu") ,  They actually post a link in an example for the medibuntu repository, but it is cut off so I can't see the last piece of it. 

Looking into a page for the medibuntu repository [here]("http://packages.medibuntu.org/"), I can't make enough sense of it to know what to put in.  It looks like it starts with:  deb [http://packages.medibuntu.org/ubun](http://packages.medibuntu.org/ubun)......  

I am probably staring right at the answer the this question on the pages linked above, but don't understand enough of this stuff to recognize it ...

In the Software Sources dialog, I am at a screen that says "```
Enter the complete APT line of the repository that you want to add as 
source The APT line includes the type, location and components of a repository, 
for example  'deb http://archive.ubuntu.com/ubuntu precise main'.
```, which would also I suppose be what I would need to put in at a command line, however I don't know exactly what to put in there, since I don't really know what the hell I am doing anyway.  I've been able to find some hints, but not the real answer.  

So, anyone care to help me figure out what that APT line should be to allow the Medibuntu repository to be a trusted source under ubuntu 12.04?  How would I find this info?

---

### Post by oldos2er on 2012-06-01
"Untrusted" means the gpg key for a given repository is not installed. See the first command here: [http://medibuntu.org/repository.php](http://medibuntu.org/repository.php) to install it.

---

### Post by lile001 on 2012-06-04
> **oldos2er said:**
> "Untrusted" means the gpg key for a given repository is not installed. See the first command here: [http://medibuntu.org/repository.php](http://medibuntu.org/repository.php) to install it.

AHA!  That's what I was looking for.  In case someone else stumbles across this thread looking for hte same thing:

```
Adding the repository
The following bash command adds Medibuntu's repository to Ubuntu. It also adds Medibuntu's GPG key to your keyring, which is needed to authenticate the Medibuntu packages.

This command should be run in the Terminal (Applications &#8594; Accessories &#8594; Terminal):

sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
Medibuntu's repository is deactivated by upgrading to a newer Ubuntu release, so you should run this command again after the release upgrade.

You may also wish to add the following packages. The first will cause many apps from the Medibuntu repository to appear in Ubuntu Software Center (Ubuntu 9.10+) or Add/Remove Applications (versions prior to 9.10). The second will allow users to generate crash reports against Medibuntu packages and submit them to the Medibuntu bugtracker.

sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu

```

The key point is, adding Medibuntu as a repository is a separate step from installing it.  That's the part I didn't understand.  Even if it was added, if one upgrades to a new version of Ubuntu, these repository additions disappear.  This repository stuff is all new to me and I'm just getting used to it. 

One can find this sort of stuff in help files or by googling only if one knows the right question to ask, which is why I could not find it.  It takes a human being (thanks!) to figure out what the right question is!

---

### Post by oldos2er on 2012-06-04
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

---

### Post by lile001 on 2012-06-14
Well, the problem is still there after doing all the stuff recommended above.  

Here are two issues: 

At the end of that command line stuff that is supposed to add Medibuntu to repositories, I see this gibberish, which I do not understand but doesn't look good:

```
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Authentication warning overridden.
Err http://packages.medibuntu.org/ precise/free medibuntu-keyring all 2008.04.20
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Failed to fetch http://packages.medibuntu.org/pool/free/m/medibuntu-keyring/medibuntu-keyring_2008.04.20_all.deb  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


```

I have done the recommended thing in the last line, which doesn't seem to change the outcome.  Rebooted a couple of times, but Update Manager still claims:

```


Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.

Details:  libavcodec-extra-53 libavutil-extra-51 mencoder mplayer
```

What would you suggest i try now?

---

### Post by oldos2er on 2012-06-15
See post #18 here: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886)

---

