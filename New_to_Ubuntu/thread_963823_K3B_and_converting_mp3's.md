---
title: "K3B and converting mp3's"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by GeordieJedi on 2008-10-30
Hi all, quick question.

Does K3b convert mp3 files back to CDA (CD Audio/ "normal" audio Cd's?)

Im sure I read somewhere that it could, but I've had a look at the homepage - (no-joy).
And tried to use the K3b's help documentation (But got a error message)

Thanks for any help offerd.

---

### Post by robert shearer on 2008-10-30
> **GeordieJedi said:**
> Hi all, quick question.

Does K3b convert mp3 files back to CDA (CD Audio/ "normal" audio Cd's?)

Im sure I read somewhere that it could, but I've had a look at the homepage - (no-joy).
And tried to use the K3b's help documentation (But got a error message)

Thanks for any help offerd.

You want "soundconverter". It is configurable, Edit, Preferences when it opens and set the output file to .wav. then select the files you want to convert and it will .
Go to the folder you nominated as the output and the .wav files will be there.Then you can burn them to cd with k3b

```
sudo apt-get install soundconverter
```

Or use Synaptic if you prefer

---

### Post by GeordieJedi on 2008-10-30
Awesome!

Cheers Robert. Its much appreciated mate. :)

---

### Post by GeordieJedi on 2008-10-30
Hmmmm. downloaded soundconverter. Converted the album to .wav
then tried to re-burn in K3B but its still a no-go.

Is there anything else I need to do?

thanks

---

### Post by robert shearer on 2008-10-30
What exactly doesn't work?

When you open k3b and choose to make an audio cd does that open the window so you can add files?

After you add the files (your mp3's converted to wav .Make sure they are the wav ones and not the origonal mp3s) and choose to burn does it start to burn the cd?

Does it burn the cd? or are there errors.

Does the cd play in a cd player?

At what step is the problem happening.?

---

### Post by GeordieJedi on 2008-10-30
Hi Robert.

I downloaded soundconverter as suggested.
converted the folder of songs to .wav.
Started K3B. Navigated to said folder.
Selected a track.

Here's a copy of the error message =

Unable to handle the following files due to an unsupported format:
You may manually convert these audio files to wave using another application supporting the audio format and then add the wave files to the K3b project.
/media/Music/MP3's/S/Simon & Garfunkel - Definitive Collection/simon_&_garfunkle_wavs/simon and garfunkel - a hazy shade of winter.wav

(Aplogies for the bad taste in music. Its actually for my flat mate).

---

### Post by robert shearer on 2008-10-30
looks like k3b isn't recognising your converted files.

Open soundconverter and go Edit, Preferences again.

When that window opens click on "into folder" and then 'Choose' next to it.
In the window that opens Create a new folder.
Leave it in the Music folder and call it something like 'converted'.

Run the conversion again then go to the 'converted' folder  and click down through each folder until you find the individual tracks .
They will show an icon of a musical nature and have a .wav suffix.
Dragndrop them into the k3b audio window and try again.

Have you got the restricted extras installed?
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by GeordieJedi on 2008-10-30
Hallow again Robert.

I tried that. The files diddnt go into the specified folder..Doh
(they went into the folder, that the original files came from).

However I tried to select one of the new .wav files in K3B before I moved them into thier own folder.

And Lo-and-behold....K3B recognised them this time??

I've just burnt the disc, and it plays fine on my PC, but not in my
discman.
But thanks for your time and patience so far mate.
Much appreciated! :)

---

### Post by robert shearer on 2008-10-30
> **GeordieJedi said:**
> Hallow again Robert.

I tried that. The files diddnt go into the specified folder..Doh
(they went into the folder, that the original files came from).

However I tried to select one of the new .wav files in K3B before I moved them into thier own folder.

And Lo-and-behold....K3B recognised them this time??

I've just burnt the disc, and it plays fine on my PC, but not in my
discman.
But thanks for your time and patience so far mate.
Much appreciated! :)

Ok. progress!
 As the tracks were in the original folder, with the tracks being converted from, then k3b may have had trouble working out which one you were trying to burn.

Anyhows, have you finalised the cd? or left it open to add tracks later?

If the latter then it won't play in an audio cd player until it is finalised.
Best to burn an audio cd in one hit.

You could try Brasero, the Gnome default cd burning app.
 As the tag on this thread is Ubuntu I assume you are using it and have added k3b rather than using Kubuntu?.

Did you check the k3b debug log when it finished.This may give you some hint as to why it may not be playing.

Try it in another cdplayer(not a discman- has you discman played other burnt cds before?)

---

### Post by ellgor on 2008-10-31
Hi,

Try Rhythmbox, I think it comes as default, use the create function where it will make the files into something playable and then burn it as well, hope this of use.

Regards, Ellgor.

---

### Post by skullmunky on 2008-10-31
Doesn't K3B do the conversion from MP3 or OGG to regular CD audio automagically?  Create an audio CD project, drag a bunch of MP3's into it, and just burn it - I could swear I've done that before, but maybe my memory's hazy ...

---

