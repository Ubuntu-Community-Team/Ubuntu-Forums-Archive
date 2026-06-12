---
title: "HOWTO: Take back the Firefox icon, improved."
date: 2006-05-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Pu7o on 2006-05-28
This is a somewhat better way to restore the firefox icon, because it will change the icon everywhere, including in About dialogues, and so on. It also updates your copy of Firefox to the latest version in the process. Here's how you do it. Open a terminal, and type the following:

```

wget http://kernel.ws/~puto/fix-firefox
sudo sh fix-firefox
(It will ask for your password, type it)

```

Then log out, and log back in again. Now the icon should have been replaced. Works on dapper too!

(NOTE: This is for x86 users only. It might work on AMD64. It won't work on PowerPC.)

---

### Post by Sammi on 2006-05-28
What about Thunderbird?

---

### Post by Sammi on 2006-05-28
Anyway the script in [this tread]("http://ubuntuforums.org/showthread.php?t=34354&highlight=firefox+original+icon") does the job quite nicely too. It claims to be able to fix Thunderbird too, but I experienced no changes I that regard :-k

EDIT: ok this is not acurate. It did change most icons to the original Thunderbird icons, but I had manually specify it for my dock launcher icon, which was a bit tricky as it kept reverting back.
First I made a copy of "/usr/share/pixmaps/mozilla-thunderbird.xpm
" in "/home/*user*/.mozilla-thunderbird" ->
then I right clicked on my launcher ->
Propeties ->
clicked on the Icon -> 
and chose the copied icon.

---

### Post by kokas on 2006-05-28
I got this error

"Could not load icon

Details: Failed to open file '/usr/share/pixmaps/mozilla-firefox.png': No such file or directory"

Now I have no icon :( what should I do

---

### Post by Sammi on 2006-05-28
Need to know what you did to be able to help you man, so please specify.

Did you run Pu7o's commands?

---

### Post by kokas on 2006-05-28
I did what Pu7o said exactly....it looked fine but when I logged in again I had a icon with a "?" in the midlle and that error message.

"wget [http://kernel.ws/~puto/fix-firefox](http://kernel.ws/~puto/fix-firefox)
sudo sh fix-firefox"

---

### Post by kokas on 2006-05-28
Question solved :D I this method and it changed all my firefox icons...much better looking now :D

---

### Post by Pu7o on 2006-05-29
I fixed the script and it should work now. I'll make a thunderbird version now.

---

### Post by Pu7o on 2006-05-29
OK, here's the thunderbird one:

```

wget http://kernel.ws/~puto/fix-thunderbird
sudo sh fix-thunderbird
(It'll ask for your password, insert it, then wait)

```

---

### Post by yteh on 2006-05-29
Thanks Pu70! Works like a charm and I don't have to deal with the ugly icons anymore.

---

### Post by Pu7o on 2006-05-29
Oh and a small request. For f***'s sake, don't implant a zero in my username. You have no idea how much that can be annoying, and how often that happens.

---

### Post by pjot on 2006-05-29
Gah, the script ruined my FF! 

I'm not in any way negative towards you Po7o but I'd like to give you some of my ideas. I usually look into a script before I execute it and in this one I changed en-GB to sv-SE (english to swedish) before I executed it.

- Let the user choose which language they want to install (not everyone prefers en-GB).
- Let the user choose if he wants to keep his current firefox and just update the icons instead of writing it over with the newest version from the mozilla ftp.

Just wanted to throw in my two cents :)

---

### Post by yteh on 2006-05-29
Sorry about the zero.........

---

### Post by groggyboy on 2006-05-29
What *exactly* makes this different from *that other* howto on how to change the FF logo?

Is the icon better done?  The old howto's icon has an ugly black border around it, and looks horrible at bigger sizes.  I used it for a while, but eventually switched back to the blue globe because it looked so ugly compared to other application icons.

Make a good case for your script, and I may just run it! ;) 

Really, I just want to know if you get your icons from the same place, or if you get them from a different (maybe better) place.

Now, if only FF's icon was more like Swiftfox's...

cheers, groggyboy

---

### Post by Pu7o on 2006-05-30
I get my icon from the official mozilla.org ftp, so it shouldn't have an ugly black border around it.

---

### Post by groggyboy on 2006-05-30
The FF icon certainly does look better than *that other* howto's icon.
Haven't tried your TB script - I'm kinda partial to the new Dapper default TB logo. :)

Nice job on the Help > About box, too, btw.

Thanks Pu7o!

groggyboy

---

