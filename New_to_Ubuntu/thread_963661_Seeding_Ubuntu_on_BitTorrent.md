---
title: "Seeding Ubuntu on BitTorrent"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by undoIT on 2008-10-30
Well, I'm almost finished downloading Kubuntu. Going to be installing that on one laptop. Ubuntu is taking longer to download and that will be going on my other laptop.

:guitar:

I'm not familiar with BitTorrent and I'm wondering how I add the install image after I have finished downloading.

---

### Post by Het Irv on 2008-10-30
With Bit-Torrent you should be downloading the .iso file.  In your CD burner you should have an option to burn an Image to CD.  Its not the same as a data CD, so be careful there, but its not hard.  If you burn it right you should be able to stick the CD in and boot to it.

---

### Post by phidia on 2008-10-30
> **undoIT said:**
> Well, I'm almost finished downloading Kubuntu. Going to be installing that on one laptop. Ubuntu is taking longer to download and that will be going on my other laptop.

:guitar:

I'm not familiar with BitTorrent and I'm wondering how I add the install image after I have finished downloading.

If I understand your question-you are asking how to host the image?-then just leave the torrent client open you should see a ratio between the amount of the file you have put out to the web vs how much you grabbed whenever a torrent is working.

If the question is about burning the image you can just use the nautilus file burner. Right click on the iso and select "Write to Disc...".

---

### Post by jpeddicord on 2008-10-30
> **undoIT said:**
> Well, I'm almost finished downloading Kubuntu. Going to be installing that on one laptop. Ubuntu is taking longer to download and that will be going on my other laptop.

:guitar:

I'm not familiar with BitTorrent and I'm wondering how I add the install image after I have finished downloading.

You want to know how to seed it after it is downloading? Your torrent client will automatically begin seeding when it is done. Or do you mean something else?

---

### Post by undoIT on 2008-10-30
I downloaded from the servers and now I want to add the finished file to Bit Torrent so other people can download from me.

---

### Post by _sAm_ on 2008-10-30
Just download the same *.torrent file as you did last time; if you store the already downloaded *.iso file in the same place as last time your torrent client will check it and then start to share it. 

Thanks for sharing:-)

---

### Post by undoIT on 2008-10-30
Okay. If I understand correctly, I would start the torrent file in Transmission

for example:

[http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.iso.torrent)

Then, close Transmission, move the completed download to where the torrent was downloading and then open Transmission again?

---

### Post by drubin on 2008-10-30
> **undoIT said:**
> I downloaded from the servers and now I want to add the finished file to Bit Torrent so other people can download from me.

> **_sAm_ said:**
> Just download the same *.torrent file as you did last time; if you store the already downloaded *.iso file in the same place as last time your torrent client will check it and then start to share it. 

Thanks for sharing:-)

The OP stated he downloaded it via the the webserver..

---

### Post by carolinason on 2008-10-30
As said, just leave the iso in bittorrent it should seed automatically. For those viewing, make sure the ratio is 1:1, so you've uploaded it once.

---

### Post by Axos on 2008-10-30
The exact procedure depends upon which BT client you are using. But here's the general procedure:

Download the *.torrent file(s) which corresponds to the image(s) you want to share.

Add each .torrent to your BT client, telling it to download to the directory in which you've got the image(s) you've already downloaded.

If your BT client is smart, it will see that the files already exist and will automatically validate them against the checksums in the .torrent files and, if they match, will begin to seed them rather than download new copies.

If your BT client is dumb, it will erase the files you already downloaded and start over. :) So you might want to save a copy in a different directory just in case.

Just to be clear, these are the links to the official .torrent files:

[http://releases.ubuntu.com/8.10/ubuntu-8.10-alternate-amd64.iso.torrent](http://releases.ubuntu.com/8.10/ubuntu-8.10-alternate-amd64.iso.torrent)
[http://releases.ubuntu.com/8.10/ubuntu-8.10-alternate-i386.iso.torrent](http://releases.ubuntu.com/8.10/ubuntu-8.10-alternate-i386.iso.torrent)
[http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.iso.torrent)
[http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-i386.iso.torrent)

[http://releases.ubuntu.com/kubuntu/intrepid/kubuntu-8.10-alternate-amd64.iso.torrent](http://releases.ubuntu.com/kubuntu/intrepid/kubuntu-8.10-alternate-amd64.iso.torrent)
[http://releases.ubuntu.com/kubuntu/intrepid/kubuntu-8.10-alternate-i386.iso.torrent](http://releases.ubuntu.com/kubuntu/intrepid/kubuntu-8.10-alternate-i386.iso.torrent)
[http://releases.ubuntu.com/kubuntu/intrepid/kubuntu-8.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/kubuntu/intrepid/kubuntu-8.10-desktop-amd64.iso.torrent)
[http://releases.ubuntu.com/kubuntu/intrepid/kubuntu-8.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/kubuntu/intrepid/kubuntu-8.10-desktop-i386.iso.torrent)

---

### Post by gnuvistawouldbecool on 2008-10-30
> **undoIT said:**
> Okay. If I understand correctly, I would start the torrent file in Transmission

for example:

[http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.iso.torrent)

Then, close Transmission, move the completed download to where the torrent was downloading and then open Transmission again?

Pretty much, yes.  Step by step(the way I do it);

1. Download the torrent file.
2. open torrent file in Transmission.
3. point transmission to where you downloaded the .iso in the "save to" screen".
4. it then checks the file, then you click 'add' and you will be seeding.

---

### Post by undoIT on 2008-10-30
> **Axos said:**
> If your BT client is dumb, it will erase the files you already downloaded and start over. :) So you might want to save a copy in a different directory just in case.

That is what I was concerned about. Just finished the integrity check for Kubuntu so no problem now.

And it is working. I just dropped the iso in the default download folder, opened the torrent in Transmission, it saw the completed file and now people are downloading :D

---

### Post by undoIT on 2008-10-30
Time to give Comcast some exercise.

I've got 200 KiB/s available. Come and get it!

---

### Post by omegamormegil on 2008-10-30
If you are using a router, you also need to make sure that the inbound port is forwarded correctly, if you want to seed the iso back into the swarm.  If you don't do this, you can only take from the swarm, and can't give back to everyone else who is sharing with you.

It's easy to check if you need to do anything to get it to work.  If you are using transmission, open the program, and go to Edit > Preferences > Peers tab, and look about half way down the window.  The field you are looking for says "Listening Port", followed by a number, and "Testing Port" in italics.  "Testing Port" will change to "Open" or "Closed".  Other bittorrent programs have similar functionality.

If it says the port is closed, you need to forward the port (this means you will forward traffic coming in to your internet connection/router on a particular port, to the appropriate port on one of your computers in your home network, even if there is just one computer).  

For instructions on how to forward a port on your particular router, go to this website for router specific instructions:  [http://portforward.com/english/routers/port_forwarding/routerindex.htm](http://portforward.com/english/routers/port_forwarding/routerindex.htm)

You can pick which port to use for the torrents by changing the number in the "Listening Port" box.  Just pick any 5-digit number.  You'll need to specify the same number in your Router's Port Forwarding configuration.

---

