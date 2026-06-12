---
title: "Google Chrome errors"
date: 2015-07-03
forum: New to Ubuntu
---

### Post by jeff131 on 2015-07-03
I installed google chrome with the command```
sudo apt-get install google-chrome-stable
```, and everything was fine. But then, when I ran google chrome from the terminal, with ```
google-chrome-stable
```, it the terminal, a whole bunch of errors occurred. What do they mean? Here they are:
```
[4052:4052:0703/113037:ERROR:url_pattern_set.cc(240)] Invalid url pattern: chrome://print/*
[4052:4052:0703/113037:ERROR:background_mode_manager_aura.cc(14)] Not implemented reached in virtual void BackgroundModeManager::EnableLaunchOnStartup(bool)
[9:9:0703/113039:ERROR:resource_request_policy.cc(57)] Denying load of chrome-extension://apdfllckaahabafndbhieahigkjlhalf/page_embed_script.js from hosted app.
[9:9:0703/113040:ERROR:resource_request_policy.cc(57)] Denying load of chrome-extension://apdfllckaahabafndbhieahigkjlhalf/page_embed_script.js from hosted app.
[4087:4087:0703/153040:ERROR:gles2_cmd_decoder.cc(11539)] [GroupMarkerNotSet(crbug.com/242999)!:D0062B330A050000]GL ERROR :GL_INVALID_OPERATION : glTexStorage2DEXT: <- error from previous GL command
[9:9:0703/113049:ERROR:resource_request_policy.cc(57)] Denying load of chrome-extension://apdfllckaahabafndbhieahigkjlhalf/page_embed_script.js from hosted app.
[4052:4197:0703/113049:ERROR:get_updates_processor.cc(243)] PostClientToServerMessage() failed during GetUpdates
[9:9:0703/113549:ERROR:resource_request_policy.cc(57)] Denying load of chrome-extension://apdfllckaahabafndbhieahigkjlhalf/page_embed_script.js from hosted app.


```

I tried running Chrome multiple times, and all of these errors popped up. They don't seem to be affecting my browsing in there though. I am not sure if this is relevant or not, but my default browser is still Mozilla Firefox.

You can also download a .deb file from the google chrome website, which takes you to ubuntu software center, so both ways are the same.

-Thank you

---

### Post by vasa1 on 2015-07-03
I didn't know Google Chrome could be installed by```
sudo apt-get install google-chrome-stable
```

Is Google Chrome now being offered by the software center?

---

### Post by jeff131 on 2015-07-03
Well, there is a .deb file offered by the google chrome website, which takes you to ubuntu software center, where it was labled as google-chrome-stable. Either way, by graphical, or by terminal, The errors are the same

---

### Post by Geoffrey_Arndt on 2015-07-03
I installed Chrome by downloading the deb file from Google/Chrome site, and then using "gdebi" (a stand-alone deb file install tool) to install it.  (just right clik the deb file).   Note, you may need to go into Synaptic or the USC to install gdebi.

---

### Post by monkeybrain20122 on 2015-07-03
Not sure what you have done. You CANNOT install Chrome with sudo apt-get because Chrome is a third party software and it is not in the repository. As Geoffery_Arndt said download the deb and right click it to install (by default the software centre will come up but gdebi would be much faster. You need to install it first "sudo apt-get install gdebi", then right click a .deb and from properties choose gdebi as the default application to open .deb)

---

### Post by vasa1 on 2015-07-03
Anyway, this is what I see when launching google-chrome-stable from the terminal:```
10:10 PM ~ $ google-chrome-stable
[8943:8943:0703/221102:ERROR:url_pattern_set.cc(240)] Invalid url pattern: chrome://print/*
[9:9:0703/221103:ERROR:resource_request_policy.cc(57)] Denying load of chrome-extension://apdfllckaahabafndbhieahigkjlhalf/page_embed_script.js from hosted app.
[9:9:0703/221103:ERROR:resource_request_policy.cc(57)] Denying load of chrome-extension://apdfllckaahabafndbhieahigkjlhalf/page_embed_script.js from hosted app.
[9:9:0703/221111:ERROR:resource_request_policy.cc(57)] Denying load of chrome-extension://apdfllckaahabafndbhieahigkjlhalf/page_embed_script.js from hosted app.
[8943:9071:0703/221114:ERROR:get_updates_processor.cc(243)] PostClientToServerMessage() failed during GetUpdates
10:11 PM ~ $ 

```Unless something doesn't work, I'd ignore those errors. And I rarely launch GUI programs from the terminal.

---

### Post by PaulW2U on 2015-07-03
> **monkeybrain20122 said:**
> Not sure what you have done. You CANNOT install Chrome with sudo apt-get because Chrome is a third party software and it is not in the repository. 

Actually you can if the Google PPA has already been added to your sources list.

I agree with vasa1, if Chrome works starting normally why bother with errors encountered by starting it from a terminal?

---

### Post by monkeybrain20122 on 2015-07-03
> **PaulW2U said:**
> Actually you can if the Google PPA has already been added to your sources list.


But I think the Google ppa is added when you install the .deb the first time.

---

### Post by PaulW2U on 2015-07-03
> **monkeybrain20122 said:**
> But I think the Google ppa is added when you install the .deb the first time.

Yes and no. See [http://tecadmin.net/install-google-chrome-in-ubuntu/](http://tecadmin.net/install-google-chrome-in-ubuntu/) and numerous other sites.

You can add the PPA first then install Chrome. ;)

---

### Post by Mike_Walsh on 2015-07-04
> **Geoffrey_Arndt said:**
> I installed Chrome by downloading the deb file from Google/Chrome site, and then using "gdebi" (a stand-alone deb file install tool) to install it.  (just right clik the deb file).   Note, you may need to go into Synaptic or the USC to install gdebi.

Agree with this. ^^^

I've always used 'gdebi' for installing one-off .deb files that I trust to install correctly and not mess up my system. It's more efficient, faster, and also handles the necessary dependencies much more effectively.

I always use it install my Epson printer/scanner drivers & software. The Software Centre, on the couple of occasions I've used it for this purpose, seems to hang halfway through installation. It does eventually get there, but it seems to take forever.

There ARE more efficient ways of installing stuff. Once you've used Ubuntu for a little while, you come to realise this..!


Regards,

Mike. :)

---

