---
title: "Requirements for Ubuntu 11.10?"
date: 2011-11-06
forum: New to Ubuntu
---

### Post by skandyrv on 2011-11-06
Hey.. Its been about a year since I've shifted to Ubuntu. But basically.. I had a question. Whenever I try to play Videos in Ubuntu 11.04 on my computer.. It restarts. This happens no matter what I do. Im only able to play videos if I dont move the mouse at all during the entire duration of the video and even then, it restarts upon closing the video. What exactly is causing this problem? Is it due to some system requirement missing in the computer?

My computer's specifications are 50GB HDD, 768 MB DDR RAM, Pentium 4 processor and no graphics card that I know of. I know its quite old but thats what I have atm.

With this specification.. Will I be able to run 11.10 on my computer? Should I expect any major problems or the like?:(

---

### Post by Diametric on 2011-11-06
Hmmm....while your system is quite old, it does seem odd that videos are re-starting.  I'd imagine that if it were a simple ram/cpu issue the behavior would be more choppy or some lag/buffer issue.  However, I'd wager there is more than I'm aware of.

What type of video file and player are you using? How large is the file?  What other info can you provide?

---

### Post by JRV on 2011-11-06
What video player are you using?
Some videos will play better in Totem and some in VLC.

---

### Post by Kyoushuu on 2011-11-06
Try running your video player in the terminal. If it's the default in Ubuntu, it's Totem. Type totem/vlc/smplayer then press enter. Try opening the video file (File -> Open or similar). Check if there's any message printed in the terminal.

---

### Post by Mark Phelps on 2011-11-06
Your PC has to have a video chip, else you would get no video.  To find out what it is, open a terminal and enter "lspci" -- and look for the line containing "VGA".  That will give you the make and model of the chip.

---

### Post by skandyrv on 2011-11-07
> **Diametric said:**
> Hmmm....while your system is quite old, it does seem odd that videos are re-starting.  I'd imagine that if it were a simple ram/cpu issue the behavior would be more choppy or some lag/buffer issue.  However, I'd wager there is more than I'm aware of.

What type of video file and player are you using? How large is the file?  What other info can you provide?

Btw.. I'm using xfce in 11.04. Oh and.. its not the video player that  restarts. The entire system does. Goes to the login screen immediately  upon moving the mouse over the video screen.

 As for the player.. Its generally the default M-Player/GNOME Player[I'm  using xfce] or VLC. And the file sizes are generally around 700MB to  1GB.. Almost default size for rips... Oh and the files are generally AVI  files.

> **JRV said:**
> What video player are you using?
Some videos will play better in Totem and some in VLC.
Default[M-Player I think] and VLC]

> **Kyoushuu said:**
> Try running your video player in the terminal. If it's the default in Ubuntu, it's Totem. Type totem/vlc/smplayer then press enter. Try opening the video file (File -> Open or similar). Check if there's any message printed in the terminal.

Terminal startup? Will try it..

> **Mark Phelps said:**
> Your PC has to have a video chip, else you would get no video.  To find out what it is, open a terminal and enter "lspci" -- and look for the line containing "VGA".  That will give you the make and model of the chip.


And the video device upon using lspci was 
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)

[Although I couldn't make head or tail of it:sad:]

---

### Post by mastablasta on 2011-11-07
you are using graphics chip form S3. they are not the best supported.
 
you say that computer restarts. that can be due to:
- faulty capacitors (you can open thebox and see if any capacitors are bulged). this was a common problem with these older maschines (see: [http://[COLOR=#009933]en.wikipedia.org/wiki/**Capacitor**_**plague]("http://en.wikipedia.org/wiki/Capacitor_plague")**[/COLOR] )
- overheating - you can try to cleaning the computer of any dust. video will use more processing power and if ther eis dust there it will heat up too much and as precaution computer could reboot. clean the dust (vaccum it or blow it away with compressed air)
 
next, you have enough memorry to run the OS. also the processor should be just fine.  you could try to get a better graphics card if you can get an old one for free (or at very very low price) it might be worth it.

---

### Post by skandyrv on 2011-11-07
> **mastablasta said:**
> you are using graphics chip form S3. they are not the best supported.
 
you say that computer restarts. that can be due to:
- faulty capacitors (you can open thebox and see if any capacitors are bulged). this was a common problem with these older maschines (see: [http://[COLOR=#009933]en.wikipedia.org/wiki/**Capacitor**_**plague**[/COLOR]]("http://en.wikipedia.org/wiki/Capacitor_plague") )
- overheating - you can try to cleaning the computer of any dust. video will use more processing power and if ther eis dust there it will heat up too much and as precaution computer could reboot. clean the dust (vaccum it or blow it away with compressed air)
 
next, you have enough memorry to run the OS. also the processor should be just fine.  you could try to get a better graphics card if you can get an old one for free (or at very very low price) it might be worth it.


Ah.. Ill check the capacitor and also redust after exams. Thats been pending long anyhow. I hope my system can support a proper graphics card[I'm not sure if the processor will hold or not]. I guess if 11.10 is supported then ill try to run it. Btw.. Any major bugs?

---

### Post by amjjawad on 2011-11-07
> **skandyrv said:**
> My computer's specifications are 50GB HDD, 768 MB DDR RAM, Pentium 4 processor and no graphics card that I know of. I know its quite old but thats what I have atm.

Hello and Welcome to Ubuntu Forum :)

Regardless of the other issues you do have at the moment, I recommend to use Lubuntu. What is Lubuntu? please have a look at my signature > Lubuntu One Stop Thread ;)

---

### Post by skandyrv on 2011-11-08
> **amjjawad said:**
> Hello and Welcome to Ubuntu Forum :)

Regardless of the other issues you do have at the moment, I recommend to use Lubuntu. What is Lubuntu? please have a look at my signature > Lubuntu One Stop Thread ;)

Lubuntu? Thats a new one.. Lightweight version? Something like Kubuntu or XUbuntu then?

---

### Post by amjjawad on 2011-11-08
> **skandyrv said:**
> Lubuntu? Thats a new one.. Lightweight version? Something like Kubuntu or XUbuntu then?
To answer all your questions, please: 
[B][[COLOR=Red]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

[/B]

---

### Post by Elfy on 2011-11-08
It's just based on a different de - lxde.

I'd try it with your machine - but I do prefer xfce personally :)

---

