---
title: "Getting your Webcam to work with Skype"
date: 2010-05-27
forum: Outdated Tutorials &amp; Tips
---

### Post by TyTiger on 2010-05-27
Forgive me in advance if this is already been done in some dark forgotten depth of the forum, but I never came across a complete clear How to for doing this so I will contribute.
---

So here's the deal, You have a web cam on your Linux Ubuntu box, And all applications like Cheese and whatnot all work fine with your web cam, but then the one application where it really counts for you, Doesn't.. 

*My Diagnosis of the issue, It used to work once upon a time, but lately does not... It is to my understanding Skype is not using v4l, but some other custom library that doesn't really work for 99.9% of us (I cloud be wrong) I have herd of some cams working with Skype without the need of tweaking, But if like me your one of the unlucky ones reading this post, the read on because this may work for you.

So, you consider giving up all hope and selling your web cam on e-bay give this quick and easy fix a try. 

(Please note I only tested this with the .deb package downloaded from Skypes Website)

Preparation:
Somehwere safe, create a file and call it skype.sh (Right click - create empty document)
Open this file with your favourite text editor and fill it with the following 2 lines:

```
#! /bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

save changes and then right click and select properties, go to the permissions tab and select the "Allow Execution as a program", then close (or use 'chmod a+x /location/of/skype.sh' in the command line (without the quotations))

To edit the Skype launcher do the following:-

1. Right Click on your Applications Menu (or main menu) and select Edit Menus.
2. Locate your Skype Entry (By default under the Internet category)
3. Select it and click the properties button. 
4. In the Launcher properties dialogue, select the text skype in the command feild, delete it and click browse,
- Locate your shype.sh file and click open, so that the launcher now shows the directory of your skype.sh file.
5. Click Close once done, and then Close again on the Menu editor. 

Now Run skype, go to your preferences and see if your webcam works, if it does, Enjoy! :guitar:


*Note
If you are using the Dynamic or Static Binary version of skype, your skype.sh will need to contain the full directory of your Skype binary. 


```
#! /bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /location/of/skype
```


However I have not tested this. Good luck! :)

---

### Post by bapoumba on 2010-05-28
T&t :)

---