### Post by badrad on 2006-06-04
EDIT: I spoke too soon, just fixed it by installing firefox 1.5.0.4 with the instructions with this thread:
[http://ubuntuforums.org/showthread.php?t=186337](http://ubuntuforums.org/showthread.php?t=186337)
Now I have a working firefox with good icons!
/EDIT

Well, this did update all the icons good, but I have issues.

First of all not offering a language choice and defaulting to en-GB is annoying.

But the big problems is now my flash and java doesn't work. No amount of installing, manually or with easy ubuntu, can get it to work. Is there a way I can back out of this install?

I figured I would just reinstall,  but the add Add/Remove program tool won't uninstall Firefox, it says I have to use the Synaptic Package Manager. But Synaptic also wants to uninstall:
-firefox-gnome-support
-gnome-app-install
-sun-java5-plugin
-ubuntu-desktop
-yelp
Which sounds like a lot to a Ubuntu newbie like me. Anyway, thanks for any help.

---

### Post by geearf on 2006-06-04
I tried your script but kept ubuntu's thunderbird version.
In the systray the icon is circled by a black square  :(
, but now the rest of it is the good icon, not the orange message thing like before *
In the about box  and the welcome screen, still the old one, can anything be done on this, without having to install mozilla.org version ?

Thanks

---

### Post by starfire1983 on 2006-06-04
I just want to say great job. Not only does it use a nice PNG image for the icon but it also updates Firefox and Thunderbird. I was a little puzzled after the Thunderbird update because my launcher was using mozilla-thunderbird instead of just thunderbird. Everything looks awesome for me on Dapper.

---

### Post by grsing on 2006-06-04
Thanks, it works perfectly.

---

### Post by M-Theory on 2006-06-04
thanks for the script, it would be better if I could choose the language though ;)

---

### Post by darthvivi on 2006-06-04
I would say good job, it works, but Firefox was upgraded to 1.5.4 and now my Flash/Java plugins won't work, and I can't get them to work...

---

### Post by The_Shady_1 on 2006-06-04
I was able to get the Fx icon working but not the TB one. I copied the script exactly and no luck. Fx also update to 1.5.0.4 when I copied the icon code.

---

### Post by darthvivi on 2006-06-04
This has caused me a lot of problems...

1) I had to reinstall the Flash plugin, which didn't work automatically so I had to manually do it.

2) After installing I needed to log out, when I logged back in I received an error about GNOME. Could have been a coincidence, but I've never receieved an error while logging in before.

3) Now Flash works in Firefox, but it's kind of glitchy. When I go to a flash-only site (homestarrunner.com) it tries to load everything on the left, then it flashes white and switches to the middle where it should begin at. I think it's loading the Flash before the <center> tags. It didn't do this before and it's kind of annoying.

4) Everytime I click my scroll-button to enable auto-scroll (which I use a lot) Firefox switches to another page. I don't know why it does this, and I don't know how to turn it off. Edit: I fixed this my editing a line in about:config.

This is a ridiculous amount of trouble just to get a Firefox icon.

---

### Post by AndyAWS on 2006-06-04
I lost all plugins doing this script. To restore them I simply re-installed firefox from synaptic.

---

### Post by edwing on 2006-06-04
If you've lost all your plugins after using the fix-firefox script, here's how you can get them back:

```
sudo mv /usr/local/firefox/plugins /usr/local/firefox/plugins-orig
sudo ln -s /usr/lib/mozilla-firefox/plugins /usr/local/firefox/plugins

```
Restart firefox and all should be well :)

---

### Post by Dave N on 2006-06-05
[QUOTE=Pu7o]OK, here's the thunderbird one:

```

wget http://kernel.ws/~puto/fix-thunderbird
sudo sh fix-thunderbird
(It'll ask for your password, insert it, then wait)

```[/QUOTE]

Worked great, thank you

---

### Post by Pu7o on 2006-06-06
I fixed the script so you don't get problems with plugins, and if you want a language different than en-GB, then instead of typing:

```

sudo sh fix-firefox

```

type:

```

sudo sh fix-firefox pt-BR

```

( pt-BR is an example here, change it to whatever language you want. List of languages available at [http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.4/linux-i686/](http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.4/linux-i686/) )

---

### Post by edurm on 2006-06-06
......

---

### Post by dicecca112 on 2006-06-06
this brok evolution, if I click on links in emails it won't open them.  How do I fix this?

---

### Post by Psquared on 2006-06-07
FF worked great, but TB did not. I am using Breezy with the latest version of FF and Thunderbird obtained using Automatix.

