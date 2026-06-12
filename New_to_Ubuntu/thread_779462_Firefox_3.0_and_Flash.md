---
title: "Firefox 3.0 and Flash"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by mlanza on 2008-05-02
I recently upgraded to 8.04 which came with Firefox 3.  I am now having an issue with Flash.  It works, however all the pages always fill the flash items with a gray background and a circled, play button.  I think this is coming from the 'swfdec' plugin.  I have installed Adobe's nonfree flash player and I went to "Preferences > Applications" and set the default player to libflashplayer.so (I assume this is Adobe's flash player) but I still keep getting these frustrating gray backgrounds and have to click on them to see the underlying flash.  

I DO NOT WANT THIS.

I realize this is supposed to be a feature, but to me it's a major annoyance.  I cannot seem to figure out how to get it to go back to the way it used to be, where all the items on the page are visible.

Ideas?

---

### Post by Jammerdelray on 2008-05-02
Try going to add/remove programs and removing the swfdec plugin, then reinstall the adobe flash plugin.

---

### Post by aysiu on 2008-05-02
Paste this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get update && sudo apt-get remove swfdec-mozilla flashplugin-nonfree && sudo apt-get install flashplugin-nonfree
```

---

### Post by sergest on 2008-05-02
I had the same problem with Firefox 3.  I installed the free player, but all I got was the big gray play button, and when I clicked on it nothing would happen.  I then tried the Adobe tarball and when I tried "sudo flashplayer-installer" it got to where it asked me for the directory to install to such as /usr/lib/mozilla/plugins, and then gave me the following message:

WARNING: Please enter a valid installation path.

Entering any directory at all resulted in the above message.  Installing it to my local directory without using "sudo" worked, but I still could not get flash to work.

I then tried to use the .rpm file after running "alien" on it.  That installed, but still no joy.

I finally gave up, removed Firefox 3 and reinstalled Firefox 2.  Now everything works like a charm.  I guess I will wait until Firefox 3 is out of beta phase.  My old Sony Vaio is happy.

Now if someone would solve the issue of tiny screen with 800x600 resolution when Ubuntu 8.04 is installed under VirtualBox on my console system that would be great.....

---

### Post by tjwoosta on 2008-05-02
flash works fine for me with firefox3 you just need to uninstall the swfdec player and install the flashplugin-nonfree (you dont have to pay, nonfree just means its not freeware)

---

### Post by Tatty on 2008-05-02
> **tjwoosta said:**
> (you dont have to pay, nonfree just means its not freeware)

Dont mean to be pedantic but i think it actually means its not open source :)

---

### Post by tjwoosta on 2008-05-02
...:p yea thats what i meant to say

---

### Post by mlanza on 2008-05-04
I used the commands provided by aysiu.  That solved most of the issue.  Sidebar on this site not showing up:

[http://www.noobkit.com/show/ruby/ruby/ruby-core.html](http://www.noobkit.com/show/ruby/ruby/ruby-core.html)

Thanks, by the way!

---

