---
title: "Clevo w740su"
date: 2015-03-05
forum: New to Ubuntu
---

### Post by Dino_Jakolis on 2015-03-05
Hello everyone, 

I'm glad I finally switched to Ubuntu after years of Windows experience. I have successfully installed Ubuntu 14.04 LTS 64-bit. Hooray for me! Hehe

Alright. I would like to ask previous owners of Clevo W740SU or anyone else who knows how to set it up correctly to work with Ubuntu and stay rock stable. You know, drivers, tweaks, etc. 

What I have done so far:
1) Installed Ubuntu
2) Ran Update and installed Synaptics
3) Removed Firefox, Thunderbird and installed Google Chrome (because of synchronization)
4) Ran System Testing and got some results. Everything is good except **microphone**. There is low sound and distortion. Got a text file (results) saved I believe.

That is it. I hope you could point me in good direction on how to set it up correctly to be a stable OS. 

If I forgot something, feel free to correct me!

---

### Post by sudodus on 2015-03-05
Welcome to the Ubuntu Forums :-)[I][B]

Backup[/B][/I]! Tough guys never backup their data. They do the job twice instead ;-)

Microphone: have you tried to use ***pavucontrol*** to tweak all the settings relevant for it?

---

### Post by Dino_Jakolis on 2015-03-05
I'm making a backup as I'm writing this. Thanks for the note! I'll remember it. :)

I haven't tried ***pavucontrol***. Let me see what that gives me.

Edit: Played with the settings and microphone is still low along with distortions. Shall I update drivers?

---

### Post by JeQhdMD on 2015-03-05
Since your Clevo w740su is the same Laptop as the "Galago UltraPro" by System76, you might want to check out the System76 subforum on this forum.  Also, there is a link on their home page to adding the PPA (personal package archive) for the System76 drivers.   Might as well see if that's something that would help.    I'll have to try the microphone at my end and see how it works with the drivers installed.

One positive aspect of getting the laptop from System76 is the support - - excellent for me so far, and good for the life of the product.

Also . . see this site re "Tweaking an Ubuntu install" . . . [http://itsfoss.com/things-to-do-after-installing-ubuntu-14-04/](http://itsfoss.com/things-to-do-after-installing-ubuntu-14-04/)

---

### Post by Dino_Jakolis on 2015-03-06
I appreciate the input!

Will drivers for Galago UltraPro work right away for me? I see that it is the same laptop, but maybe something else was changed in description. Just to be on the safe side. 

Also, is it safe to add all these updates since I've read that if I don't know what it is, it is better to stay away from updating so that system stays stable. Again, just to be on the safe side.

Edit #1: I just ran commands to download System76 drivers. After installing and restarting, WiFi is extremely slow and signal is weak as opposed to full strength before update.

Edit #2: BT doesn't want to pair with my Logitech Bluetooth adapter anymore.

Edit #3: Uploading a [screenshot]("http://i62.tinypic.com/2uf3lao.png") of System76 app. Wrong laptop.

Edit #4: Had a black non-responsive screen after resuming from suspend mode. Had to hard reset it using button. Hm...

---

### Post by sudodus on 2015-03-06
I'm glad you made a backup before installing the System76 drivers :-) Obviously something is different.

---

### Post by Dino_Jakolis on 2015-03-06
I did, but I'm not sure if that restored everything in my laptop. 

Where can I download newest drivers for RTL8723AE and how to install them?

I'm looking at Github website, but have no idea what to input to have driver installed.

---

### Post by sudodus on 2015-03-06
I have not much experience of finding and installing linux drivers. Let us hope someone else chip in and help :-)

