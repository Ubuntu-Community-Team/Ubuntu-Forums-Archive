---
title: "Firefox Update"
date: 2013-09-23
forum: New to Ubuntu
---

### Post by czgirb on 2013-09-23
[SIZE=2]Today, when I check my Firefox's add-ons manager > plugins it said that my **Shockwave Flash 11.2 r202** are **Vulnerable**. So I click the **Update Now** button.[/SIZE]
And it leads me to [http://get.adobe.com/flashplayer/?promoid=JZEFT](http://get.adobe.com/flashplayer/?promoid=JZEFT) (according to the [http://support.mozilla.org/en-US/kb/keep-flash-up-to-date-and-troubleshoot-problems](http://support.mozilla.org/en-US/kb/keep-flash-up-to-date-and-troubleshoot-problems)), I required to choose the **tar.gz** ... is this RIGHTor NOT?
If **RIGHT**, after I restart the machine > launch the Firefox > re-check the plugins ... it still said that [SIZE=2]my **Shockwave Flash 11.2 r202** is **Vulnerable**[/SIZE] and required to **Update**.
Please advice ... thank you

---

### Post by deadflowr on 2013-09-23
AFAIK it's a mozilla/firefox site problem/bug.
For some reason, if the version you have isn't the latest, which you would get with windows/mac/google-chrome, then it reports that it is out of date.
Just keep your system up to date and the flash plugin should be as well.

---

### Post by czgirb on 2013-09-23
SORRY ... currently I used **Ubuntu 12.04 LTS**.

---

### Post by deadflowr on 2013-09-23
The version of Ubuntu doesn't matter in this case, as flash is the same on all versions.

---

### Post by czgirb on 2013-09-23
Oooohh! But it has been installed yesterday.
 Now, what should I do?

---

### Post by deadflowr on 2013-09-23
Do you mean you installed 12.04 yesterday?
Then see if you have any updates available in the update manager, and if so update them.
(If it says a new version of Ubuntu is available at the top, you can ignore that)

As far as running flash above 11.2, you would need to install google-chrome, or add a ppa that will add the chrome used pepperflash plugin, but that only works for chromium.
[http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html](http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html)

Other than that, there's not much you can do, as adobe stopped building flash for linux(except for google's pepperflash plugin), and will only offer support for version 11.2 (and maybe older versions) for linux.

---

