---
title: "[SOLVED] How to install firefox 3.0.1?"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by diwas on 2008-08-06
I have downloaded firefox 3.0.1 from their website. But i dont know how to install it...here are the list of files after extracting.
```

diwas@diwas-desktop:~/Desktop/firefox$ dir
application.ini             
libfreebl3.so    
libxul.so
blocklist.xml               
libjemalloc.so   
modules
browserconfig.properties    
libmozjs.so      
mozilla-xremote-client
chrome                      
libnspr4.so      
old-homepage-default.properties
components                  
libnss3.so       
platform.ini
crashreporter              
 libnssckbi.so   
 plugins
crashreporter.ini          
 libnssdbm3.so   
 README.txt
crashreporter-override.ini 
 libnssutil3.so   
removed-files
defaults                   
 libplc4.so      
 res
dictionaries               
 libplds4.so      
run-mozilla.sh
extensions                  
libsmime3.so     
searchplugins
firefox                     
libsoftokn3.chk  
Throbber-small.gif
firefox-bin                
 libsoftokn3.so 
  updater
greprefs                   
 libsqlite3.so   
 updater.ini
icons                      
 libssl3.so
libfreebl3.chk             
 libxpcom.so

```


What do i have to do in order to install it??? 
Thank you.

---

### Post by AliL on 2008-08-06
The best thing to do is not to download it from their website, but install it from the ubuntu repositories. You need to go to the programs menu, then add/remove programs, and type in firefox on the search bar after you've done all the password verification thing.

That way, you can get automatically updated to the newest version when it gets updated in the repositories (in my experience that's about 2 days after it's been released on mozilla's site).

Hope this helps,

AliL

---

### Post by mevets on 2008-08-06
You should have Firefox 3.0.1 if you're running hardy and have installed all your updates. Are you using an older version of ubuntu? If you run the 'firefox' file in that directory it will run, just not installed.

---

### Post by DJ_Peng on 2008-08-06
Actually you don't need to install it. Just extract it someplace handy (I simply extract it into my [FONT=Courier New]/home[/FONT] folder) and run [FONT=Courier New]firefox[/FONT] within that directory. You can even make a launcher for your desktop or existing launchers to your new installation. You will also need to get the plugins into the [FONT=Courier New]/firefox/plugins[/FONT] folder so Firefox can use them, but that's just a little tedious, not a major pain in the rear.

> **AliL said:**
> The best thing to do is not to download it from their website, but install it from the ubuntu repositories. You need to go to the programs menu, then add/remove programs, and type in firefox on the search bar after you've done all the password verification thing.

That way, you can get automatically updated to the newest version when it gets updated in the repositories (in my experience that's about 2 days after it's been released on mozilla's site).

I have to disagree with you, AliL. Yes, it's easier to use Ubuntu's Firefox, but it also has enough changes from the Mozilla Firefox (autoupdates, possibly some hassle using add-ons not blessed and put into the Ubuntu repos) that I dispute the fact that what Ubuntu has is in fact *Firefox*. It's based on Firefox, and is dammned close, but it isn't the same thing that Mozilla puts out, and people coming from other OSes can get confused by the differences.

I have checked out the Ubuntu-fied Firefox, and I always go back to Mozilla's Firefox. There are just enough differences that I prefer the real deal over Ubuntu's. Other people shouldn't be minimized just because they want to use Mozilla's code. (Not that you're belittling the OP, just making a comment.)

---

### Post by billgoldberg on 2008-08-06
Do you use Ubuntu 8.04 "Hardy Heron"?

Update your system and you are using Firefox 3.0.1

---

### Post by diwas on 2008-08-07
Yes, i can install it through synaptic no problem...but i wanted to know how to install this type of package. Now i know that xtracting will do the work. But smthg's messed up here.

Actually i upgraded firefox from synaptic. It went fine. But now when i click the launcher icon (the default one in the top GNOME panel of ubuntu 8.04) firefox executes but the "back", "forward", "refresh" and "stop" buttons on the top are faded. Also i dont remember wat used to be below those and above the "tabs"...it has also disappeared....
what is the problem?? i think i should remove it and reinstall mozilla.

how to remove through the command line??

---

### Post by diwas on 2008-08-07
Yes, i can install it through synaptic no problem...but i wanted to know how to install this type of package. Now i know that xtracting will do the work. But smthg's messed up here.

Actually i upgraded firefox from synaptic. It went fine. But now when i click the launcher icon (the default one in the top GNOME panel of ubuntu 8.04) firefox executes but the "back", "forward", "refresh" and "stop" buttons on the top are faded. Also i dont remember wat used to be below those and above the "tabs"...it has also disappeared....
what is the problem?? i think i should remove it and reinstall mozilla.

how to remove through the command line??

---

### Post by diwas on 2008-08-07
Ok i was messing up with things here and now...now when i enter 
```

sudo firefox

```
the old firefox comes up...ie with the back, forward, refresh and stop button. and the address bar is working too...
But if i start firefox from the launcher...the above explained firefox comes up. 
any idea?

Oh yes, i forgot to mention...the version name is 3.0.1 now.

---

### Post by diwas on 2008-08-08
bump

---

### Post by sharks on 2008-08-08
follow this guide:
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)
[http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux](http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux)

---

### Post by gjoellee on 2008-08-08
remove Frefox and click on the link below:
[apt://firefox](apt://firefox)

---

### Post by diwas on 2008-08-09
How to open this??? When i click this link a dialouge box comes up asking me to choose the software with which it should be opened. But there isn't any software list in the box...instead it asks me to browse and which i click it...my home/diwas directory comes up.

---

### Post by diwas on 2008-08-10
bump

---

