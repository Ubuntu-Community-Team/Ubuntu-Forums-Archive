---
title: "[SOLVED] Unable to hear sound although log in sound does play"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Cale Collins on 2008-05-19
Hello, I am new to Ubuntu and the forums. Thank you very much for spending the time to read my thread.  I am experiencing an issue currently with my sound.  I have a fresh install of Ubuntu 8.04.  When I log in the default log in tone is played. When I click the sound volume control no sound is played, and when I run a sound test there is sound to be precise a steady tone.  How do I resolve this?

---

### Post by muted1987 on 2008-05-19
hi i have found that goign to system>>> preferences >>> sound and setting them first 3 to multichannel playback will work. click the test button next to see if you get sound.

---

### Post by Cale Collins on 2008-05-19
I'm looking at sound prefrences now, I'm still unclear on how to change to multichannel.  Is it the devices tab?

---

### Post by muted1987 on 2008-05-19
yes this is what my sound preferences looks like this hope it helps click on the drop down icon for each box, might want to bear in mind i have onboard sound and a soundcard.


[IMG]http://i174.photobucket.com/albums/w85/muted_apoc/Screenshot-SoundPreferences.png[/IMG]

---

### Post by Cale Collins on 2008-05-19
My sound prefrences looks far diffrent.  I would show a screen shot, but as I said I am new to the Os and am still uncertian on how to operate it properly.  I use onboard sound also.  I have a KV-85 mother board.  Are we bolth running the same version of ubuntu?

---

### Post by Cale Collins on 2008-05-19
Ha, Im a fool, It is the same but there is no multichannel option there.  the collor diffrence threw me off :)

---

### Post by muted1987 on 2008-05-19
goto apps accesories take screen shot and make click capture current window and make sure your sound settings is the window in foreground

---

### Post by muted1987 on 2008-05-19
lol ok well if theres no multichannel there try the diff ones till you get it right lol simple but if no work let me know

---

### Post by Cale Collins on 2008-05-19
Thank you verry much for you help.  I see a thanks item below your name, Is there a way I can add a thanks to you?

---

### Post by Cale Collins on 2008-05-19
file:///home/cale/Desktop/Screenshot.png

---

### Post by muted1987 on 2008-05-19
lol the screenshot has to be uploaded to the net somewhere e.g photobucket.com

and the little ribbon on bottom right of my posts is the thx button although i didnt really help just led you there


btw is it working now/?

---

### Post by Cale Collins on 2008-05-19
[IMG]http://i243.photobucket.com/albums/ff317/calecollins/Screenshot.png[/IMG]

---

### Post by Cale Collins on 2008-05-19
No not yet but many of the options play a steady tone.

---

### Post by muted1987 on 2008-05-19
i think you might have to change the defualt device driver to you onboard via chipset


sry defualt mixer tracks

---

### Post by Cale Collins on 2008-05-19
How would I go about that?

---

### Post by muted1987 on 2008-05-19
> **Cale Collins said:**
> How would I go about that?

its the last drop down box in sound preferences

---

### Post by Cale Collins on 2008-05-19
dar

---

### Post by muted1987 on 2008-05-19
also on top right of your screen theres a lil pic of a speaker jsut before the date right click it and goto preferences make sure your via chipset is selected in there and that master is highlighted in orange

---

### Post by Cale Collins on 2008-05-19
I may have it now, athough, I have not a single audio track availible to me currently.  Its going to take a second to find something on the web

---

### Post by Cale Collins on 2008-05-19
When I move the slider there is a light static sound but nothing else.

---

### Post by muted1987 on 2008-05-19
hmm try right clicking on the speaker and going to open volume control and muting the mic

what program you use to test the software??

---

### Post by Cale Collins on 2008-05-19
Im not quite sure what you meant by this.

what program you use to test the software??[/QUOTE]

The microphone was already muted.

I'm curious, How do you install or update a driver in Ubuntu?

---

### Post by muted1987 on 2008-05-19
sudo apt-get update
sudo apt-get upgrade 

run both in terminal

i ment what program you use to test music?

---

### Post by Cale Collins on 2008-05-19
I downloaded adobe flash and just selected a random youtube video.  The video played fine although the sound did not.

---

### Post by muted1987 on 2008-05-19
there is a problem with sound in firefox but thats completely diff subject which i also have problems with and am solving as we speak

