---
title: "BBC iPLAYER"
date: 2012-09-16
forum: New to Ubuntu
---

### Post by CAMEMBEAR on 2012-09-16
Since updating Firefox and Flashplayer, BBC i-player does not work. The window appears, but the timer bar does not appear and there is no sound. Add-ons indicate we have 2 versions of Shockwave installed, although we have disabled one. Using Lucid Lynx. Can anyone help?

Thanks

---

### Post by Zill on 2012-09-17
CAMEMBEAR:  I run a fully updated Ubuntu Lucid Lynx (10.04.4) with Firefox (15.0.1) and the BBC IPlayer works fine.  However, AIUI, IPlayer only works correctly if you live in the UK.  If you are trying to access this from a different country then this could explain the problem.

If you *are* in the UK then it may be that you have a problem with flash - the two versions you see worry me slightly.

I would suggest uninstalling flash completely and then reinstall such that only one version shows on your Firefox "about:plugins" page.  FWIW, my "about:plugins" shows the following:
> Shockwave Flash
    File: libflashplayer.so
    Version: 
    Shockwave Flash 11.2 r202
Depending on whether your PC is 32 or 64 bit there are two recommended methods of installing flash.  See the following documentation for details:
[LIST]
[*][https://help.ubuntu.com/community/RestrictedFormats/Flash]("https://help.ubuntu.com/community/RestrictedFormats/Flash")
[/LIST]
Personally, as I prefer 32-bit, I just install ubuntu-restricted-extras and flash "just works". :-)

When I run the test at [http://www.adobe.com/software/flash/about/]("http://www.adobe.com/software/flash/about/") I get the following result:
> You have version 11,2,202,238 installed

It would also be useful to know if you have problems with any other flash-related websites. eg. [http:/www.youtube.com/]("http://www.youtube.com/")

---

### Post by CAMEMBEAR on 2012-09-17
Have removed both versions of flash and reinstalled via synaptic still no joy. Problem also with internet radio not just BBC. I am in the UK the installed version of flash is 11.02.202.238

---

### Post by Zill on 2012-09-17
CAMEMBEAR:
[LIST=1]
[*]Are you running 32 or 64 bit Ubuntu?
[*]How did you install flash?
[*]Do you see a flash graphic when you run the test at [http://www.adobe.com/software/flash/about/]("http://www.adobe.com/software/flash/about/")?
[*]Can you run videos correctly from  [http://www.youtube.com/]("http://www.youtube.com/")?
[*]Do you now only have one version of flash visible with Firefox "about:plugins" page?
[/LIST]

---

### Post by CAMEMBEAR on 2012-09-19
1 I am Running 32 BIT
2 Flash was Installed via synaptic
3 The Adobe test page does nothing it sees neither OS or version of flash      
4 No videos from you tube
5 Only one version of flash visible shockwave flash 11.2 r202

---

### Post by Zill on 2012-09-19
CAMEMBEAR:  You could give the Firefox add-on [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") a try.
> Remove conflicting flash plugins from Ubuntu/Debian Linux systems, install the appropriate version according to system architecture and apply some tweaks to improve performance and fix common issues.

---

### Post by bryncoles on 2012-09-19
Hi CAMEMBEAR.  

A broad number of people I know ran into this issue.  The problem is the new flash player.  The solution (as found [here](http://tulsawebresults.com/solution-flash-player-broken-in-firefox-unbutu-12-04-precise-pangolin) is to fully remove **all** traces of the flash player from your system and install an older version.  

Get an old flash player from [here](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html).  I recommend Flash Player 10.3.183.25.  

extract the archive to the desktop and follow the instructions in the above link.  Don't use su to get into admin mode, use sudo to get root privileges for each command instead.  

So, you'll do:
```
cd /home/yourusername/Desktop/install_flash_player_11_linux.x86_64
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
sudo cp -r usr/* /usr
```

Try the commands one at a time, and if you're unsure about anything, ask before doing!

Good luck

---

### Post by mips on 2012-09-20
What happens if you try using Chromium browser?

---

### Post by CAMEMBEAR on 2012-09-24
Have downloaded as advised and now have the following on my desktop: a zip file called fp_10.3.183.23_archive.zip and a folder called: fp_10.3.183.23_archive.

Have tried the first line as you advise: 
cd /home/yourusername/Desktop/install_flash_player_11_linux.x86_64, but putting my username in and using "fp_10.3.183.23" instead of flash_player_11 .....". I got the following message at one point:

ron@ron-desktop:~$ cd: /home/ron/Desktop/install_fp_10.3.183.23_linux.x86_64
No command 'cd:' found, did you mean:
 Command 'cda' from package 'xmcd' (universe)
 Command 'cdb' from package 'tinycdb' (main)
 Command 'cdo' from package 'cdo' (universe)
 Command 'cdv' from package 'codeville' (universe)
 Command 'cdw' from package 'cdw' (universe)
 Command 'cd5' from package 'cd5' (universe)
 Command 'cdp' from package 'irpas' (multiverse)
cd:: command not found
 
What do I do now?

---

### Post by CAMEMBEAR on 2012-09-24
Sorry, forgot to add that I tried Flash-Aid, but got the following message "unable to execute child process".

---

### Post by aka-John99 on 2012-10-06
Note many of the Firefox problems with Flash Player relate to WINDOWS and use of Adobe's  *protected mode. *Flash 10.3 does not use protected mode, but it is possible to disable protected mode in later Flash versions.  See [http://kb.mozillazine.org/Flash#Flash_Player_11.3_Protected_Mode_-_Windows](http://kb.mozillazine.org/Flash#Flash_Player_11.3_Protected_Mode_-_Windows)

As I said many of these problems relate to Windows not Linux/Ubuntu. 

[B]BBC iPlayer
[/B]AFAIK live streams and the Embeded Media Players on for instance the News site, and the sites outside the UK use Flash Player, but the installed iPlayer used to play downloads also needs Adobe AIR. [http://iplayerhelp.external.bbc.co.uk/help/downloading/desktop_problems](http://iplayerhelp.external.bbc.co.uk/help/downloading/desktop_problems)

---

