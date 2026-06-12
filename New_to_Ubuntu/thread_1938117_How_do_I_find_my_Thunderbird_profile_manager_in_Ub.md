---
title: "How do I find my Thunderbird profile manager in Ubuntu 11.10?"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by bigfisheatslittlefish on 2012-03-09
I have searched forums and google and tried everything I've seen.  I cannot find the hidden files etc.  Do I need to search for this using a terminal?  I am a beginner but have tried everything and taught myself how to do what I do not know. What I've read seems to apply to earlier versions of Ubuntu.  I am working on a new computer and my reason for searching is to install my thunderbird mail file from my old computer to my new one.  My old one was Windows and I'm using Linux on the new one.  If there is a workaround I'm happy to try it other than finding profile manager.

---

### Post by Jon Monreal on 2012-03-09
I don't use Thunderbird, but if you go to your home folder and press ctrl+h, I believe the folder will be something like "~/.mozilla-thunderbird[name]".

After you're finished, press ctrl+h again.

---

### Post by forrestcupp on 2012-03-09
I'm running Ubuntu 11.10, and my folder is called ~/.thunderbird. Just to make what Jon said clear, he's talking about pressing Ctrl+H in Nautilus, the file manager, not in the terminal. In Nautilus, Ctrl+H toggles showing hidden files and folders. Your .thunderbird folder is in your user's /home folder.

But if you actually want to access Thunderbird's profile manager app, like your title suggests, then open a terminal, and type:
```
thunderbird -p
```

---

### Post by Frogs Hair on 2012-03-09
View > show hidden will also work .>  my reason for searching is to install my Thunderbird mail file from my old computer to my new one. My old one was Windows and I'm using Linux on the new one. If there is a workaround I'm happy to try it other than finding profile manager. 

The import option works with other programs not files .

---

### Post by Jon Monreal on 2012-03-09
It's also worth noting that there may be some (easily solved) problems initially when you move the profile due to thunderbird on Windows using the windows directory structure. If that happens, just post in this thread and I'm sure it can be fixed.

---

### Post by oldfred on 2012-03-11
I used to share my Thunderbird profile with XP but I moved it to a shared NTFS partition. I also copy my profile from my desktop to my laptop when we travel.

This is where my profile is:
/home/fred/.thunderbird

The profile is XXXXXX.default and profile.ini controls which & where the profile is.

I install Thunderbird and load it once. It creates a new profile. I then copy my profile to it and edit profile.ini to use the older profile.

Update to tb3
[http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)
new 
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by presence1960 on 2012-03-11
I have my thunderbird and firefox profiles in a shared NTFS partition. Over time I learned that for Firefox it is best to have separate profiles for Linux and Windows. Thunderbird seems to show no ill effects of sharing the profile between Windows & Linux. doing this will allow you to simply choose the profile to use on any OS or new install. Of course the profile won't be in your /home folder which in my opinion is an advantage. You just need to make sure your partition containing the mozilla profiles is mounted prior to running firefox or thunderbird.

To set which profile to use from Linux open a terminal and run ```
firefox -P
```and ```
thunderbird -profilemanager
```
follow the prompts to select your profile folder.

From windows use the run dialogue to run ```
firefox.exe -profilemanager
``` for thunderbird simply substitute thunderbird for firefox in the run dialgue command.

---

### Post by bigfisheatslittlefish on 2012-03-11
Thank you all so much for your help.  Ctl + H was the easiest and solved how to find my profile manager.
 
I now have a new problem related to my profile.  Not sure if I need to start a new thread, and again, I searched for solutions before posting and tried to solve with what I read.
 
Problem:  After finding my profile I copied my thunderbird profile from my old windows computer.  I replaced my files by simply deleting the original profiles.ini file & xxxxxx.default folder (I do not need any data from the new thunderbird as I have only loaded it - not used it for mail as yet).  Then copied across my profiles.ini file and xxxxx.default folder.  
 
Trying to open thunderbird I got the error: "Thunderbird is already running, but not responding. To open a new window you must close the existing thunderbird process, or restart your system" 
 
I restarted - didn't work
I made sure beforehand and again after this error that I had quit Thunderbird properly and ran $ps ux in the terminal to make sure the application wasn't still running
 
I then changed my default folder to match in name the exact name as the one I deleted.  I also changed the path in the profiles.ini file to match.
 
Still no solve
 
