---
title: "Firefox: Can't remove Shockwave Flash Plugin 16.0.0.235 pepperflash"
date: 2015-03-13
forum: New to Ubuntu
---

### Post by benawhile on 2015-03-13
I have been having lots of crashes, script errors and problems with Flash recently.
 

 In Firefox in my add-ons list I now have two Shockwave Flash plugin versions, 11.2.202.451 and 16.0.0.235. I can't remember how this happened. I know that 16.0.0.235 is pepperflash and used when Firefox runs in Wine, the windows emulator. I don't use Wine and don't need it. Furthermore, I cannot activate version 11 without v16 activating too, and I think v16 is causing the crashes, as the message I get , “pluginloader.exe encountered a serious problem and needs to close” is Windows related.
 

 I want to remove v16 or permanently stop it activating.
 I cannot see it anywhere else on the system except in the Firefox browser.
 It's not in the /usr/lib/mozilla/plugins folder. Nearest thing to it is a file called pipelight-flash.so which I though was related to pepperflash.

There is supposed to be a wrapper package, freshplayerplugin, but i can't find that either.

There is a clue to how to do it here: (but it doesn't make any sense. )

[https://support.mozilla.org/en-US/questions/1024170?page=2](https://support.mozilla.org/en-US/questions/1024170?page=2)

The poster, christ1,  says to follow installation instructions " in reverse order". How can you do that?

---

### Post by Frogs Hair on 2015-03-14
I use pepperflash for Opera but it doesn't appear in the Firefox plugins section ?? To remove it use the following command. ```
sudo apt-get remove pepperflashplugin-nonfree 
```  Report back if the entry remains in FF plugins after restarting the browser.

---

### Post by monkeybrain20122 on 2015-03-14
> **benawhile said:**
> I have been having lots of crashes, script errors and problems with Flash recently.
 

 In Firefox in my add-ons list I now have two Shockwave Flash plugin versions, 11.2.202.451 and 16.0.0.235. I can't remember how this happened. I know that 16.0.0.235 is pepperflash and used when Firefox runs in Wine, the windows emulator. I don't use Wine and don't need it. Furthermore, I cannot activate version 11 without v16 activating too, and I think v16 is causing the crashes, as the message I get , &#8220;pluginloader.exe encountered a serious problem and needs to close&#8221; is Windows related.
 

 

There are two ways you could have installed flash 16 in Firefox, either with pipelight or the freshplayerugin which is a wrapper for pepper flash in chrome. Since you mentioned Wine it sounds like the former (so it is not pepper flash!)

To stop using it close Firefox and run

```
pipelight-plugin --disable flash
```

Then start Firefox it should be gone

(if you have enabled flash with sudo then also prepend the above command with sudo for disabling)


Edited: If it is pepper flash then it is the freshplayerpluin. If you installed it form the webupd8 ppa, just remove it from the system using your favourite package manager or 
```
sudo apt-get remove freshplayerplugin
``` 

If you have compiled it yourself remove libfreshwrapper-pepperflash.so from ~/.mozilla/plugins.Hopefully covered all the grounds

---

### Post by benawhile on 2015-03-15
Thank you
I got a lot of help from my earlier post
[http://ubuntuforums.org/showthread.php?t=2268934](http://ubuntuforums.org/showthread.php?t=2268934) 
and finally solved it. I had to download synaptic package manager, which found pipelight and uninstalled it. 

Using terminal and 
"sudo apt-get remove pepperflashplugin-nonfree"

only returned that pepperflash, and also pipelight when I tried to remove that, wasn't on the system.

pepperflash (As shockwave flash v16..0.0.235 ) has finally disappeared from my Plugins list.
Lots of google searches reveals that a few others have had very similar problems.

---

### Post by monkeybrain20122 on 2015-03-15
You didn't have to remove pipelight. Just disable flash would be sufficient.

---

### Post by benawhile on 2015-03-16
OK, and thanks for the tip about disabling in terminal, all information useful

---