The icon for TB is in the pixmaps folder but when I select it for TB in the top starter bar it adds a "mailbox" icon instead of the TB icon. That is so weird because the right icon is in the file, but it adds a different one.

Any ideas.

---

### Post by blitzer on 2006-06-07
Pu70 thanks for putting the [COLOR="Red"]FOX [/COLOR]back in Firefox.

---

### Post by poekie on 2006-06-15
The trouble is that this actually installs thunderbird. If you're using mozilla-thunderbird, this stops working. Now, when you're a lazy sh*t like I am, you don't want to move all your mail and stuff, so how to undo this fix-thunderbird? Just uninstall thunderbird and use mozilla-thunderbird? (If that actually works again)

[edit] I've got all my mail back in mozilla-thunderbird and in working order. Now to chage that English language pack back to Dutch :) )

---

### Post by jdusablon on 2006-06-15
I'm going to agree with most here. This script is terrible. My fonts are funny-looking now, and I don't like en-gb. Also, it's not very cool that it installs other apps like thunderbird.

Worth the trouble for an icon or two? No.

I suppose that's what I get for not reading the fine print (read: the actual contents of a script before running it!)

---

### Post by garenasix on 2006-06-16
[QUOTE=jdusablon]I'm going to agree with most here. This script is terrible. My fonts are funny-looking now, and I don't like en-gb. Also, it's not very cool that it installs other apps like thunderbird.

Worth the trouble for an icon or two? No.

I suppose that's what I get for not reading the fine print (read: the actual contents of a script before running it!)[/QUOTE]

yeah i gotta say the same you get alittle more then just the icons i just had to reinstalled firefox with synaptic to get my old firefox back  then searched around  folders and found the eyecandy icon lol and  changed it out on just my desktop .. all is good .. only thing is i got 2 different firefox files on my michine the real one and the hack one now

---

### Post by The Darkness on 2006-06-16
The Fox is Back!!!
very nice,
Thx

---

### Post by bionnaki on 2006-06-16
[QUOTE=jdusablon]I'm going to agree with most here. This script is terrible. My fonts are funny-looking now, and I don't like en-gb. Also, it's not very cool that it installs other apps like thunderbird.

Worth the trouble for an icon or two? No.

I suppose that's what I get for not reading the fine print (read: the actual contents of a script before running it!)[/QUOTE]

yeah, that script sucks. waste of time.

---

### Post by Drobbins on 2006-06-16
[QUOTE=bionnaki]yeah, that script sucks. waste of time.[/QUOTE]

Worked Perfectly for me :confused:

---

### Post by WetWilly on 2006-06-16
for those of you that dont want to update and other sh*t, just simple change of icons put this text and save it a sh file:

```
#!/bin/bash

wget -c http://www.cs.cornell.edu/~djm/ubuntu/mozilla-icons/mozilla-firefox.png
wget -c http://www.cs.cornell.edu/~djm/ubuntu/mozilla-icons/document.png
chmod 644 mozilla-firefox.png document.png
dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.png
dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.xpm
dpkg-divert --rename /usr/lib/mozilla-firefox/icons/default.xpm
dpkg-divert --rename /usr/lib/mozilla-firefox/icons/document.png
dpkg-divert --rename /usr/lib/mozilla-firefox/chrome/icons/default/default.xpm
cp mozilla-firefox.png /usr/share/pixmaps/mozilla-firefox.png
cp mozilla-firefox.png /usr/share/pixmaps/mozilla-firefox.xpm
cp mozilla-firefox.png /usr/lib/mozilla-firefox/icons/default.xpm
mv document.png /usr/lib/mozilla-firefox/icons/document.png
mv mozilla-firefox.png /usr/lib/mozilla-firefox/chrome/icons/default/default.xpm
```

then run it with 

sudo sh whateveryousavedthefileas.sh

---

### Post by garenasix on 2006-06-16
this script clamed to change the icons nothing was said about the part that it changed your firefox to the en-gb and installing that ontop of your old firefox 
just reinstalling firefox to get your old one back helps but i still have some problems now im still stuck with all the crap that came with this script and i now have strange stuff going on with afew other things my mouse now acts strange my display to if i click an icon in my taskbar the michine now locksup for a few seconds ... sorry but im alittle pissed now at all this .. and yeah the script was missrepresented in this forum    and it does suck ... if this was a windows michine id be thinking that is has spyware .. cause that is how my michine is acting now

---

### Post by bionnaki on 2006-06-16
yea, and whatever build of firefox that script installed is really buggy - it did not handle several javascripts correctly.

