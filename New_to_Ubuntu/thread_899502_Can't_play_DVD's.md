---
title: "Can't play DVD's?"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by WarpCon on 2008-08-24
I can't get none of the players to play a dvd. I installed ubuntu friday night and im a complete noobe. I used to used unix and linix when all it was was a command line screen. But im stumped with this gui stuff. I tried totem first and it said it did'nt have the correct codec installed, so i went looking around and i think i installed the libdvdcss2 and some other packages correctly, but now when i start totem it pops up and then disappears. I tried mplayer, all it does is lock up. And gxine lockes the whole computer up. I have to pull the power cord to get it to go away when that happens. Or there any step by steps for a noobe to get totem up and running? I went to Medibuntu but it dont give step by step. It said Something about if i installed the whole library do this and that but it did'nt say where I could get the whole library. Any help would be thankfull.

---

### Post by bobnutfield on 2008-08-24
If you don't already have Medibuntu repo installed, go here to get it:

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Read the howtos on that site and all multimedia issues should be solved.  Much easier to install codec, etc. from this repo.

---

### Post by super.rad on 2008-08-24
theres is another guide here [http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_DVD_Support]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_DVD_Support") plus loads of other useful guides for beginners

---

### Post by WarpCon on 2008-08-24
Ok i went to medibuntu and installed w32codecs. When it finished the software update ballon poped up and said libdvdcss2 needed to be installed, so i installed that. Now totem will load the playlist but after a couple of seconds it still dissapears. Any idea's? Also, when i downloaded the package it said it wasnt part of a free library, did i download the wrong thing?

---

### Post by wolfen69 on 2008-08-24
i have noticed many people having problems lately with totem. have you considered trying another player such as vlc? whatever works, right?

---

### Post by Vivaldi Gloria on 2008-08-24
**1)** Enable medibuntu repos following the "Repository HowTo" here:

[http://www.medibuntu.org/](http://www.medibuntu.org/)

You need to enter the following commands as explained there:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

This is true for ubuntu 8.04. For other versions see that link.

**2)** Then install the following programs using the command

```
sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 build-essential ubuntu-restricted-extras
```

**3)** Check if encrypted DVDs work. If not try this command in a terminal:

```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

That should do it.

---

### Post by WarpCon on 2008-08-24
Ok i installed VLC Player and it does the same thing as totem, when it starts it just dissapears. Gloria, I tried that and it downloaded about 148 megs of sunjava stuff, installed and totem still does the same thing, it just dissapears when it comes up. I tried the last command you put up and it said in the terminal that it couldnt find that command. 

I put in a DVD that i had copied and took all the encryption off just to see if that was causing it and it done the same thing with that disk too. 


Is there any way i can take all the packeges, libraries and whatever else i put on back out? If there not going to work why have them in there? Then i will either reformat and start over , or?

---

### Post by WarpCon on 2008-08-24
Sorry for the bump. I'm starting to think that since 2 differant player or doing the same thing and just dissapearing after they start that its something to do with the operating system and not the players? any thoughts?

---

### Post by WarpCon on 2008-08-24
Ok i have tried everything. I uninstalled all the players and packages and then reinstalled totem, then a few others and they still wont play. Do i need to report a bug somewhere?

The only option i have now is to go back to windoz. My wifes tv blew up so she took mine, my computer is the only thing i got to watch movies on now . Wheres the mad emotions at? lol

---

### Post by meanburrito920 on 2008-08-24
run vlc from the gnome-terminal, so it will give you a message when it closes. post the message here.

---

### Post by SunnyRabbiera on 2008-08-24
> **WarpCon said:**
> Ok i have tried everything. I uninstalled all the players and packages and then reinstalled totem, then a few others and they still wont play. Do i need to report a bug somewhere?

The only option i have now is to go back to windoz. My wifes tv blew up so she took mine, my computer is the only thing i got to watch movies on now . Wheres the mad emotions at? lol

Dont give up, there are still many things to try.
Try other players like Xine, Mplayer and the like.
What about libdvdread, try installing that too?

---

### Post by WarpCon on 2008-08-25
I got vlc running in the terminal but i dont know how to start it. Do i have to add a playlist or open the dvd drive?

---

