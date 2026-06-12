---
title: "Voice commands"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-06-24
Hy all.I am still new to linux, and I was wandering.Does Ubuntu has a voice command program, like Vista for example?

---

### Post by Canis familiaris on 2008-06-24
> **Troll_the_Great said:**
> Hy all.I am still new to linux, and I was wandering.Does Ubuntu has a voice command program, like Vista for example?
No! Atleast I do not know of! Mainly because it is difficult to achieve and also development would take millions of dollors.
So I have to say Vista is better in this regard.

---

### Post by mishathegoat on 2008-06-24
Ubuntu does not come with one, no. But I know there is one that comes with the Xandros Linux OS that ships with the EeePC. I'm using it right now! It's called VoiceCommand.. But after some googling, it doesn't look like anyone other than EeePC users are using it.

---

### Post by bodhi.zazen on 2008-06-24
You can install Dragon Naturally Speaking and use it under wine, but no no voice commands.

It is sad to see Linux lag so far behind on this, although I acknowledge the technical difficulties of voice recognition.

---

### Post by sdennie on 2008-06-24
You can try gnome-voice-control though, I've never used it:

```

sudo apt-get install gnome-voice-control

```

---

### Post by Troll_the_Great on 2008-06-24
I just did that, lol :).The problem is I can't start it.If I type:
"gnome-voice-control" it "bash: gnome-voice-control: command not found"
Where is my package?How can I start it?I couldn't find it under "Applications" or "System"....

---

### Post by sdennie on 2008-06-24
Try:

```

dpkg -L gnome-voice-control | grep bin/

```

If nothing comes back it could be a panel applet.  Try right clicking on the panel and click Add To Panel and see if you can find it.

---

### Post by Troll_the_Great on 2008-06-24
It is a panel applet, but when I try to add it I get:
"Error
The panel encountered a problem while loading "OAFIID:GNOME_VoiceControlApplet".Do you want to delete the applet from your configuration?
Why?:(

---

### Post by sdennie on 2008-06-24
As I said, I've never used it but only know of its existence.  There is a bug on launchpad that sounds similar to your problem though: [https://bugs.launchpad.net/ubuntu/+source/gnome-voice-control/+bug/219303](https://bugs.launchpad.net/ubuntu/+source/gnome-voice-control/+bug/219303)

---

### Post by ibuclaw on 2008-06-24
It appears that the server file is pointing in the wrong location.

Open up the file
```
sudo gedit /usr/lib/bonobo/servers/GNOME_VoiceControlApplet_Factory.server
```
Then on the fifth line, change
```
location="/usr/libexec/voice_control_applet">
```
to this:
```
**location="/usr/lib/gnome-voice-control/voice_control_applet">**
```

Now it should open up with no problems whatsoever.

Now... the hard part, trying to figure out how it works... (So far I've managed to get it to recognise when I speak).

Regards
Iain

---

### Post by ibuclaw on 2008-06-24
[Well, hear is a video of all you can do.]("http://www.youtube.com/watch?v=GCSgkUnlGGA")

It seems like a good tool, but it will just give you a throat-ache at the end of the day.

Perhaps in a couple years time, maybe they will start to make some decent use out of it.

Regards
Iain

---

### Post by bodhi.zazen on 2008-06-24
> **vor said:**
> Try:

```

dpkg -L gnome-voice-control | grep bin/

```

If nothing comes back it could be a panel applet.  Try right clicking on the panel and click Add To Panel and see if you can find it.

lol @ vor

```
which gnome-voice-control
```

I will check this tool out ...
[indent]allow...  allow...  allow...[/indent]

---

### Post by sdennie on 2008-06-24
> **bodhi.zazen said:**
> lol @ vor

```
which gnome-voice-control
```


Duuude... ;)

> **Troll_the_Great said:**
> I just did that, lol :).The problem is I can't start it.If I type:
"gnome-voice-control" it "bash: gnome-voice-control: command not found"
Where is my package?How can I start it?I couldn't find it under "Applications" or "System"....

