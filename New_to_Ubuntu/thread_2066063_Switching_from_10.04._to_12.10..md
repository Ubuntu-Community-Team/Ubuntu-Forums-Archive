---
title: "Switching from 10.04. to 12.10."
date: 2012-10-03
forum: New to Ubuntu
---

### Post by Vladimir Pavic on 2012-10-03
[SIZE=2][COLOR=#800000][FONT=Verdana, sans-serif]**[COLOR=#314004][B]Hello!**[/COLOR][/B][/FONT][/COLOR][SIZE=2]
[/SIZE]**[COLOR=#314004][FONT=Verdana, sans-serif][B][SIZE=2]I am preparing myself for switching from Ubuntu 10.04. to[/SIZE] **[/FONT][/COLOR][/B]  [SIZE=2]**[COLOR=#314004][B]Ubuntu 12.10 Quantal Quetzal on 18**[/COLOR][/B]**[COLOR=#314004][B]th**[/COLOR][/B]**[COLOR=#314004][B] October. As I am a beginner, please let me know how to do it step-by-step. For example, I know that I am supposed to do backup just in case something went wrong. But, how to do it? Please give me necessary tips and hints. **[/COLOR][/B] 
**[COLOR=#314004][B]Thank you.**[/COLOR][/B]  
**[COLOR=#314004][B]Vladimir**[/COLOR][/B][/SIZE][/SIZE]

---

### Post by GreatDanton on 2012-10-03
Instead of upgrading make a fresh install. This will save your time, and the system won't have any strange problems/artefacts. Backup all your data, make live cd/usb and install the new OS. You can also make separate home and root directory, so you will not have to install everything from scratch but only the root directory.

In which part of step by step are you interested? Making live usb, installation or something else?

Regards.

---

### Post by Vladimir Pavic on 2012-10-03
Thank you for prompt response. I plan to download the new OS from Internet and store it onto a USB memory stick. Or is it better to have it on a CD?

---

### Post by cryptotheslow on 2012-10-03
Either USB stick or CD is fine - it just depends which your computer will boot from.

You can't just "store" the downloaded OS iso file onto the stick or CD you need to create a bootable stick or CD using the file.

For CDs I use Brasero Disc Burner.

For USB sticks I either use the standard Startup Disc Creator or UNetbootin.

You'll be able to find all of those in Synaptic Package Manager if they are not already present on your system.

As per GreatDanton I would also recommend a clean installation over going through the upgrade process. v10.04 to v12.10 is a very significant change, particularly with the switchover from Gnome2 to Gnome3 based desktop.

1. Backup the contents of your home directory to an external drive or DVD etc. Somewhere that you can physically remove it from the machine whilst you do the new installation or upgrade.
** Make sure to include the hidden directories with names that start with a dot.
*** Triple check you can read your backed up files!

2. Make your bootable USB stick or CD.

3. Boot from your USB stick or CD and take the option to Try Ubuntu without installing. This will give you an opportunity to try the new version without changing anything on your computer. This is a great way to check the basics such as making sure your graphics work OK without tweaking. Much better to find this out using the LiveCD than when you are halfway through installing!

4. When you are happy you want to go ahead with the new installation - check your backups are OK again just to be sure. :)

How you proceed from there depends on whether you are going to do a clean installation or try the upgrade path.

---

### Post by thatguruguy on 2012-10-03
> **Vladimir Pavic said:**
> Thank you for prompt response. I plan to download the new OS from Internet and store it onto a USB memory stick. Or is it better to have it on a CD?

12.10 won't fit on a CD, so a USB stick is probably a better bet. Plus, they seem to work somewhat faster, in my experience.

---

### Post by AlanR8 on 2012-10-03
And....installation from a USB stick is much quicker than from an optical disk.

Would go with the general advice to do a fresh install rather than an upgrade as well.

---

### Post by cryptotheslow on 2012-10-03
> **thatguruguy said:**
> 12.10 won't fit on a CD, so a USB stick is probably a better bet. Plus, they seem to work somewhat faster, in my experience.

Is that just because it is currently in Beta and a bit bloated at this point in the cycle or is it intended that it will be released in DVD size iso?

I seem to remember when testing 12.04 there were a few times in the cycle that the image exceeded CD size but it was always intended that it would be trimmed back to fit for final release.

---

### Post by Pletched on 2012-10-03
Is 12.10 another LTS release? Why switch from 10.04 to 12.10? Your next stop should be 12.04 LTS.

---

### Post by Vladimir Pavic on 2012-10-04
[COLOR=#800000][FONT=Verdana, sans-serif][SIZE=2][COLOR=#314004]Dear Ubuntu brethren,[/COLOR][/SIZE][/FONT][/COLOR]
 [COLOR=#800000][FONT=Verdana, sans-serif][SIZE=2][COLOR=#314004]Thank you for your helpful suggestions. I will definitely follow your advice. Now, I am waiting 18[/COLOR][COLOR=#314004]th[/COLOR][COLOR=#314004] October for the final version of 12.10.[/COLOR][/SIZE][/FONT][/COLOR]
 [COLOR=#800000][FONT=Verdana, sans-serif][SIZE=2][COLOR=#314004]Or should I install 12.04 LTS as Pletched suggests? I am confused about this issue. What is better – 12.10. or 12.04 LTS? 
[/COLOR][/SIZE][/FONT][/COLOR]
 [COLOR=#800000][FONT=Verdana, sans-serif][SIZE=2][COLOR=#314004]Greetings from Bosnia![/COLOR][/SIZE][/FONT][/COLOR]

---

### Post by zombifier25 on 2012-10-04
> **Vladimir Pavic said:**
> [COLOR=#800000][FONT=Verdana, sans-serif][SIZE=2][COLOR=#314004]Dear Ubuntu brethren,[/COLOR][/SIZE][/FONT][/COLOR]
 [COLOR=#800000][FONT=Verdana, sans-serif][SIZE=2][COLOR=#314004]Thank you for your helpful suggestions. I w
ill definitely follow your advice. Now, I am waiting 18[/COLOR][COLOR=#314004]th[/COLOR][COLOR=#314004] October for the final version of 12.10.[/COLOR][/SIZE][/FONT][/COLOR]
 [COLOR=#800000][FONT=Verdana, sans-serif][SIZE=2][COLOR=#314004]Or should I install 12.04 LTS as Pletched suggests? I am confused about this issue. What is better – 12.10. or 12.04 LTS? 
[/COLOR][/SIZE][/FONT][/COLOR]
 [COLOR=#800000][FONT=Verdana, sans-serif][SIZE=2][COLOR=#314004]Greetings from Bosnia![/COLOR][/SIZE][/FONT][/COLOR]

If you want stability and 5 years of support, use 12.04. If you want the latest and greatest, use 12.10.

---

### Post by vasa1 on 2012-10-04
I agree with all of what has been suggested here:
"Burn" the download to USB using the standard Startup Disc Creator or UNetbootin.
Do a clean install and not an upgrade since too many things have changed.
Depending on your personality, you may decide between 12.04 and 12.10. It's difficult to suggest one over the other without knowing more.

The nice thing about going for 12.04 now is that many initial issues have been sorted out over the past ~5 months. So you should be relatively okay.

The other big thing that hasn't got much of a mention here is the flavor of 12.04/12.10 you should go for. Be aware that Unity is quite, quite different from what you've been used to.

I suggest you head over to YouTube and look at as many distros as you feel like. Here's one on Unity:
[http://www.youtube.com/watch?v=xA9EHaNc2VI](http://www.youtube.com/watch?v=xA9EHaNc2VI)
Look for videos by **quidsup**. They're pretty decent (once you get used to his accent).

If you like reading about Unity, here's a nice presentation:
[http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-basic-unity-interface-desktop-tutorial](http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-basic-unity-interface-desktop-tutorial)

Also keep in mind the age of your hardware and its specs. If you put your specs here, people may have more suggestions to offer.

---

### Post by Vladimir Pavic on 2012-10-04
OK. I have got the point. 12.04. LTS is for me.
Big thanks!

---

### Post by thatguruguy on 2012-10-04
> **cryptotheslow said:**
> Is that just because it is currently in Beta and a bit bloated at this point in the cycle or is it intended that it will be released in DVD size iso?

I seem to remember when testing 12.04 there were a few times in the cycle that the image exceeded CD size but it was always intended that it would be trimmed back to fit for final release.

Canonical announced that there is[ no longer a CD-sized image of Ubuntu]("https://wiki.ubuntu.com/QuantalQuetzal/TechnicalOverview/Beta2#Ubuntu"). The new image size is 800MB, and that will not be shrunk down to CD-sized for the launch of 12.10.

---

