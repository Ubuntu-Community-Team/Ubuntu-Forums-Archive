---
title: "Ubuntu 11.10 / Annoying Swinging Side Panel"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by Andavane on 2012-03-16
Been getting used to Ubuntu 11.10, although some niggles remain.
For me the worst is when I want to expand a page to full screen, I always explore with my pointer to the left. But if I go too far to the left, the sidebar comes over and blocks what I'm trying to see. Incredibly annoying.

Also when I take a page up to the top of the screen, it fills the screen, always when I don't want it to.
Been meaning to post this for ages, but always said. "Tomorrow, tomorrow".
Thus the months fly by.

--John

---

### Post by roger_1960 on 2012-03-16
Hi

Assuming you are using unity 3D and not 2D;

If you install compiz settings manager "ccsm" and go to the Unity Plugin and the behaviour tab, you can set the reveal mode of the launcher to reveal with the mouse at different locations, not just the left side.  I use the bottom left corner as there are rarely buttons or anything else there in software windows.

---

### Post by 3rdalbum on 2012-03-16
> **Andavane said:**
> Been getting used to Ubuntu 11.10, although some niggles remain.
For me the worst is when I want to expand a page to full screen, I always explore with my pointer to the left. But if I go too far to the left, the sidebar comes over and blocks what I'm trying to see. Incredibly annoying.

Also when I take a page up to the top of the screen, it fills the screen, always when I don't want it to.
Been meaning to post this for ages, but always said. "Tomorrow, tomorrow".
Thus the months fly by.

--John

Ubuntu 12.04 fixes the first problem - you must actually push the mouse against the side in order to make the Launcher pop out. You can change the sensitivity too.

You can turn off the maximise function too, even in 11.10. The option is in Compizconfig Settings Manager, but I can't remember what it is called! Don't mess with CCSM until you get an answer - if you turn off the wrong thing you can stop the desktop working properly.

---

### Post by yetiman64 on 2012-03-16
> **roger_1960 said:**
> ...  I use the bottom left corner as there are rarely buttons or anything else there in software windows.
+1 that is a good position for the mouse activation.

OP, To install ccsm, use the key combination ctrl+alt+t to bring up a terminal then copy and paste in the code below,
```
sudo apt-get install compizconfig-settings-manager
``` When the terminal finishes close it, then go into Dash and type in "ccsm" (without the quotes), click on the icon and ccsm will open. 

Click the "Ubuntu Unity Plugin" and then the "Reveal Mode" button that reads "left" click the green left side to turn it red and the red left bottom corner so it turns green, click OK and it is now set up for you.

**Please note:** altering any other settings with ccsm can be very unsettling as it can crash and/or lock up Unity, freezing up your desktop. It is fixable but best to avoid it if you can.

**Edit** @ 3rdalbum, that is the Automaximize value on the Experimental tab of the Unity plugin, I set it to 100 % to stop it working (annoyed the living daylights out of me until I found that setting :-)). **Edit 2:** that may be the wrong setting for what the OP was referring to, sounds more like the grid plugin at work.-- Just rechecked: Grid plugin > Edges Tab > Resize Actions > Top Edge, set it to "none". That stops the window maximizing when the window is dragged to the top.

---

### Post by Andavane on 2012-03-17
> **yetiman64 said:**
> +1 that is a good position for the mouse activation.

OP, To install ccsm, use the key combination ctrl+alt+t to bring up a terminal then copy and paste in the code below,
```
sudo apt-get install compizconfig-settings-manager
``` When the terminal finishes close it, then go into Dash and type in "ccsm" (without the quotes), click on the icon and ccsm will open. 

Click the "Ubuntu Unity Plugin" and then the "Reveal Mode" button that reads "left" click the green left side to turn it red and the red left bottom corner so it turns green, click OK and it is now set up for you.

**Please note:** altering any other settings with ccsm can be very unsettling as it can crash and/or lock up Unity, freezing up your desktop. It is fixable but best to avoid it if you can.

**Edit** @ 3rdalbum, that is the Automaximize value on the Experimental tab of the Unity plugin, I set it to 100 % to stop it working (annoyed the living daylights out of me until I found that setting :-)). **Edit 2:** that may be the wrong setting for what the OP was referring to, sounds more like the grid plugin at work.-- Just rechecked: Grid plugin > Edges Tab > Resize Actions > Top Edge, set it to "none". That stops the window maximizing when the window is dragged to the top.
Thank you and thank you all.
I've clicked the Unity Plugin and reveal mode, but can't see this green button. I seem to be missing this.
regards,
John

---

### Post by roger_1960 on 2012-03-17
Hi

At top right in your posted screen shot, click where it says "left" and you should then get a choice of area for the mouse activation of the launcher.

---

### Post by yetiman64 on 2012-03-17
> **Andavane said:**
> Thank you and thank you all.
I've clicked the Unity Plugin and reveal mode, but can't see this green button. I seem to be missing this.
regards,
John
See the attachments below, I should have thought to put these on earlier, Cheers OP.

