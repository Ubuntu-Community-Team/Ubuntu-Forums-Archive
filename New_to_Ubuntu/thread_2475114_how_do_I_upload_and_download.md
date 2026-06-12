---
title: "how do I upload and download"
date: 2022-05-17
forum: New to Ubuntu
---

### Post by smallville1979 on 2022-05-17
I am brand new to unbuntu. 
how do I upload and download on firefox? 
I am struggling as everything on google points to old versions and doesnt work. not sure whether to go back to windows 10 or persevere.

---

### Post by smallville1979 on 2022-05-17
i insatlled google chrome and the same. when I go to email attachments it just goes grey and I need to close it down?

---

### Post by mIk3_08 on 2022-05-17
> **smallville1979 said:**
> I am brand new to unbuntu. 
how do I upload and download on firefox? 
I am struggling as everything on google points to old versions and doesn't work. not sure whether to go back to windows 10 or persevere.
Please run this command below and paste your result here in this thread so that community may know your Linux Ubuntu Operating System. Regards and cheers.
```
hostnamectl status
```

---

### Post by yancek on 2022-05-17
Upload or download what and from what site(s).  That's an extremely vague question.  How to download would depend upon how it is set up on a particular site, usually a button or tab saying Download.  You'll need to be a lot more specific with your problem to get help.f

---

### Post by Impavidus on 2022-05-17
Which version of Ubuntu? If you installed Ubuntu 22.04 LTS (latest version at the moment), Firefox was installed as a snap package, which means that it's put in a container (partly for security, but also to make things easy for the packagers). That gives Firefox only limited access to your filesystem. I don't use 22.04, but I think that at least your Downloads directory should still be accessible.

---

### Post by ActionParsnip on 2022-05-17
Upload and download what? You don't just "upload", you upload to a Web site or github or something like that... Details please

---

### Post by Skaperen on 2022-05-17
do you have a URL for the site that you want to download from or upload to?  is it just one file or many files?  there is no "one solution" for any system.  often the site has some kind of assistance provided.  but that "assistance" could be a security risk and except for well trusted sites, should be avoided.

if you are downloading an application (app) to use/run, that could be a grave security risk (someone can take over your computer).

"the greatest security risk for *any* computer is the _human_ at the controls."  --Skaperen

---

### Post by smallville1979 on 2022-05-18
Static hostname: tom-OptiPlex-3080
       Icon name: computer-desktop
         Chassis: desktop
      Machine ID: 3d9ac242103a41e7a6b2218e63fe08b5
         Boot ID: 1b98dee44e404a5dbd021493f8972646
Operating System: Ubuntu 22.04 LTS                
          Kernel: Linux 5.15.0-30-generic
    Architecture: x86-64
 Hardware Vendor: Dell Inc.
  Hardware Model: OptiPlex 3080
tom@tom-OptiPlex-3080:~$

---

### Post by smallville1979 on 2022-05-18
it wont work on hyperlinks in firefox where u can attach files on a website. i.e. to apply for job that I need. I cant upload or work with attachments. 
It wont work on email. its some kinda setting in firefox.

---

### Post by TheFu on 2022-05-19
The first thing to do is to ensure your system is fully patched. Run
```
sudo apt update
sudo apt full-upgrade
```
Restart any applications that were updated. Reboot if necessary. There was a fix to GTK libraries that was patched a few weeks ago that some people said was related to this.

If that doesn't fix it, then the possible problem is due to the switch of firefox to snap packaging in 22.04, as others have said.  Not much can be done about that, except to use a browser that isn't installed with snap packaging.  In Ubuntu, firefox and chromium are both snap packages by default.  

There are other ways to get them installed without a snap, but I'm not comfortable recommending it, since I haven't done it myself and don't use 22.04 yet.  [https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04) has instructions and they are a reputable website.

---

### Post by smallville1979 on 2022-05-22
is there a backup browser I can install please that doesnt use snap. 
I have a course tmrw so might need it. I need teams to work and the ability to screenshot and upload. chrome and firefox stopped working when I installed teams. there was a previous code fix that worked that stopped working.

---

### Post by smallville1979 on 2022-05-22
your a genius thanks. the firefox install without snap fixed it. many thanks.

---

### Post by TheFu on 2022-05-22
> **smallville1979 said:**
> is there a backup browser I can install please that doesnt use snap. 
I have a course tmrw so might need it. I need teams to work and the ability to screenshot and upload. chrome and firefox stopped working when I installed teams. there was a previous code fix that worked that stopped working.

Hundreds.  Ok, perhaps not, but 25.  I bet wikipedia has an article that lists web browsers.  You can work your way through the ones that grab your interest.  If it were me, I'd run each inside a container to prevent the damage bad-acting software can cause.  Snaps sorta do this, but they don't allow local control over the limitations like other sandboxing/container tool do.  Some people here use a full Linux Container to run their browsers inside.  I go with a lighter touch and use **firejail**, which provides 50+ controls for what is allowed and what is disallowed, even down the local file system areas that are allowed to be accesses.  Firejail has a virtual file system mode that presents a file system that isn't the truth, allows full read-write everywhere, but when the program closes, all those writes are gone. They never touched any real storage.  Every time firejail runs a program in that --private mode, it seems like the very first run of the program.  There are many excellent reasons for this mode to be used.  I use it every week for online meetings.  It also means that less-than-secure browsers like Google-Chrome can be used, but not trusted. That's a huge win in my book.  I struggle to understand why anyone would install a browser by the worlds largest online tracking company onto their computers.  Boggles my mind, it does.  I feel bad enough using Chromium, because some of the core hooks still use Google servers, which means tracking.

I really don't mind if Joe's Body Shop tracks me on their website.  What I do mind is when Joe's decides to outsource their tracking to some huge tracking company (say using google-analytics). THAT is unacceptable to me.  Joe's gets access to most of the data, but Google gets access to all of Joe's data AND all the data from every other website in the world (nearly), then correlates the data in ways that is beyond creepy.  Google and other tracking companies exchange data. Sometimes they have the same clients, so they can synchronize the different unique-user-numbers that each system uses and vastly increase the creepy levels.  Average people have no idea.  Don't get me started about gmail, yahoomail, or any other "free" email providers.

I'm partial to lynx and dillo browsers, but those specifically don't support javascript, which can make much of the web not "work", but for access to the information on a website, they are excellent. They also prevent 99% of the attack vectors that bad websites use, since there's no downloading of remote code to run on your local system with every page view, like javascript causes.

---

### Post by TheFu on 2022-05-22
> **smallville1979 said:**
> your a genius thanks. the firefox install without snap fixed it. many thanks.

Almost forgot.  Help the community out. Use the _Thread Tools button_ and mark this thread as **SOLVED**.  That will keep people from wasting time.

---

