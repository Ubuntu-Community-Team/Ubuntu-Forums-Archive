---
title: "reinstalling ubuntu"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Sham885 on 2008-05-31
After nothing but repeating problems trying to get ubuntu to recognize my new radeon x1650 card I finally decided to just reinstall it.  So I used windows to wipe the partition, put in the live cd, booted up, and was met with ubuntu log in screen but all the text was in squares.  I tried to type in a login but nothing happened.  I hit ctrl+alt+F1 and saw the following message repeated across the screen "User not known to the underlying authentication module".  I can't enter any commands.  So I'm still stuck with no working os on my computer and had to stop by the office to type this.  I can see why people give up on linux.  How do I manage to put a clean install of ubuntu back on my computer?

---

### Post by Crafty Kisses on 2008-05-31
What are your system specs?

---

### Post by pytheas22 on 2008-05-31
It sounds like a problem with the live CD.  Is it the same one you used to install Ubuntu the first time?  Did you try checking it for defects (there's an option for this at the first screen after BIOS finishes)?

Also, [envy]("http://www.albertomilone.com/nvidia_scripts1.html") makes it very easy to get the drivers set up for ATI and nvidia video cards.  You might want to take a look at it for your Radeon card.

---

### Post by ugm6hr on 2008-05-31
> was met with ubuntu log in screen but all the text was in squares

The LiveCD does not require a login.

Which version of Ubuntu are you using?

Did you run the "check CD" option?  Did you check md5 before burning?

---

### Post by Sham885 on 2008-05-31
I couldn't install envy because I had no internet connection in recovery mode (only way I could get it to do anything) to get it or update the drivers.  Which is why I finally gave up.  No internet and no way to add files to ubuntu so I saw no way to get a working driver.

I have a dell dimension xps gen 2 with some parts replaced.  3.0ghz P4, 2gb ram, the x1650 graphics card, 250gb harddrive divided into ~100gb ntfs for xp, ~50gb formatted as FAT32, and the last 100gb is now unformatted.  I did have it connected to a vga monitor but I couldn't find a setting in ubuntu (used dpkg-reconfigure xserver-xorg) that would work on it so I now have my dell crt monitor connected which ubuntu automatically detects.

I ran a check on the livecd I used to install the first time and it had 3 file errors so I burnt a new copy of ubuntu 8.04 off ubuntu.com yesterday and am using that.

---

### Post by ugm6hr on 2008-05-31
> **Sham885 said:**
> I ran a check on the livecd I used to install the first time and it had 3 file errors so I burnt a new copy of ubuntu 8.04 off ubuntu.com yesterday and am using that.

Is it this CD that gives you a login screen?  If so - there is a problem with that one too.

---

### Post by WRDN on 2008-05-31
I think you can install using a text based installer even on the normal Live CD. Someone else will have to give you the commands though, as I dont know them.

Im very intrigued though as to why you got a login screen if you were booting from the live CD. Though the disk errors will probably have caused it, its still very wierd.

---

### Post by sayakb on 2008-05-31
[http://ubuntuforums.org/showthread.php?t=804362](http://ubuntuforums.org/showthread.php?t=804362)

ugm6hr helped me out :)

---

### Post by Sham885 on 2008-05-31
I burnt another cd at half the max speed and ubuntu installed.  :)  Then I set something for 3D graphics, restarted, and now I have a white screen.  I'm not sure whether to laugh at myself or start banging the keyboard against my head. :lol: ](*,)

---

### Post by pytheas22 on 2008-05-31
When do you get the white screen?  If it's after you login to the desktop, there's a good chance that it has to do with desktop effects.  Press alt-f2, type:

```
metacity --replace
```
(you won't see anything, but just type it and press enter) to turn compiz off, and hopefully the white screen will go away.  From there we can figure out what's wrong with compiz on your system (this is a common issue and it's usually not hard to work around).

If you're getting the white screen at another point, please tell us when.

---

