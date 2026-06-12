---
title: "Ubuntu won't get past the splash screen"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by ameanjoe on 2008-04-29
Aloha, folks,
Well, I upgraded to 8.4 and had to do a bit of clean-up of my software packages. Now when I power up my computer (a Dell 530) it goes through the initial start-up screens, then at the Ubuntu splash screen with the orange bar that goes left to right below the title, nothing happens. It doesn't boot to my desktop. That little orange bar just keeps going across repeatedly....
If I power down manually and restart 2 or 3 times it might get past the splash screen, but not always...(It's working fine at the moment...)
Anyone got any ideas???
meanjoe

---

### Post by Helios38 on 2008-04-29
if ur using grub, press 'e' when ubuntu is highlighted, and delete --quiet from the set.


you may find your poison.

---

### Post by ameanjoe on 2008-04-30
Aloha, Helios38,
Being a newby I don't understand what you are saying.
#1: Do you mean to hit "e" when the Ubuntu splash screen comes up?
#2: Exactly what am I supposed to delete? "Quiet" or "Quiet from the set"?
Forgive me if I sound dumb. I tried hitting "e" when the Ubuntu splash screen came up and nothing happened...That orange bar just kept on truckin' back and forth.
To clarify further my problem: After I downloaded the 8.4 and my computer was going through the set-up process, there was a momentary power outage. Not more than a few seconds. When the power returned Ubuntu was still running, but was possibly hung on the last part of the set-up.
Maybe I should try re-downloading 8.4 (takes a God awful long time even with so called DSL, so I've held off doing that), or maybe reverting to 7.10?
I know Windows pretty well, but Linux is a whole new ballpark and a lot I don't understand.
Thank you for responding tho'. Nobody else has yet....
Aloha, meanjoe

---

### Post by ameanjoe on 2008-05-01
Aloha, Helios38, (again),
Well, I kept trying and finally figured what you were talking about.
Success! One more time I have been frustrated by simple things and feel embarrassed for asking dumb questions, but to quote my college math professor, Ernie Abbot, "The only dumb question is the one you don't ask..."
Thank you again. Now I have to figure out whats-up with the shut down screens...
aMeanJoe

PS: Is there some trick to making an "Official" Thank You?

---

### Post by linfidel on 2008-05-01
> **ameanjoe said:**
> Aloha, Helios38, (again),
Well, I kept trying and finally figured what you were talking about.
Success! One more time I have been frustrated by simple things and feel embarrassed for asking dumb questions, but to quote my college math professor, Ernie Abbot, "The only dumb question is the one you don't ask..."
Thank you again. Now I have to figure out whats-up with the shut down screens...
aMeanJoe

PS: Is there some trick to making an "Official" Thank You?Learning how grub works is a rewarding experience - it's fairly easy, and you get to customize your start up screen, the menu text and the colors if you want.  Permanent changes are made by editing a file in /boot/grub, called "menu.lst" (sudo gedit /boot/grub/menu.lst). 

The way to "officially" thank someone for a helpful post is to click on the star icon at the bottom-right of the post.

---

### Post by ameanjoe on 2008-05-01
Aloha linfidel & helios38,
The solution offered by helios solves the problem temporarly, but at next boot the computer does the same thing, locking up on the splash screen. 
So, I re-start, open grub, and the "quiet" command is there again. How do I delete it permanently? I've tried backspacing over it, moving the cursor to the start of the line and pressing Delete until it is gone. Went into Edit for that line and added "clear"...It will go away until the next boot then it's there again. Any further thoughts????
As for the Thank You, I don't find a "Star" anywhere except for the "Smilies". Maybe once again I'm missing something simple...I dunno', but
Thanks again.
Aloha, ameanjoe

---

### Post by spiderbatdad on 2008-05-01
Hi. I think linfidel was trying to explain. The change is made permanent by editing the file called /boot/grub/menu.lst. It must be edited with root/user privileges, so open the file with the command:```
gksu gedit /boot/grub/menu.lst
```
Scroll down till you see this section:```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=604f2b74-7f64-424f-a8bf-1160a71d9ea3 ro **lapic pci=routeirq**
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
savedefault
```

Above, I have highlighted the end of the line beginning with the word kernel. This is where you will make your changes. Save the file by clicking the little floopy disk icon near the top of the window. Good luck.

---

### Post by Spoken on 2008-05-01
> **Helios38 said:**
> if ur using grub, press 'e' when ubuntu is highlighted, and delete --quiet from the set.


you may find your poison.

yep

---

### Post by ameanjoe on 2008-05-02
Aloha, Folks,
Well, I changed the "menu.lst", tried rebooting and my computer went into some sort of loop. I manually powered down after about an hour and rebooted again. This time it went through several pages of commands (terminal type screen) and finally did boot to ubuntu. I then powered down using the green man and was met with another series of pages of commands that lasted for a couple of minutes. I copied and pasted the highlighted terms into the first kernal as directed. Now I'm afraid that I'm going to have to do a re-install of ubuntu. 
As Mama always said, "If it ain't broke, don't fix it..." My 7.10 was working fine, but thought I should upgrade....Mistake...
Thanks for all your help and comments...Yeep..
ameanjoe

---

### Post by linfidel on 2008-05-02
> **ameanjoe said:**
> Aloha, Folks,
Well, I changed the "menu.lst", tried rebooting and my computer went into some sort of loop. I manually powered down after about an hour and rebooted again. This time it went through several pages of commands (terminal type screen) and finally did boot to ubuntu. I then powered down using the green man and was met with another series of pages of commands that lasted for a couple of minutes. I copied and pasted the highlighted terms into the first kernal as directed. Now I'm afraid that I'm going to have to do a re-install of ubuntu. 
As Mama always said, "If it ain't broke, don't fix it..." My 7.10 was working fine, but thought I should upgrade....Mistake...
Thanks for all your help and comments...Yeep..
ameanjoe
How did you change the menu.lst file?  I hope you didn't copy and paste exactly from spiderbatdad's post.  Your's should be similar, but with a different UUID.  That long UUID is actually the unique identifier for (presumably) his hard disk.  Yours would need the UUID that refers to your hard disk.  I don't think you can boot his hard disk from your computer; if so, well, you've discovered a great power. :)

It should be the same as when you edited the grub menu at boot time.

You can probably fix it if you changed it.  Do you have a backup?  If not, you probably still have the UUID below that for the recovery option.

By the way, you can get the UUIDs, and lots of other info, for all disks by typing "sudo blkid" at a terminal prompt (if I remember correctly - I'm not at home right now).

One nice thing about linux is that it is fixable in most cases, without reinstalling.

---

### Post by ameanjoe on 2008-05-02
Aloha, linfidel,
To respond...using terminal I entered "gksu gedit /boot/grub/menu.lst" as directed.
I found the line to be edited ending in "ro quiet splash".
I copied the highlited portion only, not the UUID...
That really screwed things up. (See my post entitled something like "Re-installing 8.04...")
I have tried since then different boot selections and of them all, booting to "22" works (sort-of) the best. Every "device" now acts woonkie intermittantly. Video, cd drive, as well as most of my programs. It takes 3 to 4 retries to get the beast to boot, and now I don't know what to do. I've been backing up all of my data, photo, and music files to CD's (big job when it works), and am looking at my 7.10 "live" disk like that might resolve some of the problems.
You say,"Don't need to re-install. Everything can be fixed."
Well, I never learned Unix or command line programming. I have a hard time figuring out what works where...
I know Windows like the back of my hand and can do pretty much whatever I want/need to do, but I've only been working/learning Ubuntu for a few months, and most of that has been figuring out what I need, where it is, and how to use it. Now I'm just frustrated...
But Thank You for your responses. They have helped to eliminate some of the possible causes.
Aloha, Joe Green

---

### Post by linfidel on 2008-05-03
> **ameanjoe said:**
> Aloha, linfidel,
To respond...using terminal I entered "gksu gedit /boot/grub/menu.lst" as directed.
I found the line to be edited ending in "ro quiet splash".
I copied the highlited portion only, not the UUID...
That really screwed things up. (See my post entitled something like "Re-installing 8.04...")
I have tried since then different boot selections and of them all, booting to "22" works (sort-of) the best. Every "device" now acts woonkie intermittantly. Video, cd drive, as well as most of my programs. It takes 3 to 4 retries to get the beast to boot, and now I don't know what to do. I've been backing up all of my data, photo, and music files to CD's (big job when it works), and am looking at my 7.10 "live" disk like that might resolve some of the problems.
You say,"Don't need to re-install. Everything can be fixed."
Well, I never learned Unix or command line programming. I have a hard time figuring out what works where...
I know Windows like the back of my hand and can do pretty much whatever I want/need to do, but I've only been working/learning Ubuntu for a few months, and most of that has been figuring out what I need, where it is, and how to use it. Now I'm just frustrated...
But Thank You for your responses. They have helped to eliminate some of the possible causes.
Aloha, Joe Green
Hi Joe,
I guess I'm not clear on the state of the problem... when you removed "quiet" from the grub startup menu, and got it to boot, did it run normally?  When it doesn't boot, can you tell where it's hanging?

If adding that highlighted part caused a problem, I'd take it out, and simply remove the "quiet".  That would solve your immediate question about how to make it permanent.  Then you could work on whatever is next.

About reinstalling - I didn't really mean to imply that you shouldn't - just that once you get it running, you can usually fix problems without reinstalling, unlike Windows.  Everything has configuration files that can be edited with a text editor, grub can be configured using any live CD, you can copy the kernel files (in the /boot directory) using a simple "cp", etc.

I am a lot like you, in that I know Windows very well, and have been using and programming it for over 10 years, ever since Windows 3.0.  My first attempts a linux were frustrating, and I gave up easily.  But then I started using it at work for cross-platform development, and learned enough bash to start feeling comfortable, learned to use and love the gvim editor, and then, my crowning achievement, learned how to use grub. :)  After screwing things up a bit with that, I was forced to learn about UUIDs, moving partitions around, and mounting filesystems, etc.  I now have 2 drives with 4 or 5 different versions of linux, and about a dozen partitions all working together.  Grub is on its own partition, so usually when I do an OS version upgrade, I need to customize my grub before it will boot.  

So, don't get frustrated.  If you have more problems, it might be helpful to start a new topic, as some people who can help might skip ones that seem to have help already.  A topic with zero replies is often good bait. :)   So is a good subject line.

By the way, do you know Windows/DOS command line programming?  With a few tips, the linux command line can become a breath of fresh air if you know DOS.

---

### Post by linfidel on 2008-05-03
> **ameanjoe said:**
> Aloha, linfidel,
...
Aloha, Joe Green
):P  By the way, Joe...  Are you from Hawaii?

---

### Post by ameanjoe on 2008-05-04
Aloha, Linfidel,
Well, I live in Hawaii now. Retired from Sony in San Jose in '02 and moved back here.I don't miss the bay area one bit. Even with the volcano acting up, it's still paradise for a few more years....
I went back in to "menu'lst" again and simply removed the terms "quiet splash" and "quiet" from both kernels (22 and 24).Re-booted and instead of the "splash", a "river" of lines of script, checking and loading, and I don't know what all. It moved pretty fast. Then it went through a couple of bleeps and flashes and black screens and came up with my desktop. Have to play with that more...
I don't know what, but something I did messed up the Nivida graphics driver and the best res. I can get is 800X600 in the 22 boot, 640X480 in the 24, and it won't stay enabled if I reboot...I think that's for a new thread. I also think with the responses from you and Helios I've gained a greater understanding of grub and this thread can be closed (I even learned how to say "Thank You"...Mahalo nui loa!)....
Watch for the "New Thread"...Might be good for a few laughs!
Got a lot to learn...
Aloha, Joe Green

---

### Post by linfidel on 2008-05-04
> **ameanjoe said:**
> Aloha, Linfidel,
Well, I live in Hawaii now. Retired from Sony in San Jose in '02 and moved back here.I don't miss the bay area one bit. Even with the volcano acting up, it's still paradise for a few more years....
I went back in to "menu'lst" again and simply removed the terms "quiet splash" and "quiet" from both kernels (22 and 24).Re-booted and instead of the "splash", a "river" of lines of script, checking and loading, and I don't know what all. It moved pretty fast. Then it went through a couple of bleeps and flashes and black screens and came up with my desktop. Have to play with that more...
I don't know what, but something I did messed up the Nivida graphics driver and the best res. I can get is 800X600 in the 22 boot, 640X480 in the 24, and it won't stay enabled if I reboot...I think that's for a new thread. I also think with the responses from you and Helios I've gained a greater understanding of grub and this thread can be closed (I even learned how to say "Thank You"...Mahalo nui loa!)....
Watch for the "New Thread"...Might be good for a few laughs!
Got a lot to learn...
Aloha, Joe Green
Aloha, Joe,
FYI, the "quiet" option just hides all the text that flashes by; it should have no other effect.  But the text can sometimes be informative - well, not while it's flashing by, but if it hangs, and stops flashing by, you can see where it's having a problem, which can be a good clue as to how to go about fixing it.  There is also information in the system log, available from the "system", "administration" menu.

The problem with Nvidia might be a mismatch between the version of the proprietary driver necessary for desktop effects and the kernel version.  Usually, you can fix the standard nvidia driver by going through a short configuration exercise, which is initiated by "sudo dpkg-reconfigure -plow xserver-xorg", but I'm nt sure how that affects the desktop effects settings - it may require reenabling.  In the past, I've had to play around with disabling the proprietary drive, then reenabling it, in various sequences until it worked.

You would probably be interested in this article:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

I'll look for your new thread, which might get better suggestions.  I'm still not an expert, although I've always been able to muddle through and fix my system.  It's usually not that difficult.

I spent a week in Hawaii (Waikiki) last Christmas, my first visit.  I loved it, and plan to visit some of the other islands.  It was a great way to spend Christmas.  I live in the Bay Area (East Bay), so I can see why you like it better - it's a great change. Wish I could afford to retire there!  Actually, I wish I could afford to retire. :icon_frown:

---

### Post by ameanjoe on 2008-05-04
Good morning and Aloha Marty,
I did the reconfiguration script you suggested and it gave me bact the ability to select all the different resolutions...Yea....
After my last post (last nite), I played around a bit with editing the menu.lst and figured out the differences with "splash" and "quiet".
I had found the //help.ubuntu.com/community site and was going to go there in search of solutions this morning, but tried your(?) script first. Still more to do, but with the help of the forum (and folks like you) it's getting fixed little by little...Thank you again for your help.
If you come back to Hawaii, don't go to Waikiki..Don't go to Oahu. Come to the Big Island or Kauai. You'll get closer to the "real" Hawaii. I can't really afford to live here myself, but there's no other place I want to live....My email is:joe@bighawaii.net, should you decide to come over...
Again and again, Mahalo nui loa, notsomeanjoegreen

---

### Post by Victormd on 2008-05-04
I quickly read through the post and am not sure where you got... but here's something you can try.
From the terminal, open your menu.lst
```
sudo gedit /boot/grub/menu.lst
```
then, scroll down to (as shown before):
> title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,1)
[COLOR="Red"]*kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=5610c634-bc0e-4ac8-bb50-6fc28ae9e0c3*** ro quiet splash**[/COLOR]
initrd		/boot/initrd.img-2.6.24-17-generic
quiet
savedefault

