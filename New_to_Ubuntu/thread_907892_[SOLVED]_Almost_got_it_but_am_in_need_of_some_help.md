---
title: "[SOLVED] Almost got it but am in need of some help............Please?"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by Sava8420 on 2008-09-01
So I've got almost everything up and running on my new laptop from ATI HD3450 through bluetooth (which was easier than I was making it out to be).  But I just am having one hell of a time with this wireless card.  It's an Atheros AR5009 802.11 a/g/n internal card.  I am fairly fresh into the world of Ubuntu and installing it on my desktop was so painless I didn't bother checking what hardware I should configure my laptop with.  Ok anyways I installed ndisgtk and got drivers off HP's website.  Installed wine to run .exe file and produced the .inf file and copied it to the ndisgtk app with success.  But go to configure hardware and card isn't listed.  When looking in Hardware Manager it is listed as a network card but not the ethernet card.  I have to use Vista for net as of right now so will try to be quick in retrieving any info you need off ubuntu.  If you can help would greatly appreciate it.

---

### Post by dRock1286 on 2008-09-01
have you tried the ndiswrapper?  I don't know anything about using it, as my atheros based d-link wireless card worked out of the box in ubuntu 8.04

EDIT:  but, i did have problems with the earlier versions and the ndiswrapper worked like a charm for me.

---

### Post by Sava8420 on 2008-09-01
Will give it a shot

---

### Post by ctswhole on 2008-09-01
> **dRock1286 said:**
> have you tried the ndiswrapper?  I don't know anything about using it, as my atheros based d-link wireless card worked out of the box in ubuntu 8.04

EDIT:  but, i did have problems with the earlier versions and the ndiswrapper worked like a charm for me.

The way I understand it is that ndisgtk is the GUI frontend to ndiswrapper.  If someone was to install ndisgtk on their system, ndiswrapper would be installed as well.

Now my question to the OP is, after you installed the driver using ndisgtk what was the resulting display?  Did it say something like "Driver installed, hardware present"?

---

### Post by Sava8420 on 2008-09-02
> **ctswhole said:**
> The way I understand it is that ndisgtk is the GUI frontend to ndiswrapper.  If someone was to install ndisgtk on their system, ndiswrapper would be installed as well.

Now my question to the OP is, after you installed the driver using ndisgtk what was the resulting display?  Did it say something like "Driver installed, hardware present"?
Yes this is correct as I just got done checking into.  I have the Official Ubuntu Book 3rd edition and it says something about the wireless adapter being listed under the ethernet section of hardware info.  Well that is not the case with mine Realtek ethernet adapter is listed there as I think it probably should be.  I don't know what to think.

---

### Post by ctswhole on 2008-09-02
Well, if you're getting the display of "driver installed, hardware present" then you've hit my limit of knowledge in this area.  When I installed windows wireless drivers this way and got that message I was then able to click on the network manager applet in the panel and view/connect to wireless networks.

Sorry if I couldn't be more help to you on this, maybe someone more knowledgeable will swoop in here and provide some answers. :)

---

### Post by Sava8420 on 2008-09-02
> **ctswhole said:**
> Well, if you're getting the display of "driver installed, hardware present" then you've hit my limit of knowledge in this area.  When I installed windows wireless drivers this way and got that message I was then able to click on the network manager applet in the panel and view/connect to wireless networks.

Sorry if I couldn't be more help to you on this, maybe someone more knowledgeable will swoop in here and provide some answers. :)

That is what has got me.  I to say the least was a bit confused when I wasn't able to configure network after it said that.  While I may be quite the newb still I have come to find that this may just be what I love about ubuntu.  It isn't fun if it ain't a challenge.  I don't care if I have to teach myself to make a damn driver this is gonna work in the end.

---

### Post by nothingspecial on 2008-09-02
I`m 99% sure that card works with madwifi. If you need some help with that post back.

---

### Post by hyper_ch on 2008-09-02
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by Sava8420 on 2008-09-02
> **hyper_ch said:**
> It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

Not to justify my lack of a using descriptive title but the tags clearly indicate what the post is about.](*,)  At the same time I understand your point and will take note for any future posts.

---

### Post by Sava8420 on 2008-09-02
> **nothingspecial said:**
> I`m 99% sure that card works with madwifi. If you need some help with that post back.

Sorry for not getting back sooner as I have been toying with it.  Still no luck but have found that driver isn't proper for ndiswrapper that I am currently using.  So would like any advice you have got for me.  Thanks.

---

