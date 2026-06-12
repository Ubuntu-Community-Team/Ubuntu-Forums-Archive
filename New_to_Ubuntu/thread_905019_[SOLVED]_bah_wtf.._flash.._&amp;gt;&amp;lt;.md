---
title: "[SOLVED] bah wtf.. flash.. &amp;gt;&amp;lt;"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by adobrakic on 2008-08-29
Alright, I have Linux Mint, so all that flash stuff is downloaded and installed. I also installed 'build-essential' and 'ubuntu-restricted-extras'. My Youtube videos stop working at 0:02, they load and everything though. It just stops at 2 seconds and I can't do anything about it.

Also, if I try to play a flash game, it tells me I need missing plugins, but then when I press the install button, it doesn't know what plugins i need. >_> How convenient.

Also, when I try to listen to stuff from zshare (for example -- [http://www.zshare.net/audio/17746906864c0bef/](http://www.zshare.net/audio/17746906864c0bef/)), it says I have to install missing plugins there, also.

---

### Post by Crafty Kisses on 2008-08-29
Are you using FireFox?

---

### Post by adobrakic on 2008-08-29
Yes I am. Also, I just went to newgrounds and played a game. 
It seems like some sites work and some don't.

---

### Post by Crafty Kisses on 2008-08-30
Post the results > java --version

---

### Post by adobrakic on 2008-08-30
If you mean in terminal:

```

ado@ado-desktop ~ $ java --version
Unrecognized option: --version
Could not create the Java virtual machine.
ado@ado-desktop ~ $ 

```

---

### Post by SunnyRabbiera on 2008-08-30
odd, what are your specs and have you tried to install firefox 2?

---

### Post by adobrakic on 2008-08-30
my specs are:
735mb of ram
32mb video mem. -- s3 prosavage gfx card
1.7ghz processor

i dont really get what that has to do with this issue though. :x

and nah, i haven't tried installing ff2 cause of the memory leak.

---

### Post by SunnyRabbiera on 2008-08-30
> **adobrakic said:**
> my specs are:
735mb of ram
32mb video mem. -- s3 prosavage gfx card
1.7ghz processor

i dont really get what that has to do with this issue though. :x

and nah, i haven't tried installing ff2 cause of the memory leak.

I only asked as sometimes hardware can come into play.
I wouldnt worry about firefox 2's memory leak, as I just suggest a quick fix here...
It may help until we can see what the issue is.

---

### Post by adobrakic on 2008-08-31
ah, yeah... bump.

is there maybe a code that could uninstall any possible streamers (m-player, vlcmozilla) and then install just one. As I've heard that more than one can mess stuff up.

---

### Post by adobrakic on 2008-09-01
bamp

---

### Post by alzie on 2008-09-01
In terminal type java -version  (pesky typos)

---

### Post by adobrakic on 2008-09-01
i get:

> 
ado@ado-desktop ~ $ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)
ado@ado-desktop ~ $ 


---

### Post by alzie on 2008-09-02
I'd check and see that you don't have both flash and gnash installed in synaptic.

There are some issues with flash and firefox and both mozilla and adobe are aware of it.

I was able to solve my issues with flash at games sites like pogo by uninstalling java6 and using synaptic.  (marking sun-java6 packages for uninstall and sun-java5-plugin for install,  It pulled the jre and bin files for me automatically)

Another option would be to try flash 10.  There is a link here: [http://packages.ubuntu.com/hardy-backports/flashplugin-nonfree](http://packages.ubuntu.com/hardy-backports/flashplugin-nonfree) 

I'm holding off until it is available through synaptic.  I had it before through the backports, and while it did solve some issues it created new ones for me.

I hope this is of help to you.

If you do decide to try flash10 remember to remove the old flash first:)

---

### Post by adobrakic on 2008-09-02
Actually, I did have gnash installed. I uninstalled that.
It seems that I only have problems with flash when I have Songbird opened.

I tested youtube.com without songbird opened, and everything played flawlessly. But when I do open it, the videos have no sound (even though i have everything checked as Alsa in prefs > sound), and the videos load but stop playing after 2 seconds.

I'll try downgrading to java5

--edit--

Yeah, i downgraded to java5 and it's the same exact thing. Is there anything I could do to "fix" Songbird?
If not, I can just change to a different music player.

---

### Post by alzie on 2008-09-02
You can look for a fix,  I'm not aware of any but I don't use songbird.

After that a new thread about songbird and flash issues or a different player i guess.  Sorry I can help more.

---

### Post by adobrakic on 2008-09-02
No no, you did help me. I'll switch to other music players and see if there's a difference.

thank you :)

---