### Post by czgirb on 2013-09-23
[SIZE=2]I installed the update yesterday ...
1. click the **Update Now** button >[/SIZE]
2. it leads me to [http://get.adobe.com/flashplayer/?promoid=JZEFT](http://get.adobe.com/flashplayer/?promoid=JZEFT)
3. according to the [http://support.mozilla.org/en-US/kb/...shoot-problems]("http://support.mozilla.org/en-US/kb/keep-flash-up-to-date-and-troubleshoot-problems"), I should choose the **tar.gz** file and download it.
4. extract it, and copied it to /usr/lib/mozilla/plugins folder

---

### Post by Impavidus on 2013-09-23
The latest Flash version available for Linux is 11.2.202.310. This version is outdated (latest is something like 11.8 or so), but Adobe doesn't support Flash any longer on Linux, except for security updates. These affect the right-most version numbers. The plugin check will always complain it's outdated.

There's no need to go to adobe.com to download a new flash player. The package **flashplugin-installer** from the Ubuntu repository installs the flash player automatically and keeps you updated as far as still possible. Just install the regular Ubuntu updates and your flash will be updated too.

---

### Post by czgirb on 2013-09-24
[COLOR=#000000]Thank you for all advice given
  But I had already download the **tar.gz** file, **download**, **extract** and **copied** to [/COLOR]**/usr/lib/mozilla/plugins **folder.
Now, how can I delete the** .iso** file?

---

### Post by Impavidus on 2013-09-24
You never mentioned a .iso file.

You can delete any files that you installed manually. Just make sure **flashplugin-installer** is installed. You can install it with **sudo apt-get install flashplugin-installer** or, if you lready had it and overwrote it in your attempt to install te latest version, reinstall it with **sudo apt-get --reinstall install flashplugin-installer**. Shouldn't really be necessary as you replaced the latest version from one source with the latest version from another source, but flashplugin-installer doesn't directly store the plugin in /usr/lib/mozilla/plugins, but via a few symlinks. So I'm not sure it will be automatically overwritten a the next update.

---

### Post by czgirb on 2013-09-24
within my **/usr/lib/mozilla/plugins**, there is:
[B]
* flashplugin-alternative.so[/B]
*** libflashplayer.so**
*** libjavaplugin.so**
*** libnpjp2.so**
*** libtotem-cone-plugin.so**
*** libtotem-gmp-plugin.so**
*** libtotem-mully-plugin.so**
*** libtotem-narrowspace-plugin.so**

Please tell me which one to delete? Is it the **libflashplayer.so** as the [http://support.mozilla.org/en-US/kb/keep-flash-up-to-date-and-troubleshoot-problems](http://support.mozilla.org/en-US/kb/keep-flash-up-to-date-and-troubleshoot-problems) guidance?
If YES ... would you mind to tell me how to delete it?
 Cos I used ... click **File System > usr/lib/mozilla/plugins** and choose the file and delete it ... nothing happen.

---

### Post by Impavidus on 2013-09-24
My /usr/lib/mozilla/plugins contains flashplugin-alternative.so, but not libflashplayer.so. My flash plugin works, so I think you can remove the libflashplayer.so. To do so, use the file manager with root permissions (**gksu nautilus**) or use the terminal (**sudo rm /usr/lib/mozilla/plugins/libflashplayer.so**).

---

### Post by johnlittler on 2013-09-25
In reply to your original concern about the outdated flash plugin version, In brief there is no need to worry about that for two reasons.

Reason 1
You are unlikely to find any video on the internet which specifically requires a more recent version of the flash plugin. 

Reason 2
Year by year the number of websites using flash is declining. It is the Adobe company who will have to live without flash and not you.

If you are using Firefox 24 or above,  you can make a few changes to your Linux system and Firefox to enable you to watch in html5 ( H-264, mp3-aac ) without any plugin all the videos on Youtube ( which have been uploaded within the last two years) without entering the html5 trial and other sites like dailymotion.com.
 see
[http://www.ghacks.net/2013/06/23/firefox-24-for-linux-gets-native-mp3-aac-and-h-264-support/](http://www.ghacks.net/2013/06/23/firefox-24-for-linux-gets-native-mp3-aac-and-h-264-support/)

If you are interested, these are the steps to follow:

1. Type about:config into the  firefox browser's address bar and hit enter.
    2. Confirm that you will be careful if this is your first time.
    3. Search for    media.gstreamer.enabled
    4. Make sure it is set to to true (which means enabled).
5. You need to install gstreamer: `libgstreamer0.10-dev` and `libgstreamer-plugins-base0.10-dev`

 

In the Ubuntu terminal ( open with ctrl + alt + t ) type these lines separately. Press enter after each line of code.

$ sudo apt-get install libgstreamer0.10-dev

$ sudo apt-get install bgstreamer-plugins-base0.10-dev

sudo add-apt-repository ppa:gstreamer-developers/ppa
sudo apt-get update
sudo apt-get install gstreamer1.0*

6. Install the following Firefox extension (to view Youtube videos)

[https://addons.mozilla.org/ja/firefox/addon/youtube-all-html5/?src=api](https://addons.mozilla.org/ja/firefox/addon/youtube-all-html5/?src=api)

7. Deactivate the flash plugin. There is no need to remove it. Just deactivate it. ''Add-ons &#8594;Plugins&#8594;ShockwaveFlash&#8594;Never activate

8. Restart Firefox. It is unlikely that you will need to restart your computer, but if these steps do not work restart.

9. Now test it with the flash plugin deactivated.

From Firefox 24, you can view Youtube without flash without joining the HTML5 trial.

Test it  on non-Youtube tube videos such as Dailymotion.com and this test video.

[http://mirrorblender.top-ix.org/movies/sintel-1024-surround.mp4](http://mirrorblender.top-ix.org/movies/sintel-1024-surround.mp4)

10. You may need to reactivate flash for other sites. To do that easily, install this Fiorefox extension:

[https://addons.mozilla.org/en-US/firefox/addon/flash-onoff/](https://addons.mozilla.org/en-US/firefox/addon/flash-onoff/)

An icon can be dragged from Menu Bar&#8594;View&#8594; Toobars&#8594;Customize to a toolbar and clicking it can turn flsh on and off.

---

### Post by kostkon on 2013-09-25
Ignore what Firefox says, don't trust it. Your plugin IS safe. Adobe continues to support the 11.2.x Flash with security updates and these updates always end up in Ubuntu after 1-2 days. You don't need to worry about it and you CAN'T install a newer version of Flash in Firefox (in Linux), you just can't.

If you want to have the latest Flash, then use Chrome.

Hope that helps.

---