Edit: if you note my Unity plugin disabled, that is because I use the ppa version to rotate it to the bottom of the screen. I do have Unity in use :-)

---

### Post by Andavane on 2012-03-18
Hey Guys that was fun.
I have always got extremely muddled between lefts and rights and greens and reds. Any how a friend came in and read it out to me and I focussed and managed it! :p:)

Many many thanks
And believe you me it's a HUGE relief not being driven nuts by those things swinging out then filling the screen.

Rgards, John

PS: You'd have thought they would have chosen a better contrast than red & green. I believe those colours are used in colour-blindness tests .

---

### Post by Alwimo on 2012-03-18
> **Andavane said:**
> Hey Guys that was fun.
I have always got extremely muddled between lefts and rights and greens and reds. Any how a friend came in and read it out to me and I focussed and managed it! :p:)
 
Many many thanks
And believe you me it's a HUGE relief not being driven nuts by those things swinging out then filling the screen.
 
Rgards, John
 
PS: You'd have thought they would have chosen a better contrast than red & green. I believe those colours are used in colour-blindness tests .
I have just reported that as a bug. If you have a Launchpad account (if you use Ubuntu One, it's the same as that), you can click up the top that it affects you too.
[https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/958865](https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/958865)

---

### Post by Andavane on 2012-03-19
> **Alwimo said:**
> I have just reported that as a bug. If you have a Launchpad account (if you use Ubuntu One, it's the same as that), you can click up the top that it affects you too.
[https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/958865](https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/958865)
Cherrs mate. It's done &#10003;

---

### Post by Andavane on 2012-04-01
> **3rdalbum said:**
> Ubuntu 12.04 fixes the first problem - you must actually push the mouse against the side in order to make the Launcher pop out. You can change the sensitivity too.

You can turn off the maximise function too, even in 11.10. The option is in Compizconfig Settings Manager, but I can't remember what it is called! Don't mess with CCSM until you get an answer - if you turn off the wrong thing you can stop the desktop working properly.

Indeed.
Since I marked this thread ad 'SOLVED' a few strange things have been happening:
[LIST]The terminal always maxes out and won't easily go down[/LIST]
[LIST]I can only alter the size of a LibreOffice Document partially. I can alter the bottom and the sides of the document but not the top which I can't see so I can't drag it down. If I want to move a file about the screen (which I do all the time) I have to leave my Thinkpad and switch to my 'old work-horse' laptop bought in 2004[/LIST]
 
REALLY annoying!

As always, help from experts much appreciated. I've UNSOLVED the thread for the time being.

Regards,  John

---

### Post by yetiman64 on 2012-04-01
> **Andavane said:**
> ...The terminal always maxes out and won't easily go down...
Have you tried setting the automaximize value to 100% ? 
Then reduce the size of the terminal before shutting it off. 
Restart the terminal it should hold the size without maximizing, that worked here for me. Good luck.

---

### Post by Andavane on 2012-04-01
> **yetiman64 said:**
> Have you tried setting the automaximize value to 100% ? 
Then reduce the size of the terminal before shutting it off. 
Restart the terminal it should hold the size without maximizing, that worked here for me. Good luck.
On an old machine which is behaving well atm the moment. Going there later tonight.
In the meantime,
How do I set the automaximise value?
Regards, John

---

### Post by yetiman64 on 2012-04-01
ccsm > Ubuntu Unity Plugin > Experimental Tab, there is a slider very near the bottom, slide it fully to the right hand side.

---

### Post by Andavane on 2012-04-03
> **yetiman64 said:**
> ccsm > Ubuntu Unity Plugin > Experimental Tab, there is a slider very near the bottom, slide it fully to the right hand side.

Oh man, I can MOVE my LibreOffice panel around again now, just as I want — I am SOOO relieved!  
Woo hoo, thanks for ending my days of purgatory! :-)

---

### Post by Andavane on 2012-04-04
&#8594;  > Oh man, I can MOVE my LibreOffice panel around again now, just as I want — I am SOOO relieved!
Woo hoo, thanks for ending my days of purgatory!
whoops!, having said that, yes I can move my LibreOffice panel around again, however the side panel launcher has developed a mysterious habit of disappearing back into a side, like a snail withdrawing its horns back into its shell.   ](*,)

thread has reverted to UNSOLVED.

---

### Post by yetiman64 on 2012-04-04
> **Andavane said:**
> &#8594;  
whoops!, having said that, yes I can move my LibreOffice panel around again, however the side panel launcher has developed a mysterious habit of disappearing back into a side, like a snail withdrawing its horns back into its shell.   ](*,)

thread has reverted to UNSOLVED.
That sounds a bit like you still have the setting for "Hide Launcher" set to "Dodge Windows" (the default for 11.10) or maybe even "Dodge Active Window". 

