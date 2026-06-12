---
title: "dropbox"
date: 2014-06-19
forum: New to Ubuntu
---

### Post by vegas89 on 2014-06-19
My dropbox icon just flashes in the launcher and will not open, It had been working fine, don't know what has happened. Any suggestions will help.:confused::confused::confused:

---

### Post by Jack_Ryan on 2014-06-19
Has it been updated recently and also are you on Ubuntu, Lubuntu, Xubuntu? 14.04? 
Did you try checking it out in the terminal?

---

### Post by vegas89 on 2014-06-19
I am useing ubuntu 12.04 and what do you mean checking it out in the terminal

---

### Post by deadflowr on 2014-06-20
Do you have an indicator for dropbox in the top panel?

---

### Post by vegas89 on 2014-06-20
I did have one there and it worked just fine. I used it for months to add to my dropbox account or I could click from the launch panel to open up dropbox. Now the icon is gone from the top and the icon on the launcher just flashes when I click on it and dropbox will not open.

---

### Post by nerdtron on 2014-06-20
Try running dropbox from the terminal. Just type dropbox and hit enter. If it fails to launch, it will throw off some logs on you terminal.

Have you tried uninstall and reinstalling dropbox?

---

### Post by JeQhdMD on 2014-06-20
Have you checked your setting at the Dropbox site . . . ?  Does everything look normal - check all 3 tabs especially security.   Have you changed anything on your system especially Nautilus or startup programs?

---

### Post by vegas89 on 2014-06-21
Thanks for the help! I uninstalled dropbox then reinstalled it but it still acts as I described before. I have dropbox checked on the startup application box. I cant get dropbox to come up to check anything else. I have made no changes to anything else. any more suggestions? ](*,)

---

### Post by sandyd on 2014-06-21
Try uninstalling and emptying the ~/.dropbox folder as well

---

### Post by bapoumba on 2014-06-21
If you open a terminal and enter **dropbox start**, what does it return ?

---

### Post by vegas89 on 2014-06-23
I opened up the terminal and typed dropbox start. It directed me to [https://www.dropbox.com/cli_link?host_id=b5bfdf14b4595cac76f47e8fee584af5](https://www.dropbox.com/cli_link?host_id=b5bfdf14b4595cac76f47e8fee584af5). When I went there to link my desktop with the site it said my desked top was already linked with the dropbox site. My andriod phone links to the site with no problems and I am able to view my saved information. I just cant get my desktop to open the dropbox icon. There used to be an icon in my top panel on my screen which I could click on to open my folders, but it is no longer there. When I click on the launcher icon it just blinks off and on and does nothing.](*,)](*,)

---

### Post by buzzingrobot on 2014-06-23
Can you open and  browse the Dropbox folder in Nautilus? If so, add something to Dropbox with your phone.  Then, see if it eventually becomes visible in Nautilus.  If so, that will tell you the Dropbox software on the machine is working and correctly synching with server. That narrows the focus to why the blue panel icon doesn't open the local folder.  Have you tried right-clicking on it and examining the settings?

In Startup Applications, the Dropbox command should be "/home/<YourHomeDirectory>/.dropbox/dropboxd".

---

### Post by vegas89 on 2014-06-24
Thank you Buzzingrobot!!! I copyed and pasted the start up comand you suggested in my system settings, then restarted the desktop and whammy, the icon was back on my upper control panel. A click and my folders are on the screen:grin:):P

---

