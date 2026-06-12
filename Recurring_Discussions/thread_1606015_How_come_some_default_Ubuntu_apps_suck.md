---
title: "How come some default Ubuntu apps suck?"
date: 2010-10-26
forum: Recurring Discussions
---

### Post by cosmolee on 2010-10-26
My question is why do some default Ubuntu applications get chosen, when they suck and there are better apps available?

In a post about how to play encrypted DVDs on Ubuntu, [http://blog.sudobits.com/2010/05/04/how-to-play-encrypted-dvd-in-ubuntu-10-04/comment-page-1/#comment-1902]("http://blog.sudobits.com/2010/05/04/how-to-play-encrypted-dvd-in-ubuntu-10-04/comment-page-1/#comment-1902")

I made some comments about problems I've had playing DVDs with Totem, the default movie player:

> 
I have the same problem on a completely fresh install of 10.04. 

Ubuntu offers to run Totem “Movie Player” upon insertion of the DVD. A pop-up offers to find plugins to be able to play “DVD source”. This, despite the fact that I’ve already installed the libdvdread4 package and run the shell script as instructed. The search, however, doesn’t find any plugins that can play the DVD. The movie player doesn’t seem to have any idea that the decryption libraries have been installed.

I installed VLC and it is able to play the DVD fine. I’ve never liked the Totem player and have often had problems with it. I think it’s junky and I don’t know why the Ubuntu team makes it the default player, because it does not provide a good user experience with its problematic usage…


I've had problems with Totem for years.  It's been crap for years on my various computers.  It's especially junky when it comes to playing alternate audio tracks in video files.  

I've always had to resort to VLC as an alternative when Totem was junking out.  But Totem has remained the default player for media, and it must be giving other users the same crap experience too.  So many times it just doesn't work right.  And it has finally bothered me so much that I have to ask here, "If it sucks so badly, why does it continue to be the default player?  Who makes such a crap decision?"  It must provide a terrible impression to new users of Ubuntu, leading to the impression that Ubuntu is not ready for normal users.  I've used Ubuntu for years, and this kind of experience makes me disgusted with Ubuntu.

Another issue: Brasero sucks.  Why does it suck?  Because it doesn't verify written media.  If you can't verify written media, you can't trust the copy.  It's that simple.  

CD/DVD writing is a VERY error prone activity.  Anyone who verifies their burned media knows this.  This is particularly problematic when it comes to burning ISOs or backups.  If one is burning ISOs to install applications or an OS or backups of important data, one wants to be darned sure that all the bits are accurate.  But Brasero doesn't have it as an option.  That's crap!  Why is it the default burning application is a crap one?!  If you make a crap backup you're screwed!

I've always resorted to K3B to burn ISOs, which verifies.  Time and again, I've burned media with Brasero, only to do MD5SUMs manually to find that I'd gotten a bad burn.  But if I didn't do that, I'd never know.  And that means that lots of people are getting crap burns, but don't even know it.  Oddly, Brasero and K3B seem to use the same underlying libraries, WODIM or something by that name.  But I continually get bad burns on the same computers with Brasero vs K3B.  

OK, rant mode off...](*,)

---

### Post by kerry_s on 2010-10-26
it all works fine here & suspect it works fine for many others. your issues could be all hardware related.

the programs you use are qt, gnome is gtk, i don't think they will ever mix tool kits.

i do use the standard burner
for video i prefer gnome-mplayer

---

### Post by tcelgen on 2010-10-26
This has to do with a lot of factors. 

1. Limited space on the release media. 
2. The default GNOME applications, Totem is the official movie player of the GNOME desktop environment based on GStreamer.
3. Toolkit environments. It would be inconsistent to use QT applications as you would require both libraries.
4. Popular software can be installed easily from the repositories/software center.
5. Not everyone has the same issues you have described.

---

### Post by garvinrick4 on 2010-10-26
App's are like beauty, in the eye of the beholder.

---

### Post by Elfy on 2010-10-26
moved to recurring

---

### Post by johntaylor1887 on 2010-10-30
Actually, Brasero does have a verify feature. It's in Tools>Check Integrity

---

### Post by uRock on 2010-10-31
You are entitled you opinion, but if you don't like the defaults, then do a minimal install and install what you like.

I install the default system, then run a command that removes unwanted programs, then runs updates, then reboots the system, then I run another line that installs everything I want and need.

---

### Post by Rubi1200 on 2010-11-01
Care to elaborate on this uRock?

What do you remove/what do you add?

Are you using a bash script?

---

### Post by uRock on 2010-11-01
Here are the two command sets that I run upon install. They change slightly depending on which machine I am installing on, but these are the ones I snagged from my latest test install.
```
sudo apt-get remove empathy evolution gwibber gnome-games -y && sudo apt-get update && sudo apt-get dist-upgrade -y && sudo reboot

sudo apt-get install zenmap ubuntu-restricted-extras gparted thunderbird pidgin sound-juicer linux-firmware-nonfree vlc htop xchat-gnome gufw apparmor-profiles alltray parcellite clamav clamtk gimp supertuxkart supertux ubuntustudio-desktop -y
```

---

### Post by Rubi1200 on 2010-11-01
Thanks for the information; much appreciated :)

+1 to vlc and htop; these are also amongst the first programs I always install.

---

### Post by uRock on 2010-11-01
You're welcome.:guitar:

---

