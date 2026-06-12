---
title: "Problems after installing Xubuntu"
date: 2014-12-16
forum: New to Ubuntu
---

### Post by roy27 on 2014-12-16
1) Desktop background won't switch. I can only switch my desktop to the pictures available in backdrop through the "Desktop" application. I can't click "set as desktop background" button. (Picture: [http://imgur.com/OZ6o73F](http://imgur.com/OZ6o73F)) 

2)Language won't switch. It also wouldn't let me copy text from other languages (if I do copy it, it displays it as letters and numbers). (Picture: [http://imgur.com/0VW3nW5](http://imgur.com/0VW3nW5))


 ~ Can you recommend a file encryptor and a sound mixer?

Thank you for help

---

### Post by slickymaster on 2014-12-16
Hi roy27, welcome to the forums.

> **roy27 said:**
> 1) Desktop background won't switch. I can only switch my desktop to the pictures available in backdrop through the "Desktop" application. I can't click "set as desktop background" button. (Picture: [http://imgur.com/OZ6o73F](http://imgur.com/OZ6o73F))
To change your desktop backdrop click the Desktop button in the Settings Manager, or alternatively, right clicking your desktop and select the 'Desktop Settings...' option. Once the Desktop settings dialog is open, the Background tab gives you options for choosing to use a single image or multiple images as wallpaper.
The location of the images in the 'Wallpaper for my desktop' pane is controlled by the **Folder:** option. By bringing up this pick list, you can choose an alternate location for the source of your images by navigating to the desired folder and clicking the 'Open' button in the **Select a file** dialog.

For reference: [http://smdavis.us/doku/doku.php?id=xfdesktop-docs:usage](http://smdavis.us/doku/doku.php?id=xfdesktop-docs:usage) 
> **roy27 said:**
> 2)Language won't switch. It also wouldn't let me copy text from other languages (if I do copy it, it displays it as letters and numbers). (Picture: [http://imgur.com/0VW3nW5](http://imgur.com/0VW3nW5))
Are you saying that you're unable to install additional languages packs?
> **roy27 said:**
> ~ Can you recommend a file encryptor and a sound mixer?
Thank you for help
I would recommend you [encfs]("https://help.ubuntu.com/community/FolderEncryption").

---

### Post by roy27 on 2014-12-16
Thank you for the welcome and for replying to my post. 

I just fixed the first problem, using the Desktop application, I was able to pick the folder and open the folder (I thought you need to click on the individual picture. Usually clicking the "open" button would just open a folder, not all the pictures in it.)

I'm not sure if it doesn't let me install the language packs themselves or not. It appears that it did install. ( Picture: [http://imgur.com/0VW3nW5](http://imgur.com/0VW3nW5) ). But it is grayed out, as if it needs me to somehow activate it? When I switch to the language (Japanese) it actually only switches to the Japanese keyboard. For example, it doesn't display Japanese characters, so it would let me type in Roman characters (as the ones that this message is typed in) but it would just switch the function of a couple of keys, an apostrophe would be a colon instead.

---

### Post by slickymaster on 2014-12-16
See if this can be of help: [Writing Japanese with Ubuntu 14.04 Trusty Tahr]("http://moritzmolch.com/1453")

---

### Post by roy27 on 2014-12-16
> **slickymaster said:**
> See if this can be of help: [Writing Japanese with Ubuntu 14.04 Trusty Tahr]("http://moritzmolch.com/1453")

I can follow the guide up to step 7. I can't access my system settings. I'm in Xubuntu so to access them I click on the computer icon. (About This Computer tab also doesn't work. ) 
  I've tried restarting the computer but that doesn't help.

---

### Post by slickymaster on 2014-12-16
> **roy27 said:**
> I can follow the guide up to step 7. I can't access my system settings. I'm in Xubuntu so to access them I click on the computer icon. (About This Computer tab also doesn't work. ) 
  I've tried restarting the computer but that doesn't help.

You can access system settings in Xubuntu from the whisker menu icon in the top left of your desktop. See the image below:
[ATTACH=CONFIG]258631[/ATTACH]

---

### Post by roy27 on 2014-12-16
Okay, I fixed it. Apparently there are multiple settings in the Japanese language setting when you add the language, and you need to choose the right one to be able to type Japanese. 
 &#26085;&#26412;&#35486;&#12384;&#12424;&#12290; Thanks for your help.



I have another question: Is Wine safe to install, will it make my Xubuntu as vulnerable as my Windows system was? And do I need an antivirus on my Xubuntu? Lets say I accidently go on a malicious website, can a worm or some PUP get onto my system?

---

### Post by slickymaster on 2014-12-16
> **roy27 said:**
> Okay, I fixed it. Apparently there are multiple settings in the Japanese language setting when you add the language, and you need to choose the right one to be able to type Japanese. 
 &#26085;&#26412;&#35486;&#12384;&#12424;&#12290; Thanks for your help.

Glad it's fixed and running. Please mark this thread as [SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") so other people searching the forums know it provides a working solution for this problem.
> **roy27 said:**
> I have another question: Is Wine safe to install, will it make my Xubuntu as vulnerable as my Windows system was? And do I need an antivirus on my Xubuntu? Lets say I accidently go on a malicious website, can a worm or some PUP get onto my system?
Since the issue that was behind this thread is already solved, I advise you to start a new one regarding this.

From [Suggestions on how to get your support questions answered as quickly as possible]("http://ubuntuforums.org/showthread.php?t=1422475")> Post only one thread on your topic. Posting multiple threads dilutes community effort, and makes it more difficult for others to help.

---

