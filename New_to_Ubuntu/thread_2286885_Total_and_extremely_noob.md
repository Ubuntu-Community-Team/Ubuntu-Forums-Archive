---
title: "Total and extremely noob"
date: 2015-07-15
forum: New to Ubuntu
---

### Post by tetra82 on 2015-07-15
Hello. I am a windows user (mainly for gaming) since i remember myself. The last couple of years I almost stop playing due to less time and the small gaming I do is on consoles. I always wanted to try Linux. But I am heavily invested in Google's services. 
These are the Google products I use almost every day.

Search, Youtube, Maps, Google Play, Gmail, Calendar and Google Plus are no problem cause I can use them from the browser. And I mainly use them from my Android so... But, What about Drive, Music and photos? I have a sub to Google Drive and Google Music and I use the Drive client to throw stuff in the folder to upload. I also use Play Music and Photos uploader to auto upload any photos and music I have. Are there clients for Linux? I don't care if they are unoficial if they do good job. Also what about Chrome? I know there is Chromium but can I login to it with my Gmail and have my bookmarks/history etc on it?

Thank you for any answer

---

### Post by mastablasta on 2015-07-15
> **tetra82 said:**
>  But, What about Drive, Music and photos?

Drive works (g[rive tools)]("http://askubuntu.com/questions/544646/how-to-install-google-drive-on-ubuntu-14-04"), I don't use the other two. Music manager has some [beta version]("http://sysads.co.uk/2014/08/install-google-play-music-manager-beta-on-ubuntu-14-04/"). I think photos can be uploaded with digikam (there should be a plugin for that)?! Picassa used to have some version that used wine I think.

> 
 Also what about Chrome? I know there is Chromium but can I login to it with my Gmail and have my bookmarks/history etc on it?


Chromium is Chrome without the Google's closed source code and branding. anyway it's compiled from same code or something like that. bookmarks history and such works the same as chrome.

but on the other hand you can just install Chrome if you want to and if you are used to it.

---

### Post by tetra82 on 2015-07-15
Thank you very much for the quick and informative answer. I will install Ubuntu tonight and hopefully I manage to work them

---

### Post by roger_1960 on 2015-07-15
Hi

I use google as much as you I think.

Install chrome from the google website

Note that with the chrome browser installed you can be logged into 2 (or more) google accounts at the same time and very easily switch between them ( not as easy with chromium).  If you just use ione google account, you may as well stick with chromium which is almost identical (but no flash player - but that may be a good thing!)

---

### Post by Ricial on 2015-07-16
As stated from their website ([https://www.thefanclub.co.za/how-to/ubuntu-google-drive-client-grive-and-grive-tools](https://www.thefanclub.co.za/how-to/ubuntu-google-drive-client-grive-and-grive-tools)) GRIVE is no longer supported. Good news is, they created a new one called overGrive ([https://www.thefanclub.co.za/overgrive](https://www.thefanclub.co.za/overgrive)). You can follow the installation instructions that they provided here ([https://www.thefanclub.co.za/overgrive/installation-instructions-ubuntu](https://www.thefanclub.co.za/overgrive/installation-instructions-ubuntu)).

---

### Post by dellboy56 on 2015-07-16
Hi there tetra if ubuntu isn't ur kind of style and it say lags a lot consider getting Linux lite because its much faster more stable it's based on ubuntus LTS and it comes preinstalled with Steam so you don't have to download it or anything also it works really snappy when I used it so if you wanna install Linux lite if ur ubuntu doesn't work for you go to [www.linux](www.linux)
liteos.com :)

---

### Post by yetimon_64 on 2015-07-17
> **roger_1960 said:**
> ...chromium which is almost identical (but no flash player - but that may be a good thing!)

> I know there is Chromium but can I login to it with my Gmail and have my bookmarks/history etc on it?


Or you can install chromium plus the package pepperflashplugin-nonfree for a chromium browser with flash. As mentioned above chromium is the open source aspect of chrome, the pepperflashplugin-nonfree downloads the flash packaging from google and installs only it. Then by having the latest flash version your install should be a bit more secure than with firefox and flash for example. You should be fine using that with any flash content or flash dependent sites.

I log into gmail with firefox usually and it has worked fine, though I never tested any of the google plugins like google-talk with it. I suspect they'll work better with pepperflash in either chrome or chromium than the usual firefox flash version (very old now). 

Regards, yeti.

---

### Post by coffeecat on 2015-07-17
> **yetimon_64 said:**
> Or you can install chromium plus the package pepperflashplugin-nonfree for a chromium browser with flash. As mentioned above chromium is the open source aspect of chrome, the pepperflashplugin-nonfree downloads the flash packaging from google and installs only it. Then by having the latest flash version your install should be a bit more secure than with firefox and flash for example. 

Except that you must remember to update it manually if you want to keep it at the latest. It doesn't happen automatically. This:

```
$ sudo update-pepperflashplugin-nonfree --status
Flash Player version installed on this system  : 18.0.0.204
Flash Player version available on upstream site: 18.0.0.209
```

Tells me that I need to update, and I need to run:

```
sudo update-pepperflashplugin-nonfree --install
```

---

### Post by yetimon_64 on 2015-07-17
> **coffeecat said:**
> Except that you must remember to update it manually if you want to keep it at the latest. It doesn't happen automatically. This:

```
$ sudo update-pepperflashplugin-nonfree --status
Flash Player version installed on this system  : 18.0.0.204
Flash Player version available on upstream site: 18.0.0.209
```

Tells me that I need to update, and I need to run:

```
sudo update-pepperflashplugin-nonfree --install
```

Thanks coffeecat, I wasn't aware of that, I suppose I assumed the package on updates would automatically install.
> Flash Player version installed on this system  : 18.0.0.194
Flash Player version available on upstream site: 18.0.0.209

Good info alright, just checked here and now fully up to date, thank you. Cheers, yeti

---

