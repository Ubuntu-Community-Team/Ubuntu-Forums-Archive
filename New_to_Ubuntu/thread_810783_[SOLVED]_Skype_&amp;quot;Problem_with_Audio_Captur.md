---
title: "[SOLVED] Skype: &amp;quot;Problem with Audio Capture&amp;quot; upon test call"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by diablo75 on 2008-05-28
I don't know what it is, but I've been having a lot of really funky audio problems lately.  Yesterday, I had to fix my flash player by installing the "libflashsupport" package...and that seems to have only fixed it half way.  I still have problems occasionally with flash, and rebooting (not just logging off, but rebooting completely) seems to be the only solution for times when flash doesn't produce sound now.  Though come to think of it, rebooting is the option I would have to take because I wasn't getting sound system wide.

Anyway, Skype suddenly stopped producing sound a couple days ago to but I'm just now getting around to troubleshooting it.  Up until seemingly a few days ago, using "default" for sound in, out and ring worked just fine.  Then it quit working, until I recently changed the settings as below:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=71929&stc=1&d=1212001805[/IMG]
The "plughw:Audigy2,4" is what I have selected right now and it produces sound just fine.  But when I try to make a test call, it fails with this message:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=71930&stc=1&d=1212001958[/IMG]
"Problem with Audio Capture"

I took a look at [The Perfect Setup (Re: Skype)]("http://www.pulseaudio.org/wiki/PerfectSetup#Skype") which suggests you do as I've done (with the sound device settings, selecting the first plughw in the list), then quit, and the run "pasuspender skype" in terminal to restart skype.  Unfortunately, this does not solve my problem.

What am I doing wrong?

---

### Post by diablo75 on 2008-05-29
I've just finished reinstalling Ubuntu from a fresh install CD that I downloaded a couple hours ago, and unfortunately, the exact same problems I'm experiencing above are still occurring.  I've tried "pulseaudio -k" before runing Skype, and different combinations of it running and not running with different sound device settings.

I uninstalled Skype, but stumbled upon the "skype-static-oss" package, which uses OSS.  This works, but the audio is really really choppy and to be honest, not acceptable.  I was hoping a destructive recovery would shake out the bugs...  What should I try now?

---

### Post by Primefalcon on 2008-05-29
I've noticed this myself just fiddle around and try the other defences that have the same name

---

### Post by diablo75 on 2008-05-29
I followed a guide found here:

[http://ubuntuforums.org/showthread.php?t=686911](http://ubuntuforums.org/showthread.php?t=686911)

[COLOR="Red"]Edit:  Don't follow this guide.  It got my sound working in Skype, but the rest of my system is now soundless.  :([/COLOR]  Reversing the instructions got things back to the way they were.  So now at least I can hear music, but can't use Skype.../edit

Post #10, and the guide worked.... with a little minor exception:

The first confusing part is where you're told to edit your asoundrc file.  I had never done this before, so was initially under the impression that it needed to be found so I could edit.  But the file didn't actually exist, and you're actually supposed to just create one in your home folder.

I went out and finished the guide, getting to the part where I entered the killall pulseaudio command, followed by the restarting of pulse audio, ignoring the output in terminal and closing the Window.  From the sounds of it, my sound is working.  Within Skype's sound settings, I found new devices listed "skypein, skypeout".  I had to set my input sound to the Skypein, but changing any other setting from the plughw device I had originally would cause the output sound to disappear and I could hear nothing.  Leaving it as plughw:Audigy2,4 on output and ringing did the trick, and now, my microphone finally works!

---

### Post by diablo75 on 2008-05-29
> **Primefalcon said:**
> I've noticed this myself just fiddle around and try the other defences that have the same name

It's surprising but tinkering around did the trick.  It was kind of like trying to figure out a combination lock, but easier.  I was just under the impression the whole time that the input and output devices would (should?) be the same.  But in this case, they're not.  Setting them up like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=72061&stc=1&d=1212080175[/IMG]

Did the trick.  Both my speakers and microphone are working as is the rest of my system sound.  No need to modify config files.  :guitar:

---

### Post by phpmonkey on 2008-07-29
Great! Thanks diablo, I've been having similar probs since I pkill pulsausio on setup and fiddled with a few other things to get flash sound to work, more improtantly Firefox and rhythmbox to play nicely and not hog the card. Your last post helped me fiddle with my Skype Prefs and fix the problem!! Thank you!

---

### Post by Nausser on 2008-11-07
What were your other sound config settings? Did you change them from the defaults at all? I'm referring to the ones under System > Preferences > Sound. Also your settings available when you double click the speaker icon in the task bar.

---

