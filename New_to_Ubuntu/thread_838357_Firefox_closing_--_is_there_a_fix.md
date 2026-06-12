---
title: "Firefox closing -- is there a fix?"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by JimmyJim on 2008-06-23
When loading any flash-based page, such as Youtube, Firefox (version 3.0) often closes without prompt. I understand that this is a common bug, but is there any fix that I could use? I didn't find anything.


As you can imagine, its been driving me nuts ](*,). Thanks for any help.

---

### Post by Nikitas350 on 2008-06-23
Did you installed flash player without errors?

---

### Post by JimmyJim on 2008-06-23
> **Nikitas350 said:**
> Did you installed flash player without errors?

Yep, there weren't any errors from when I installed it. I should also mention that I tried reinstalling it -- and I'm still getting the same FF closing problem.

---

### Post by Nikitas350 on 2008-06-23
And your proseccor is amd64?

---

### Post by cubeist on 2008-06-23
I don't have a direct solution, but an alternative browser is Opera... works well on amd64 with flash...

---

### Post by JimmyJim on 2008-06-23
> **Nikitas350 said:**
> And your proseccor is amd64?

Yes. I'm using Hardy 32-bit though.

---

### Post by waspbr on 2008-06-23
the problem also affects 32 bit processors. Swiftweasel still runs on the firefox 2 platform so that's an option. Also I watch youtube videos on songbird.

---

### Post by nightwolf2k5 on 2008-06-23
your firefox files seems to have been corrupted..
goto places -> home folder
then press cntrl h, this will show all hidden files
Open the mozilla folder, then go into firefox.
u will see a xxxxx.default and profiles.ini folder and file respectively..
delete them..
p.s. Make sure u backup your bookmarks before u do this..

---

### Post by ibizatunes on 2008-06-23
I know this may sound stupid, but have u ran the update manager, i had the same problem till firefox 3 was release as a full version!

---

### Post by nightwolf2k5 on 2008-06-23
i had the same problem.. with firefox 3.. after the update.. deleting that folder and file sorted it all out..
works smooth now.. :)

---

### Post by silkstone on 2008-06-23
I think I may have fixed it, but it's too soon to be sure. First I followed the guide by reassuringlyoffensive which is posted here...

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

> UBUNTU FAMILY 8.04 HARDY HERON USERS ONLY

Note: You can safely install the Ubuntu package (flashplugin-nonfree) over the top of this manual installation method at a later date, I've tested it several times. The method used below will install the plugin into the same directory the Ubuntu package does, with the same symlinks and can be overwritten cleanly.

Install the Flash plugin manually by downloading the tar archive of Adobe Flash v10 beta. Simply open the tar archive, then find the file named "libflashplayer.so" and place it on your desktop. Next, execute this command in the terminal:

32-Bit Ubuntu Family Users Only:

sudo apt-get purge flashplugin-nonfree && sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so

You may now restart Firefox and use the plugin.

Then I deleted **libflashsupport** from Synaptic, and also deleted **pluginreg.dat** which is in .mozilla/firefox/xxxxx/ (this is recreated automatically when Firefox restarts).

I've now played several flash videos in succession without a problem, but the jury is still out!

---

### Post by S1xp4ck on 2008-06-23
> **silkstone said:**
> I think I may have fixed it, but it's too soon to be sure. First I followed the guide by reassuringlyoffensive which is posted here...

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)



Then I deleted **libflashsupport** from Synaptic, and also deleted **pluginreg.dat** which is in .mozilla/firefox/xxxxx/ (this is recreated automatically when Firefox restarts).

I've now played several flash videos in succession without a problem, but the jury is still out!


I am trying this as wel... so far so good.

---

### Post by onero on 2008-06-23
> **JimmyJim said:**
> When loading any flash-based page, such as Youtube, Firefox (version 3.0) often closes without prompt. I understand that this is a common bug, but is there any fix that I could use? I didn't find anything.


As you can imagine, its been driving me nuts ](*,). Thanks for any help.

Yeah, I used to have this problem too. Following [this]("http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio") tutorial solved it though! Just do parts A & B.

---

### Post by silkstone on 2008-06-23
Part B of that tutorial seems to do the same as the procedure in my post above - it installs the Flashplayer 10 plugin and removes libflashsupport - although by a different method. I'll hold off trying Part A for now, since at the moment everything appears to be working. (Fingers and everything else crossed! :) )

---

### Post by silkstone on 2008-06-23
FF3 has not closed unexpectedly for me when playing Flash video since doing what I suggested in post #11 above.

I would be pleased to hear from anyone else who has tried this - it does seem to work.

---

