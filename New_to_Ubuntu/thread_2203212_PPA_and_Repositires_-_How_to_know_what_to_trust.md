---
title: "PPA and Repositires - How to know what to trust?"
date: 2014-02-02
forum: New to Ubuntu
---

### Post by fluctuatinganomaly on 2014-02-02
As I've been browsing around the Ubuntu forums and general intetnets, I have seen mentioned PPA's and Repositries. I assume PPA and a Respositiry is the same thing really? but am unsure. Either way, I get how they are used for the apt-get install etc to install packages and apps etc.

What I don't know, is how do you trust them? I don't want to go around adding randomd repositries that may contain malicious codes and the likes, but sometimes its likely that the repositires that I have dont have the apps I'm looking for at the time and stuff. But I don't want to just add some random repositry off the internet.

I'm very particular and rather paranoid when it comes to downloading information from sources I have never used before, seem a little shady, or have VERY little public mention.

~Matt

---

### Post by grahammechanical on 2014-02-02
You are quite right to be paranoid. A PPA is a Personal Package Archive. They are a way for developers to make their software available to Ubuntu users.

> [COLOR=#333333][FONT=Ubuntu]Personal Package Archives (PPA) allow you to upload Ubuntu source packages to be built and published as an apt repository by Launchpad. [/FONT][/COLOR]

[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

Repositories are sources of software that are maintained by the Ubuntu community. They are a means by which we can download applications and get updates and security fixes. Ubuntu has four "official" repositories.

1) Main - Canonical-supported free and open-Source software.
2) Universe - Community-maintained free and open-source software.
3) Restricted - Proprietary drivers for devices.
4) Multiverse - software restricted by copyright or legal issues.

Both apt-get and the Ubuntu Software Centre will access the repositories (computer servers) including any PPA repositories to install software. Applications submitted for inclusion in the Ubuntu Software Centre catalogue are code audited to check if they contain malicious code. I will trust anything that I install through the software centre.

If we download and install software from web sites we increase the likelihood that we will be running malicious code.

Things are done differently with the Ubuntu Mobile platform. Apps are not accepted into the app store unless the developer provides a list (called a manifest) of all the permissions/authorisations that the code will need. If it is safe to run that app then a profile is created and if the app tries to do something that is not in the manifest then it will be prevented for carrying out that action. Furthermore, on Ubuntu phones and tablets applications will run in their own container and will not be allowed access outside of that container. 

All the work being down on the Ubuntu mobile platform will be converged into the Ubuntu Desktop platform over the next 12 - 18 months. So, all of us will benefit from a very secure Ubuntu distribution provided we do not do something stupid such as installing software from sources that cannot be trusted.

Regards.

---

### Post by Dave_L on 2014-02-02
Regarding trusting PPAs:

I think the best approach is to look for recommendations from other people.

It's analogous to when I used to download Window's applications from third-party sites. I gradually accumulated a list of sites that seemed trustworthy based on other people's recommendations.

---

### Post by fluctuatinganomaly on 2014-02-02
Okay, I think I get it. I did happen to stumble onto something after I posted that explained the ppa and repositires and the likes[URL="https://help.ubuntu.com/community/Repositories/Ubuntu"]

Repositires/Ubuntu[/URL]

Felt bad about posting this, but I did search for "PPA" and "repositries" and "repositry" before hand and came up with alot of very vauge and general matches. Things that were above my understanding.

So I get that the main ones for Ubuntu are there, and I allowed the canonical partners as well (Although not the source one) These should be the main ones that provide access to the main apps suppoorted by linux?

How can I find out if an app I'm looking for is located on these repositires? Other than just attempting sudo apt-get install "whatever" as that seems like a fairly reckless method :p 

Is there a way to browse the repositry like a file explorer and look through the files etc to see if the app I'm looking for is in there?

~Matt

---

### Post by oldos2er on 2014-02-02
> **fluctuatinganomaly said:**
>  I did search for "PPA" and "repositries" and "repositry" before hand 
~Matt

It helps if you spell "repositories" and "repository" correctly.  :)

---

### Post by Dave_L on 2014-02-02
> **fluctuatinganomaly said:**
> Is there a way to browse the repositry like a file explorer and look through the files etc to see if the app I'm looking for is in there?

The Ubuntu Software Center lets you browse and search.  So does Synaptic, which I prefer.

This site is also a good reference: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

