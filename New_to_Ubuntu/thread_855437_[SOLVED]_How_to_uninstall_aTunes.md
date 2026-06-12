---
title: "[SOLVED] How to uninstall aTunes"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by socngill on 2008-07-10
I no longer require aTunes but I can't find it in the add/remove Programs or in Adapt Manager.  I've gone to the aTunes folder and clicked on Uninstaller.jar but it just brings up a huge list of stuff - none of which are aTunes..?

Is there a basic terminal command I can type that will remove it?

Cheers.

---

### Post by jualin on 2008-07-10
> sudo apt-get purge atunes? just a shot in the dark

---

### Post by socngill on 2008-07-10
Didn't work.  Says couldn't find package atunes.

I also tried sudo apt-remove and sudo apt-uninstall as wild guesses but nothing doing.  Thanks for trying though.

---

### Post by jualin on 2008-07-10
This is the [link]("http://sourceforge.net/forum/message.php?msg_id=4552343") for the Atunes forums. Maybe someone there can point you to the right direction. I am guessing it shouldn't be that complicated. Sorry I couldn't help you more.

---

### Post by jerome1232 on 2008-07-10
atunes isn't an Ubuntu package so far as i can see so either you built it from source or you downloaded a pre-compiled binary. with a binary file you either use the programs supplied uninstaller or you have to manually delete the files. If you built the program from source you would navigate to the source folder and do ```
sudo make uninstall
```


edit: I googled atunes went to their site, it's a java program and according to their site you use that uninstall.jar you were talking about [http://www.atunes.org/]("http://www.atunes.org/") Will probably have more info

---

### Post by socngill on 2008-07-10
I tired those forums originally but they appear to be down.

Tried your suggestion - sudo make uninstall - but it came back with:

> make: *** No rule to make target `uninstall'. Stop.

Thanks for trying.  I shall just leave it there for now.  Plenty of space on the HDD so no real problem.  I was just uninstalling all the stuff I no longer use.

I'll be doing a clean install in 3 months anyway when the new 8.10 is released - it can wait till then.

Thanks again.

---

### Post by stchman on 2008-07-10
> **socngill said:**
> I no longer require aTunes but I can't find it in the add/remove Programs or in Adapt Manager.  I've gone to the aTunes folder and clicked on Uninstaller.jar but it just brings up a huge list of stuff - none of which are aTunes..?

Is there a basic terminal command I can type that will remove it?

Cheers.

Where did you get aTunes?  aTunes is not in the repositories.

Rhythmbox would better server you IMO.

---

### Post by socngill on 2008-07-10
Downloaded it from the site - I think...  May have been an RPM file.  Didn't really like it.  Whenever I added things like podcasts and radio stations it would wipe it everytime I closed and opened again.

Currently using Amarok instead but might try out Song Bird.  been having a look at in on my XP machine and it seems pretty good although a bit buggy.

Never tried Rhythmbox.  might have a look at it.  Thanks for the suggestion :)

---

### Post by stchman on 2008-07-10
> **socngill said:**
> Downloaded it from the site - I think...  May have been an RPM file.  Didn't really like it.  Whenever I added things like podcasts and radio stations it would wipe it everytime I closed and opened again.

Currently using Amarok instead but might try out Song Bird.  been having a look at in on my XP machine and it seems pretty good although a bit buggy.

Never tried Rhythmbox.  might have a look at it.  Thanks for the suggestion :)

To uninstall that app you can probably just trash the folder it created.  Also you can delete the menu entry it created as well.

---

### Post by socngill on 2008-07-10
> **stchman said:**
> To uninstall that app you can probably just trash the folder it created.  Also you can delete the menu entry it created as well.

That would seem to have done the trick!  How simple these things can be.

Cheers :guitar:

---

### Post by stephenburnett on 2008-07-30
[FONT=Arial][SIZE=3][COLOR=Navy]Why don't you give [Songbird]("http://getsongbird.com/") a try?8-)

It is a Mozilla Firefox-based product at version 0.6.1, and now has many [the website says "hundreds"] of extensions, and a number of themes [sometimes referred to as "feathers"].:rolleyes:

Just download the .tar.gz file to your desktop, extract it there, open the resulting folder and lastly open the "songbird" executable there.  The install proceeds and you are off to the races.):P

I am still working on determining what my opinion is of its playback qualifications [I am a certified audiophile:guitar:, with 20 years of experience as a radio announcer, not an amateur], and will most likely post my observations in the coming days or weeks.  The product aims to be a FOSS replacement for iTunes -- iHopeSo!!!:lolflag:
[/COLOR][/SIZE][/FONT]

---

### Post by goatroapr on 2008-12-27
Hello. Open a terminal window and go to the directory your uninstaller.jar file is located and run this:

```
java -jar uninstaller.jar
```

Worked like a champ for me.

---

