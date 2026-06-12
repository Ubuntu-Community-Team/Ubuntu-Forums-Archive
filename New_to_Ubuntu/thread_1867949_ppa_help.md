---
title: "ppa help"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-10-23
Hi Everyone,

I've been using Ubuntu since 10.04 and the other day did a clean install of 11.10.

I'm having ppa issues that I never had before.

1. If I go to software sources and add a ppa, for example ppa:weather-indicator-team/ppa, I'm told there is no public key installed.  I don't remember this being an issue in earlier releases, but perhaps my memory is faulty.

2. To avoid the no key notice, I've started adding ppas through the terminal. 
```

sudo add-apt-repository ppa:weather-indicator-team/ppa

```

followed by
```

sudo apt-get update

```

3. When I go to synaptic it is a roll of the dice as to whether the ppa will show up in the left hand column.

[IMG]http://dl.dropbox.com/u/23115609/Origin.png[/IMG]


4. The ppa will show up in the list of repositories however. 

[IMG]http://dl.dropbox.com/u/23115609/sources.png[/IMG]

Is this a bug? Am I doing something wrong?

---

### Post by celticbhoy on 2011-10-23
I guess the first question is are the packages available to install ?

If so, and they are visible in synaptic, I don't think you really have anything to worry about.Regarding the public key, they have been about since I first started adding third party repo's, so nothing new with that.

---

### Post by GrouchyGaijin on 2011-10-23
> **celticbhoy said:**
> I guess the first question is are the packages available to install ?

If so, and they are visible in synaptic, I don't think you really have anything to worry about.Regarding the public key, they have been about since I first started adding third party repo's, so nothing new with that.

Thank you.

I guess I really wasn't clear.
I know that there have been public keys used for a long time.  I guess I just don't remember having to do anything other than add the ppa in the add repository section of synaptic. I don't remember having to do anything to have the public key installed where as now it seems I need to add ppas via the command line in order to have the keys installed as well.

Do you mean that if there is no package to install then the name of the ppa does not appear in the list along the left hand side of synaptic? 

This came about, because I am having trouble with the weather indicator and *think* I read that the version they have in their ppa works better than the version in the Ubuntu repository.

I was hoping to see another version for download after adding the ppa, but the ppa doesn't show up.  The only version I see is the Ubuntu version, in the Ubuntu repository, that was there before I added the ppa.

---

### Post by celticbhoy on 2011-10-23
First the keys again, I cant remember not have to add public keys in software sources.

On the other point, have they updated their PPA to include Oneiric yet? When you run 'sudo apt-get update' do you have any errors ?

---

### Post by beew on 2011-10-23
You will get a gpg error warning everytime you reload synaptic or do "sudo apt-get update", but don't worry about it, your program will install (with a warning that you are going to install unauthenticated software). I have a few GPG errors even from Ubuntu's own repositories, it is easy to fix, just haven't got around to.

[http://ubuntuforums.org/showthread.php?t=1221323](http://ubuntuforums.org/showthread.php?t=1221323)

However if you use the update manager to update your software instead of Synaptic then you should fix the gpg errors otherwise update manager will not work.

---

