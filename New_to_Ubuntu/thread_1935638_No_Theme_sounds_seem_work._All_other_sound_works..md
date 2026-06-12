---
title: "No Theme sounds seem work. All other sound works."
date: 2012-03-04
forum: New to Ubuntu
---

### Post by wilsonB on 2012-03-04
Iv'e read a lot of People are having problems with the system sounds don't play. I can play sounds when going into ;
System Settings\sound\
sound effect tab
There are no options here to select sound themes or anything like that.
This plays sounds and I can listen to music, youtube.. etc.

but I hear no Desktop system sound effects.
log on/off , or minimizing windows, etc..

I successfully copied a new sound theme in  
usr/share/sounds
and have gone back to default ubuntu theme. Still no sound played for system sounds.

Lost system theme sounds. Don't know how to get it back.
Anyone?

Thanks so much

Im a Ubuntu newbie and don't know what log files would be useful. Please let me know.
Ubuntu 11.10, all updates

---

### Post by Frogs Hair on 2012-03-04
Install the following if using 11.10. 

```
sudo apt-get install dconf-tools 

```

Open from dash by typing dcon .

Proceed to org > gnome > desktop > sound and make sure event sounds is checked . 

If the word next "Theme Name" is not Ubuntu select the word and change to Ubuntu .

Close and re open the dconf editor to make sure the change was saved . I had to do this more than once before the change was saved.

---

### Post by wilsonB on 2012-03-04
Thank you so much for the reply/help.

Yes, I have done extensive googling before posting the problem.
I already made sure that is all correct in dcon.

Thanks though

---

### Post by wilsonB on 2012-03-04
EEEEEYYYYYYYYYYYYYYYYAAAAAAAAAAAAAAA

Im so happy.. I think I figured it out. insde Dcon everything is case sensitive. The folders names have to be exact. 
Im learning.. and I guess Dcon is compared to Registry in Windows.

I kept typing Ubunt and the folder name was actually ubuntu. I think this was a bug in the release, not sure how it would have gotten renamed in the protected folder.

Now looking for some nice Theme sounds. Wouldn't mind having something with minimizing/maximizing sounds.
BTW: Where is the spell check option in this forum editor?


:popcorn:


Hope this helps someone else out there.

---

### Post by Frogs Hair on 2012-03-04
You're welcome , What  I posted solved my problem , so I didn't look for any other solutions.

---

### Post by wilsonB on 2012-03-09
Sound Themes is actually not in Ubuntu these days for some reason. I hope in the future they will put it back in Sound Settings

---

### Post by d4m1r on 2012-03-10
> **Frogs Hair said:**
> Install the following if using 11.10. 

```
sudo apt-get install dconf-tools 

```Open from dash by typing dcon .

Proceed to org > gnome > desktop > sound and make sure event sounds is checked . 

If the word next "Theme Name" is not Ubuntu select the word and change to Ubuntu .

Close and re open the dconf editor to make sure the change was saved . I had to do this more than once before the change was saved.

Just a heads up that this actually broke my sound on 11.10...the default value for me is "freedesktop" and switching it to "Ubuntu" removed my login sound and etc.

---

### Post by wilsonB on 2012-03-10
Heya thanks for the reply.

Ya, that's the way Iv'e been changing it. This option should be in the Native Settings-Sounds menu and still isn't in the latest weekly build. :-(

Anyway, mine is working great. Im using the Geoffe buttler one.. ;-) Might add start and shutdown from other themes. It seems they are specificly named for certain 'tasks'. Geoffe has a lot of sounds for many things. I also enabled input-feeback-sounds


Go here;
[http://ubuntu-art.org](http://ubuntu-art.org)

and select Systemsounds. The website seems to be down at this specific time though. "Internal Error. Exception id:6100147056"  ????


Copy sound theme you want, then extract it to 
your system sound theme folder. (Need Root access)
\usr\share\sounds

Open Dcon and branch to location 
desktop\org\gnome\desktop\sound
and type in the folder name. (EXACTLY) Linux is case sensitive. I made this error and couldn't figure it out. ;-)

---

### Post by Frogs Hair on 2012-03-10
> **d4m1r said:**
> Just a heads up that this actually broke my sound on 11.10...the default value for me is "freedesktop" and switching it to "Ubuntu" removed my login sound and etc.

Sorry to here that . the solution was posted by another user and I think Ask Ubuntu as well . As posted it is case sensitive and I had try more than ounce. This fixed my login sound.

---

### Post by Scott Baker on 2012-03-10
Regarding sounds for your machine, here's what I do. You'll need "Audacity" installed. Do this, then cruise over to the place that you download your phones ringtones from. I personally use crackberry.com, but any site that you can get ringtones from should work. Ringtones are used because they're normally close to the right size and require little, if no modification. Once you've chosen and saved some tones, open the tones in Audacity, and convert them to .OGG files (Ubuntu sound files are .OGG). Once you're in the file that contains your system sounds, pick the ones that you want to change. Instead of deleting those sounds, change the name slightly ("example" > "example2" for instance) Now pick the converted sound you want to sub in, and give that sound the name of the original system sound ("new sound" > "example"). Now drag that converted sound into your sound file, check to make sure it's showing up next to the original sound, then close the file. Next time you have an instance when that sound should come up, you should have the new sound play instead of the old sound. There's nothing quite like firing up your Ubuntu box at the local coffee house, and having the poor windows users eating their hearts out when your box is playing the THX sound bite as it's booting up. HAA HAA HAA HAA!!  :lolflag:

---

