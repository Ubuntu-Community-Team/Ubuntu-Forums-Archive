---
title: "[SOLVED] problem installing realpalyer 11"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by koba101 on 2008-08-27
Hi,

I've downloaded RealPlayerGold 11 from [www.real.com](www.real.com)

problem is when  i try to install it on Hardy
```

sudo sh RealPlayerGOLD11.bin 
```

i get the following error:

```
RealPlayer11GOLD.bin: 7: Syntax error: "(" unexpected
```


what can i do about this?

---

### Post by kellemes on 2008-08-27
> **koba101 said:**
> (..) what can i do about this?

```
chmod +x RealPlayerGOLD11.bin
sudo ./RealPlayerGOLD11.bin
```

---

### Post by Ryadt on 2008-08-27
Hi..Is there any particular reason to why you want to install Realplayer?

---

### Post by koba101 on 2008-08-27
yeah...the seek bar is much better than mplayer....you can click anywhere on the bar and it will take you there; rather than mplayer which you have to drag to the right place

and it's good to have a variety of players, is it propriety? if it is then i might not.

anyway  i tried the chmod +x and it works, i find that weird since that's the first thing i thought about when the error happened by i gues there's a difference between 

**./ **  and **sh**

---

### Post by linuxguymarshall on 2008-08-27
realPlayer is ultra-proprietary. Might I recommend VLC?

---

### Post by kellemes on 2008-08-28
> **koba101 said:**
> (..)i gues there's a difference between **./ **  and **sh**

Indeed there is..
In many cases you will execute a script using . (dot)
This is needed when the scripts directory (current directory) isn't in your path, this will most often be the case.
Your script will be executed in the current shell, meaning any changes to your environmet (made by the script) will be visible when the script finishes.

**sh script.sh** will create another subshell of your current shell and execute the script. This means any changes to your environment will be "forgotten" when the script finishes.
General it will be used for debugging a script, see how it functions in a shell environment with specific conditions.

---

### Post by SunnyRabbiera on 2008-08-28
well there is a debian installer:
> **benerivo said:**
> I would install a program to Ubuntu via a .deb file rather than  a .bin file, as it is easier to uninstall. If you download [this]("http://debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.9-0.2_i386.deb") file and double click on it then it should install real player.

that should work, realplayer 10 is good enough and there is no urgency to use realplayer 11

---

### Post by koba101 on 2008-08-29
there's something i don't...helix is available in synaptic so my guess is that it's open source, when you check whether or not there's an update...it takes you to realplayer11...interesting

anyway like i said, the seek  bar with real player is better than anyother player i've seen...choose the position you want and click and it takes you there...other players you'd need to drag the thing like a stupid fast forward.

---

### Post by Jimmy9pints on 2008-08-29
I use Realplayer to listen to the BBC. 

I strongly prefer not to use it because it is proprietary software, but as far as I know, there is not an opensource replacement to it. Helix player for example won't handle the .rm from the BBC.

I'd be happy to be corrected on this if I am wrong.

James.

---

### Post by p_quarles on 2008-08-29
Please keep your answers on topic, folks. The question is how to use RealPlayer. Asking the OP why he/she wants to use this program is off-topic. 

Don't let that continue, please.

---

### Post by brons2 on 2008-08-29
> **SunnyRabbiera said:**
> well there is a debian installer:


that should work, realplayer 10 is good enough and there is no urgency to use realplayer 11

those instructions worked for me, thanks!

I need realplayer because my job requires it...

---

### Post by msayed2004 on 2008-09-25
> **koba101 said:**
> yeah...the seek bar is much better than mplayer....you can click anywhere on the bar and it will take you there; rather than mplayer which you have to drag to the right place> **koba101 said:**
> anyway like i said, the seek  bar with real player is better than anyother player i've seen...choose the position you want and click and it takes you there...other players you'd need to drag the thing like a stupid fast forward.Well, I don't see any seek bar :roll: ?!

---

