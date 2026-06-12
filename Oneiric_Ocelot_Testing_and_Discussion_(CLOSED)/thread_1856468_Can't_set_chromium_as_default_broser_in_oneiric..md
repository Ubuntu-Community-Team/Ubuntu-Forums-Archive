---
title: "Can't set chromium as default broser in oneiric."
date: 2011-10-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by nuttzo31 on 2011-10-08
I'm having a problem with firefox staying as default browser after i have set chromium to be the default both in the chromium preferences and the default applications of the system menu applet.If i remove firefox it will allow chromium to become the default but if they are side by side firefox takes over.I was going to file a bug report but i'm not sure if it is classed as a bug because chromium is not the default browser in ubuntu or maybe  i have overlooked something.Any help would be appreciated.

---

### Post by ronacc on 2011-10-08
try configuration-editor>desktop>applications>browser

---

### Post by nuttzo31 on 2011-10-08
ronacc
i tried setting it to chromium and then logged out and restarted and it still brings up firefox instead of chromium.I attached a screenshot of the setting i changed in case i got i wrong.

---

### Post by ronacc on 2011-10-08
make sure  you have it pointed at where chromium ( or chrome ) is , I didn't install from the repos I got the .deb from google and my chrome is located in /opt/google/chrome and is called google-chrome not chromium .

---

### Post by cariboo on 2011-10-08
You didn't say what DE you are using, but if you are running Unity, go to System Settings->System Info->Default Applications, and make sure chromium is set as the default browser there.

---

### Post by nuttzo31 on 2011-10-08
It is set to chromium there as well and I am using unity.Can someone see if they can reproduce this by installing chromium alongside firefox from the default repo,launch chromium and set it to default when it asks you the first time you run it.Shut chromium down and click on system info in the unity launcher and check to see if chromium is set as prefered web browser like mine is.Then click on ubuntu software centre and click on one of the apps that have a link to take you to the developer website and for me firefox will open instead of chromium.

---

### Post by vasa1 on 2011-10-08
What happens if, while running Chromium **alone**, you click on the Wrench, Preferences, Basics, and then, near the bottom, click on make Chromium the default browser?

---

### Post by ronacc on 2011-10-08
cariboo just a note ! I'm using GS and system-settings is available there also and when I changed it with configuration-editor and restarted GS it also changed in system-settings .

---

### Post by nuttzo31 on 2011-10-08
vasa1
Chromium says its the default browser in the preferences tab.When i click on a link in thunderbird it will open up chromium but when i click on a link in the software centre it will open up firefox.

---

### Post by ronacc on 2011-10-08
I'm on GS not unity and using google-chrome not chromium but the test you suggested brought up chrome for me ,

---

### Post by nuttzo31 on 2011-10-08
ronacc
so when you click on a link from the ubuntu software centre with gnome shell it launches in chrome and not firefox is that correct.

---

### Post by nuttzo31 on 2011-10-08
I have the same problem in gnome shell and unity when i click on links in the ubuntu software centre they open up in firefox

---

### Post by ronacc on 2011-10-08
> **nuttzo31 said:**
> ronacc
so when you click on a link from the ubuntu software centre with gnome shell it launches in chrome and not firefox is that correct.

yes

---

### Post by nuttzo31 on 2011-10-08
> **ronacc said:**
> yes

And you also have firefox installed i assume.Can anyone else reproduce this preferably with chromium and not chrome?

---

### Post by mc4man on 2011-10-08
Try this - 
 ```
sudo update-alternatives --config  x-www-browser
```
Even if chromium-browser is set as default in Auto mode, switch it to manual mode
Ex.
> $ sudo update-alternatives --config  x-www-browser
There are 2 choices for the alternative x-www-browser (providing /usr/bin/x-www-browser).

  Selection    Path                       Priority   Status
------------------------------------------------------------
  0            /usr/bin/chromium-browser   40        auto mode
* 1            /usr/bin/chromium-browser   40        manual mode
  2            /usr/bin/firefox            40        manual mode

Press enter to keep the current choice[*], or type selection number: 



---

### Post by ronacc on 2011-10-08
well pursuing this a little further I did a fresh install from the latest daily . on bootup went to USC and installed chromium , made it default and checked system>settings and it was listed as default there . I then went to USC and chose an app and selected its "developer website" link and FIREFOX opened it , checked system-settings and it had been changed back to firefox changed it back to chromium and rebooted system-settings showed chromium on reboot but USC still opens firefox . tried mac4man suggestion and chromium shows there exactly as in his post but USC still opens firefox .

---

### Post by ronacc on 2011-10-08
@ nuttzo31 you found the bug , you file it and I'll confirm and me-too . and please post a link to it .

---

### Post by mc4man on 2011-10-08
> **ronacc said:**
> well pursuing this a little further I did a fresh install from the latest daily . on bootup went to USC and installed chromium , made it default and checked system>settings and it was listed as default there . I then went to USC and chose an app and selected its "developer website" link and FIREFOX opened it , checked system-settings and it had been changed back to firefox changed it back to chromium and rebooted system-settings showed chromium on reboot but USC still opens firefox . tried mac4man suggestion and chromium shows there exactly as in his post but USC still opens firefox .
Did you set it to manual mode?
At least here it would always open in FF until I did that, now it opens in chromium

