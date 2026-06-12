---
title: "How to upgrade software in Ubuntu?"
date: 2014-04-15
forum: New to Ubuntu
---

### Post by sanssadness on 2014-04-15
Hi everyone, I am new to Ubuntu, so I hope you bear with my newbie questions. I am using version 12.04 LTS of Ubuntu. How does one go about upgrading software in Ubuntu? I used the "Update Manager", thinking it would do the trick, but it only updated some software and not others.

For example, after letting Update Manager download whatever updates were available, I checked my version of Firefox and found that it was 28.0 (because the Firefox version in the "Try Ubuntu" feature of the CD is only 26.0, I assumed Update Manager updated it). However, when I check my version of LibreOffice Writer, it shows that I have LibreOffice 3.5.7.2. According to Wikipedia, version 4.0 was released 7 February 2013, so why doesn't Update Manager update my version of LibreOffice to the latest version?

In general, how do you update software on Ubuntu? When is using the Update Manager sufficient, and when do you have to do it yourself?

---

### Post by pfeiffep on 2014-04-15
This might [help]("https://wiki.ubuntu.com/SoftwareUpdates#Update_settings")

---

### Post by evan8 on 2014-04-15
Check out PPA's. Mainly keep you updated the most. Just watch out and add the official ones. You know never know what could happen. Never had a problem on my side though.Try out synaptic package manager if you haven't.

---

### Post by papibe on 2014-04-15
Hi sanssadness. Welcome to the forum ):P

> **sanssadness said:**
> why doesn't Update Manager update my version of LibreOffice to the latest version?
Short answer: Linux updates are different than Windows, and Mac OS. There are several pros of the 'Linux way', and a few cons like the one you are experiencing.

Long answer: ...mmh.. read this: [How software installation package managers work on Linux]("http://www.howtogeek.com/117579/htg-explains-how-software-installation-package-managers-work-on-linux/").

If your concern is just LibreOffice, I'd recommend installing the version 4+ from this ppa: ppa:libreoffice/ppa . Usually you add a 'few' ppa's to your system to get the most recent versions. However, adding to much of them produces library conflicts with other softwares and even instability.

In a few days, the new Ubuntu version will come out, 14.04. If you are concern about recent versions, I'd recommend upgrading to it as soon as possible.

In case you want to mostly 'newer' versions, I'd recommend another upstream distribution, like 'Debian-testing'.

In case you want 'ALL' your applications to be the most recent available, take a look at a distribution called Arch.

Hope it helps. Let us know if that helped, and if you have more questions.
Regards.

---

### Post by sanssadness on 2014-04-15
I have this program called Ubuntu Software Center. Is this the same as Synaptic Package Manger? If not, what does Synaptic Package Manager offer that Ubuntu Software Center doesn't?

