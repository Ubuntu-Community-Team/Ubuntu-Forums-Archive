---
title: "HandBrake in a Repository"
date: 2009-03-03
forum: Repositories &amp; Backports
---

### Post by JDorfler on 2009-03-03
I would like to propose that we put [HandBrake]("http://handbrake.fr/?article=download") into the repositories.  They already have a .deb for Ubuntu called HandBrake-0.9.3-Ubuntu_Gui_amd64.deb.  Is there a way of proposing this officially?

---

### Post by happyisland on 2009-08-13
I second this emotion - handbrake is great!

---

### Post by Beatbreaker on 2009-08-31
check it [https://launchpad.net/~handbrake-ubuntu/+archive/ppa](https://launchpad.net/~handbrake-ubuntu/+archive/ppa)

it would be great if you could use Semantic Package Manager and it was in the main with everything else. Ubuntu tends to drag the chain when getting stuff in there though.

---

### Post by kpkeerthi on 2009-08-31
If you are using PPA, you should be able to install the package using Synaptic (not Semantic :) ) package manager.

---

### Post by mambazo on 2009-12-15
Who is maintaining the PPA. It's fallen behind on releases. It still has 0.9.4 and 0.9.10 is out!

EDIT:
Ok cancel the above. I'm a fool. The website had a deb for ubuntu 9.10, which is of version 0.9.4. I read it all wrong. :-P

---

### Post by HDave on 2010-04-27
I couldn't agree more and have filed a launchpad bug.  Please add your 2 cents there.

[https://bugs.launchpad.net/ubuntu/+bug/571060](https://bugs.launchpad.net/ubuntu/+bug/571060)

---

### Post by JohnAStebbins on 2010-04-28
If you want to live on the bleading edge, there is a PPA for nightly snapshots of svn head.

[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by Woodwa on 2011-01-14
> **JohnAStebbins said:**
> If you want to live on the bleading edge, there is a PPA for nightly snapshots of svn head.

[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

Cheers

---

### Post by oldmankit on 2012-05-18
Is there any good reason why it's not in the repository? 

As the first question asked - how would we officially recommend it goes in?

It's a first-rate piece of software that really does it's job well, and I don't know of anything comparable (though I'll probably be corrected on that).

---

### Post by oldmankit on 2012-05-18
BTW, I found an up-to-date repository here:

[https://launchpad.net/~stebbins/+archive/handbrake-releases](https://launchpad.net/~stebbins/+archive/handbrake-releases)

---

### Post by oldmankit on 2012-05-18
Yet when I update after having added the repository, I get:

```
W: Failed to fetch http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Is this because they haven't yet released a package for Precise Pangolin yet?

---

### Post by TomB19 on 2012-06-03
> **oldmankit said:**
> Yet when I update after having added the repository, I get:

```
W: Failed to fetch http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Is this because they haven't yet released a package for Precise Pangolin yet?

I believe so.

---

### Post by oldmankit on 2012-06-04
> **TomB19 said:**
> I believe so.

Thanks, Tom.  Any ideas how I can get Handbrake working until they get a repository sorted for Precise?  

I explored the handbrake.fr site for a debian download but couldn't find one.  

Update: I followed the link into the launchpad ppa and found a deb from the oneiric page: 

[https://launchpad.net/~stebbins/+archive/handbrake-releases/+build/3246882](https://launchpad.net/~stebbins/+archive/handbrake-releases/+build/3246882)

---

### Post by JohnAStebbins on 2012-06-05
> **oldmankit said:**
> Thanks, Tom.  Any ideas how I can get Handbrake working until they get a repository sorted for Precise?  

I explored the handbrake.fr site for a debian download but couldn't find one.  

Update: I followed the link into the launchpad ppa and found a deb from the oneiric page: 

[https://launchpad.net/~stebbins/+archive/handbrake-releases/+build/3246882](https://launchpad.net/~stebbins/+archive/handbrake-releases/+build/3246882)
There will not be an official release made for 12.04 till the next HandBrake release. Till then, you can use the nightly builds.
[https://launchpad.net/~stebbins/+archive/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by oldmankit on 2012-06-11
> **JohnAStebbins said:**
> There will not be an official release made for 12.04 till the next HandBrake release. Till then, you can use the nightly builds.
[https://launchpad.net/~stebbins/+archive/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/handbrake-snapshots)

Thank you!

---

### Post by shreepads on 2012-08-31
Handbrake Release 0.9.8 for Precise is available in Stebbins' PPA:

[https://launchpad.net/~stebbins/+archive/handbrake-releases?field.series_filter=precise](https://launchpad.net/~stebbins/+archive/handbrake-releases?field.series_filter=precise)

And yes pls sign up on this bug in Launchpad if you want to try and get Handbrake in the official repos..

[https://bugs.launchpad.net/ubuntu/+bug/105458](https://bugs.launchpad.net/ubuntu/+bug/105458)

---

