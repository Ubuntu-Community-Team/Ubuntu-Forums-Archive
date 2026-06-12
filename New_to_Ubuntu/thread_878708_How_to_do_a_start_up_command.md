---
title: "How to do a start up command"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by Garden Furniture on 2008-08-03
Hello,

I am very new to Linux and have just installed Ubuntu 8.04 LTS (?) onto one of my laptops. The reason for this was due to windows dying all of the time. I must say I like the new setup and it seems to work very well. My laptop has an over temping problem when running at full CPU speed (1.6Ghz) so I use cpufrequtils to set it to the powersave governor which stops it getting too hot (it was dying regularly at 89 degrees!!!) I use the command:

sudo cpufreq-set -g powersave

The thing is, I want it to boot up in powersave mode so I don't have to keep resetting it with the above command - it always boots to the ondemand governor.

I have tried adding that command to the session startup thingy and also to the rc.local file but it still bots into the onedemand governor.

How do I get this command to work automatically?

regards,

---

### Post by ion072002 on 2008-08-03
all you have to do is create a text file, put that comand in it, then, in a console type   > chmod -x Filename.   then, go to system -> preferences -> sessions and insert your now executable file as a startup command. however, i am not sure wether it will work with sudo. you can try your command without sudo too.

---

### Post by WRDN on 2008-08-03
Make a shell script, by creating a new file, then giving it the name "[script].sh" (replace [script] with the name you want). Open the file with a text editor, and give it the contents:

> #! /bin/bash
sudo cpufreq-set -g powersave


Now, right click and select Properties, then click the "Permissions" tab and select "Allow executing file as program".
Now copy the script to the /etc/init.d folder:

```
sudo cp [script].sh /etc/init.d
```

Finally, type:

```
sudo update-rc.d [script].sh defaults 90
```

This will ensure it runs at bootup.

---

### Post by northern lights on 2008-08-03
> **Garden Furniture said:**
> The reason for this was due to windows dying all of the time. I must say I like the new setup and it seems to work very well. My laptop has an over temping problem when running at full CPU speed (1.6Ghz) so I use cpufrequtils to set it to the powersave governor which stops it getting too hot (it was dying regularly at [COLOR="Red"]89[/COLOR] degrees!!!) 
Jesus Murphy!

That's way too much. My laptop CPU reached that 4 years ago when in summer, with 35 degrees centigrade outside and being used on the porch in direct sunlight. Under normal conditions though, this may not happen.

Is your fan screwed, or what?

While I'm happy say 'welcome to Ubuntu' and all, there's "Notebook Hardware Control" for Windows, it's open source (I think) well at least it's free for sure and pretty slick, does the downclocking also.

---

### Post by Garden Furniture on 2008-08-03
Thankyou very much WRDN, unfortunately that didn't work - it still booted up in ondemand mode. Thankyou for your detailed response though as I have now learned how to make a startup script!

regards,

---

### Post by drs305 on 2008-08-03
A couple of points. In the /etc/init.d folder the scripts do not require the "sudo" command. Run the line without it since the script is run as root at boot.

Also, I don't have cpufreq-set on my computer. Depending on it's location, it may be best to type the full path in the script if it is not in the /usr/bin folder - e.g. /path.to.file/cpufreq-set -g powersave

I also don't know much about ondemand - is it a function of cpufreq? Otherwise it may be started and override the cpufreq command, depending on when it's started.

**Added:**
Also to get rid of the links you've created if you want/need to, run this command. It will remove the links in the rcX.d folders. The script in /etc/init.d will remain.
```

update-rc.d -f *scriptname* remove


```

---

