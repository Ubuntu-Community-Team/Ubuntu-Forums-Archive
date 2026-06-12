---
title: "Lubuntu Audio Issues"
date: 2013-06-29
forum: New to Ubuntu
---

### Post by TCZaro on 2013-06-29
Hello absolute linux/lubuntu beginner here, and I have some issues. I installed the latest lubuntu (intelx86) onto my desktop, and everything is working perfectly however my audio from youtube/music is very poor quality. I have to turn my speaker all the way up to have normal volume, and all I hear is static. I have used the "*volume contro*l" setting to try different audio configs but it is no use. I have tried every config with pulseaudio with no result. I tried uninstalling/reinstalling pulseaudio with no results.When running windows XP, the sound was just fine, but now its no longer functioning. I'm using a dell XPS 400. I have tried most everything that the lubuntu wiki on sound issues has told me to do, but i can get anywhere. If it helps I also have a Zylux external subwoofer, and lubuntu recognizes my X-Fi sound in pulse audio.
I would appreciate any help, and will gladly answer any questions that will help diagnose the problem.
EDIT:

lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring
dovidio@dovidio-Dell-DXP051:~$ 


sudo lshw -C multimedia
*-multimedia UNCLAIMED  
       description: Multimedia controller
       product: Theater 550 PRO PCIe
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
       resources: memory:fbe00000-fbefffff memory:f0000000-f1ffffff
  *-multimedia
       description: Multimedia audio controller
       product: SB X-Fi
       vendor: Creative Labs
       physical id: 4
       bus info: pci@0000:05:04.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=snd_ctxfi latency=64 maxlatency=5 mingnt=4
       resources: irq:16 ioport:cce0(size=32) memory:fb600000-fb7fffff memory:f4000000-f7ffffff

More info: With headphones plugged in the sound is perfect, so maybe it is just my speakers that are causing the trouble? I am having this issue with all sound, not just youtube.

---

### Post by TCZaro on 2013-06-30
Any suggestions?

---

### Post by newb85 on 2013-06-30
First, welcome to Ubuntu and the forums!

Is this problem confined to Youtube (indicating it's probably an issue with your Flash player) or system-wide (probably a hardware or driver issue)?

It might help if you gave us some information about your system, starting with the outputs of these two terminal commands. (You can simply highlight them in your browser and drag them to the terminal, rather than copying them manually.)

```
lsb_release -a
```
```
sudo lshw -C multimedia
```

---

### Post by amjjawad on 2013-06-30
Hello and Welcome :)

Thank you for choosing and using Lubuntu!

> sudo lshw -C multimedia
*-multimedia UNCLAIMED  
       description: Multimedia controller
       [COLOR=#ff0000][B]product: Theater 550 PRO PCIe
[/B][/COLOR]       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
       resources: memory:fbe00000-fbefffff memory:f0000000-f1ffffff
  
Is this the main speaker that you have?


> *-multimedia
       description: Multimedia audio controller
       product: SB X-Fi
       vendor: Creative Labs
       physical id: 4
       bus info: pci@0000:05:04.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: [COLOR=#ff0000]**driver=snd_ctxfi**[/COLOR] latency=64 maxlatency=5 mingnt=4
       resources: irq:16 ioport:cce0(size=32) memory:fb600000-fb7fffff memory:f4000000-f7ffffff

Is this your headphone?

> More info: With headphones plugged in the sound is perfect, so maybe it is just my speakers that are causing the trouble? I am having this issue with all sound, not just youtube.
From the information you have shared so far, I think the system is not recognizing your speaker while it does for the headphone. The 

```
lshw -C multimedia

```
is showing that.

The first product has no driver while the 2nd one does. If the 2nd one is your headphone and the first is your speaker, then that is the issue. As long as everything is fine with your headphone, this means the system itself has no issue but the output device is having an issue. It could be driver issue (most likely).

Thank you!

---

### Post by newb85 on 2013-06-30
I could be wrong, but I think the Theater 550 PRO is a TV tuner, and the SB X-Fi is the sound card that includes the headphone jack in addition to three speaker jacks (for surround sound).    At least, that's the description I get here [http://accessories.us.dell.com/sna/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=A1544782&ef_id=UZbtBwAABD6jGyV@:20130630195911:s&dgc=ST&cid=262077&lid=4742363&acd=1230980731501410](http://accessories.us.dell.com/sna/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=A1544782&ef_id=UZbtBwAABD6jGyV@:20130630195911:s&dgc=ST&cid=262077&lid=4742363&acd=1230980731501410).

Is that correct?

---

### Post by TCZaro on 2013-07-01
@ newb85 I think that you are correct. I do not believe I have any component called "[COLOR=#000000]Theater 550 PRO", but I do know that my X-Fi sound card (which is recognized in pulseaudio) "[/COLOR][COLOR=#000000] includes the headphone jack in addition to three speaker jacks (for surround sound)". [/COLOR]
[COLOR=#000000]If my system did not recognize my speaker, then could it still produce sound, no matter how poor quality? Would getting new speakers solve this problem? If I got USB speakers (I don't care about sound quality) would the system not recognize them?[/COLOR]

---

### Post by TCZaro on 2013-07-02
Anybody have any ideas?

---

### Post by newb85 on 2013-07-02
If the speaker jacks are standard 1.5mm stereo jacks, then there's no recognition to be done, and either the speaker outputs of your card aren't working correctly, or your speakers are bad.

---

### Post by newb85 on 2013-07-02
If you run alsamixer in a terminal, does it show different volumes for each channel?

---

### Post by TCZaro on 2013-07-02
I tried different speakers, with the same result. When I run alsamixer it shows the channels at 100 <> 100. With these new speakers I was able to plug my headphones into the speaker, and I heard the same static, and garbled noise. The speakers are new, so its unlikely that something is wrong with them, so I guess it's something wrong with my computer.  I don't know why switching over to lubuntu would cause this problem though.

Solved!!
The problem was that for some reason, the back audio jack for the 3.5mm cable produced the low quality sound, while the front jack did. Thanks for everyone who helped.

---

### Post by newb85 on 2013-07-02
If it worked fine with Windows, my guess is it's the drivers.  They're provided by Creative (The sound card manufacturer).  They haven't left BETA yet.  And they haven't been updated since April 2008.  [Insert crow noises and tumbleweed blowing by here.]  How do you feel about dropping a new/different inexpensive sound card in this machine?

---

### Post by TCZaro on 2013-07-02
Why do my headphones work but not my speakers?

---

