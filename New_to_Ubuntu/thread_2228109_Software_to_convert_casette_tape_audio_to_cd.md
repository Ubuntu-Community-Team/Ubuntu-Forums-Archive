---
title: "Software to convert casette tape audio to cd?"
date: 2014-06-05
forum: New to Ubuntu
---

### Post by AbleTassie on 2014-06-05
Is there Linux/Ubuntu software to convert casette tape audio to cd? Such software apparently exists for Windows 7 Professional.

Thanks,

R.

---

### Post by Dennis N on 2014-06-05
Two programs will handle it: Audacity and Brasero (or other CD burner)

Use Audacity to convert the audio tape to a Audacity project file, edit into individual tracks, and export each track to a WAV file. Then Brasero to burn the tracks to CD. I've done it many times.

---

### Post by deadflowr on 2014-06-05
+1 to audacity.
I used it, forgot how.
 But I do remember I did some extra clean up to the recording for a tinny bit more cleaner sound.
My tapes were in very bad condition, but I was able to make the sound quality a little better.(still garbage,though)
Here some good help on that, possibly
[http://audacity.sourceforge.net/help/faq_i18n?s=recording&i=records-tapes](http://audacity.sourceforge.net/help/faq_i18n?s=recording&i=records-tapes)

---

### Post by AbleTassie on 2014-06-06
Thanks Dennis and Deadflwr,

I take it that the "  'line in' connector" referred to at  [http://audacity.sourceforge.net/help/faq_i18n?s=recording&i=records-tapes](http://audacity.sourceforge.net/help/faq_i18n?s=recording&i=records-tapes)  is the microphone input jack of the computer, correct?

Is there a Terminal Command for downloading the Audacity software?

Thanks,

R.

---

### Post by monkeybrain20122 on 2014-06-06
> **RMcGinnis said:**
> Thanks Dennis and Deadflwr,


Is there a Terminal Command for downloading the Audacity software?

Thanks,

R.

For Ubuntu <=13.10
```
sudo apt-get install audacity
```
or install with your favourite GUI (synaptic, software centre, muon)

For Ubuntu 14.04
[https://launchpad.net/~mc3man/+archive/testing5](https://launchpad.net/~mc3man/+archive/testing5)
Read the instructions.

---

### Post by squakie on 2014-06-06
If you haven't already, you may want to install one of the package manager front-ends.  Synaptic isn't installed by default anymore, but you can easily install it to get a gui'd package manager back:

This has been edited to show the correct syntax:

sudo apt-get install synaptic

---

### Post by Dennis N on 2014-06-06
> **RMcGinnis said:**
> Thanks Dennis and Deadflwr,

I take it that the "  'line in' connector" referred to at  [http://audacity.sourceforge.net/help/faq_i18n?s=recording&i=records-tapes](http://audacity.sourceforge.net/help/faq_i18n?s=recording&i=records-tapes)  is the microphone input jack of the computer, correct?

Is there a Terminal Command for downloading the Audacity software?

Thanks,

R.

I do all of this kind of work on a desktop machine.  The line-in jack (connector) is not the same as a microphone jack. Desktop computers are likely to have line-in (color-coded blue) and line-out (color-coded green) connections as well as a microphone jack (color-coded pink).  LIne-in is for connections from cassette player or CD player. If you don't have a line-in on the computer, try the microphone connector. 

In the past, I recall a few times recording a cassette from a Sony Walkman using the headphone jack as the output (there is no other output). That works, but your input sound level is low.  I haven't recorded tapes through the computer's microphone connection.

I think best results are when you play the cassette on a standard tape deck with a line-out jack (normally goes to an amplifier). Line-out connects directly to the computer's line-in jack.

Audacity is in the repositories, as the other post has noted.

---

### Post by Rob Sayer on 2014-06-06
The actual command to install synaptic in terminal is:

sudo apt-get install synaptic

And before installing anything you should run:

sudo apt-get update

Which is an option in synaptic (hit 'Reload').

I also highly recommend synaptic.  Never mind me, pretty much all the REALLY knowledgeable linux geeks here do too.  It has a bit of a learning curve which is well worth it.

My favorite thing about synaptic is probably that it has a well organized history function.

Actually I use synaptic or the terminal to install everything nowadays.  It's been a long time since I used the ubuntu software center.  It's too slow and I don't find the ratings all that useful really.

---

### Post by squakie on 2014-06-06
> **Rob Sayer said:**
> The actual command to install synaptic in terminal is:

sudo apt-get install synaptic

And before installing anything you should run:

sudo apt-get update

Which is an option in synaptic (hit 'Reload').

I also highly recommend synaptic.  Never mind me, pretty much all the REALLY knowledgeable linux geeks here do too.  It has a bit of a learning curve which is well worth it.

My favorite thing about synaptic is probably that it has a well organized history function.

Actually I use synaptic or the terminal to install everything nowadays.  It's been a long time since I used the ubuntu software center.  It's too slow and I don't find the ratings all that useful really.


Thanks for that!  I had a cell phone ringing in my pocket AND my cat decided to jump up on the laptop right when I was typing - got extremely distracted and never checked it after the cat jumped on the keyboard!  Thanks again! ;)

To the OP - if you don't know, Synaptic package manager provides a GUI'd interface to review, install and remove software packages, so unless you really enjoy just using the command line some of us actually do!) you may want it.  You can search packages by group type, read descriptions, etc..

---

### Post by squakie on 2014-06-06
There are also preamp adapters available to allow you to take line-level outputs from things like turntables, stereo cassette players, etc., and connect via USB and work directly with Audacity.  See such things as [http://www.ebay.com/itm/New-Behringer-U-PHONO-UFO202-USB-Audio-Interface-w-Built-in-Phono-Preamp-/181273994676?pt=US_Computer_Recording_Interfaces&hash=item2a34c5a5b4](http://www.ebay.com/itm/New-Behringer-U-PHONO-UFO202-USB-Audio-Interface-w-Built-in-Phono-Preamp-/181273994676?pt=US_Computer_Recording_Interfaces&hash=item2a34c5a5b4)

---

### Post by AbleTassie on 2014-06-06
> **Dennis N said:**
> I do all of this kind of work on a desktop machine.  The line-in jack (connector) is not the same as a microphone jack. Desktop computers are likely to have line-in (color-coded blue) and line-out (color-coded green) connections as well as a microphone jack (color-coded pink).  LIne-in is for connections from cassette player or CD player. If you don't have a line-in on the computer, try the microphone connector. 

In the past, I recall a few times recording a cassette from a Sony Walkman using the headphone jack as the output (there is no other output). That works, but your input sound level is low.  I haven't recorded tapes through the computer's microphone connection.

I think best results are when you play the cassette on a standard tape deck with a line-out jack (normally goes to an amplifier). Line-out connects directly to the computer's line-in jack.

Audacity is in the repositories, as the other post has noted.

Unfortunately my machine is a laptop, with no "line in" or "line out." The microphone jack is color coded pink, the headphone jack is color coded green. 

Regarding download and installation of apps, unless I am mistaken, one of the forum moderators here recommended using terminal commands if at all possible, rather than using the Lubunu Software Center (or similar GUIs), I think.

Thanks,

R.

---

### Post by deadflowr on 2014-06-06
> **RMcGinnis said:**
> 
Regarding download and installation of apps, unless I am mistaken, one of the forum moderators here recommended using terminal commands if at all possible, rather than using the Lubunu Software Center (or similar GUIs), I think.


My take is, "Whatever floats your boat."

---

### Post by The Cog on 2014-06-06
> **RMcGinnis said:**
> 
Regarding download and installation of apps, unless I am mistaken, one of the forum moderators here recommended using terminal commands if at all possible, rather than using the Lubunu Software Center (or similar GUIs), I think.

It's not that the mods recommend command line. It's just that when giving help, a one-line command is much easier to type than writing a paragraph each on how to do something with Ubuntu(Unity), Ubuntu(gnome3), Ubuntu(gnome2), Xubuntu, Kubuntu and Lubuntu. And that's before any possible user GUI customisations. And assuming the other person even has a GUI (Ubuntu server doesn't install a GUI by default).

To my mind, if somebody can't be bothered to type a command because they would rather use a GUI, then I can't be bothered to write an essay for them. Especially when I'm in a cantankerous mood. But that's my choice when giving help, and other contributors are free to write as many essays as they want.

---

### Post by Dennis N on 2014-06-07
> **RMcGinnis said:**
> Unfortunately my machine is a laptop, with no "line in" or "line out." The microphone jack is color coded pink, the headphone jack is color coded green... 

Well, both my laptops are like that also - no line-in jack. I tested recording a cassette with Audacity on my Dell laptop (with Xubuntu 12.04) using it's audio-in jack (which is supposed to be for a microphone, according to the specs) and it all worked fine for me and the result sounds good. So I would say say go ahead with using the microphone jack. I used my old Sony Walkman as the cassette player.

It will take some practice to get familiar with Audacity, but the documentation they have is pretty good.

---

### Post by AbleTassie on 2014-06-07
> **The Cog said:**
> It's not that the mods recommend command line. It's just that when giving help, a one-line command is much easier to type than writing a paragraph each on how to do something with Ubuntu(Unity), Ubuntu(gnome3), Ubuntu(gnome2), Xubuntu, Kubuntu and Lubuntu. And that's before any possible user GUI customisations. And assuming the other person even has a GUI (Ubuntu server doesn't install a GUI by default).

To my mind, if somebody can't be bothered to type a command because they would rather use a GUI, then I can't be bothered to write an essay for them. Especially when I'm in a cantankerous mood. But that's my choice when giving help, and other contributors are free to write as many essays as they want.

Unless I am mistaken I think the moderator said it was safer to use a terminal command, but I could be mistaken about this.

Thanks,

R.

---

### Post by AbleTassie on 2014-06-07
> **Dennis N said:**
> Well, both my laptops are like that also - no line-in jack. I tested recording a cassette with Audacity on my Dell laptop (with Xubuntu 12.04) using it's audio-in jack (which is supposed to be for a microphone, according to the specs) and it all worked fine for me and the result sounds good. So I would say say go ahead with using the microphone jack. I used my old Sony Walkman as the cassette player.

It will take some practice to get familiar with Audacity, but the documentation they have is pretty good.

Thanks Dennis, I may look into using the microphone jack. Since the audio is not music, but "Books on Tape" type voice narration, one approach may be the "poor man's approach" of just playing the tape and putting an actual microphone near the speakers and connecting the microphone to the computer. 

The page at this link  [http://manual.audacityteam.org/o/man/how_to_connect_your_equipment.html](http://manual.audacityteam.org/o/man/how_to_connect_your_equipment.html)  cautions that using the microphone jack could result in too strong a  signal being inputted to the computer, with the resultant problems (see below):
[I]"You should **not** generally connect to the microphone (red) port of the computer. 
[/I]

[LIST]
[*][I] It will excessively amplify the stronger line-level signals  produced by a tape deck or receiver/amplifier. This could lead to damage  to the port or to your sound device. 
[/I]
[*][I] A microphone port is typically mono. If the port is mono then,  even if you connect a stereo input to it and set Audacity to record in  stereo, you will only record "dual mono" which has the same content in  left and right.  
[/I]
[/LIST]
[I]The are only a few exceptions where you should connect to a computer microphone input: 
[/I]

[LIST]
[*][I] On some personal recorders, connecting from a low power  minijack intended for connection to the microphone input of a recorder;  
[/I]
[*][I] On some Macs, or some Windows laptops or desktops, connecting  to a "switchable" port which can be toggled to line-level stereo. Check  your computer manual to see if there is a switch on the computer itself  or in the sound card control panel. On a few laptops the line-level  source is called "mix" or "stereo mix", but on most machines "stereo  mix" will only record computer playback. 
[/I]
[*][I] On recent Windows laptops, notebooks or netbooks, there may be  a "compliant" single port which will tolerate line level input and may  provide stereo input. Even if stereo, the quality may not be as high as  that of a dedicated line-in port.   
[/I]
[/LIST]
[I]Always try line-level input first, and only use a microphone input if  you cannot otherwise get adequate recording volume. You can buy  modestly priced, decent quality USB interfaces with line level stereo  input if needs be.  
[/I]
[I]If there is no way to record at line-level, add a line-in by adding a  sound card or interface that connects to the computer via USB. Examples  of recommendable devices: 
[/I]

[LIST]
[*][I] [Behringer UCA202]("http://www.behringer.com/EN/Products/UCA202.aspx") (left and right RCA inputs/outputs)  
[/I]
[*][I] [Roland Duo Capture UA-11]("http://www.roland.co.uk/products/productdetails.aspx?p=1155") (jack 1/8" & 1/4" inputs and 1/8" mini-jack output) 
[/I]
[*]* [Griffin iMic]("https://store.griffintechnology.com/imic") (standard 1/8 inch input)"*
[/LIST]
 
 
Thank you,

R.

---

### Post by Dennis N on 2014-06-07
As to the input level, turn the volume on the player down to zero before you start playing the tape, monitor the input level with Audacity (it has a signal level meter) and slowly increase the volume on the player until the level is correct. The documentation tells you how to determine the correct level. After this adjusting to the correct level, you can begin making the real recording.

Edit: I didn't mention that you can also adjust the input levels within Audacity. But if you are concerned about damaging something using the mic input, start the player at zero volume to be safe.

---

### Post by echotech2 on 2014-06-07
I picked up an (older) amplifier at a yard sale.  It has MIC, PHONO, AUX1 and AUX2 inputs. I connect Amp LineOut -> Soundcard LineIn and I'm ready to record from just about anything.

It also has a SPEAKER ON/OFF switch FWIW.

---

### Post by Dennis N on 2014-06-07
I would use an amplifier when using a record on a phonograph turntable as the audio source, but find it isn't needed for connecting the computer line-in to devices such as a cassette deck line-out or cd player line-out.

---

### Post by squakie on 2014-06-07
As I mentioned earlier, take a look at the the audio interface/preamp devices that connect via USB.  You won't have to worry about "overloading" an input, etc..  They can be used to basically connect any analog audio source as the input can be set for line level - hence the preamp - or for just "normal" audio.  Output is to USB for input to the computer.  No worries about interfacing, what goes where, will it overload, none of that.  Simple as can be.  It's also mentioned in the bottom of the post RMcGinnis is quoting from.

---

### Post by AbleTassie on 2014-06-07
> **Dennis N said:**
> Two programs will handle it: Audacity and Brasero (or other CD burner)

Use Audacity to convert the audio tape to a Audacity project file, edit into individual tracks, and export each track to a WAV file. Then Brasero to burn the tracks to CD. I've done it many times.

Dennis,

I will use Ubuntu to burn the CDs as you suggest. But I have a question. If I use audacity to create files before CD burning and I want to send one or more of those files over the internet to somebody else, do they have to have the Linux operating system to play the files?

Thanks,

R.

---

### Post by deadflowr on 2014-06-07
> **RMcGinnis said:**
> Dennis,

I will use Ubuntu to burn the CDs as you suggest. But I have a question. If I use audacity to create files before CD burning and I want to send one or more of those files over the internet to somebody else, do they have to have the Linux operating system to play the files?

Thanks,

R.

I'll answer quickly. 
No, they don't need a linux machine.
You can export the recorded output as mp3 or any other format, which will play on linux or windows.
(Don't use macs so don't know what formats macs can use, I would guess it can use the same, but that's a guess)

---

### Post by AbleTassie on 2014-06-12
Thank you to everybody. I got Audacity working well with Windows XP -- I am dual booting Lubuntu and Windows XP. There seem to be some problems on the Linux side in terms of the output and input drop down menus and selection in Audacity. This problem may well relate to the age of my machine. I will try to figure these out evnetually and see if I can use the Linux side. But I'll likely used Brasero (LInux) to burn the CDs using files that are in MP3 format.

I am using a standard cassette player and running a lead from the earphone jack of the cassette player to the microphone jack of the PC and this works well. I have to adjust the volume on the cassette player to get the signal right. The monitoring signal plot in Audacity is very helpful for this. As an aside I had to add some downloadable patches to get Audacity working for Windows XP and also to export Audacity files as MP3 files. These patches were explained on the Audacity website.  

Thanks again, I will mark this thread as SOLVED.

R.

---

