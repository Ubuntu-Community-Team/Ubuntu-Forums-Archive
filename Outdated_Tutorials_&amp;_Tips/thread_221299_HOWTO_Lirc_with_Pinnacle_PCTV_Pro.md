---
title: "HOWTO Lirc with Pinnacle PCTV Pro"
date: 2006-07-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Rilson Raposo on 2006-07-22
Kernel: 2.6.16.15.26
Lirc: 0.8.0

First, instal the following packages:

```

# sudo apt-get install build-essential
# sudo apt-get install linux-headers-2.6.15-26 (replace it by your kernel release number)
# sudo apt-get install dialog

```

Download the last lirc source from [http://www.lirc.org](http://www.lirc.org). Untar it on a working folder:

```
# tar -xvjf lirc-0.8.0.tar.bz2
```

Chdir to lirc-0.8.0. Execute setup.sh

```

# cd lirc-0.8.0
# ./setup.sh

```

Select option "1 Driver Configuration". A new meu will show. Select option "4 Other serial port devices", select "b Pinnacle Systems PCTV (pro) reciever" on the new menu. Finally, select COM port where your IRD is connected.

Select option "2 Software configuration", and select "1 Compile tools for X-Windows" and "5 Use syslogd instead of own log file"

Select option "3 Save configuration & run configure".
Run make and make install:

```

# make
# sudo make install

```

Now install the packages for lirc. It will create some files that you will need.

```

# sudo apt-get install lirc

```

edit the file /etc/lirc/hardware.conf and change the following lines:

> 
    LOAD_MODULES="false"
    DRIVER="pinsys"
    DEVICE="/dev/ttyS0" #To COM1. To COM2, user /dev/ttyS1 and so on.


Copy the right lircd.conf. 

> 
# sudo cp /usr/share/lirc/remotes/pinnacle_systems/lircd.conf.pctv /etc/lirc/lircd.conf


Now the tricky part.  The lirc package installed another copy of lirc binary, which didn't work for me. So, I had to replace it with the compiled one. To do this, execute the following commands:

```

# sudo mv /usr/sbin/lircd /usr/sbin/lircd-original
# sudo mv /usr/sbin/lircmd /usr/sbin/lircmd-original
# sudo cp /usr/local/sbin/lircd /usr/sbin
# sudo cp /usr/local/sbin/lircmd /usr/sbin

```

It's time to test. The best way I found is open two terminals. On the first one execute:

```

# sudo /etc/init.d/lirc stop
# sudo lircd --nodaemon

```

The message will be showed

> 
lircd-0.8.0[28291]: lircd(pctv) ready


On the second terminal execute

```

# irw

```

Press the remote control buttons and you should see somenthing like this:

> 
000000000000001b 00 vol+ PinnacleSysPCTVRemote
000000000000000b 00 Stop PinnacleSysPCTVRemote
0000000000000015 00 pause PinnacleSysPCTVRemote
000000000000000d 00 Play PinnacleSysPCTVRemote


If it's all ok, your system is ready. Press <CTRL-C> on both terminals and restart de daemon with:

```

# sudo /etc/init.d/lirc start

```

If something didn't work, take a look at /var/log/syslog. It can help you understand what didn't work.





[FONT="Arial Black"][SIZE="4"]Totem[/SIZE][/FONT]

I use totem as my movie player. To make it work with your remote control, create a file named .lircd in your home folder

```

# gedit ~/.lircrc

```
 
Put the following lines on it:

> 

# edit the "button =" part for each entry according to your remote, 
# and stick this stuff in ~/.lircrc

begin
	prog = Totem
	remote = *
	button = Play
	repeat = 1
	config = play
end

begin
	prog = Totem
	remote = *
	button = pause
	repeat = 0
	config = pause
end

begin
	prog = Totem
	remote = *
	button = FForward 
	repeat = 1
	config = seek_forward
end

begin
	prog = Totem
	remote = *
	button = Rewind
	repeat = 1
	config = seek_backward
end

begin
	prog = Totem
	remote = *
	button = Fullscreen
	repeat = 1
	config = fullscreen
end

begin
	prog = Totem
	remote = *
	button = vol+
	repeat = 1
	config = volume_up
end


begin
	prog = Totem
	remote = *
	button = vol-
	repeat = 1
	config = volume_down
end


begin
	prog = Totem
	remote = *
	button = next
	repeat = 1
	config = next
end

begin
	prog = Totem
	remote = *
	button = YOUR_BUTTON
	repeat = 1
	config = previous
end

begin
	prog = Totem
	remote = *
	button = Power
	repeat = 1
	config = quit
end



That's it! I hope this howto helps you.

---

### Post by Icarosaurus on 2007-04-21
Thanks!
Seems to work in Feisty too :)

