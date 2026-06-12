---
title: "update problem"
date: 2011-12-25
forum: New to Ubuntu
---

### Post by waleed.mohammed on 2011-12-25
when i update my ubuntu this message show up "Failed to download repository information"

when i press details i found:
W:GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease: File /var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_oneiric_InRelease doesn't start with a clearsigned message, W:GPG error: [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease: File /var/lib/apt/lists/partial/archive.canonical.com_ubuntu_dists_oneiric_InRelease doesn't start with a clearsigned message, W:GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease: File /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric_InRelease doesn't start with a clearsigned message, W:GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease: File /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-updates_InRelease doesn't start with a clearsigned message, W:GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports InRelease: File /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_InRelease doesn't start with a clearsigned message, W:GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease: File /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_InRelease doesn't start with a clearsigned message, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Index](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_oneiric_main_i18n_Index
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/partner/i18n/Index](http://archive.canonical.com/ubuntu/dists/oneiric/partner/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/archive.canonical.com_ubuntu_dists_oneiric_partner_i18n_Index
, E:Some index files failed to download. They have been ignored, or old ones used instead.



i am using ubuntu 11.10
please help me

---

### Post by Bucky Ball on 2011-12-25
Have you got more than two packages managers open at the same time? For instance, have you got Synaptic Package Manager open and you are attempting to update via the terminal?

Is this a fresh install and this is your first update or has this just 'popped up'? What machine?

Note: 11.10 can be problematic on some machines. If you were fine with 11.04 I would stick to that and the principal of 'if it ain't broke, don't fix it.' Unless you have a good reason to upgrade and break your system ... I don't. I generally work with the LTS releases as I need my machines to be up and solid/stable. ;)

---

### Post by waleed.mohammed on 2011-12-25
no i updated it before and the update was done without any problem. I don't have Synaptic installed, and there is no any other package manager working

---

### Post by Bucky Ball on 2011-12-25
I have edited my previous post. Please re-read. ;) And yea, no Synaptic in 11.10. Software Centre is it, that is the package manager ... boring! Xubuntu fan meself ...

Don't know a lot about 11.10 cos haven't used it yet but aware many people have had problems.

---

### Post by waleed.mohammed on 2011-12-25
> **Bucky Ball said:**
> Have you got more than two packages managers open at the same time? For instance, have you got Synaptic Package Manager open and you are attempting to update via the terminal?

Is this a fresh install and this is your first update or has this just 'popped up'? What machine?

Note: 11.10 can be problematic on some machines. If you were fine with 11.04 I would stick to that and the principal of 'if it ain't broke, don't fix it.' Unless you have a good reason to upgrade and break your system ... I don't. I generally work with the LTS releases as I need my machines to be up and solid/stable. ;)

i agree with you 100% ver 11.4 was work perfect in my laptop 
thank you my friend

---

### Post by Bucky Ball on 2011-12-25
Pleasure. You could always have 11.04 stable on one partition and whatever unstable version you want on another partition to learn, tweak, and play with.

---

### Post by QIII on 2011-12-25
If I may intrude...

I don't think it is a "stability" problem at all.  I think it is a mundane GPG key error.

For a similar discussion (but with Maverick), see here.

[http://ubuntuforums.org/showthread.php?p=10961816](http://ubuntuforums.org/showthread.php?p=10961816)

As far as "a lot of people are having problems with it", be careful.

You have what is known as a "referral bias" if you come to a help forum.  By definition, what you see are the people who are having problems.  What fraction of all users does that represent?

You don't know.  Neither do I.  That is because we have visibility only of the segment of the population that is having problems.  That may be "a lot" from that perspective.

But if 300 people come here with problems and 1,500,000 upgraded without issue, the story changes.

I am an Applied Mathematician and a Computer Scientist who develops software that models population phenomena.  Your perception may seem valid from your point of view but is not, in fact, because it is incomplete.  Your sample size is small, anecdotal and contains referral bias.

---

### Post by waleed.mohammed on 2011-12-25
> **QIII said:**
> If I may intrude...

I don't think it is a "stability" problem at all.  I think it is a mundane GPG key error.

For a similar discussion (but with Maverick), see here.

[http://ubuntuforums.org/showthread.php?p=10961816](http://ubuntuforums.org/showthread.php?p=10961816)

As far as "a lot of people are having problems with it", be careful.

You have what is known as a "referral bias" if you come to a help forum.  By definition, what you see are the people who are having problems.  What fraction of all users does that represent?

You don't know.  Neither do I.  That is because we have visibility only of the segment of the population that is having problems.  That may be "a lot" from that perspective.

But if 300 people come here with problems and 1,500,000 upgraded without issue, the story changes.

I am an Applied Mathematician and a Computer Scientist who develops software that models population phenomena.  Your perception may seem valid from your point of view but is not, in fact, because it is incomplete.  Your sample size is small, anecdotal and contains referral bias.

sadly i returned back to fedora actually i didn't like it and thir huge amount of update and odd system if you sure about this commands:
sudo bash
 apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update

going to solve my problem i will install immediately ubuntu again because i like it i am waiting for your reply

---