---

### Post by ibuclaw on 2008-06-25
> **bodhi.zazen said:**
> lol @ vor

```
which gnome-voice-control
```

I will check this tool out ...
[indent]allow...  allow...  allow...[/indent]

cut...  Cut...  CUT... CUT!...

/me gets a glass of water.

---

### Post by Troll_the_Great on 2008-06-25
Thank you all for your answers.It works! :) I must get used with it, but it works.Thx again.

---

### Post by Canis familiaris on 2008-06-25
> **vor said:**
> You can try gnome-voice-control though, I've never used it:

```

sudo apt-get install gnome-voice-control

```

I have to say the open source developers should be given pat on their back for this. I'm amazed. It seems like an unfinished product but really this effort should be lauded.

---

### Post by peacewithall on 2008-07-07
I agree I was very impressed with this program, it really does help when opening the terminal, without going through all the menu's. But when i try to open my chosen browser or mail client (Firefox, and Thunderbird), it opens programs which are default to it, such as Epiphany and Evolution, although it recognizes the command 'run mail' and opens 'Evolution' instead, Thunderbird is chosen as my default system mail client.

Since it recognizes the mail and browser commands, could it be configured to open my chosen applications? (Firefox, Thunderbird), any one know?.

---

### Post by miggols99 on 2008-07-08
Just change your default applications in the "Preferences" menu..

---

### Post by peacewithall on 2008-07-08
> **miggols99 said:**
> Just change your default applications in the "Preferences" menu..

Thanks for the reply :).

I have changed my default applications, I assume you mean the 'preferred applications' option, but still 'gnome-voice-control', chooses 'evolution' for mail, and does nothing for 'Epiphany' as I don't have it installed.

---

### Post by Ben Carlin on 2008-07-29
Hey I have the applet on the destop but when I click start control it comes up with a message in the little icon thing saying "Calibration" and I try all of the comands but none of them seem to work? My microphone works as I can record using sound recorder after selecting Line-in as the input device? Hmmm I'd love to get this to work, seems awesome!

Any help would be much appriciated!

Benj

---

### Post by sam_delta on 2008-11-21
> **Ben Carlin said:**
> Hey I have the applet on the destop but when I click start control it comes up with a message in the little icon thing saying "Calibration" and I try all of the comands but none of them seem to work? My microphone works as I can record using sound recorder after selecting Line-in as the input device? Hmmm I'd love to get this to work, seems awesome!

Any help would be much appriciated!

Benj

exact same as me, hangs on calibration, mic works great on skype, sound recorder, and audacity...
ubuntu amd64

sam

---

### Post by NeoZiggy on 2009-02-23
-deletes-

---

### Post by wjwh on 2009-03-09
> **tinivole said:**
> It appears that the server file is pointing in the wrong location.

Open up the file
```
sudo gedit /usr/lib/bonobo/servers/GNOME_VoiceControlApplet_Factory.server
```
Then on the fifth line, change
```
location="/usr/libexec/voice_control_applet">
```
to this:
```
**location="/usr/lib/gnome-voice-control/voice_control_applet">**
```

Now it should open up with no problems whatsoever.

Now... the hard part, trying to figure out how it works... (So far I've managed to get it to recognise when I speak).

Regards
Iain

Many thanks for this!  I have now managed to get the applet added to the panel.  I'm still trying to get it to do something useful.  Its list of commands is very limited.  The version which installs in 8.04 is the 0.1.0 version which only has the commands:

RUN TERMINAL : Open gnome-terminal

RUN MAIL : Open Evolution

RUN BROWSER : Open Epiphany

MINIMIZE WINDOW

MAXIMIZE WINDOW

CLOSE WINDOW

NEXT WINDOW

Since I don't use either Evolution or Epiphany this leaves me with almost nothing that is any use!

---

