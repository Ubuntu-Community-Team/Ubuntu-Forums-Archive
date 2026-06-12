---
title: "No UI.........Still!!"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by zizzle on 2008-08-25
Hi, I posted a couple of days ago and patiently waited for some help/advice.  The problem is this - I d/ld ubuntu studio and set it up ok. When it came to first boot and log in, it was all ok until after I pressed enter. No gui. I tried the recommended "startx" command and still nothing but a prompt telling me that it wasn't installed. So I followed the instructions to install it (sudo apt get, etc) and still nothing. 
After receiving little or no help form the forum, I decided to format my whole disk and start again. This meant, of course, that I l had to do away with my Vista installation as well. As you can imagine this p*ssed me off to a very great extent. reloaded Vista, reloaded Ubuntu Studio and lo and behold, the same thing again.
Is any one going to help??
Intel celeron D, 3.2ghz, 160 gig, 1 gig ram, Vista.

 Thanks, Mike.

---

### Post by stubblepoo on 2008-08-25
why did you format vista? surely it was on another partition? are you installing the newest version of ubuntu studio?, maybe try sending of for a live cd if you can wait, i have never managed to successfully install ubuntu from a dl'ed iso, but it always works with an ordered livecd, and its free.

---

### Post by Thelasko on 2008-08-25
> I decided to format my whole disk and start again. This meant, of course, that I l had to do away with my Vista installation as well.
Why did you do that?  You can format just your Ubuntu partition.

About your Ubuntu Studio install.  I've helped a few people with it in the past.  I've never used it personally, but from what I gather, the installation disk isn't very good.  [I wrote a suggestion to fix it.]("http://brainstorm.ubuntu.com/idea/11864/")

**[SIZE="3"]The best way to install Ubuntu Studio:[/SIZE]**
[LIST=1]
[*]Install the [regular version of Ubuntu]("http://www.ubuntu.com/getubuntu/download") from CD.

[*][Upgrade]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy") your installation with by opening the terminal and entering:
```
sudo aptitude update && sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```
[/LIST]

Other people I've talked to have had success with this approach.  Sorry, I didn't see your original post.

---

### Post by howlingmadhowie on 2008-08-25
the problem is probably that the default window manager (compiz) is not playing well with your graphic card driver. try editing $HOME/.gconf/desktop/gnome/applications/window_manager/%gconf.xml to replace the word "compiz" with metacity. the file should then look something like this:

```
<?xml version="1.0"?>
<gconf>
        <entry name="current" mtime="any_old_numbers" type="string">
                <stringvalue>/usr/bin/metacity</stringvalue>
        </entry>
        <entry name="default" mtime="any_old_numbers" type="string">
                <stringvalue>/usr/bin/metacity</stringvalue>
        </entry>
</gconf>
```

then restart the x-server and log in.

to edit the file, you can either log in to gnome in rescue mode (whatever it's called) and edit the file in a text editor, or use the command line by going to a virtual terminal.

---

### Post by zizzle on 2008-08-25
Hi guys,:)
Thank you all for your prompt replies.
I'm going to get straight on the case with these solutions!
the reason that I didn't format just the Ubuntu drive, is I don't know how to. All I would like to do is get away from windows and all that stuff and learn to use a sensible OS like ubuntu.
Thanks again guys, Catch ya later.
Mike aka zizzle

---