---

### Post by sjukdom on 2007-05-01
With edgy I have no problem,but with feisty,installation goes right but remote give no sign.
Someone has same problem?

---

### Post by sjukdom on 2007-05-01
A clean ubuntu installation solved any problem.

---

### Post by Locomeister on 2007-05-14
Do not work. When i test in the terminal i have this error message in the first terminal:


gsc@gsc-room:~/Desktop/lirc-0.8.1$ sudo lircd --nodaemon
lircd-0.8.1[23124]: could not open config file '/etc/lircd.conf'
lircd-0.8.1[23124]: No such file or directory
lircd-0.8.1[23124]: lircd(pctv) ready
lircd-0.8.1[23124]: accepted new client on /dev/lircd
lircd-0.8.1[23124]: could not reset tty
lircd-0.8.1[23124]: caught signa
Finalizado



Ubuntu Feisty

---

### Post by mlitty on 2007-05-28
> Locomeister  	Do not work. When i test in the terminal i have this error message in the first terminal:


gsc@gsc-room:~/Desktop/lirc-0.8.1$ sudo lircd --nodaemon
lircd-0.8.1[23124]: could not open config file '/etc/lircd.conf'
lircd-0.8.1[23124]: No such file or directory
lircd-0.8.1[23124]: lircd(pctv) ready
lircd-0.8.1[23124]: accepted new client on /dev/lircd
lircd-0.8.1[23124]: could not reset tty
lircd-0.8.1[23124]: caught signa
Finalizado



Ubuntu Feisty

Me too.  Anyone have a solution to this?

---

### Post by mlitty on 2007-05-29
Ok, 
A little progress.
I'd been following a few different howto's looking for one that would work.  I think this cause a problem.

So, if you're getting the "could not reset tty" issue, try this.
do 
```

setserial /dev/ttyS0

```
using your device in place of /dev/ttyS0
If your uart is "unknown" then try to fix it with
```

setserial /dev/ttyS0 autoconfig

```
again, replacing ttyS0 with your device.
Then retry the "lircd -n -d /dev/ttyS0" and "irw" combination described above.  If you're still getting errors, try 

```

lsmod |grep lirc

```
 and then use rmmod to remove all of the lirc modules.

Then go back and try that lircd / irw thing again.

I still can't get a signal, but It's not crashing in an error anymore.

---

### Post by Locomeister on 2007-05-29
But still not working eheheh
When i press the remote control buttons  do not appear nothing in the second terminal

Press the remote control buttons and you should see somenthing like this:

---

### Post by paparucino on 2007-05-29
> **Locomeister said:**
> But still not working eheheh
When i press the remote control buttons  do not appear nothing in the second terminal

Press the remote control buttons and you should see somenthing like this:
May be you missed something :-)

---

### Post by matijn on 2007-05-29
How did you set up the Pinnacle PCTV, tv-card?
Mine wont run any tv-program.

---

### Post by pleban on 2007-06-16
that does not work for me.
I have pctv 110i. lirc says that I dont need any lirc kernel module.
Kernel itself register remote at /dev/input/event4, but I don't get any events from that device

---

