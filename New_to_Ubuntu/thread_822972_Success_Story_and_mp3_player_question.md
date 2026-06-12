---
title: "Success Story and mp3 player question"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by squid68 on 2008-06-08
My friend who is not too computer savoy's 2002 AMD system running XP was in trouble.  It needed to have the mainboard replaced as well as the power supply and the XP had way too many issues to diagnose. I intended to reinstall XP but the computer would not read the CDs. But I was able to get an Ubuntu live CD to work on it. So I convinced her to make the change. She pretty much needs a computer to type papers for school, search the internet with her newly added cable modem she just recently got and to manage her music players.  When I was working on her to decide her decision was mainly based on the fact that Ubuntu Linux was not going to steal all her system resources just to turn on, has little to no virus, adware, spyware, threats, and cleans it self when told (cookies, no temp files, etc.) and well simply is not XP.  Her dad has been in a never-ending nightmare with a new computer running Vista and she wanted none of that.

I installed Hardy and got it up and running.  I had to replace the Firefox 3 Beta 5 because of font issues--I could not even read or search these forums because of it.  After reading 4 or 5 posts I found the easy way to do it. I used Synaptic to remove it and install Firefox 2.  I had to rename the .mozilla folder in the home folder to get the addons and plugins to work then deleted the folder when the new one got made.  That took another post reading.  

I used the unrestricted extras to let sound juicer rip to mp3s and got gtkpod running to allow her to add and remove songs from her iPod Nano. I saw way too many posts of people complaining which program is better or not but none on why it was needed or how to use them.  I found a post from here that linked to simplehelp.net and it did the trick.  I had gotten my girlfriend a Sony Walkman player and it needed nothing to work with Ubuntu so this iPod thing was new to me.

But here is the success. Jen had not even heard of Linux before never mind not knowing what it was.  Ubuntu, Linux huh?  

She was impressed that everything worked right away.  It worked with all her hardware and with no drivers. It found her recently installed cable modem in seconds and needed no tweaks.  She was seriously impressed with how easy and fast it was to rip CDs with Sound Juicer and how easy and fast it was to use gtkpod to load songs versus iTunes.  She liked Firefox and the cool plugins it has.  She also was impressed with the amount of cool software included in the distro.  

I got her the computer this morning and gave her like a 2 hour lesson.  Spending 10 minutes on the phone was all we needed to get the gtkpod up, running, and her using it.  I gave her my copy of Moving to Ubuntu (which I intend to replace), and she is way happy now.  A non-computer geek has been converted, has a cool book to learn from and is finally happy with her dinosaur computer. If her car did not need unexpected repairs then maybe improvements could have been made. But that is a different matter.  So Vivat Ubuntu!  And welcome Jen into the Linux world.

But I do have a question. Her boyfriend has two Scandisk Sansa mp3 players.  When plugged in none of them show up.  I am not sure how to get the system to recognize them.  Any ideas?  Also I tried to have her set the removable drives and media settings to open gtkpod when her ipod is connected but she said Hardy was not showing the Multimedia tab.  I am just about to upgrade from Gusty to Hardy so I am not sure what is up with that. Any ideas on that as well?  Thanks.

---

### Post by laptoplinux on 2008-06-10
Do the mp3 players use MTP (Media Transfer Protocol) for file transfer?  MTP is a Microsoft Windows protocol, with hooks for all the DRM "goodies" you've come to expect from Microsoft built right in. It's been my experience that the Sansa players are all too happy to announce how compatible with Windows Media Player and "Plays for Sure" they are, so MTP is one place to start looking.

(If memory serves, all Plays for Sure media will be rendered unplayable once MS throws the killswitch on the DRM validation servers on August 31, 2008, but I digress)

In the Hardy repos, there is a libmtp package that should allow Hardy to read and write to MTP devices.  I'm not sure if it is in the Gutsy repos or not.

I don't know for sure that that is the problem, but I hope this helps.

---

