---
title: "How do I switch off Mouse Over Audio Prieview ?"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by newperson2this on 2008-07-03
Hi everyone

I have installed the latest version of Ubuntu and find that whenever I go anywhere near a MP3 file audio is automatically played.

How do I disable this daft and unwanted feature.  IT'S DRIVING ME MAD !!!

PS  I have looked everywhere in the docs and there is no mention of how to anywhere !!!

Kind Regards

---

### Post by Marshal0505 on 2008-07-03
preview tab in nautilus maybe? there's an audio section


so you open nautilus then go to edit>>preferences and look for this tab.

[IMG]http://i29.photobucket.com/albums/c251/MarshalMehilal/Screenshot-FileManagementPreference.png[/IMG]

---

### Post by newperson2this on 2008-07-03
Many Thanks

Have found the procedure for turning off the Audio Preview ..
 

Perhaps this feature would have been better administrated from a sound control panel.


I am planing to use Ubuntu for Multimedia purposes and having all the AV and Sound controls in a logical place would have been handy.


My first experiments have been promising  but some of the Ubuntu interface are sadly not all that intuitive.

I'd like for example to colour code my files and folders and individual folder backgrounds as I have a visual disability but here again the documentation is not clear and the available options are limited.

However I like the fact that I have escaped Mac and Windows world and may learn something !!!!

---

### Post by philinux on 2008-07-03
I love the preview.

---

### Post by Marshal0505 on 2008-07-03
> **newperson2this said:**
> 
However I like the fact that I have escaped Mac and Windows world and may learn something !!!!

Over the last few months i started using Ubuntu this has given me so much joy :D 
Hope it all works out for you ;)

---

### Post by wolke on 2008-08-01
Audio preview is the single coolest thing in the entire world.

The only flaw: good song starts while you are ignoring your mouse, and you are totally helpless to continue, for fear of interrupting your awesome song.


Solution: make a keybinding to turn off sound preview, which prevents nautilus from killing totem-sound-preview, stopping your super-cool music experience
> gconftool-2 --set /apps/nautilus/preferences/preview_sound --type string "never"


move your mouse off the kickass sound file and turn preview back on
> gconftool-2 --set /apps/nautilus/preferences/preview_sound --type string "local_only"

{use 'always' to turn preview on for remote files, as well}

I use Ctrl+Alt+P and Ctrl+Alt+Shift+P.

---