If no luck here within a day and night, I suggest that you create a new thread in the [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") Forum about RTL8723AE.

-o-

I quick internet search for ***RTL8723AE linux*** gave me for example this link [http://zach-adams.com/2014/06/fixing-rtl8723ae-driver-ubuntu-linux/](http://zach-adams.com/2014/06/fixing-rtl8723ae-driver-ubuntu-linux/)

---

### Post by JeQhdMD on 2015-03-06
Dino,

Do you know if any modifications were made to the hardware listed by Clevo for your model?  Who was your reseller or systems integrator?

See specs here:  [http://www.clevo.com.tw/clevo_prodetail.asp?id=639&lang=en](http://www.clevo.com.tw/clevo_prodetail.asp?id=639&lang=en)

For US support:

[COLOR=#0065B9][FONT=verdana]**U.S.A. Contract Service Center **[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]ADD: 663 Brea Canyon Rd, #7, Walnut, CA 91789, USA [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]TEL: +1-909-598-2263[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]FAX: +1-909-598-0015[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]E-mail: [/FONT][/COLOR][EMAIL="support@goldenstarusa.com"]support@goldenstarusa.com[/EMAIL]

List of other support centers:  [http://www.clevo.com.tw/clevo_contact.asp?lang=en](http://www.clevo.com.tw/clevo_contact.asp?lang=en)

Can you list your laptops specific specs (especially wireless).

Anyway, I wish I would have seen your post about doing the install of drivers, as there are ways to test the drivers without installing them.

At this point, if you also installed all the recommended standard post-install tweaks . . . in my opinion, *the safest course to restore the system is a clean re-install* (IF you're comfortable and know how to do that . . . did you install Ubuntu yourself?)   A final point, I know the System76 computers do not have UEFI-GPT firmware . . . they use a standard BIOS which is extremely easy to work with and modify.   Is this the case for your specific laptop?

---

### Post by Dino_Jakolis on 2015-03-07
Hello, 

I got it on eBay. Is there a program that could save my hardware info in a text file?

In the end, I did complete re-install by myself. Steps I took after it:
1) Ran Update and let it finish.
2) WiFi & BT starting making problems after update. Installed newest RTL8273AE drivers from Github. Both work flawlessly now.
3) Installed Intel Graphics Installer for Linux and installed the driver.
4) Touchpad stopped working so I installed it through Synaptic: xserver-xorg-input-synaptics.

Everything works so far except microphone. Low noise and distortion. It was working perfectly on Windows 8.1 As for the BIOS, yes, I have it. Everything seems to be good there.

---

### Post by sudodus on 2015-03-07
You can run ***lshw***, a command line tool, and redirect the output to a text file. Then you can cut and paste the text into a reply and surround it with [noparse]```
tags
```[/noparse]

```
sudo -s
lshw -sanitize > lshw-clevo.txt
exit   # from the superuser
```

---

### Post by JeQhdMD on 2015-03-07
Impressive work!   Especially for a new Ubuntu user.   I've installed rtl drivers including from source code, and it can be challenging (plus - - may need re-installs after kernel updates) . . so keep those drivers handy.

Here is a thread about the internal mic. on a system "similar" to your Clevo . . . . see the second to last post in the thread for add'l ideas.   It seems one user was able to install (using Chrome browser) the Google Hangouts extension.   Apparently, that fixed the mic. problem (using a safe, unobtrusive process).

Here's the Link:  [http://ubuntuforums.org/showthread.php?t=2170623&page=2&highlight=galago+microphone](http://ubuntuforums.org/showthread.php?t=2170623&page=2&highlight=galago+microphone)

---

### Post by Dino_Jakolis on 2015-03-07
Thank you very much! Google is my 'best' friend.

I will check that link about internal mic and see what it is. 

As for the ***lshw*** command, I'm attaching the .txt file. (thanks for the ***-sanitize*** command)

Edit #1: There are some freezes here and there. For example, when working with Workspace Switcher as well as when reloading some website with huge content such as Facebook. I have to CTRL+ALT+F1 to reboot system. Is this issues driver related?

Edit #2: Alright, I've fixed Skype microphone sound. I have yet to see how Workspace Switcher works...

---

