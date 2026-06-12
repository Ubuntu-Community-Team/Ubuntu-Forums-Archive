---
title: "xmms"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by Sevy on 2008-07-03
Hi
Im tyring to enable xmms media player to be my default player and in particular play m3u files.
I want to be able to click on an m3u link on a website and have it play it automatically and not have to save it to disk first and then right click it and open with xmms.
Ive entered XMMS in system>preferences>preferred applications>multimedia.
In firefox I have gone to preferences>content>manage file types but when I search for m3u,nothing appears in the download actions list.
Any ideas?

---

### Post by aktiwers on 2008-07-03
Right-click on a m3u file and pick properties. Then go to the "open with" tab and pick Xmms.

I am not sure if this will affect Firefox, but if you click "open" instead of "download to disc" in firefox, I am pretty sure it will open i XMMS this way.

---

### Post by Sevy on 2008-07-03
I tried right clicking the m3u file and selecting properties but I dont get an "open with" option.
It gives just the file name and "will open in:same window"

---

### Post by Sinkingships7 on 2008-07-03
Say "xmms2" instead of "xmms".

---

### Post by PinkFloyd102489 on 2008-07-03
> **Sinkingships7 said:**
> Say "xmms2" instead of "xmms".

There are people who still have XMMS installed, like me for example. The client-server interface never impressed me.

---

### Post by Sevy on 2008-07-03
I tried xmms2 in prefered applications(is that what you mean?) but no joy

---

### Post by aktiwers on 2008-07-04
> **Sevy said:**
> I tried right clicking the m3u file and selecting properties but I dont get an "open with" option.
It gives just the file name and "will open in:same window"

Sorry I was not clear.

Dont do it in firefox, do it in ubuntu. Find a m3u file on your harddrive or download one, and when it is on the computer, right-click, pick properties and find the "open with" tab.

There you can set it to xmms, and then Ubuntu will always open m3u files in Xmms. Even if you click a link in firefox and pick "open file" instead of "download file" I think.

---

### Post by Sevy on 2008-07-06
I managed to right click an m3u file on my hardisk and open with xmms-it plays fine but when I try to play an m3u file off the net I get-
/tmp/mr250318.m3u couldnt be opened because the associated helper application does not exist.Change the association in your preferences

---

### Post by Sevy on 2008-07-10
Previously when listening off the net worked for me I would click an m3u file and I could then choose what to do with it (see attachment)
I selected "Do this automatically for files like this from now on" and thats when the problem started.
How do I get the "open with" box to come up again?

---

### Post by Sevy on 2008-07-12
Is there anyway I can return to Firefox default settings?Will this help?
Anyone,or am I stuffed??:confused::(

---

### Post by cariboo on 2008-07-12
I don't really advise doing this unless you are really sure you need to:). Export your bookmarks to your home directory, then delete .mozilla.
This will delete all your Bookmarks, saved passwords addons and other settings. The next time you start firefox the directory will be recreated

---

### Post by Sevy on 2008-07-12
> then delete .mozilla.
What exact file would I need to delete?
Is this the only way to return to default and will it return my file type settings in preferences?
thanx

---

### Post by aktiwers on 2008-07-12
Go to your home folder and press CTRL+H to view hidden files.
then start typing .mozilla until you find the folder and delete it.

This will completely reset everything in Firefox, making it look and act like a complete fresh install.
You could make a copy of the folder as a backup, if you decide to go back. then you simply replace the new one with the old one.

I dont know if it will fix your problem though..but I guess it is worth a try.. 
Did you try go to "Edit" ="preferences" and then the Application tab to change the default application?

---

### Post by halitech on 2008-07-12
if you can locate a .m3u file on line somewhere, right click it and select save link as, that should allow you to save the file to your computer then right click it and you can select what program you want to open it with.

---

### Post by Sevy on 2008-07-13
@actiwers-I went to preferences and in file types under content but have no m3u under extensions,my xmms just plays pls.when clicking a link.Im using Firefox 2.

@halitech-Like what you wrote I can save to file and right click to play a m3u but I need it to automatically open when I click on a link.Doing this doesnt associate xmms.

---

### Post by aktiwers on 2008-07-13
Maybe this could be something for you?
[https://addons.mozilla.org/en-US/firefox/addon/3023](https://addons.mozilla.org/en-US/firefox/addon/3023)

And this does not work for you?
[http://ubuntuforums.org/showthread.php?t=264914](http://ubuntuforums.org/showthread.php?t=264914)

Meanwhile I will look and see if I can find another way to do it.

---

### Post by TheDemonHell on 2008-07-13
Try looking under Firefox Preferences to see if it's there?

Also, I'm one of the ones who likes XMMS ;) But I'm usig Auducity (The one in the repos)

---

### Post by Sevy on 2008-07-13
And this does not work for you?
[http://ubuntuforums.org/showthread.php?t=264914](http://ubuntuforums.org/showthread.php?t=264914)

I did find this post but tried it again.I get to the point where I enter m3u in the search field but the change action button is greyed out.
Ill try the addon until we find a better solution
Many thanks

---

### Post by halitech on 2008-07-13
> **Sevy said:**
> @actiwers-I went to preferences and in file types under content but have no m3u under extensions,my xmms just plays pls.when clicking a link.Im using Firefox 2.

@halitech-Like what you wrote I can save to file and right click to play a m3u but I need it to automatically open when I click on a link.Doing this doesnt associate xmms.

ok, right click the file and go to properties. You should have a tab called Open With, go to that tab and then select xmms and click close. It should work from there

---

### Post by Sevy on 2008-07-14
Ive selected "open with" xmms in properties for the m3u file but still cant play m3u's from links or associate m3u files in firefox preferences

---

### Post by SunnyRabbiera on 2008-07-14
Xmms is kind of out of it anyway, try audacious instead

---

### Post by Sevy on 2008-07-14
I prefer xmms and works fine on my other ubuntu box.

---

### Post by Sevy on 2008-07-16
OK,Ive deleted .mozilla in my home folder which has reset everything including my file type associations,so now I can use xmms to play m3u's straight off the net.
Luckily as I havent used Ubuntu for long,I only had a few bookmarkes and no addons etc.
Thanks for your time and help peeps

---

### Post by markbuntu on 2008-07-16
Now that you have xmms working, you can use streamtuner to get your shoutcasts and play them without having to go through firefox.

---