Setting Hide Launcher to either Never (for visible all the time) or Autohide (stays hidden till you move the mouse to the Reveal mode location) should stop that, if you like their behaviour that is. 

The Reveal Mode location is what you set previously in the thread, the red and green sides/corners etc and is two settings above "Hide Launcher".

---

### Post by Andavane on 2012-04-04
> **yetiman64 said:**
> That sounds a bit like you still have the setting for "Hide Launcher" set to "Dodge Windows" (the default for 11.10) or maybe even "Dodge Active Window". 

Setting Hide Launcher to either Never (for visible all the time) or Autohide (stays hidden till you move the mouse to the Reveal mode location) should stop that, if you like their behaviour that is. 

The Reveal Mode location is what you set previously in the thread, the red and green sides/corners etc and is two settings above "Hide Launcher".

Well Yetiman you must be some kind of god cos you know far more about what I did all those days ago than I do. I can't even remember what I did first thing this morning.
But see, you were quite right, it is in Dodge.
Also I know how to put pointer down left when I want launcher and what the <super> button does :-)

But re >  **Edit** @ 3rdalbum, that is the Automaximize value on the Experimental tab of the Unity plugin, I set it to 100 % to stop it working (annoyed the living daylights out of me until I found that setting :-)). **Edit 2:** that may be the wrong setting for what the OP was referring to, sounds more like the grid plugin at work.-- Just rechecked: Grid plugin > Edges Tab > Resize Actions > Top Edge, set it to "none". That stops the window maximizing when the window is dragged to the top.

Now I can't find the grid plugin for the life of me, and I really don't want that window maxing out every time it hits the top.
So now I *really want to know* where that grid plugin is.

---

### Post by yetiman64 on 2012-04-04
> **Andavane said:**
> Well Yetiman you must be some kind of god cos you know far more about what I did all those days ago than I do. I can't even remember what I did first thing this morning.No, definitely not that, just thought that a part of your last post had been covered before and reread the thread. :)


> **Andavane said:**
> But see, you were quite right, it is in Dodge.
Also I know how to put pointer down left when I want launcher and what the <super> button does :-):confused: Not sure what you are referring to there in the second sentence. After this post I'll re-analyze the thread, but if you could point me to what you mean I'd appreciate it.

> **Andavane said:**
> But re 

Now I can't find the grid plugin for the life of me, and I really don't want that window maxing out every time it hits the top.
So now I *really want to know* where that grid plugin is.In the main ccsm window scroll down to the "Windows management"  section towards the bottom, it is in there. Once again I thought this was already dealt with.** Edit**: my previous post covering this missed out "Windows Management" at the start of the path, it had been covered but not completely, my omission sorry.

Good luck.

---

### Post by Andavane on 2012-04-04
>"Quote:
Originally Posted by Andavane View Post
But see, you were quite right, it is in Dodge.
Also I know how to put pointer down left when I want launcher and what the <super> button does
> "Not sure what you are referring to there in the second sentence. After this post I'll re-analyze the thread, but if you could point me to what you mean I'd appreciate it." "

The reference was to the second, smaller screenshot which showed "Dodge Windows". Also I remembered that the <super> button = the windows logo button. Useful to know how to invoke the launcher. Ah i see a quick tap launches it, and holding it down gives it numbers. 

Re the Grid Plugin:
Yes, found it now and Top Edge is set to "None"
Many thanks again, and I won't marked this as solved again until it all behaves itself for a couple of days!  [crossed-fingers smiley if it was there]
Regards
John

---

### Post by yetiman64 on 2012-04-04
Ah, ok, I understand the reference now. I clean missed the screenshots when rereading even :). Being in ABT I sometimes put a bit more info than I do in General Help or elsewhere, even if you don't need it someone else researching a problem of their own similar to yours may find it useful though (at least that is my theory :)).

The super button should actually launch the dash search box, which of course has to raise the launcher. If you want the launcher only the key combo ALT + F1 will bring up the launcher by itself. ALT + F2 will give the run command screen, oops did it again :lol:

Hope it all works and holds for you. 

Regards, yetiman64

---

### Post by Andavane on 2012-04-04
Thanks.
yes the extra info is most useful as it acts like a digest in the threads.
All holding so far & touch wood.

what's ABT?

---

### Post by yetiman64 on 2012-04-04
> **Andavane said:**
> Thanks.
yes the extra info is most useful as it acts like a digest in the threads.
All holding so far & touch wood.

what's ABT?
Sorry I keep forgetting I shouldn't use acronyms, another habit I need to get out of :). ABT is Absolute Beginner Talk, this forum. That's good news, fingers crossed here for it to hold too.

---

### Post by Andavane on 2012-04-05
:-)

I wish there was a forum more advanced that ABT
but not high enough to be geeky
Thanks again.

An unrelated display problem has arisen, but I'll start another thread for that (in ABT, unless you can suggest a more appropriate forum).

Kind regards

John

---

