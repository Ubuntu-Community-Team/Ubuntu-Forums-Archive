---
title: "How to set up a Presonus Firepod on Ubuntu\Kubuntu Gutsy"
date: 2008-03-03
forum: Outdated Tutorials &amp; Tips
---

### Post by swedishfrog on 2008-03-03
This is the method I use to install a Presonus Firepod on Ubuntu. I have tested this on clean installs of (K)Ubuntu Gutsy, although this may work in Feisty as well. This method also works on Linux Mint Daryna. 

KDE users should replace 'gedit' with the editor of their choice (kate, kedit, etc)

In summary, you install the realtime kernel, which can give your audio special priority and prevents xruns\dropouts as much as possible. Then you add some modules to that kernel, tune some permissions, reboot, set up jack and you're good to go. Just read carefully and copy and paste.

**Make sure the Firewire cable is plugged into Port 2 on the Firepod.**

Open a terminal window.

Install the realtime kernel
```
sudo apt-get update
sudo apt-get install linux-rt
```

Install Ubuntu Studio audio suite.
```
sudo apt-get install ubuntustudio-audio
```

Reboot your machine and select the realtime kernel. It ends with -rt

Next, install necessary kernel modules
```
sudo modprobe raw1394 ieee1394
```

Fix permissions problem on 1394
```
sudo adduser $USER disk
```


Set up security permissions such that audio programs like jack can have access to your memory and can request high scheduling priorities. You might want to tweak memlock to suit your system, but don't experiment until you set up the firepod successfully. Type 'man limits.conf' for more info.

```
sudo gedit /etc/security/limits.conf
```
Paste the following text at the end of the file
```
	*               -       rtprio          99
	*               -       nice            -10
	*               -       memlock         4000000
```



Reboot to apply the new settings. It's possible that you may be able to get away with merely logging off. I prefer to reboot to be on the safe side. 

Physically connect the Firewire cable to **Port 2** on the Firepod. Plug in your Firepod and turn the unit on. The light should turn red in a few seconds.

Start qjackctl, which is a program that controls Jack. Jack talks to your device for you and serves up audio streams to your sound programs.
```
qjackctl
```

Now we set up jack. Hit the 'Setup' button. 

These settings are set to be safe, at the expense of being a bit latent (8.71 ms). You can tweak the latency to your system by adjusting Frames/Period and Periods/Buffer. Recording at a higher sample rate (96000) can also help reduce latency.
```

Qjackctl -- Settings tab


Server Path: /usr/bin/jackd			Driver freebob

X Realtime		Priority 70		Interface hw:0
			Frames/Per 128		
			Sa. Rate 44100		Audio Duplex
			Per/Buf 3

			Port Max 256		Inp Laten 0
			Timeout 500		Out Laten 0
```



Optional- Start jackd directly by command line
```
jackd -R -P70 -dfreebob -dhw:0 -r44100 -p128 -n3 -D
```

When Jack and Freebob connect to the Firepod, the device's light should turn from Red to Blue. You should now be able to use Jack to send audio to any Jack apps. Use the 'Connect' button on Qjackctl to manage audio connections.

Known issues with this setup:

1- Jack\Ardour do not compensate for latency. This is very annoying if you plan on doing alot of overdubs, because the latency will pile up to something noticible before too long. This is all due to a design flaw in the FreeBob 1 driver, which should be fixed when the Freebob 2/FFADO driver comes out. It's not ready for the public as of 3-08.

Technical info on the problem's cause: [here]("http://osdir.com/ml/linux.drivers.freebob.devel/2006-12/msg00022.html")

FFADO web site: [FFADO.org]("http://ffado.org")


2- I have not been able to use the Firepod with my MIDI keyboard. However my keyboard is an old Roland Juno 106 that doesn't quite completely work in general, so this might not be related to my Linux setup at all.

---

### Post by Torque313 on 2011-01-03
well i went through all the steps you have here but for some reason i still can't get it to work. The light is still red.

---

### Post by shpongled on 2011-02-14
Hi there, I'm not using Ubuntu, but I think the problem might be the same...
My Firepod has actually turned blue! And no, it's not drowning. But I am not able to get any sound working!!!
For instance, if I open up a music player like VLC, the only drivers it lists are ALSA, Unix OSS, File Audio and Dummy Audio output. Any ideas? Am I able to use ALSA With the Firepod instead of Freebob?
I would appreciate any, any help at all.

---