I uninstalled
and reinstalled
to get back to normal.

---

### Post by bionnaki on 2006-06-16
[QUOTE=WetWilly]for those of you that dont want to update and other sh*t, just simple change of icons put this text and save it a sh file:

```
#!/bin/bash

wget -c http://www.cs.cornell.edu/~djm/ubuntu/mozilla-icons/mozilla-firefox.png
wget -c http://www.cs.cornell.edu/~djm/ubuntu/mozilla-icons/document.png
chmod 644 mozilla-firefox.png document.png
dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.png
dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.xpm
dpkg-divert --rename /usr/lib/mozilla-firefox/icons/default.xpm
dpkg-divert --rename /usr/lib/mozilla-firefox/icons/document.png
dpkg-divert --rename /usr/lib/mozilla-firefox/chrome/icons/default/default.xpm
cp mozilla-firefox.png /usr/share/pixmaps/mozilla-firefox.png
cp mozilla-firefox.png /usr/share/pixmaps/mozilla-firefox.xpm
cp mozilla-firefox.png /usr/lib/mozilla-firefox/icons/default.xpm
mv document.png /usr/lib/mozilla-firefox/icons/document.png
mv mozilla-firefox.png /usr/lib/mozilla-firefox/chrome/icons/default/default.xpm
```

then run it with 

sudo sh whateveryousavedthefileas.sh[/QUOTE]

worked perfectly! thanks.
now, what about thunderbird?

---

### Post by jdusablon on 2006-06-17
> for those of you that dont want to update and other sh*t, just simple change of icons put this text and save it a sh file:
Now THAT's what I call making lemonade from lemons.

Very helpful, thanks, **wetwilly**!:D

---

### Post by poekie on 2006-06-18
[QUOTE=garenasix]this script clamed to change the icons nothing was said about the part that it changed your firefox to the en-gb and installing that ontop of your old firefox 
just reinstalling firefox to get your old one back helps but i still have some problems now im still stuck with all the crap that came with this script and i now have strange stuff going on with afew other things my mouse now acts strange my display to if i click an icon in my taskbar the michine now locksup for a few seconds ... sorry but im alittle pissed now at all this .. and yeah the script was missrepresented in this forum    and it does suck ... if this was a windows michine id be thinking that is has spyware .. cause that is how my michine is acting now[/QUOTE]

I agree with you, ever since I used this script FF uses way more time starting up. And I have to click the icon twice, because the first time it loads and loads and nothing happens. 
My thunderbird is still in English as I can't seem to change it's locale to Dutch. 
Pretty f*cked up... 
Furthermore, since I used the script, Thunderbird wanted to go in Systray 
(the actual program, not just a new mail notifier) and I got rid of thunderbird (using mozilla-thunderbird again) but now other programs like gaim and konqueror want to go in systray as well. Very irritating. I have no idea how to make it stop...

---

### Post by Owdy on 2006-06-18
This script broke my Finnish locale. Firefox is now english. How do i fix this?

edit: Fixed with this [http://ubuntuforums.org/showthread.php?t=186337]("http://ubuntuforums.org/showthread.php?t=186337")

---

### Post by andrewabc on 2006-06-25
Thought I'd say thanks for the fix. The other icon isn't as good looking as the fox.

---

### Post by oskvaz on 2006-07-09
Good job!!! looks very foxy.

---

### Post by jamadagni on 2006-08-20
This method practically downloads the original Mozilla binaries of Fx and Tb for Linux. Somewhere I read that Debian people worked hard on integrating Fx and Tb with the rest of the distro, so I think we may be losing out on such functionality.

---

### Post by Owdy on 2006-08-20
> **jamadagni said:**
> This method practically downloads the original Mozilla binaries of Fx and Tb for Linux.  Yes it does and theres no need for that. It brakes things. It should be written in first post that script does that.

---

### Post by Jeeks on 2006-09-20
Thank you for the HOWTO, it was amazing to see the fox and the bird back :)

I have a problem though, I was using aoss so that flash would work with sound. The settings of firefox are still the same however there is no sound coming from flash websites.

What can I do to fix it?

---

### Post by Jeeks on 2006-09-20
Anyone?

---

### Post by Jeeks on 2006-09-23
Bumping again

---

### Post by termite on 2006-09-24
try changing aoss to alsa in your /etc/firefoxrc file.

Can't promise it'll work, but it did for me.

---

### Post by Jeeks on 2006-10-06
Cheers, I am no longer using ubuntu, I changed to Gentoo, where the grass is greener.

---