Now, remove the "quiet" option from the kernel and after "splash", type "noapic" (leave a space after the command). This is ***usually*** a must on laptops and sometimes works on desktops. The line highlighted above should look like this:
> [COLOR="Red"]*kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=5610c634-bc0e-4ac8-bb50-6fc28ae9e0c3 ***ro splash noapic **[/COLOR]
removing the "quiet" option will allow you to verify where your computer is freezing and will shed some light as to why it's freezing.

NOTE: Don't mind the code in italic... that's unique for each configuration.

---

### Post by linfidel on 2008-05-04
> **ameanjoe said:**
> Good morning and Aloha Marty,
I did the reconfiguration script you suggested and it gave me bact the ability to select all the different resolutions...Yea....
After my last post (last nite), I played around a bit with editing the menu.lst and figured out the differences with "splash" and "quiet".
I had found the //help.ubuntu.com/community site and was going to go there in search of solutions this morning, but tried your(?) script first. Still more to do, but with the help of the forum (and folks like you) it's getting fixed little by little...Thank you again for your help.
If you come back to Hawaii, don't go to Waikiki..Don't go to Oahu. Come to the Big Island or Kauai. You'll get closer to the "real" Hawaii. I can't really afford to live here myself, but there's no other place I want to live....My email is:joe@bighawaii.net, should you decide to come over...
Again and again, Mahalo nui loa, notsomeanjoegreen
Thanks, maybe I'll look you up next time I come to Hawaii.  Waikiki wouldn't have been my preference, but my wife's sister's family made reservations, then asked us to come too.  But I'm glad I got to see it.  A friend at work prefers the big island, and I'd like to go there.  He has relatives who grow coffee.

I'm glad you're making progress.  One thing I wanted to suggest is to duplicate your default configuration in grub, and then change it to experiment.  That way, you'll have a working configuration to fall back on.  I think by now you probably see how simple it is, pretty easy to follow even if you don't know exactly what each line does.

I have enough space on my drive to have created some extra partitions, and one of them has a fairly plain ubuntu installation that I can use for comparison if needed.  It can be used to access anything on my normal partition, including the kernel files, so it's useful to fix things, and easier than booting up the live CD.  If you want to learn how to do any of this, feel free to ask.  You can send email to me if you have any basic questions, and don't want to start a new topic.

Good luck - hope everything goes more smoothly from now on.  And, thanks for the thanks. :)

---