---

### Post by ronacc on 2011-10-08
no I had set to auto , my bad , setting it to manual chromium opens instead of FF . I still think its a bug , you shouldn't have to go through all that to changed your default browser , kind of reminds me of the browser wars between netscape and IE back in the 90's :lolflag:

---

### Post by mc4man on 2011-10-08
Well -  then a bug should be filed on Sc not respecting a change to x-www-browser in auto mode or -  see last comment (changing the default does not change x-www-browser

If you where now to switch back to 'auto mode - chromium-browser' I'm sure it will still stay with chromium
I'm not 100% sure but my impression is x-www-browser is only set/changed on a browser install/removal, certainly is not affected by changing the default in System Setting & or the browit sers themselves

(had a similar bug concerning this but against apport - no one really cares there & anyway at release apport is disabled
There difference there is apport does use the new 'auto mode' setting, Sc doesn't

---

### Post by ronacc on 2011-10-08
I wonder why this would affect unity but not GS ? in GS USC respected my setting in system-settings .

---

### Post by mc4man on 2011-10-08
> **ronacc said:**
> I wonder why this would affect unity but not GS ? in GS USC respected my setting in system-settings .
I think the best way to test that (to see if there is a diff) is to remove one of your browsers, log out/in & then re-install the removed one.
That should set a new 'auto mode' default to the newly installed browser
Then see if Sc opened in Gs uses the newly set 'auto mode' default or the one that was left installed

Ex.
> $ sudo apt-get purge chromium-browser
whatever
Removing chromium-browser ...
update-alternatives: using /usr/bin/firefox to provide /usr/bin/x-www-browser (x-www-browser) in auto mode.


Then re-installing chromium-browser (I'd do the logout/in 1st. to clear things) will reset chromium-browser  as the auto mode default - see what gs does

---

### Post by ronacc on 2011-10-08
curiouser and curiouser , booted into my GS partition , and checked update-alternatives --config  x-www-browser then using synaptic removed (completely ) firefox reloaded the repos and updated then reinstalled FF , again checked update-alternatives --config  x-www-browser , logged out and back in again checked update-alternatives --config  x-www-browser the results of the check were identical all 3 times .```
There are 5 choices for the alternative x-www-browser (providing /usr/bin/x-www-browser).

  Selection    Path                    Priority   Status
------------------------------------------------------------
* 0            /usr/bin/opera           200       auto mode
  1            /usr/bin/firefox         40        manual mode
  2            /usr/bin/google-chrome   120       manual mode
  3            /usr/bin/konqueror       30        manual mode
  4            /usr/bin/midori          39        manual mode
  5            /usr/bin/opera           200       manual mode

Press enter to keep the current choice[*], or type selection number: 
```
opened USC and clicked on a link chrome opened it . note google-chrome shows as the default in system-settings see SS

---

### Post by mc4man on 2011-10-08
I'll have to try with Gs, you have so many browsers I can't get past all the potentials there

---

### Post by ronacc on 2011-10-08
> **mc4man said:**
> I'll have to try with Gs, you have so many browsers I can't get past all the potentials there

I usually have more :lolflag: I like to play with browsers .

---

### Post by mc4man on 2011-10-08
curious & inconsistent - 
Now when I re-install a browser (chromium) nothing is set update-alt..., chromium is listed as the auto default but nothing is shown as enabled

Software center is still acting the same here - stays with FF & changing the default in g-c-c doesn't help but update-alt.. will

Initially after installing c-b to ck. this Thunderbird did the same thing as Sc - now Tb reacts to changes in g-c-c

Am going to do a fresh final install tonight - will recheck this  Starting in Gs instead of unity

I guess the way to 'leave' this is if Sc doesn't open the browser you want then set in update-alt..

I'm currently viewing 11.10 as a bit of an Alice in Wonderland experience at times

---

### Post by ronacc on 2011-10-08
isn't just about every dev cycle a trip through the looking glass :p

---

### Post by rojaasensei on 2011-10-08
> **nuttzo31 said:**
> I have the same problem in gnome shell and unity when i click on links in the ubuntu software centre they open up in firefox

Same here with Xubuntu 11.04.  Opera is my default browser, but links from the software center open firefox, so do links in Thunderbird.

---

### Post by ronacc on 2011-10-08
try mac4man's suggestion in post 15 in this thread .

---

### Post by nuttzo31 on 2011-10-08
> **mc4man said:**
> Try this - 
 ```
sudo update-alternatives --config  x-www-browser
```
Even if chromium-browser is set as default in Auto mode, switch it to manual mode
Ex.

Thanks mc4man that solved the problem for me.Now when i click on links in the software centre it launches in chromium.Thanks to everyone else who helped as well.

---

