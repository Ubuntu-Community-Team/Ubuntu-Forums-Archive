---
title: "No System Sounds"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by bartnortthwest on 2012-05-13
kubuntu 12.04 installed and all updates are installed. I just noticed I have no system sounds although I have sounds for videos and music.  I saw a script in another forum category that you can place in your home directory and run to fix this, but I wonder if this bug has been addressed by an update.

Maybe it's time for me to run the script?   Do  I just put it in a plain text file? Are spaces critical or will the be ignored when the script is parsed.

---

### Post by whatthefunk on 2012-05-13
What script is it?

Before you go running scripts, have you checked your sound settings?
System Settings > Multimedia > Phonon

Check to see what output Notifications are running to and test that sound device using the test button.

---

### Post by bartnortthwest on 2012-05-13
I don't seem to have phonon.  In multimedia > Pulse Audio Volume Control seems ok.  The script is :

#!/bin/bash for j in /usr/share/kde4/apps/*/*.notifyrc do   sudo sed -i 's_Sound=_Sound=file:///usr/share/sounds/_g' $j done[]("http://www.kubuntuforums.net/member.php?19063-SteveRiley")<<<<

From other thread, the complete instructions: 				 				 				 					     				
 			 		 		 			 				 				   						 						 				 					 						[INDENT] 							Use the same command...the bug is still apparently present. I've  now put it in a small shell script so that I can run in whenever an  update borks the config.

 	Code:
 	#!/bin/bash for j in /usr/share/kde4/apps/*/*.notifyrc do   sudo sed -i 's_Sound=_Sound=file:///usr/share/sounds/_g' $j done 
Name it **systemsounds.sh**, place it in your home directory, and then run
 	Code:
 	sudo chmod a+x systemsounds.sh 
to make it executable.

Then run
 	Code:
 	~/systemsounds.sh 
whenever you need to apply the fix.

>>>>>>>

Thanks for any suggestions!

[/INDENT]

---

### Post by whatthefunk on 2012-05-13
> **bartnortthwest said:**
> I don't seem to have phonon.  In multimedia > Pulse Audio Volume Control seems ok.  The script is :

#!/bin/bash for j in /usr/share/kde4/apps/*/*.notifyrc do   sudo sed -i 's_Sound=_Sound=file:///usr/share/sounds/_g' $j done[]("http://www.kubuntuforums.net/member.php?19063-SteveRiley")<<<<

From other thread, the complete instructions: 				 				 				 					     				
 			 		 		 			 				 				   						 						 				 					 						[INDENT] 							Use the same command...the bug is still apparently present. I've  now put it in a small shell script so that I can run in whenever an  update borks the config.

 	Code:
 	#!/bin/bash for j in /usr/share/kde4/apps/*/*.notifyrc do   sudo sed -i 's_Sound=_Sound=file:///usr/share/sounds/_g' $j done 
Name it **systemsounds.sh**, place it in your home directory, and then run
 	Code:
 	sudo chmod a+x systemsounds.sh 
to make it executable.

Then run
 	Code:
 	~/systemsounds.sh 
whenever you need to apply the fix.

>>>>>>>

Thanks for any suggestions!

[/INDENT]

First, you should have Phonom.  Maybe attach a screenshot of your Multimedia System Settings page?

For the script, Im pretty sure it should look like this:
```
#!/bin/bash 

for j in /usr/share/kde4/apps/*/*.notifyrc do   
  sudo sed -i 's_Sound=_Sound=file:///usr/share/sounds/_g' $j 
done
```

Im not great with bash scripts, but that should do it.
Create a file in your home directory, paste that code in there and save it as systemsounds.sh.  Then, open up a terminal and make the script executable:
```
sudo chmod a+x systemsounds.sh
```

Then you should be able to run the script in the terminal by typing systemsounds.sh  Assuming that it works, you can make a link for it on your desktop to make it easier.

---

### Post by bartnortthwest on 2012-05-14
Well I'm beginning to feel like a really stupid absolute beginner.  The package manager showed phonon as not installed, so I installed it (and 18 related packages), but still no gui for phonon available as far as I can see.  Can't create a launcher for it, and the application finder only shows Pulse Audio.   Does phonon not have a gui?

See attached screenshots.

And thanks[ATTACH]217904[/ATTACH]

[ATTACH]217905[/ATTACH]

[ATTACH]217906[/ATTACH][ATTACH]217906[/ATTACH]

---

### Post by whatthefunk on 2012-05-14
You need to go to System Settings.  From your Menu go to Settings > System Settings > Multimedia

---