Then I changed the path in profiles.ini from Profiles/xxxxxx.default to Home/.thunderbird/xxxxxx.default.
 
Is it clear to anyone what I'm doing wrong?

---

### Post by bigfisheatslittlefish on 2012-03-11
> **oldfred said:**
> I install Thunderbird and load it once. It creates a new profile. I then copy my profile to it and edit profile.ini to use the older profile.
 
 
This sounds like what I did.  How exactly did you edit profile ini. ?
 
Mine reads:
[General]
StartWithLastProfile=1
 
[Profile0]
Name=default
IsRelative=1
Path=Home/.thunderbird/xxxxxx.default (I changed it from Profiles/xxxxx.default - which also didn't work)

---

### Post by presence1960 on 2012-03-11
> **bigfisheatslittlefish said:**
> Thank you all so much for your help.  Ctl + H was the easiest and solved how to find my profile manager.
 
I now have a new problem related to my profile.  Not sure if I need to start a new thread, and again, I searched for solutions before posting and tried to solve with what I read.
 
Problem:  After finding my profile I copied my thunderbird profile from my old windows computer.  I replaced my files by simply deleting the original profiles.ini file & xxxxxx.default folder (I do not need any data from the new thunderbird as I have only loaded it - not used it for mail as yet).  Then copied across my profiles.ini file and xxxxx.default folder.  
 
Trying to open thunderbird I got the error: "Thunderbird is already running, but not responding. To open a new window you must close the existing thunderbird process, or restart your system" 
 
I restarted - didn't work
I made sure beforehand and again after this error that I had quit Thunderbird properly and ran $ps ux in the terminal to make sure the application wasn't still running
 
I then changed my default folder to match in name the exact name as the one I deleted.  I also changed the path in the profiles.ini file to match.
 
Still no solve
 
Then I changed the path in profiles.ini from Profiles/xxxxxx.default to Home/.thunderbird/xxxxxx.default.
 
Is it clear to anyone what I'm doing wrong?

 open a terminal and run ```
thunderbird -profilemanager
``` Choose create profile. Choose next. Enter profile name and then click choose folder. Now select your profile folder, if there is another profile already delete it after creating the new one but select to not delete files when prompted with a choice and next click finish. You should be OK after this.

P.S. I just copy the profile folder over without inserting it into the existing profile folder. You don't have to edit those files if you use the thunderbird -profilemanager command as it does all the editing for you when you select a profile.

---

### Post by bigfisheatslittlefish on 2012-03-12
Thank you presence1960.
When I type thunderbird -profilemanager in the terminal it returns with "Error: no display specidfied"

---

### Post by Kevin McCready on 2012-03-12
I have a related problem. I backed up my thunderbird files with Sylpheed and now Sylpheed and Thunderbird both refuse to decipher the backup folder which is named:
3scj3k8r.default

I took a screenshot but I cannot upload it to this forum. 
Does anyone know how to upload the image?
Would be grateful for help on both these issues.Does anyone know how to upload the image?

---

### Post by bigfisheatslittlefish on 2012-03-12
> **presence1960 said:**
> open a terminal and run ```
thunderbird -profilemanager
``` Choose create profile. Choose next. Enter profile name and then click choose folder. Now select your profile folder, if there is another profile already delete it after creating the new one but select to not delete files when prompted with a choice and next click finish. You should be OK after this.

P.S. I just copy the profile folder over without inserting it into the existing profile folder. You don't have to edit those files if you use the thunderbird -profilemanager command as it does all the editing for you when you select a profile.
THANK YOU Presence1960!!!!
 
Yay!  It finally worked.  I thought I was still getting errors but what I did do to get to my Profile Manager after getting Display Error in Terminal was type DISPLAY=:0 thunderbird -profilemanager and when I went back to the main screen (Ctl +Alt +F7) Profile Manager had appeared.  I followed your direction and now I'm all set!  Thanks again!

---

### Post by presence1960 on 2012-03-12
> **bigfisheatslittlefish said:**
> THANK YOU Presence1960!!!!
 
Yay!  It finally worked.  I thought I was still getting errors but what I did do to get to my Profile Manager after getting Display Error in Terminal was type DISPLAY=:0 thunderbird -profilemanager and when I went back to the main screen (Ctl +Alt +F7) Profile Manager had appeared.  I followed your direction and now I'm all set!  Thanks again!

Glad you got it working! Enjoy.

---

