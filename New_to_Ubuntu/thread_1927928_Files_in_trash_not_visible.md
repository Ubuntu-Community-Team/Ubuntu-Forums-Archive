---
title: "Files in trash not visible"
date: 2012-02-19
forum: New to Ubuntu
---

### Post by mopalia on 2012-02-19
When I open Trash (icon on panel) there is nothing listed.  But Properties shows 410 files in Trash.  When I delete something, it seems to vanish and still doesn't show up in Trash.  Is there any way to retrieve the folder that I just accidentally sent to Trash but that doesn't show up there? (running 10.04) TIA

---

### Post by Gone fishing on 2012-02-19
I'm not sure why the files aren't appearing in trash when you click the trash bin, however, your deleted files should be in 

/home/your_username/.local/share/Trash/files

I hope you can find the files you accidentally deleted

---

### Post by mopalia on 2012-02-19
No luck - I get 
bash: /home/mopalia/.local/share/Trash/files: No such file or directory

The files must delete immediately without going into trash.  I wonder why?  Hmm, maybe because there's no such directory!  Maybe I can fix this... Thanks!

---

### Post by winh8r on 2012-02-19
Any files deleted by root or whilst using nautilus will not be visible in Trash.

Check which user you are running as when deleting files, but most of all , be very careful before you delete anything!!


To view files deleted by root you will need to launch

```
gksudo nautilus
```

and navigate to 

/root/.local/share/Trash/files


remember to use ctrl +H to show hidden files


you should be able to view them all this way (and recover if needed)

---

### Post by mopalia on 2012-02-19
Thanks - I did all that, but the only thing in there is a font I deleted in 2007!  I know that there are problems with this installation, and this must be one of them.  Time for a new install.  I give up on the files, I'm sure they're gone. I was trying to re-size an icon when I slipped and grabbed move to trash instead.  I wish I could rearrange that menu, or always default to the smallest possible icon.  :(
Thanks for the very lucid help, though - at least I learned something.

---

### Post by winh8r on 2012-02-19
Just a thought, you can boot your machine from a live cd and run testdisk/photorec on the drive 

```
sudo apt-get install testdisk
```

you can set it to only look for specific types of files and it usually gives very good results.

there is a wiki with how-to's here:

[http://www.cgsecurity.org/wiki/Main_Page]("http://www.cgsecurity.org/wiki/Main_Page")


And also, YES it is time for an upgrade!!!!!

---

### Post by mopalia on 2012-02-19
Actually, I have upgraded, which makes the 2007 files a mystery.  I've run Meerkat and Ocelot and sadly find myself with the people who can't stand Unity.  I gave it a good try and concede that the 4-split screen and the search bar are nice. but not enough to overcome the giant Icons and the totally unintuitive (for me) way things are laid out.  So I've put off cleaning up my system while I mull over the possibilities of Mint vs.PC-BSD.  All of which makes me very unhappy, since I've been a devoted Ubuntu user since before Hardy Heron.   
But maybe I'll play with the live CD idea - it will be good practice.  Thanks again!

---

### Post by Gone fishing on 2012-02-20
I find it odd that Trash isn't where I said it should be so try running

sudo find / -type d -name *Trash*

This should find where your Trash directory is.

Sorry you don't like Unity - personally I quite like it and feel when it is mature it will be a great improvement. Mint is cool and well liked, coming from Ubuntu you wont find it very different (it is based on Ubuntu). PCBSD is also cool I like FreeBSD on servers a lot, however, you will find PCBSD quite different and it has less available software etc. I would have thought Kubuntu would be worth a look at if you are considering a KDE distrobution (PCBSD is KDE) and also OpenSuse which has one of the best KDE desktops.

---

### Post by winh8r on 2012-02-20
You could always go back to a gnome environment if you do not like Unity, have a look here:

[http://mate-desktop.org/]("http://mate-desktop.org/")

I use it on my 11.10 installation and find it is closer to what I need.


Good Luck.

---

### Post by mopalia on 2012-02-20
That worked!  I have them all back, thank you.  ThankYou!
I don't object to the way Unity works, I could get used to that.  But I live with an almost perpetual migraine and excess movement on the screen aggravates it and makes work impossible. This is why I hate Macs - everything seems to include a "whoosh" or some superfluous animation. I find it difficult to focus on the large icons, too. I work with everything I am currently using on the desktop, with he smallest possible icons - which is why it's easy to accidentally click "Move to Trash" instead of "Stretch Icon."  My desktop horrifies everyone, but it's been working for me since I left DOS 3.x. Believe it or not, this is the first time I've ever lost a folder. I should probably just buckle down and learn to use the command line exclusively. Thank you again for your help.

---

### Post by mopalia on 2012-02-20
Oh, MATE is interesting.  I will give that a try before giving up Ubuntu - because really, where will I ever find such great people on the help forum?  Thank you - not only has my missing folder been found, I've got a problem solved that I didn't even ask about.  I am happy!

---

### Post by Gone fishing on 2012-02-21
Mopalia could you mark as solved and say what worked.

Very pleased you got your data back. :D

---

### Post by mopalia on 2012-02-21
Thanks for the reminder - file marked as solved.  What worked: 

sudo find / -type d -name *Trash* 
gave me:
/home/my_name/.local/share/Trash

Going there and using Crtl H brought up all the mysteriously missing files.  (and 2 GB of other deleted files, since I had not been able to clear Trash for a while.)  

I now have back hours of research on Tennis for Two, The Space War Arcade game, and our Taiko no Tatsujin game.  Thank you!

judith
digitalgamemuseum.com

---