### Post by Icarosaurus on 2007-06-22
For the problem "file not found".
Just move lircd.conf **not in /etc/lirc/** but in **/etc/**.
Worked for me, I think the HOWTO should be fixed.
Bye!

---

### Post by skooter on 2007-07-02
One tiny typo: "...create a file named .lircd in your home folder...", guess you mean ".lircrc"?

I have my remote almost working. irw gives response... But when i try to use the remote with MythTV I get no reaction. I've tried with 2 different lircrc-mythtv files and placed them in "/home/mythtv" and also tried "/home/mythtv/.mythtv" ... But didn't work. 

Should i "sudo /etc/init.d/lirc restart" after placing a new lircrc-file? I restarted it a lot... :-s

---

### Post by skooter on 2007-07-05
Turns out that it was lircrc which was troubling me. I had a hard time finding the right one. I tried copying lircrc from my mates server. And it worked well. I attached my lircrc to this post. I know it says "Hauppauge remote" but it works well for my Pinnacle PCTV remote. You can make your own adjustments if you like.

I installed MythTV with apt-get on Feisty. And found out that MythTV installed with apt-get has native lirc support built-in. So you dont need irxevent (that app bugged me a lot *grr*).

It's very important that you place the lircrc file (without the dot) in /home/mythtv/.mythtv/lircrc and then do a symbolic link:
```
ln -s ~/.lircrc ~/.mythtv/lircrc
```

After placing my lircrc-file i restarted both myhtfrontend and lirc... and then tried out my remote. No reaction. Then i got the Windows-syndrome and restarted the whole machine. Then it worked. Maybe someone has a better solution?

Finally my remote is working!

---

### Post by bluntz on 2007-09-18
Can You please tell us how you got PCTV sound to work???
I've spent many hours fiddling with my pctv/rave card with no success.
heres my current dmesg,if it helps.
I have everything working fine eccept SOUND.
I can record video under xawtv and several other progs great,but no sound. .

[17179593.508000] bttv0: Bt878 (rev 17) at 0000:00:05.0, irq: 185, latency: 32, mmio: 0xe2000000
[17179593.508000] bttv0: detected: Pinnacle PCTV [card=39], PCI subsystem ID is 11bd:0012
[17179593.508000] bttv0: using: Pinnacle PCTV Studio/Rave [card=39,autodetected][17179593.508000] bttv0: gpio: en=00000000, out=00000000 in=00ffefff [init]
[17179593.508000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17179593.508000] bttv0: pinnacle/mt: id=5 info="NTSC / mono" radio=no
[17179593.508000] bttv0: using tuner=33
[17179593.508000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17179593.512000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179593.512000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179593.560000] tda9887 0-0043: chip found @ 0x86 (bt878 #0 [sw])
[17179593.596000] tuner 0-0060: Chip ID is not zero. It is not a TEA5767
[17179593.596000] tuner 0-0060: chip found @ 0xc0 (bt878 #0 [sw])
[17179593.604000] tuner 0-0060: microtune: companycode=4d54 part=04 rev=04
[17179593.664000] tuner 0-0060: microtune MT2032 found, OK
[17179593.696000] bttv0: registered device video0
[17179593.696000] bttv0: registered device vbi0
[17179593.696000] bttv0: PLL: 28636363 => 35468950 ..<4>nvidia: module license 'NVIDIA' taints kernel.
[17179593.768000]  ok
[17179593.796000] NVRM: The NVIDIA GeForce2 GTS/GeForce2 Pro GPU installed in this system is
[17179593.796000] NVRM:  supported through the NVIDIA Legacy drivers. Please
[17179593.796000] NVRM:  visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more
[17179593.796000] NVRM:  information.  The 1.0-8776 NVIDIA driver will ignore
[17179593.796000] NVRM:  this GPU.  Continuing probe...
[17179593.796000] NVRM: No NVIDIA graphics adapter found!
[17179594.012000] bt878: AUDIO driver version 0.0.0 loaded
[17179594.012000] bt878: Bt878 AUDIO function found (0).
[17179594.012000] ACPI: PCI Interrupt 0000:00:05.1[A] -> GSI 16 (level, low) -> IRQ 185
[17179594.012000] bt878(0): Bt878 (rev 17) at 00:05.1, irq: 185, latency: 32, memory: 0xe2001000

---

### Post by Icarosaurus on 2007-09-18
Did you connect the audio cable to the line-in input of your soundcard?
My pctv sound works with the cable... I'm not sure yours will work without. What's your card model?

---

### Post by bluntz on 2007-09-18
theres nothing but static from the sound port on the card.
cabling it to the sound card wont be any help.
Ive tried kernels 2.6.20 2.6.18 2.6.22 2.6.15 2.6.17 and none can auto configure it. Im thinking maybe it needs firmware?

Pinnacle pctv/rave ,lspci -v returns:
0000:00:05.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
        Subsystem: Pinnacle Systems Inc. PCTV pro (TV + FM stereo receiver)
        Flags: bus master, medium devsel, latency 32, IRQ 185
        Memory at e2000000 (32-bit, prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:05.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
        Subsystem: Pinnacle Systems Inc. PCTV pro (TV + FM stereo receiver, audio section)
        Flags: bus master, medium devsel, latency 32, IRQ 185
        Memory at e2001000 (32-bit, prefetchable) [size=4K]
        Capabilities: <available only to root>
But I dont think it actually has FM,
This card worked fine on older 2.4 kernels, in fact I bought it because it was the best supported tv card in its time!
I hate to give up on UBUNTU but if I cant get video recording to work
then I will have to find another distro.Slackware works but is a PITA.

---

### Post by bluntz on 2007-09-19
I read somewhere that sound works without the cable now but has to be redirected with SOX.
When I plug in my headphones to the output jack I hear static. is this
the sound of raw digital I wonder? Does SOX encode/decode it?

---

### Post by Icarosaurus on 2007-09-20
I'm using only PCTV remote control, 'cause I removed my card and I don't use it now...

I think we're going off-topic. This thread is about remote control... Try open a new thread or search if there is a more specific one.

As far as I remember, the kernel didn't recognize my card (probably due to a card problem) and I had to force it.
It seems that your card is bad recognized from the kernel:
```

[17179593.508000] bttv0: detected: Pinnacle PCTV [**card=39**], PCI subsystem ID is 11bd:001

```
While it should be **card=52**: see [here]("http://linuxtv.org/hg/v4l-dvb/file/tip/linux/Documentation/video4linux/CARDLIST.bttv")
See [here]("http://linuxtv.org/v4lwiki/index.php/Bttv_devices_%28bt848%2C_bt878%29") for getting more informations.
See [here]("http://ubuntuforums.org/showthread.php?t=390727&highlight=bttv+force+card") for a thread about audio problems.
See [here]("http://tldp.org/HOWTO/BTTV/modprobe.html") at point 4.4 for forcing a card.

I hope this helps.
Regards

---

### Post by bluntz on 2007-09-25
First off, I'd like to thank you for your help.
over the years I've used your brain more than once!
Dude you rock!
I will follow up on your advice and get back to you (I was wondering if it shouldn't be 52 as well)
I even tried Mythdora today and got mythtv all setup and running sweet with all the  toys working great but no sound ,even on the 2.6.22 kernel. Same id issue there
card detected as 39. 
Again ,Thank you sir.

---

### Post by bluntz on 2007-09-27
WooHoo!
finally got it to work again...
Even got stereo too sweet.
Now to set up mythtv again and finally after fiddling with this for 2 weeks I can
watch and record my TV from anywhere in the world!
Thank you so much.

---

### Post by Icarosaurus on 2007-09-28
You're wellcome :) 
I'm so happy I helped someone to solve a problem :)
:mrgreen:

---

### Post by bluntz on 2007-09-30
In case anyone else would like the fix it was simple:

su root

rmmod bt878

rmmod bttv

modprobe bttv card=39 tuner=33

I used the patch cable from pctv card to line in on soundcard and set
capture to line in. Then enabled surround sound to get stereo.

You were correct in your asumption that it was a kernel bug
As we see here dmesg shows the correction of the driver:

[17181194.844000] bt878(0): unloading
[17181194.852000] bt878_mem: 0xe0924000.
[17181194.852000] ACPI: PCI interrupt for device 0000:00:05.1 disabled
[17181201.776000] bttv0: unloading
[17181236.292000] bttv: driver version 0.9.16 loaded
[17181236.292000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17181236.296000] bttv: Bt8xx card found (0).
[17181236.296000] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 16 (level, low) -> IRQ 185
[17181236.296000] bttv0: Bt878 (rev 17) at 0000:00:05.0, irq: 185, latency: 32, mmio: 0xe2000000
[17181236.296000] bttv0: detected: Pinnacle PCTV [card=39], PCI subsystem ID is 11bd:0012
[17181236.296000] bttv0: using: Pinnacle PCTV Studio/Rave [card=39,insmod option ]
[17181236.296000] bttv0: gpio: en=00000000, out=00000000 in=00ffefff [init]
[17181236.300000] tda9887 0-0043: chip found @ 0x86 (bt878 #0 [sw])
[17181236.316000] tuner 0-0060: Chip ID is not zero. It is not a TEA5767
[17181236.316000] tuner 0-0060: chip found @ 0xc0 (bt878 #0 [sw])
[17181236.364000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17181236.368000] bttv0: pinnacle/mt: id=5 info="NTSC / mono" radio=no
[17181236.368000] bttv0: using tuner=33
[17181236.376000] tuner 0-0060: microtune: companycode=4d54 part=04 rev=04
[17181236.436000] tuner 0-0060: microtune MT2032 found, OK
[17181236.436000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17181236.440000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17181236.444000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17181236.468000] bttv0: registered device video0
[17181236.468000] bttv0: registered device vbi0
[17181236.468000] bttv0: PLL: 28636363 => 35468950 .. ok

---

### Post by FredySparx on 2007-10-17
I'm still trying to get my Remote working..

I allready tried several tutorials.. so that might be a problem why it doesn't work.
When i type:
```
sudo lircd --nodaemon
```
i get the response:
```
lircd-0.8.2[15148]: lircd(pctv) ready
```
if i type "IRW" in the other terminal and then switch back i get the answer:
```
lircd-0.8.2[15148]: accepted new client on /dev/lircd
lircd-0.8.2[15148]: could not reset tty
lircd-0.8.2[15148]: caught signal
Terminated
```

What should i do to make ik work? Please help me!
Thanks in advance,

Fredy

---

### Post by franganghi on 2008-03-30
it worked in g. gibbon!
fantastic.

---

### Post by nickblame on 2008-06-13
well in gutsy i get the same error too when trying to get signal on irw :/

the sad thing is that in windows winlirc works just fine... shame..

---

### Post by bikas4u on 2008-07-17
I am getting the following error !!!!
what to do !!

sudo lircd --nodaemon
lircd-0.8.3pre1[6796]: lircd(userspace) ready
lircd-0.8.3pre1[6796]: accepted new client on /dev/lircd
lircd-0.8.3pre1[6796]: could not get file information for /dev/lirc
lircd-0.8.3pre1[6796]: default_init(): No such file or directory
lircd-0.8.3pre1[6796]: caught signal

---

### Post by bikas4u on 2008-07-18
I was able to solve that somehow. But this is the new error !!

Please help

sudo lircd --nodaemon
lircd-0.8.3[6773]: lircd(pctv) ready
lircd-0.8.3[6773]: accepted new client on /dev/lircd
lircd-0.8.3[6773]: readlink() failed for "/dev/lirc"
lircd-0.8.3[6773]: No such file or directory
lircd-0.8.3[6773]: could not create lock files
lircd-0.8.3[6773]: caught signal
Terminated

---

### Post by freevofc6 on 2008-12-26
Hi All,
      I am using pinnacle 50i card.My remote with this card is not working.I have tried all the steps after googling like configured my lirc-0.8.4a with "./configure --with-driver=devinput" with this command and Starts the daemon in this way:
/usr/sbin/lircd -n -d /dev/input/event3. After running irw nothing comes as output.Still in the dark...Can Any one please help me in this..??

Thanks In Advance.
Regards,
Freevofc6

---

### Post by gyurman on 2009-01-22
Hy!

I can do more simply.
[http://tnlessone.wordpress.com/2007/02/08/installing-miro-pctv-remote-control-to-run-with-xdtv/]("http://tnlessone.wordpress.com/2007/02/08/installing-miro-pctv-remote-control-to-run-with-xdtv/")

And mix [http://ubuntuforums.org/showpost.php?p=1289637&postcount=1]("http://ubuntuforums.org/showpost.php?p=1289637&postcount=1")

and do ```
setserial /dev/ttyS0 autoconfig
```

tanks guys

---

### Post by bluntz on 2009-06-24
Great Job !

---

### Post by simmaren_1 on 2009-12-03
Hi,

I have a Pinnacle PCTV Analog PCI with Remote Control that is connected to a 2.5mm stereo plug on the TV card.

I am new to Linux...
I have tried several guides but every one seems to cover only the serial port???

# cat /proc/bus/input/devices

I: Bus=0018 Vendor=0000 Product=0000 Version=0000
N: Name="Pinnacle PCTV"
P: Phys=i2c-1/1-0047/ir0
S: Sysfs=/devices/virtual/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=100003
B: KEY=108fc010 2100802 0 0 0 0 48000 2180 c0000801 9e1680 0 0 4ffc

# sudo irrecord -H dev/input -d /dev/input/event7 /tmp/my-remote

respond:

irrecord: gap not found, can't continue
irrecord: closing '/dev/input/event7'


Is there a way to use my remote control in Ubuntu 8.04..3?
(Ubuntu 2.6.24-25.63-generic)

/Fredrik

---

### Post by SpiderSkull on 2010-12-30
Hi,

using command: "lircd -n -d /dev/ttyS0"
gives me reponses of my remote.
but without "-d /dev/ttyS0" I have not any response.

I think that my hardware.conf is not correct.
So if there is anyone who has this remote working could upload the hardware.conf file. That would be great.

Chears

PS: I am using ubuntu 9.10 & Lirc 0.8.6

Found the solution of this remote!

[http://ubuntuforums.org/showthread.php?1659552]("http://ubuntuforums.org/showthread.php?t=1659552")

---

