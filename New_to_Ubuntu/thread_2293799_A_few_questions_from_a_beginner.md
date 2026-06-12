---
title: "A few questions from a beginner"
date: 2015-09-07
forum: New to Ubuntu
---

### Post by fund_raiser on 2015-09-07
Hello Dear Users

I am new to Lubuntu. I am going to abandon obsolete xp system and start using Lubuntu (I don't like ubuntu because of Unity and its gaudy animations). Let me please have a few questions please. 

1. Speakers in my monitor does not work after Lubuntu instalation. I also have headphones and they work OK. On win xp I could hear both voice from headphones and monitor speakers. Now only headphones work. Why there is no voice from monitor speakers?
2. How to open CD content? There is no CD in Fail Manager PCman.
3. Are there any other applications to mount mdf files? I tries using Furius ISO, but the directory that F-ISO points out as *mount point* is empty... no content is visible there. (please do not suggest converting mdf to iso)


Thank you

---

### Post by yancek on 2015-09-07
The link below has some info on mdf files on Linux.  Seems to be microsoft proprietary.

[http://pc-freak.net/blog/how-to-mount-mdf-images-in-debian-gnu-linux-what-is-the-mdf-and-mds-file/](http://pc-freak.net/blog/how-to-mount-mdf-images-in-debian-gnu-linux-what-is-the-mdf-and-mds-file/)

A CD/DVD/flash drive will generally show up under the /media directory when inserted.  Most systems have a pop-up asking what you want to do with it.  I don't use Lubuntu so I don't know if that works.

---

### Post by SeijiSensei on 2015-09-08
[Open a terminal]("https://help.ubuntu.com/community/Lubuntu/Documentation/LXTerminal") with Ctrl+Alt+T, then enter these commands one per line to install the program **pavucontrol** from the repositories and run it from the command prompt:
```

sudo apt-get update
sudo apt-get install pavucontrol
pavucontrol &

```
You will be prompted to enter your login password after the first "sudo" command.  You will see a screen that lets you examine all the audio inputs and outputs and set their values accordingly.  It may be that the speakers are muted by default, for instance.

(The "&" tells the operating system to run pavucontrol "in the background" as a separate process.  That way you can continue to use the terminal for other commands.)

---

### Post by fund_raiser on 2015-09-16
The voice isn't muted.  I think it is about drivers.

Let me get this straight
1. My headphones are plugged into the green input
2. Speakers from my monitor (belinea 10 17 25) are plugged into the blue input

Only my headphones run. _Speakers don't run_. On windows OS there was no problem to hear voice both from  speakers and headphones. Do I really need to install what you suggest? I don't want to clutter my Lubuntu system.

---

### Post by nothingspecial on 2015-09-16
pavucontrol will let you check this.

It is very small and will not "clutter" your system

---

### Post by SeijiSensei on 2015-09-16
Most Linux software like pavucontrol have pretty minuscule footprints.  The program itself is just 299K; its associated files like manual pages and the like aren't large either.

You can choose to install this program or not, but I've found it very useful for managing audio devices.

---

### Post by fund_raiser on 2015-09-16
ok, I run as you say and a VOLUME CONTROL opens. What am I supposed to do next? Nothing is muted and the slider is set at 100%. Looks like only green input runs. The blue one is dead (I have swapped jacks). 
_Why is the blue input dead?_ My motherboard is G31M-ES2L. (I am using the rear panel of my motherboard to plug headphones and speakers.)

thx

---

### Post by tea for one on 2015-09-17
> **fund_raiser said:**
> ok, I run as you say and a VOLUME CONTROL opens. What am I supposed to do next? Nothing is muted and the slider is set at 100%. Looks like only green input runs. The blue one is dead (I have swapped jacks). 
_Why is the blue input dead?_ My motherboard is G31M-ES2L. (I am using the rear panel of my motherboard to plug headphones and speakers.)

thx

Good evening

I have an Intel motherboard which seems similar to yours.

The green jack on the back of your motherboard is audio out (to a monitor, separate speakers or headphones)

The blue jack is audio in (for example, to record from a radio or similar input device)

Do you have a green jack on the front of your PC? 

If so, plug your headphones into the front and your speakers into the green jack at the back.

Failing that, try your headphones and speakers independently in the green jack to see if both still function with Lubuntu.

---

### Post by Geoffrey_Arndt on 2015-09-17
Many speakers have headphone ports - - use the green ports as Tea for One suggests, and your problems should be taken care of.    If your speakers don't have headphone ports, buy an audio port splitter (many available online).

---

### Post by fund_raiser on 2015-09-24
Thanks for your advice. I bought a front panel to my case (the old one is broken). I screwed it and connected to the motherboard. Now I can connect headphones to the front panel, but sth is wrong. It works, but I can hear sound while scrolling down a page on the internet, or I hear the HDD running through the headphones, I even hear beeps while moving my mose. In a nutshell there are sounds in the background. Why is that and what am I supposed to do?
PS
Damn it. I thought my problem would be over after buying front panel.

---

### Post by sudodus on 2015-09-24
Please install also ***Pulseaudio***

```
sudo apt-get install pulseaudio
```

Maybe it is already installed. Then the command above will tell you.

Then give ***Pavucontrol*** a second chance. Try all the settings for input and output and hardware - spend at least an hour 'turning the knobs', while you are playing music or a video with a sound-track. I think that you will suddenly find a setting that works.

---

### Post by ian-weisser on 2015-09-24
> **fund_raiser said:**
> I can hear sound while scrolling down a page on the internet, or I hear the HDD running through the headphones, I even hear beeps while moving my mose.

I'm not sure what a 'mose' is, but that sounds to me like your system may not have proper electrical grounding.
If so, that's dangerous - don't put ungrounded electrical conductors (like headphones) near your brain until you fix it.

---

### Post by fund_raiser on 2015-09-24
There are no knobs in the pavucontrol and no hardware tab. I am not sure it is about settings

mose = mouse (sorry for the typo)

I hear the sounds only when plugging the headphones to the front panel. No murmur while plugging headphones to the rear audio panel. Shall I still fix the grounding? How to do it? My mobo is screwed to the casing.

PS
I have an audio spliter. Now I am using audio spliter and I have music both in speakers and headphones and no murmur/noise. However I am still concerned about the front panel audio connector and the sounds I hear. I wish I could use the front panel. Even when typing letters I can hear some kind of swoosh/noise every time I type a letter.

---

### Post by sudodus on 2015-09-24
Maybe the splitter is the best solution that you can get. Maybe your audio hardware does not work 100% with the driver. Maybe it is about settings.

If you run programs/commands like

```
sudo lshw | less
```
and
```
hardinfo
```

you can probably identify your audio hardware, and you can tell us about it. Someone reading this thread might recognize it, and be able to suggest what to do to make it work.

---

### Post by fund_raiser on 2015-10-03
Spliter reduces the volume. How about buying some basic music card and installing it in a PCI slot? While I type *hardinfo* it returns a graphic window. Below I present *lshw* output. I paste the multimedia info.
>  *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:28 memory:e1280000-e1283fff



---

### Post by sudodus on 2015-10-04
You can write to a file the content of what is displayed by ***hardinfo*** (in the GUI). There is a menu option

*Information -- Generate report*

I am not familiar with the particular audio device shown by ***lshw***, but often Intel hardware plays well with linux. Let us hope someone knows your particular hardware and can help you.

---

### Post by fund_raiser on 2015-10-04
I tried to generate report; it reports an empty file. By the way, there is very little info there. To the above output I could add: 
class: audio device
Domain: 0
buss, device, function: 0.27.0
IRQ: 28
Bus master: yes
memory: 16 KB - non-prefetchable

PS
I think I will purchase some music card to get another headphones jack. Is it a good idea?

---

### Post by sudodus on 2015-10-04
It might be a good idea, but I suggest that you wait for more and better advice :-) Maybe someone can help you get your current audio system work.

---

