---
title: "IDJC &amp; JACK setup - The repos way"
date: 2010-03-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Naiki Muliaina on 2010-03-20
IDJC - Internet DJ Console..... It uses Jack.... This thing had me stumped for the longest time.... I just couldn't seem to get it to work... I do however now use it all the time. So a simple guide to those who needs to use it. Written for Ubuntu of course. Ive been told you need to install ia32-libs on 64 bit, its one of the first things i install myself so not sure if thats true or not. 

Ok, first of all we need Jack. Open a terminal and enter :

```
sudo apt-get install jackd qjackctl
```

Open Limits.conf

```
sudo gedit /etc/security/limits.conf
```

Add the following lines into the file :

```
@audio   -  rtprio     99
@audio   -  memlock    unlimited
@audio   -  nice      -19
```

Save and close.

Now open System > Administration > Users and Groups

Click the keys where it says click to make changes, put in your password. Click Manage groups. You should find one called *audi*o, if not, add group and call it *audio*. Add yourself to it.

Log out and in again.

Run Jack, you should find it in Sound and Video. 

Click Setup. Below is a couple of pictures of my set up screens. Mimic them, if it doesnt work, you can tweak them.

[IMG]http://farm5.static.flickr.com/4013/4447430533_8eb6a38b1c.jpg[/IMG]

Ok few things in this window.

Realtime - Some people find its better to have it turned off, some people cant get it to work at all with this ticked.

Frames/Peroid - I have this down to 256. My partner has it at 1024. My friend has it a 2048. Youll have to play with this a bit.

Interface - This is where it takes the sound from. If you have a funny sound set up, multiple sound cards, usb sound devices, you may need to tweak this.

[IMG]http://farm5.static.flickr.com/4021/4447430535_3ac0252f06.jpg[/IMG]

Should work for everyone.

[IMG]http://farm5.static.flickr.com/4051/4447430549_8fa1fd87c8.jpg[/IMG]

Should work for everyone.

[IMG]http://www.flickr.com/photos/41380115@N06/4447430547/sizes/m/[/IMG]

Personal preferences. But this is my set up.



Ok, we have Jack set up, Wewt wewt! Now for IDJC. Open a terminal and give it a :

```
sudo apt-get install idjc
```

If you want Shoutcast aswell Icecast give one of these aswell :

```
sudo apt-get install libmp3lame0 libmp3lame0-dev
```

If you dont install these Shoutcast will be greyed out in the options. Now open Internet > IDJC

Click Server, drag the boxes bottom corner and expand it out, i mean right out! Theres a lot of options and stuff here but every time i set this up it opens as a tiny little window.

This is how i have mine set up. Password poofed of course.

[IMG]http://farm5.static.flickr.com/4037/4447461781_2cde77b30d.jpg[/IMG]

Once its all filled in hit Server Connect. Should start streaming straight away. Simply drag songs out of nautilus into playlist 1 and hit play. You can make a playlist in Rythmbox, highlight the whole playlist and drag it into playlist 1. Means you can pre make them, save them, use them later etc.  Press the big mic button in the bottom right corner to talk. I pause the music as the song ends and do my talking but i guess thats DJ dependant.

Anywhos, thous a IDJC shoutcast guide.

---

### Post by MZ250Supa5 on 2010-04-26
I got the first bit great, and have configured Jack as per that above instructions.

I have had problems setting up the IDJC application though - every time I get a pop-up message like this:


It's frustrating!!

---

### Post by jackopo on 2010-06-21
How do I set up the Server right?

I mean which is the right hostname or adress and best port?

Thanks

---

### Post by Bit Hacker on 2010-06-27
> If you dont install these Shoutcast will be greyed out in the options. Now open Internet > IDJC

Click Server, drag the boxes bottom corner and expand it out, i mean right out! Theres a lot of options and stuff here but every time i set this up it opens as a tiny little window.

This is how i have mine set up. Password poofed of course.

[IMG]http://farm5.static.flickr.com/4037/4447461781_2cde77b30d.jpg[/IMG]

Once its all filled in hit Server Connect. Should start streaming straight away. Simply drag songs out of nautilus into playlist 1 and hit play. You can make a playlist in Rythmbox, highlight the whole playlist and drag it into playlist 1. Means you can pre make them, save them, use them later etc.  Press the big mic button in the bottom right corner to talk. I pause the music as the song ends and do my talking but i guess thats DJ dependant.

Anywhos, thous a IDJC shoutcast guide.

I've configured it correctly but this last part is confusing me. I'm using [http://freestreamhosting.org/](http://freestreamhosting.org/) as my services. I donno but maybe I'm using the latest release because it doesn't have a shoutcast option. 
[[img]http://www.ubuntu-pics.de/thumb/91317/radio_server_028_y79oUV.png[/img]](http://www.ubuntu-pics.de/bild/91317/radio_server_028_y79oUV.png)
If I use Shoutcast Master, it doesn't connect but if I choose Shoutcast Stat/Relay, it would grayout the Connect Server button. Help would be appreceated.

---

### Post by Space Piranha on 2011-03-01
> **jackopo said:**
> How do I set up the Server right?

I mean which is the right hostname or adress and best port?

Thanks

I realize this is a very delayed response, but somebody else might have the same question. Your server info is unique to which radio station you are broadcasting through, and that station should give you all of the fields to fill in. 

Here is a great website for testing your broadcasting: [http://shoutbroadcast.com/demo-hosting.php](http://shoutbroadcast.com/demo-hosting.php) 

All of the information, including hostname ([http://ss1.streamrepeater.com](http://ss1.streamrepeater.com)) and password is available there, and clicking the status link will let you hear what you are broadcasting.

---

