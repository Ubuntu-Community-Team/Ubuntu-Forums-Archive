---
title: "JACK doesn't read firewire audio from Edirol FA-66 any more"
date: 2016-03-02
forum: New to Ubuntu
---

### Post by LuckyAstronaut on 2016-03-02
Hey everyone, 
I'm  hoping someone can help. I'm new to Linux and learning pretty quickly,  but I'm stuck on a mystery error. I've looked for solutions on here and  other forums and run through a few of the suggestions but can't fix  this. I'll try and be as detailed as I can without being too wordy.

A  few months ago I set up a dual boot system with Linux Ubuntu Studio  14.04 and Windows 10 sharing a common NTFS partition. I like mucking  around with music and was playing with Ardour and Hydrogen both  connected with JACK. I was able to record a line through my Edirol FA-66  firewire input right into Ardour. It all worked great. I used patchage  to manage connections and after a bunch of reading I was up and running with no problems other than figuring out a new set up.

The other day I set myself up but  couldn't see the audio inputs for my FA-66 the way it always showed up.   Instead I had "system" inputs "playback" and "capture" that I'd never seen  before.

If I hit start on QjackCtl I got the error shown here:
[http://askubuntu.com/questions/224151/jack-server-could-not-be-started-when-using-qjackctl](http://askubuntu.com/questions/224151/jack-server-could-not-be-started-when-using-qjackctl)

I ran through the steps to kill and restart pulseaudio and jack_control and now I don't get that error any more, but I'm still missing the audio JACK inputs. Looking  around the QjackCtl it seems like ALSA connections are still available,  but they only read the MIdi inputs on the FA-66. The only Audio  connections I have are for the "system" 'capture' and 'playback'.

The messages output from QjackCtl is  

```
[COLOR=#999999]22:39:06.267 Patchbay deactivated.[/COLOR]

 [COLOR=#999999]22:39:06.274 Statistics reset.[/COLOR]
 [COLOR=#CCCC99]22:39:06.278 ALSA connection change.[/COLOR]
 [COLOR=#999999]22:39:06.395 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 [COLOR=#9999CC]22:39:06.459 JACK connection change.[/COLOR]
 [COLOR=#999999]22:39:06.473 Client activated.[/COLOR]
 (qjackctl:5693): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed

 (qjackctl:5693): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:5693): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:5693): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed

```

I'm really not sure what to make of this critical error. Any ideas? I'd also love to know what causes this so I can avoid the same thing happening again. Not sure if it's important, but if I start up patchage or qjackctl I can't get any sound to on any application until I reboot the sytem.

Appreciate the help.

---