I am reading about PPAs this moment. Are you trying to say that unless I upgrade my version of Ubuntu (which I don't want to do right now, because 12.04 is a LTS version), the only way I can updates for LibreOffice is through a PPA? If so, I won't mind adding them. I'm pretty sure LibreOffice is safe to install.

 By the way, how can you tell if a program needs to be in a PPA to be updated? I already have updates from precise-security, precise-updates, and precise-backports. These were checked by default with the Ubuntu installation. According to what I'm reading, PPAs only contain softwaer that didn't come with Ubuntu by default. But LibreOffice did come installed with Ubuntu 12.04, so why aren't these 3 update sources enough?

---

### Post by QIII on 2014-04-15
I would recommend using PPAs very sparingly, if at all.  LibreOffice is definitely trustworthy, so that one is probably OK.

In answer to your question:

The repos for any given release are generally frozen at release time.  It is rare for new versions of most software to be put into the repos for a previously released version.  There would have to be some very compelling reason to put a new version there.

Security updates are one of the reasons new versions do appear in the repos.  Canonical will make sure that security updates to software in the repos is made available as quickly as possible -- for supported releases of Ubuntu.  Since the Firefox releases generally contain security updates, new Firefox versions are updated in the repositories for supported versions.

So, you see a recent update of Firefox for security reasons, but if the version update for LibreOffice does not contain a security update it will not likely be updated in the repo.

Cheers!

---

### Post by papibe on 2014-04-16
> **sanssadness said:**
> I have this program called Ubuntu Software Center. Is this the same as Synaptic Package Manger? If not, what does Synaptic Package Manager offer that Ubuntu Software Center doesn't?
Synaptic is no longer installed by default on Ubuntu. It basically does the same as the Software Center, but it has more granular and detail control. However, it does not offer newer versions.

This is because both use the same repositories.

> **sanssadness said:**
> I am reading about PPAs this moment. Are you trying to say that unless I upgrade my version of Ubuntu (which I don't want to do right now, because 12.04 is a LTS version), the only way I can updates for LibreOffice is through a PPA? If so, I won't mind adding them. I'm pretty sure LibreOffice is safe to install.
In Linux there's always 'other ways' to install software, but I'd recommend trying the ppa method first.

BTW, 14.04 will be a LTS.

> **sanssadness said:**
> By the way, how can you tell if a program needs to be in a PPA to be updated? I already have updates from precise-security, precise-updates, and precise-backports.
Adding a ppa is simplified way of adding a repository. After you add the ppa and update your sources, the system will get the latest version available that the next time you upgrade.

> **sanssadness said:**
> If LibreOffice came with Ubuntu, why aren't these 3 update sources enough?
In a common Linux distribution, the package versions are selected and tested with the goal of stability and interoperability between then as a first priority. Getting the latest version is also a concern but not a priority.

Does that help?
Regards.

---

### Post by sanssadness on 2014-04-16
Thanks for all the quick replies! It's good to know that I do get updates if they are security related. Even if I still have to do some work adding PPAs, I suppose this is still better than Windows; Windows only gives operating system updates and every program has to be updated manually unless you install some kind of third party update manager. I'm still new to all this, so I'm going to do some reading on package management and PPAs before proceding. At this point, I only have a few questions left about software updates:

1. I came across a page that seems to list the contents of many Ubuntu software sources:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

The list seemed comprehensive, so why isn't precise-security in the list? Can I rely on the list to give me a comprehensive list of what is updated and what isn't when I check the corresponding box under "Install updates from:"?

2. If I install a program by searching for it in Ubuntu Software Center, will Update Manager automatically give me updates for it as they become available, or do I still have to add it to PPA?

3. Isn't it a good idea to add PPAs for most programs anyways? Picture the following scenario: I don't have the Firefox PPA, and there is a major update, but the update doesn't fix any security flaws. This means Firefox may not be updated if I don't have its PPA added right?

---

### Post by jbaerboc on 2014-04-16
Hi Sanssadness, I have a few PPA's added to 14.04 Beta but they fill a specific requirement for me [i like to run the lates Wine version for example since I do gaming in Linux]. As previous posters have said I would recommend only added very trusted PPAs. LibreOffice should be perfectly safe and not a big problem. I'll try to answer your recent questions:

#2 - The Ubuntu Software Center and programs like Synaptic all reference the same software repositories [databases or lists if you will]. So regardless of if you install through Ubuntu Software Center or something like Synaptic you will get updates as they are approves and added to the previously mentioned repositories/databases.

#3 - When you run the updater it checks the repositories you have currently added to your system [ubuntu approves, PPAs, etc...] and if it finds a newer package it suggests you install it. If you don't add any PPAs then the only updates you will get are those added to the official repositories [generaly means they have been tested and deamed safe enough]. By adding a PPA you bypass that extra bit of testing or stability testing. But if it's from a trusted source like LibreOffice you're generaly ok.

---

### Post by sanssadness on 2014-04-16
I'm getting a message from Update Manager telling me that "Not all updates can be installed". Why is this?

I don't know if this is related, but if I intend to install a program like LibreOffice from PPA, do I have to remove the old version that came with my Ubuntu install first?

Edit: I just removed all traces of the old LibreOffice, but I'm still getting that message. My Googling suggests that it's caused by a "dependency issue". I isolated the update I cannot get: it's called libexttextcat-data (size: 194 kB). Any suggestions? I haven't installed the new version of LibreOffice from PPA yet. All I did so far was uninstall the version of LibreOffice that came with Ubuntu.

---

### Post by ian-weisser on 2014-04-16
> **sanssadness said:**
> 1. I came across a page that seems to list the contents of many Ubuntu software sources:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

The list seemed comprehensive, so why isn't precise-security in the list? Can I rely on the list to give me a comprehensive list of what is updated and what isn't when I check the corresponding box under "Install updates from:"?

Your question is vague and confusing. That website is a mashup of the current packages in the supported (official) Ubuntu repositories, and does include -security. Security updates are also pushed to the appropriate non-security repository.


> **sanssadness said:**
>  2. If I install a program by searching for it in Ubuntu Software Center, will Update Manager automatically give me updates for it as they become available,

Yes, unless you have changed the settings.


> **sanssadness said:**
>  or do I still have to add it to PPA?

PPAs can be convenient, but are NOT supported software, and and not part of the Ubuntu Repositories.
If you screw up your system by adding lots of PPAs, we cannot help you much. That's part of what 'not supported' means. It also means PPAs DON'T get security updates.
Remeber that you must uninstall the software and disable the PPA if you ever want to return to the official Ubuntu Repositories version of the software.


> **sanssadness said:**
>  3. Isn't it a good idea to add PPAs for most programs anyways? Picture the following scenario: I don't have the Firefox PPA, and there is a major update, but the update doesn't fix any security flaws. This means Firefox may not be updated if I don't have its PPA added right?

No, it simply means the new version has not been packaged yet by a human volunteer. Mozilla is a big, complex set of software, and not trivial to package properly. It's certainly NOT a good idea to load up your system with lots of unsupported repositories and packages that you must maintain manually. That's rather the opposite of that package management is supposed to do.

If you always want the latest-and-greatest version of software, then you should certainly not be using 12.04LTS, which is intended for precisely the opposite use case of as-little-change-as-possible. You should be using the normal 6-month release of Ubuntu to get newer software, rather than PPAs. If you want the absolutely-newest, then you must learn to install from source, learn how to file bugs, and become a tester.

---

### Post by sanssadness on 2014-04-17
I didn't get the latest versions of Ubuntu because I didn't want to have to keep reinstalling the operating system every few months. I figured I could keep getting operating system updates on LTS versions. I didn't anticipate that having an older operating system would actually prevent me from installing newer software, even if I have to do it manually. And really, I don't mind manually installing some safe software from PPAs. I just need a little help working out this problem:

LibreOffice is not installed. I uninstalled everything I could find that had the word "LibreOffice" from Ubuntu Software Center. Then I ran these 3 commands:

sudo apt-get remove --purge libreoffice*
sudo apt-get clean
sudo apt-get autoremove

At this point, if I add LibreOffice's PPAs (either ppa:libreoffice/ppa or ppa:libreoffice/libreoffice-4-2), I get the message "Not all updates can be installed. Run a partial upgrade, to install as many updates as possible." The 2 things listed are:

1. Other updates (LP-PPA-libreoffice)
2. libexttextcat-data

I know PPAs aren't part of the operating system, but many people, even in this thread, have reported being able to do it. This message that not all updates can be installed looks like a newbie problem, but I've been unable to find information on my specific situation. All help would be appreciated.

---

### Post by deadflowr on 2014-04-17
I would think that if you added the ppa, then you probably only needed to run an update
(I use the update manager and click "check"), then it should have listed all the updates for the new version of libreoffice.
And not only that, but would include only those updates for the packages you had/have installed for libreoffice.

At least that's how I've always ran ppa's for existing packages.

---

### Post by sanssadness on 2014-04-17
I managed to figure out a solution myself. I ran this command:

apt-get dist-upgrade

After running this command, I'm not sure exactly what happened, but if I'm not mistaken, libexttextcat0 was installed instead of libexttextcat-data. I'm not sure why, or what the relationship between these 2 files even is, but it fixed the error. I still can't directly download Libreoffice 4 from Update Manager, but I can now see version 4 of Libreoffice from Ubuntu Software Center. Presumably, if I download it there now, I can get updates via the Update Manager.

I never expected to run into so much trouble from just adding a PPA. But at least it's working now. I still don't understand what the problem was, and why apt-get told me libexttextcat-data was "held back", so if someone understands what happened, please explain. Thanks!

---

