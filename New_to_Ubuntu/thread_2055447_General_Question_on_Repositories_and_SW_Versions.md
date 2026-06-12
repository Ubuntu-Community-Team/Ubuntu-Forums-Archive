---
title: "General Question on Repositories and SW Versions"
date: 2012-09-09
forum: New to Ubuntu
---

### Post by Joe Schoen on 2012-09-09
I'm trying to fill some knowledge gaps in what I know about how software makes it into Ubuntu repositories. I'm currently running Precise LTS, which I really like, but I've been most annoyed by seeing new releases announced of software that I use on a regular basis and find that they are not available in the repositories.

I understand that these software packages are developed independent of Ubuntu and that in order for some to make it into the repository, they have to be vetted for compatibility and that can take some time. So although a new release of software might come out, it may take some time for it to be available in the software tool.

Now I've tried ppa's which is how I was able to update from GIMP 2.6 to 2.8 but it doesn't seem to me that those are available for every piece of software out there. More recently, Amarok released its 2.6 version which doesn't seem to be available in the Ubuntu repositories. It does have a (K)ubuntu ppa that I tried but quickly reversed and removed when it didn't work.

I suppose the rambling on is my way of trying to convey the confusion of ideas that would provoke such questions which I guess, would boil down to these: 

Are the software repositories for a certain release (Oneric, Precise) fixed after a certain date or are they still updated with newer versions of the third party software throughout their life? 

If so, is there a priority or criteria for the ones that do get updated? 

In the case of Amarok where it seems only a (K)ubuntu ppa for 2.6 is available, is it ok to add a (K)ubuntu ppa/package to an Ubuntu system?

Is there anything glaringly wrong with my understanding of how the repositories work?

-Joe

---

### Post by yeats on 2012-09-09
Ubuntu's software packages are mostly determined by the versions in the Debian branch with which Ubuntu syncs with when they begin a new release ('sid' for normal releases and 'testing' for LTS).  So much of your question would be best answered by investigating the way Debian selects, tests, and vets package versions.

---

### Post by mcduck on 2012-09-09
The package versions in Ubuntu's official repositories are fixed at the versions that were available during that Ubuntu release's development. After release, packages are generally only updated for security reasons and to fix serious bugs, never juts to provide people with the latest version or new features. This way the package versions available in official repositories can be thoroughly tested to work with each other without causing problems, updating the versions afterwards would make it a lot harder to test everything as well, especially since the developers are already workign on the next Ubuntu release...

So it's a matetr of balancing between stability and reasonably up-to-date software versions. In most cases getting new software versions when upgrading to new Ubuntu version should be enough.

What comes to PPA's being availbale, that's just a question of there being somebody willing to maintain such PPA. Sometimes the softwate's original developers do that, but most of the time it's just some individual from the community who decides to go through the trouble of doing it.

And for the Amarok Kubuntu PPA, all Ubuntu variants are one and the same operating system, there is no difference between them apart from the packages you get by default when you install with a certain disc. So from the OS point of view there is no Kubuntu, it's just Ubuntu with a different desktop environment by default. :) Which of course means that as long as the actual Ubuntu version is correct, it doesn't matter which variant you are running, the packages (and repositories) are all the same.

---

### Post by vasa1 on 2012-09-09
As mcduck said, the only updates to software within a particular OS version, currently 12.04, will be **if** those relate to security. If you want the latest versions and these aren't being provided from the Ubuntu Software Center because they aren't security-related updates, you'll have to get them yourself.
When we move to 12.10 in late October, that version will come with the latest software that could be tested and included by then.
If you stay with 12.04 **LTS**, you'll just get security (and stability?) updates, AFAIK.

---

