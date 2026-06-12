---
title: "Couple Things.."
date: 2011-09-24
forum: New to Ubuntu
---

### Post by ShawnxBuntu on 2011-09-24
Hi, im new to Ubuntu/Xubuntu... Learning Commands Etc but i Installed this OS Last night.. and to a surprise I Downloaded Adobe Flash Player.. went to Youtube to check the Sound to see if it was Working and the Subwoofer.. Only Played (Underneath) my laptop.. And i cannot figure out why... I tryed all these different solutiions.. I added command lines to the alsa-base.conf..  Like everyone told me to do and find the model of my computer and i did that buuut... i couldnt find the model of my computer so i used the model of a diff computer but still "MSI".  I tryed to do the Update to Alsa 1.0.24.2 with a script and nothings working.. can someone help me?..  The Model of my VC is Realtek ALC888, Model of My computer is MSI GT660
    another problem is that.. everytime i logon to xubuntu i click on Home and it just sits there.. for like 2 mins then pops up with an error message "unable to open folder"..
   Thank you..

---

### Post by oldos2er on 2011-09-24
Moved to Absolute Beginners.

Which version of Xubuntu did you install? Did you install flash from the repositories? Who is "everyone"?

---

### Post by ShawnxBuntu on 2011-09-24
I Installed Xubuntu 11.0.4.. and by everyone i ment like i went on google and went to other forums and i followed intructions on how to do it but nothing seems to work... and yes i went to Software center and installed it.

---

### Post by Lisiano on 2011-09-24
Please correct me if I'm wrong but Pulse is used now on all *buntus right?
Since I don't know if Xubuntu has a similar sound config window as gnome, install a program called padevchooser and pavucontrol
```
sudo apt-get install padevchooser pavucontrol
```
IF it tries to install PulseAudio, don't install it and ignore the rest of my post.
Now type this in your terminal```
padevchooser
``` and you will see a new icon pop up in the taskbar. Click it and select Volume Control and go to Output Devices, if you have more than 1 item in the list, try to find one that has the needed channels in the Port menu, then select the needed channels in the port menu and finaly click the padevchooser icon again -> Default Sink -> name of the output device you found in Volume Control

---

### Post by searchfgold6789 on 2011-09-24
> **ShawnxBuntu said:**
> 
    another problem is that.. everytime i logon to xubuntu i click on Home and it just sits there.. for like 2 mins then pops up with an error message "unable to open folder"..
That sounds like a serious problem. After you have done so much configuring to your computer, it would greatly help us to know *exactly* what scripts you ran, drivers you got, lines you added to what files... At this point, it may be better to simply start over and reinstall from scratch then post back here (if you still have the problem) so you don't have to rely on google to know what you are doing. I can suggest a couple of things after you reinstall:

[LIST]
[*]Running updates: Go to the Update Manager (from System), use Synaptic and reload the package information, or use the Terminal from Accessories: ```
sudo apt-get update && sudo apt-get upgrade)
```This will run updates that sometimes get missed during initial installation.
[*]Running [Sound Troubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting").
[/LIST]
 - search

---

### Post by ShawnxBuntu on 2011-09-24
I did what u told me to... and it didnt work..now why does it says hda intel (alsa mixer)? shouldnt it say like realtek or something..it says my codec is realtek alc888... im just lost.. i mean im very new to this

---

### Post by ShawnxBuntu on 2011-09-24
I didnt run any scripts that can "harm" my computer.. it was just simple "Alsa Update script" for 1.0.24.2 instead of 1.0.23... just added a line of code to the alsa-base.conf.. that shows the model of my computer thats all.. like i said im very new still learning..

---

### Post by ShawnxBuntu on 2011-09-24
This is what it says Most of the time i click on Home
 "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

---

### Post by ShawnxBuntu on 2011-09-24
[LEFT]Seachforgold.. This is what i got from it.. I reinstalled Xubuntu.. and i reinstalled all of the 173 updates that it had for the OS.. And then i retstarted the system an it says

          "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken"

  But before the Updates were Made it had no problem opening the /home/ folder.. i mean all it does it says that error msg an then opens.. But like i said It Stalls for about 1-2 mins then displays the error msg an then opens..
    And as far as my Sound is concerned It works really well with headphones.. but when i have the main Speakers on.. it doesnt play threw the right audio speakers... it plays through the subwoofer and thats all.. Im not sure if its not loading the module or what.. I know it says "HDA Intel" as my output but i have Realtek ALC888 sound card.. checked the Codec its Realtek ALC888, so Im not sure whats going on. 
 As Far as The Error Msg Nor the Sound Cardd Issue.
[/LEFT]

---

