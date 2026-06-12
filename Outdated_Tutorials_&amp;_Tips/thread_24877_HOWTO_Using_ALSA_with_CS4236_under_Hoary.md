---
title: "HOWTO: Using ALSA with CS4236 under Hoary"
date: 2005-04-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Zipslack on 2005-04-08
This is a quick-and-dirty hack to get the Alsa modules to load the cs4236 drivers (since the developers decided to leave-out alsaconf....)  This same technique should work with other Alsa drivers...just substitute the proper driver in place of "snd-cs4236"

1. Open a console and change to root
          sudo sh  (enter your password - prompt should change from "$" to "#")

2.  change to /etc/init.d
          cd /etc/init.d

3.  edit the file "bootmisc.sh"
          nano bootmisc.sh

4.  add a new line at the bottom that reads
          /sbin/modprobe snd-cs4236

5.  save the file
         ctrl-x, y, <Enter>

When you reboot, the sound will be initialized properly.  To get sound without rebooting first, (still at the console as root) enter :
       modprobe cs-4236
       /etc/init.d/alsa restart
You may need to restart the desktop to get all the sound server and mixer to respond properly.  

DIsclaimer:  There's a probably a better/safer way to fix this properly, but I was interested in getting it done quickly, and this is what works for me.  YMMV.

---

### Post by Jad on 2005-04-08
Thank you man!

---

### Post by mendicant on 2005-04-08
modules to load usually go into /etc/modules, one module name per line.

---

### Post by andlinux21 on 2005-06-08
[FONT=Comic Sans MS][SIZE=3][COLOR=Blue]Thanks I cant wait to try this when i get home I never could get sound on my laptop.[/COLOR][/SIZE][/FONT]

---

### Post by coogor on 2005-07-01
Yep, I'm  missing alsaconf too. No real reason to leave it out. Anyway, maybe one of you has a clue why I cant load the module (on a ThinkPad 770):
root@tp770:~ # modprobe snd-cs4236
FATAL: Error inserting snd_cs4236 (/lib/modules/2.6.10-5-386/kernel/sound/isa/cs423x/snd-cs4236.ko): No such device
FATAL: Error running install command for snd_cs4236
root@tp770:~ # ls -al /lib/modules/2.6.10-5-386/kernel/sound/isa/cs423x
total 120
drwxr-xr-x   2 root root  4096 Jun 19 12:06 .
drwxr-xr-x  10 root root  4096 Jun 19 12:06 ..
-rw-r--r--   1 root root 30476 Apr  5 15:40 snd-cs4231-lib.ko
-rw-r--r--   1 root root  9218 Apr  5 15:40 snd-cs4231.ko
-rw-r--r--   1 root root 17033 Apr  5 15:40 snd-cs4232.ko
-rw-r--r--   1 root root 21090 Apr  5 15:40 snd-cs4236-lib.ko
-rw-r--r--   1 root root 22288 Apr  5 15:40 snd-cs4236.ko
root@tp770:~ #        

So, it *is* there, why is it not found?
(Sorry, SuSE user new to Ubuntu)

---

### Post by varunus on 2005-07-01
> root@tp770:~ # modprobe snd-cs4236
FATAL: Error inserting snd_cs4236 (/lib/modules/2.6.10-5-386/kernel/sound/isa/cs423x/snd-cs4236.ko): No such device
FATAL: Error running install command for snd_cs4236 

Based on that error message, it looks like you don't have the cs4236 sound card in your system.  I did a little googling for you, and it seems the thinkpad 770 has a cs4232 sound card, not the cs4236.  Try the following:

```

modprobe snd-cs4232

```
If that doesn't work for you, another guide said to try this:

```

modprobe snd-cs4232 port=0x530 cport=0x538 fm_port=0x388 irq=5 dma1=1 dma2=0

```

Good luck.

---

### Post by coogor on 2005-07-02
Hi Varunus,

thx for your reply. Accordimnng to my experience it is a 4236, see [http://www.axxite.com/brn/en/index.html](http://www.axxite.com/brn/en/index.html) 

Nevertheless, the result is the same with the 4232, the error message also. 

How can I reconfigure the sound subsystem? something like
dpkg-reconfigure alsa
seems not to work....

Thx again!

---

### Post by varunus on 2005-07-02
Coogor,

Doing a little more googling, I found someone's experiences with ALSA on the TP 770, and he said he got sound to work by adding the following to /etc/modules.conf:

#ALSA portion
alias char-major-116 snd
alias char-major-14 soundcore

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-css
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1
alias sound-slot-2 snd-card-2
alias sound-slot-3 snd-card-3

alias sound snd-card-0
alias snd-card-0 snd-card-cs4236

alias snd-minor-oss-0 snd-card-cs4236
alias snd-minor-oss-1 snd-opl3
alias snd-minor-oss-3 snd-pcm-oss

options snd snd_major=116 snd_cards_limit=1 \
snd_device_mode=0660 snd_device_gid=100 snd_device_uid=0


options snd-card-cs4236 snd_port=0x530 snd_cport=0x538 \ 
snd_mpu_port=-1 snd_fm_port=0x388 snd_irq=5 snd_dma1=1 \
snd_dma2=0 snd_dma1_size=16 snd_dma2_size=16 snd_isapnp=0 \
snd_index=0 snd_sb_port=0x220

After doing this, reboot.  If that doesn't work, try switching the dma1 and dma2 sections in the last section and rebooting again.

Another thing to try, a much more desperate measure:
Ubuntu does not include alsaconf, alsa's built in script based configuration utility.  I found a version of alsaconf you can download individually, but its for a slightly older version of alsa.  Most likely it'll still work.  (It even has a special section for your laptop ;-) )  You can download it at [http://www.mland.jp/pub/Tips/alsa/alsaconf](http://www.mland.jp/pub/Tips/alsa/alsaconf)

Make sure to make it executable with chmod +x alsaconf, and then run it with sudo.

Good luck.

---

### Post by coogor on 2005-07-04
Hi Varunus,

this config in modules.conf is suitable for the 2.4.x-kernels. In the 2.6.x kernels, it should be slightly different somewhere in /etc/modprobe.d/sound.

Actually, it was a good idea just to use an existing alsaconf, although the one needs some tweaking to work properly with 5.04. Nevertheles, the customizing was similar to what I tried, it still did not work.

My impression is that something went terribly wrong when setting up either ubuntu or alsa: There is no /dev/snd at all! I tried to recreate the device nodes using an alsa-script, which did also not result in a working system. (forgot to mention: This laptop was already working under older SuSE versions....including sound)

Maybe this is now the point to file an issue in bugzilla........

---

### Post by varunus on 2005-07-04
One more thing to try:

I found [this](http://alsa.opensrc.org/index.php?page=ThinkPad600)  page that should also work with a Thinkpad 770.  They have step by step instructions; the one thing I would look at is whether or not you have "simple boot" enabled in your BIOS.  If you do, you can't get sound at all.  The instructions on that page seem like they should work; also, if simple boot was enabled, try modprobing again with the irq and dma information.

EDIT: found another link to try, this one even specifically talks about Ubuntu (halfway down the page they mention the 770)
[http://www.wlug.org.nz/ThinkpadNotes](http://www.wlug.org.nz/ThinkpadNotes) 

Good luck.

---

