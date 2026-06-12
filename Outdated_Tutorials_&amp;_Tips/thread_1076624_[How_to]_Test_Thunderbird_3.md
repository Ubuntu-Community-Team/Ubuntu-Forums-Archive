---
title: "[How to] Test Thunderbird 3"
date: 2009-02-21
forum: Outdated Tutorials &amp; Tips
---

### Post by OrelEagle on 2009-02-21
Hello,

After reading [a thread in the French Ubuntu forum]("http://forum.ubuntu-fr.org/viewtopic.php?id=238976"), I decided to try the new features brought by Thunderbird 3. And since I find it really cool, I'd like to share how to install it (in parallel with Thunderbird 2) and contribute to the tests. This tutorial will be divided into 4 parts:

Part I: install process
Part II: Create a new profile
Part III: Contribute to the tests
Part IV: Remove Thunderbird 3

Please remember that Thunderbird 3 is still in beta version and could (although very unlikely) harm your data (emails, contacts). For this reason I strongly recommend to use non critical email accounts and create a specific profile for this purpose (read part II for more information).

**Part I: install process**

The install process is very simple:
1. Download the file
2. Extract the archive
3. Move the thunderbird folder to /opt
4. Create a link to run it easily

1. Download the file

You can download the most recent public release from Thunderbird's website:
[http://www.mozillamessaging.com/en-US/thunderbird/early_releases/](http://www.mozillamessaging.com/en-US/thunderbird/early_releases/)

2. Extract the archive

Go to the folder where you downloaded the file (it should be a .tar.bz2) and extract it (right click -> extract here). Alternatively, you can also use the tar command.

3. Move the thunderbird folder to /opt

You will need sudo rights to move the file to /opt. You can either start Nautilus in root mode and move the folder graphically or use this command, assuming you are working in the folder where you extracted the archive:

```
sudo mv thunderbird /opt
```

4. Create a link to run it easily

You will create a link to the executable and put it in /usr/bin, this way you simply have to use this link to run the testing version, for example using the "run application" dialog (Alt+F2). I called it "thunderbird3" to make it clear.

```
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/thunderbird3
```


It is also possible to do all this in 1 line of command, but I prefer to detail each step. Feel free to post this command in the replies.

**Part II: Create a new profile**

Now that you have installed Thunderbird 3, you don't want it to mess up with your data. For this you will create a new profile. Simply start Thunderbird 3 with the profile manager:

```
thunderbird3 -P
```

In this dialog box, click on "Create Profile...". Follow the instructions from the wizard and chose a name for this profile. Let's call it testProfile. Now you can select testProfile in the profile manager and start testing! When you want to use your normal profile, simply start the profile manager again and select it in the list.

**Part III: Contribute to the tests**

To make Thunderbird a high quality application, the mozilla team needs your help! The first thing to do is to subscribe to the [Thunderbird-testers]("https://mail.mozilla.org/listinfo/thunderbird-testers") mailing list. You will then receive instructions about how to test the new features of Thunderbird.

I also recommend to read the wiki page about [how you can help]("https://wiki.mozilla.org/Thunderbird:Testing").

**Part IV: Remove Thunderbird 3**

We'll simply delete the folder containing the files and the link to the executable:
```
sudo rm -rf /opt/thunderbird /usr/bin/thunderbird3
```

---

### Post by canabal on 2009-03-08
Thanks for the nice easy to use guide.

---

### Post by binbash on 2009-03-09
Thanks

---

### Post by el cameleon on 2009-05-21
Thanks for this "how to", I would never success to install it alone!

Do you know how we can une the Thunderbird icon to launch Thunderbird? The only one I can find in /opt/thunderbird/icons cannot be use as an icon in Ubuntu.

---

### Post by pediatracancun on 2009-08-13
I did all the steps to install Thunderbird3A3; when I give the command thunderbird3 -P, it presents with the profile manager, but I can't create this profile and receive the following message:

Profile couldn't be created. Probably the chosen folder isn't writable.
[Exception... "Component returned failure code: 0x80520015 (NS_ERROR_FILE_ACCESS_DENIED) [nsIToolkitProfileService.createProfile]"  nsresult: "0x80520015 (NS_ERROR_FILE_ACCESS_DENIED)"  location: "JS frame :: chrome://mozapps/content/profile/createProfileWizard.js :: onFinish :: line 233"  data: no]

If I do sudo thunderbird3, there is no problem in working in such way.

Can you help me?

---

### Post by jmadero on 2009-08-18
Is there a way to import everything from thunderbird 2? This would be really helpful as I have all my email, calendars, contacts in thunderbird 2. Thanks!

---

### Post by binarymutant on 2009-08-26
I followed your guide but 
> thunderbird3 --version
 Thunderbird 2.0.0.23, Copyright (c) 1998-2009 mozilla.org

:/

---

### Post by nilsja on 2009-12-15
> thunderbird3 --version
 Thunderbird 3.0, Copyright (c) 1998-2009 mozilla.org.

---

### Post by barjea on 2009-12-22
> **pediatracancun said:**
> I did all the steps to install Thunderbird3A3; when I give the command thunderbird3 -P, it presents with the profile manager, but I can't create this profile and receive the following message:

Profile couldn't be created. Probably the chosen folder isn't writable.
[Exception... "Component returned failure code: 0x80520015 (NS_ERROR_FILE_ACCESS_DENIED) [nsIToolkitProfileService.createProfile]"  nsresult: "0x80520015 (NS_ERROR_FILE_ACCESS_DENIED)"  location: "JS frame :: chrome://mozapps/content/profile/createProfileWizard.js :: onFinish :: line 233"  data: no]

If I do sudo thunderbird3, there is no problem in working in such way.

Can you help me?
Hi,
Check the ownership of .thunderbird folder.
If owner is root then change it to your own login : 
chown -R xxx:xxx /home/xxx/.thunderbird
xxx being your login.
This solve the issue for me !

note : when you run thunderbird using sudo, you run it as root (this explains that !)

---