what you want to do is quickly throw in a misuc cd and play it using rythembox

---

### Post by Cale Collins on 2008-05-19
I got those lines into terminal, they downloaded great. Is there any thing else I should do other than go back to tinkering with the sound options menu?

Also what is Sudo preciceley?  Is it just administrator?

---

### Post by muted1987 on 2008-05-19
[QUOTE=Also what is Sudo preciceley?  Is it just administrator?[/QUOTE]


yes sudo is a command which basically give administrative rights to allow a normal user the rights to perform root tasks

---

### Post by muted1987 on 2008-05-19
have you tried the music cd option???

---

### Post by Cale Collins on 2008-05-19
Yes, it works great as does the volume control.

---

### Post by muted1987 on 2008-05-19
ok good well keep  talking as im onto something with firefox theres no point starting a new thread when i can jsut help you here

---

### Post by Cale Collins on 2008-05-19
I should have stated "YES!!! It lives!!  I had not tried an audio CD.

> **muted1987 said:**
> ok good well keep  talking as im onto something with firefox theres no point starting a new thread when i can jsut help you here

I didn't quite understand you here. 

Were you able to get the audio to work in firefox?

---

### Post by muted1987 on 2008-05-19
> **Cale Collins said:**
> I should have stated "YES!!! It lives!!  I had not tried an audio CD.



I didn't quite understand you here. 

Were you able to get the audio to work in firefox?


i am in the middle of a solution what i ment was if you have any other problems might as well get them outta the way here instead of posting loads of new threads

---

### Post by Cale Collins on 2008-05-19
I could not find the red ribbon to thank?

What is the best way to refresh the thread to see the new posts?

After running Envy, if my reselution goes to high is it safe just to copy back my Xorg.conf file, or will an error occur? 

Do you have compiz config, or something else? 
What is the best resource for infromation on it (compiz)?

---

### Post by muted1987 on 2008-05-19
> **Cale Collins said:**
> I could not find the red ribbon to thank?

What is the best way to refresh the thread to see the new posts?

After running Envy, if my reselution goes to high is it safe just to copy back my Xorg.conf file, or will an error occur? 

Do you have compiz config, or something else? 
What is the best resource for infromation on it (compiz)?

the red ribbon is blue with gold star sorry more specific next time

best way to refresh thread is to hit f5 

i didnt run envy i installed nvidia drivers from synaptic so idk sry you can reduce screen size by system preferences screen resolution.

i only use basic animations from system>>>>preferences>>>>appearance>>> visual tab as i am running old gfx card.

---

### Post by Cale Collins on 2008-05-19
Thank you very much.  Thats all I can think of for now.  I added you as a contact.  I hope you don't mind.  If you find a resolution to the firefox sound issue would you send me a link to the thread?

---

### Post by muted1987 on 2008-05-19
no i dont mind you adding me and yes i will send you the link or at least instructions as im not really follwing instructions more making my own with help from others . sounds dodgy lol i know


i jsut got the sound working lol

---

### Post by muted1987 on 2008-05-19
im taking it that you installed adobe flash as did i 

this means you have to go to terminal and type

sudo aptitude install libflashsupport

sit back and watch all the youtube vids you want:popcorn:

---

### Post by muted1987 on 2008-05-19
i have also found that firefox crashes when trying to load some flash files have you noticed this?/?

---

### Post by Cale Collins on 2008-05-19
Thank you.  Should we mark the thread as resolved?

---

### Post by Cale Collins on 2008-05-19
N/m whoop, didn't get the new messages you posted.

---

### Post by muted1987 on 2008-05-19
yes that is a good idea

---

### Post by Cale Collins on 2008-05-19
The videos play great, with sound. Thanks. 

No no problem yet with flash crashing.

---

### Post by Cale Collins on 2008-05-19
Whats your source for all of the terminal code you sent to me?

---

### Post by muted1987 on 2008-05-19
just remember all terminal codes sorry although jsut remember these ones

sudo apt-get (what your looking for) >> this will tell you if it has a package you can download

sudo apt-get install (what your looking for) will install program for you

sudo apt-get update >>>. updates repository database

sudo apt-get upgrade >> upgrades any programs drivers etc

---

### Post by Cale Collins on 2008-05-19
Thanks.

---

