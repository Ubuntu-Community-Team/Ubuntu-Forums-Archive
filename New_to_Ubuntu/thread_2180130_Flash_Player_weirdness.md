---
title: "Flash Player weirdness"
date: 2013-10-11
forum: New to Ubuntu
---

### Post by Toni_Vines on 2013-10-11
OK, I've been trying all day to sort this but it's not happening! Here goes: Youtube (in Mozilla) - won't play, then I install Flash Player and it still won't work so I disable it - and bingo! The damn thing works!!!!! So I post a clip that I like to my facebook page and firstly it works, then it doesn't! I go back to Youtube and it's working. I then try it in Chromium - it's not working so back to Mozilla and now it's not working!!!! I've been reading through the various postings on here and been trying various ideas but it's no good! 
As I'm a musician Youtube is very important to me, so much so that if this can't be fixed I'll have to ditch it and I really don't want to do that. 
Any help would be wonderful,
Thank you,
Toni. 
By the way in running Ubuntu 12.04 32 bit. I have an AMD Athlone machine with Pentium 3 and 2 gig RAM.

---

### Post by pesh1985 on 2013-10-11
Hi Toni, 

Is Flash enabled on both Chrome and Firefox in the plugins/extensions?

Chrome = type this into the address bar of chrome - [chrome://plugins/](chrome://plugins/)   and enable flash ;)

---

### Post by Toni_Vines on 2013-10-11
OK, done that and when I atempt to play a youtube clip I get a strip saying 'cannot load flash player'

---

### Post by |{urse on 2013-10-11
And when you disable?

---

### Post by |{urse on 2013-10-11
[http://www.youtube.com/html5](http://www.youtube.com/html5) <-- there is always the option to skip flash with youtube and use their html5 version, it requires that you are logged in to youtube. Also this is just youtube, it won't solve flash issues on other sites obv.

---

### Post by pesh1985 on 2013-10-11
> **|{urse said:**
> [http://www.youtube.com/html5](http://www.youtube.com/html5) <-- there is always the option to skip flash with youtube and use their html5 version, it requires that you are logged in to youtube. Also this is just youtube, it won't solve flash issues on other sites obv.

This was also my next plan of action!

---

### Post by Toni_Vines on 2013-10-12
Well I've installed, unistalled, re-installed, updated and God knows what else and I really can't sort this out! This is utterly ridiculous, surley it should be easier than this! Sorry about the rant but I'm pulling my hair out here! I don't know how to try the html5 version so a guide through would be great! I've also got this happening: when I try something I've posted to facebook it tells me to install Flash Player. When I click on this I get a box asking me to select an app that I want to download it to. I'm guessing it means Mozilla but I can't seem to navigate to it. Any guidance on this please?
Thanking you,
Toni.

---

### Post by Toni_Vines on 2013-10-12
Someone help me please. I'm beginning to think after reading so much on this subject from others that this is in fact something that cannot be fixed. I've trawled through endless advice to others. I've carefully copied the relevant code into the terminal and worked very carefully. I've tried Firefox, Chromium, Chrome etc - zilch! The strange thing is I had it working to begin with but it was dreadfully unstable. 
I certainly don't blame Ubuntu, it's obviously some crap with Adobe and them not liking Linux! 
Are there any final things that I could try please? 
Any help or thoughts would be great!
Thanking you,
Toni.

---

### Post by jdwaugh on 2013-10-12
Okay, have you tried FLash-Aid it is a extension for firefox?  That helped me get it installed properly and working in firefox.

---

### Post by JeQhdMD on 2013-10-12
Suggest you install the Synaptic Package Manager (see Software Center).   Then do a search for flash, select the two main flash packages, and process a "complete uninstall".   Then restart the system, go back into Synaptic, search for Flash again, and do a reinstall.   Enable the details viewer, so you can see if the flash install processed fully.   If so, retest on youtube or similar flash based media site.

---

### Post by Toni_Vines on 2013-10-13
Looked for Flash-Aid but found a note saying it had been removed by the auther. Do you have a link for it please?
Thanking you,
Toni.

---

### Post by mörgæs on 2013-10-13
> **Toni_Vines said:**
> I have an AMD Athlone machine with Pentium 3 and 2 gig RAM.

I have never heard of such hardware. Please run

```
sudo lshw -sanitize > lshw.txt
```

and post lshw.txt in CODE tags.


By the way, bumping is not welcome. Removed from the thread.

---

### Post by Toni_Vines on 2013-10-13
OK, done all that and still nothing. In fact less than before because I had a black box where the video should be and now I don't even have that!

---

### Post by |{urse on 2013-10-13
And really, I gave you a link to the flash 5 opt-in up there, you just click on it and then click on "join html5 trial" <-- it's a big blue button, couldn't miss it if you tried.

[http://www.youtube.com/html5](http://www.youtube.com/html5) <--- Click the link with your left mouse button ](*,)

---

### Post by jdwaugh on 2013-10-13
Try this info in this link, you will be installing it manually and it will be outside the package management.  Unless you install from the repository and then follow the directions in this link: [http://forums.adobe.com/thread/1066869](http://forums.adobe.com/thread/1066869)

---

### Post by mörgæs on 2013-10-13
> **jdwaugh said:**
> Try this info in this link, you will be installing it manually and it will be outside the package management.  Unless you install from the repository and then follow the directions in this link: [http://forums.adobe.com/thread/1066869](http://forums.adobe.com/thread/1066869)

The instructions are for ARM. 
Are you sure they work for x86 too?

---

### Post by jdwaugh on 2013-10-13
Yeah, if you follow the directions about downloading from the website, extract the tar.gz and then mv/cp to the directory shown it works fine.  That is what I had to do to get it working.  The version in the repositories wouldn't work properly for me. The post about the manual install procedure worked like a charm.

---

### Post by Toni_Vines on 2013-10-14
Firstly, the html5 stuff about clicking the blue button does zero! It just tells me I'm in the test but nothing else! It tells me that if the video does not work to right click and send a message. I right click and nothing! 
On to the next tip. I have downloaded the tar.gz and unpacked it in my downloads folder. This gives me a folder called install_flash-player_11_linux.i387
Should I move this from it's present location and if so to where please?
Thanking you,
Toni.

---

