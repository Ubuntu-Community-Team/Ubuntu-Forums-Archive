---
title: "HDHOMERUN install"
date: 2016-11-02
forum: New to Ubuntu
---

### Post by gcook12 on 2016-11-02
I am new to Linux, Ubuntu and was hoping someone could direct me where to go for help.  I have Ubuntu installed on my computer and have succeeded in installing a couple of programs but I want to install HDHOMERUN and cannot seem to get it to work. Where should I post a request for help?

---

### Post by yancek on 2016-11-02
You have purchased the hardware and used what software to try to get it working?  Did you go to the Ubuntu Software Center to get it?  Did you get a CD/DVD with the hardware to use?  What steps have you taken?

---

### Post by ian-weisser on 2016-11-02
The HDHOMERUN that I'm familiar with is hardware. You watch the video stream in any web browser or media player by using the IP address of the hardware.
What software, exactly, are you trying to install?

---

### Post by deadflowr on 2016-11-02
Aside from whether the model is one that can run in linux (not sure if all do),
did you install the *hdhomerun-config* and *hdhomerun-config-gui* packages?
Easy enough to do, open a Terminal and run
```
sudo apt-get update
sudo apt-get install hdhomerun-config hdhomerun-config-gui
```
You should get a new app in the menu to launch the configuration utility.

Perhaps some light reading for you as well:
[https://help.ubuntu.com/community/HDHomeRun]("https://help.ubuntu.com/community/HDHomeRun")


> Where should I post a request for help?
We'll keep it here, for now.

---

### Post by gcook12 on 2016-11-02
> **yancek said:**
> You have purchased the hardware and used what software to try to get it working?  Did you go to the Ubuntu Software Center to get it?  Did you get a CD/DVD with the hardware to use?  What steps have you taken?

The hardware is a little box with a tv antenna connection on one side and an ethernet conntection on the other side that connects into your router so over the air channels are accessible over wifi. The company supplies software to be used on windows, android, and Linux.  I have gotten the windows version and the android versions working but can/t seem to get the Linux version working.  It is a download from their website.  Their webpage has two compressed files that they want you to download to a folder and expand which I did but I cannot find where to go from there.

---

### Post by gcook12 on 2016-11-02
> **ian-weisser said:**
> The HDHOMERUN that I'm familiar with is hardware. You watch the video stream in any web browser or media player by using the IP address of the hardware.
What software, exactly, are you trying to install?

The software that I am trying to load is from the Silicon Dust Website which is the manufacturer.

---

### Post by gcook12 on 2016-11-02
I followed your steps but don't see an instll item on the menu.  Just to show how new I am to this.  Is the menu the list of programs on the left or  something else?

> **deadflowr said:**
> Aside from whether the model is one that can run in linux (not sure if all do),
did you install the *hdhomerun-config* and *hdhomerun-config-gui* packages?
Easy enough to do, open a Terminal and run
```
sudo apt-get update
sudo apt-get install hdhomerun-config hdhomerun-config-gui
```
You should get a new app in the menu to launch the configuration utility.

Perhaps some light reading for you as well:
[https://help.ubuntu.com/community/HDHomeRun](https://help.ubuntu.com/community/HDHomeRun)



We'll keep it here, for now.

---

### Post by gcook12 on 2016-11-02
> **deadflowr said:**
> Aside from whether the model is one that can run in linux (not sure if all do),
did you install the *hdhomerun-config* and *hdhomerun-config-gui* packages?
Easy enough to do, open a Terminal and run
```
sudo apt-get update
sudo apt-get install hdhomerun-config hdhomerun-config-gui
```
You should get a new app in the menu to launch the configuration utility.

Perhaps some light reading for you as well:
[URL="https://help.ubuntu.com/community/HDHomeRun"]https://help.ubuntu.com/community/HDHomeRun

I found that confusing but maybe it is because I don't understand teh terminology yet.[/URL]



We'll keep it here, for now.

Thanks

---

### Post by steeldriver on 2016-11-02
I don't think the version on the Silicon Dust website ("Current release: 20150826") is any newer than that available direct from the Ubuntu repositories

```

$ apt-cache policy hdhomerun-config
hdhomerun-config:
  Installed: (none)
  Candidate: **20150826**-2
  Version table:
     20150826-2 500
        500 http://ca.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages

```

I really recommend you follow the instructions in deadflowr's post above rather than following the instructions on the website - it will be WAY easier

---

### Post by gcook12 on 2016-11-02
> **steeldriver said:**
> I don't think the version on the Silicon Dust website ("Current release: 20150826") is any newer than that available direct from the Ubuntu repositories

```

$ apt-cache policy hdhomerun-config
hdhomerun-config:
  Installed: (none)
  Candidate: **20150826**-2
  Version table:
     20150826-2 500
        500 http://ca.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages

```

I really recommend you follow the instructions in deadflowr's post above rather than following the instructions on the website - it will be WAY easier

Thanks, I did try deadflowr's post but I still must be doing something wrong

---

### Post by gcook12 on 2016-11-02
> **gcook12 said:**
> Thanks, I did try deadflowr's post but I still must be doing something wrong

Life is good.  I found it and it works.  Thanks to you all!!!

---

### Post by deadflowr on 2016-11-02
> **gcook12 said:**
> Life is good.  I found it and it works.  Thanks to you all!!!

Cool.
If you feel it's working and the issue at hand is solved, [please mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").
so that others may find it and hopefully find themselves a workable solution as well.

---

### Post by gcook12 on 2016-11-03
> **deadflowr said:**
> Cool.
If you feel it's working and the issue at hand is solved, [please mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").
so that others may find it and hopefully find themselves a workable solution as well.?

Sure.  I still have a few questions, should I mark this complete and start another one to ask my related questions?  The questions are things like a better understanding of the commands you suggested and why the appearance looks different.

---

### Post by oldos2er on 2016-11-04
Create a new thread if you have questions about apt-get commands, or any question not pertaining to HDHOMERUN install.

---

### Post by gcook12 on 2016-11-05
Ok. I will post unrelated questions to anew thread. After looking into it farther I don't think I should mark this as solved. I was able to watch tv and I assumed the software had loaded but I now think it did not load and the video was not using the hdhomerun software.

---

