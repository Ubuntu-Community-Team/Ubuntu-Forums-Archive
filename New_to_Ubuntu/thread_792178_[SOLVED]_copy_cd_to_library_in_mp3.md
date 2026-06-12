---
title: "[SOLVED] copy cd to library in mp3"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by DarinB on 2008-05-12
i use rhythmbox i want to add a cd to my library as an mp3 instead of ogg, so i can use it on my ipod.

---

### Post by HotShotDJ on 2008-05-12
[LIST=1]
[*]If you haven't done so already, install ubuntu-restricted-extras
[*]Open Applications --> Sound & Video --> Audio CD Extractor
[*]In the Edit menu, open Preferences
[*]Find the Output Format options.  Select CD Quality, MP3 (MP3 audio)
[*]You may also set the other option in there, but the defaults are pretty sane
[*]Done
[/LIST]

---

### Post by DarinB on 2008-05-12
mp3 is not a choice in that program

---

### Post by HotShotDJ on 2008-05-12
> **DarinB said:**
> mp3 is not a choice in that programHave you installed the ubuntu-restricted-extras?  I assure you, MP3 is an option.  But you DO need ubuntu-restricted-extras to get MP3 support in any program.

---

### Post by chchandler on 2008-05-12
Well, I tried to add the debian source System|Adinistration|System Sources|Third=Party Software as [http://ftp.debian.org](http://ftp.debian.org) etch main.  Found out the GPG key wasn't there and haven't yet gone and found it.  Upon completion my top bar showed 2 updates available out of 4.  Installed them, shut down and restarted Audio CD Extractor, still no MP3 choice.

We must be missing a step somewheres....

---

### Post by HotShotDJ on 2008-05-12
> **chchandler said:**
> We must be missing a step somewheres....I can't imagine what the problem is.  All I know is that on my system, after doing a fresh install of Hardy, I installed ubuntu-restricted-extras and got MP3 support in all relevant applications.  I did nothing else.  No magic.  No extra steps.  Quite frankly, I'm stumped.

---

### Post by Terri on 2008-05-12
I just installed a fresh copy of Hardy last night with all the repositories and it's not a choice for me either.

---

### Post by HotShotDJ on 2008-05-12
> **Terri said:**
> I just installed a fresh copy of Hardy last night with all the repositories and it's not a choice for me either.This is strange.  Stand by for a bit... I'm going to see if there is something amiss on my side of the equation.

EDIT:  Ok... I popped in a CD and started ripping it -- I've got perfect little MP3 files. Ah HAAAAAAAAAAAA!!!   I think I know what step we're missing!!!!!!

Add the Medibuntu repositories to Software Sources.  [HERE]("https://help.ubuntu.com/community/Medibuntu") are the instructions.  Once that is done, you should install the updates and that should get you up and running. (At least I HOPE so!).

---

### Post by chchandler on 2008-05-12
It is available in the Edit Profiles box but won't populate the Output format box.

---

### Post by HotShotDJ on 2008-05-12
Can anybody verify if adding the Medibuntu repositories solved this mystery.  Its driving me crazy wondering about it.

---

### Post by Terri on 2008-05-12
Didn't work...at least I don't think so. I went your link copied and pasted the commands into the terminal. Then checked the repositories again in synaptic and it's there and check off. The update manager told me I had new updates. Downloaded them and tried again. It's still not an option. Did I miss a step?

---

### Post by HotShotDJ on 2008-05-12
> **Terri said:**
> Didn't work...at least I don't think so. I went your link copied and pasted the commands into the terminal. Then checked the repositories again in synaptic and it's there and check off. The update manager told me I had new updates. Downloaded them and tried again. It's still not an option. Did I miss a step?I can't think of anything. Just one last check.. you DID install ubuntu-restricted-extras, right?  Beyond that... I just don't know.  :confused:

---

### Post by Terri on 2008-05-12
By that do you mean the Multiverse repository?

---

### Post by HotShotDJ on 2008-05-12
> **Terri said:**
> By that do you mean the Multiverse repository?
No.. I mean the package named ubuntu-restricted-extras -- however, it is in the multiverse repository.

---

### Post by Terri on 2008-05-12
No...but I will right now

---

### Post by Terri on 2008-05-12
Extracting my CD in MP3 format as we speak :)...thank you for the help.

---

### Post by HotShotDJ on 2008-05-12
> **Terri said:**
> Extracting my CD in MP3 format as we speakThank GOODNESS!  I was honestly beginning to think that I had lost my mind.

---

### Post by andrew.46 on 2008-05-12
Hi,

 You seem to have solved your problem but can I suggest an alternative? There is a long shell script called abcde which would do exactly what you describe. I have placed a short walkthrough for it on these forums:

[http://ubuntuforums.org/showthread.php?t=535950](http://ubuntuforums.org/showthread.php?t=535950)

and published a web page which goes into a little more detail at:

[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

    Andrew

---

### Post by chchandler on 2008-05-13
> **HotShotDJ said:**
> No.. I mean the package named ubuntu-restricted-extras -- however, it is in the multiverse repository.

THAT did it!  Many thanks...

---

### Post by DarinB on 2008-05-13
I had the same problem even though the cli was to install the repo i had to go into synaptic and install the restricted extra lame then it was automatic

---

