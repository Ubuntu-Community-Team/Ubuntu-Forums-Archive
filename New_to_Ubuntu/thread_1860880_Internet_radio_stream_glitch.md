---
title: "Internet radio stream glitch"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by fractalman on 2011-10-15
I have been streaming internet radio through banshee for a while but after re installing natty, i am no longer able to do so.  i have everything set up just as before with the radio station fetcher plug in when i try to open the same station with vlc(which used to stream as well) i get the following error message

VLC is unable to open the MRL 'http://184.82.19.16:8300/'. Check the log for details.

Where can i find the relevant logs?

the same station also has 2 pop out players on their site and neither of those will stream through my browser but i can stream other sites like radio1 and some shoutcast stations

[http://tnsradio.ning.com/](http://tnsradio.ning.com/)

other people are recieving their stream ok so i know the problem is at my end, i always stream it through banshee, it says there's a plug in on the site but it's a windows one,  anyone know if there's a linux equivalent?

i Have ubuntu-restricted-extras installed but thanks to my isp my connection was cut half way through downloading the package, could this have any effect at all, if so how do i completely remove the package and re-download it? i tried with synaptic but complete removal does not actually delete the package

which port would banshee and vlc need to stream through? i can check my router too then and make sure its not blocking anything but I'm guessing i have a missing or corrupt package somehwere because it's never done this before.

please post any commands if you need to see outputs

thanks

---

### Post by fractalman on 2011-10-15
ok i have also tried my ubuntu studio installation and am currently using 11.10 but i still get the same problem, my media players wont stream the station and the pop out flash players wont work in my browser in either install.

The plugin is a wmpfirefoxplugin  i had a google and tried most of the alternatives but still no joy.

my router is also malfunctioning and my isp are sending a new one but i don't see how this could stop me listening through the flash player when it works on other sites?

How do i check my actual hardware and make sure that my ethernet sockets and network adapters are ok? again i can't see this stopping the flash player if my browser can still access the web?

Any ideas please? am i missing a dependancy package?
do flash players stream through a seperate port or through port 80 with my browser?

also with banshee everytime i try and connect to the radio the big green play button disappears and i have to kill banshee and re open it.

any help would be much appreciated

thanks

---

### Post by fractalman on 2011-10-16
when  run banshee from the terminal and try to connect i get the following

```

phi@PAPASMURF:~$ banshee
[Info  00:00:49.655] Running Banshee 2.2.0: [Ubuntu oneiric (development branch) (linux-gnu, i686) @ 2011-09-23 04:51:00 UTC]
[Info  00:00:51.592] Updating web proxy from GConf
[Info  00:00:51.624] All services are started 1.592853
[Info  00:00:53.230] nereid Client Started
[Info  00:00:53.441] GStreamer version 0.10.35.0, gapless: True, replaygain: False
[Warn  00:01:06.909]  - Ti Nar So (on Ti Nar So) <00:00:00> [<unknown>] - System.Net.WebException: The request timed out (in `System')
  at System.Net.HttpWebRequest.EndGetResponse (IAsyncResult asyncResult) [0x00000] in <filename unknown>:0 
  at System.Net.HttpWebRequest.GetResponse () [0x00000] in <filename unknown>:0 
  at Banshee.Playlists.Formats.PlaylistParser.Parse (Hyena.SafeUri uri) [0x00000] in <filename unknown>:0 
  at Banshee.Streaming.RadioTrackInfo.LoadStreamUri (System.String uri) [0x00000] in <filename unknown>:0 


```

If i try in audacious i get an error message saying i have no decoder for whichever ip i try.

still can't get the pop out players from the site to work either  but a handful of pop out players work on the shoutcast site, but not many

i have tried adding the banshee ppa and getting the good,bad and ugly gstreamer plugins too but still no joy

should i just re-install the whole o/s?

---

