---
title: "It seems a major task to switch to ubuntu."
date: 2008-06-30
forum: New to Ubuntu
---

### Post by esbo on 2008-06-30
It seems a major task to switch.
Now that I have finally installed a working system I have began thinking about the possibility of switching.
I suppose the idea would be to do it gradually by dual booting, but take for example email, you would want that on both systems, ie all the email messages on both.
In real life it would be lilke having two houses with mail going to both, that is problematic.

Another thing is poker, I play a lot of poker online, OK I night be able to get this wine thing to run the poker software but there is a problem with the 'hand histories' which are records of every game you have played which you can use to analyse how other players play by building up statistics on their actions.
However you would need a full set of histories on each machine, or ideally
a central store shared between both systems - I am not sure if that is possible.
I think you can read files one way but not the other, is that correct?
You can read windows from ubuntu but not ubuntu from windows?

So it seems to me the main problem is not the programs you run but the data those programs rely on.

Oh and one other thing, you may notice my lines are of varying lengh this is
because the edit box is not wide enough. I could change them but I think it would be more sensible to change the edit box width. Obviusly you get the 
same preoblem in windows.

---

### Post by chronographer on 2008-06-30
I think you should ry to NOT use Windows at all, if you have essential applications that you need to use, get a virtual maching like [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")Virtualbox and run them in that. I tried running applications which share ddata between OSs but it is unmanageable. I now run Ubuntu all the time, and sometimes play games on the XP partition. I have the virtualbox virtual machine to use some important windows programs that don't run in wine.

Just make the change!

---

### Post by mcduck on 2008-06-30
For the mail, use IMAP instead of POP, and configure your mail application to leave the mail on server. This way you can acces your mail from anywhere.

I can't really say anything about te poker, as I don't know what kind of program you need to play it and how the program works.

For the line length, just don't push press enter at the end of every line. The lines will be changed automatically depending on how much space there is available in on the viewer's browser window. Just like with any other text editor. ;)

---

### Post by esbo on 2008-06-30
> **mcduck said:**
> For the mail, use IMAP instead of POP, and configure your mail application to leave the mail on server. This way you can acces your mail from anywhere.

I can't really say anything about te poker, as I don't know what kind of program you need to play it and how the program works.

For the line length, just don't push press enter at the end of every line. The lines will be changed automatically depending on how much space there is available in on the viewer's browser window. Just like with any other text editor. ;)

Well actually you can run the poker clients in Wine apparently and also
the main commercial program which analyses hand histories called 'Poker Tracker', however I have written my own program in C to analyse the hand
histories, it is pretty basic but I am quite proud of it and it is 'all mine' and I can tailor it to my needs.
The only hard bits were the bits I had to do in MSDOS, and I was thinking at the time I could have done those so much easier in a 'unix' type enviroment.
That is a positve if I switch, it is all text based and the C code should be machine independant.
Anyway I will see how it goes with dual booting for the time being.

I don't think there is a solution to the typing problem though, it's all done subconsciously, sometimes unconsciously :lolflag:

---

### Post by esbo on 2008-06-30
> **chronographer said:**
> I think you should ry to NOT use Windows at all, if you have essential applications that you need to use, get a virtual maching like [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")Virtualbox and run them in that. I tried running applications which share ddata between OSs but it is unmanageable. I now run Ubuntu all the time, and sometimes play games on the XP partition. I have the virtualbox virtual machine to use some important windows programs that don't run in wine.

Just make the change!

Well I will have to see how it goes, I really am not experienced enough in ubuntu to switch yet so I will have to build up my skills before I condsider that option.

---

### Post by aktiwers on 2008-06-30
What poker site do you use?
I have seen PlayonLinux will download and install some clients for you automatically
[http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)

Also Pokerroom.com has a Java based Poker client that works great with Firefox.

To read the Linux partition from Windows, install the Ext3 driver on Windows:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

The email thing..  if you don't just use the webbased interface of your email account, you can use Thunderbird and simply set it not to download the mails you read. This way the windows client downloads them and the linux client does not.

---

### Post by scotcella on 2008-06-30
> **esbo said:**
> Well I will have to see how it goes, I really am not experienced enough in ubuntu to switch yet so I will have to build up my skills before I condsider that option.

Thats the advantage of dual booting, is that if you can't do something in Ubuntu, you can switch over to windows.

All my work, internet, emailing etc etc is done in ubuntu. I guess this transition is easy.

To date, I haven't found a suitable application to use in ubuntu for photo editing and making photo slide shows, so I do this in Windows. 
(Before other posters suggest to me use GIMP, yes it's there but not for what I'm after). 

Until something comes up, I'll keep using Windows for this.

For emails, use IMAP as the previous poster said.

Not sure for your other Poker game request as I'm not much of a gamer except for the occasional Solitare, Tetris and Frozen Bubble.

Anyway welcome to Ubuntu!

---

### Post by mevets on 2008-06-30
Linux can read NTFS (windows) drives and Windows can read ext3 (linux) disks if you install a product like Ext2 Ifs at [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by aktiwers on 2008-06-30
> **scotcella said:**
> Thats the advantage of dual booting, is that if you can't do something in Ubuntu, you can switch over to windows.

All my work, internet, emailing etc etc is done in ubuntu. I guess this transition is easy.

To date, I haven't found a suitable application to use in ubuntu for photo editing and making photo slide shows, so I do this in Windows. 
(Before other posters suggest to me use GIMP, yes it's there but not for what I'm after). 

Until something comes up, I'll keep using Windows for this.


[http://www.osalt.com/2006/09/photoshop-plug-ins-for-gimp---now-also-for-linux](http://www.osalt.com/2006/09/photoshop-plug-ins-for-gimp---now-also-for-linux)

[http://www.osalt.com/photoshop](http://www.osalt.com/photoshop)

Sorry..  couldn't resist.. :)

---

### Post by hyper_ch on 2008-06-30
you could try gimpshop... it uses a photoshop-style interface for gimp.

---

### Post by katiad on 2008-06-30
Frankly, photoshop isn't necessarily what he's after, either. Not everyone has the time, need, or desire to learn a complex program for simple photo desktop photo editing, a market linux is quite poor in, if you ask me. 

However, Picasa for linux works quite well these days!

---

### Post by katiad on 2008-06-30
To the original poster:

Email is fairly easy to work around. Use webmail (most ISPs/email providers support this) on the OS you intend to use less, and use regular email for your main OS. Or use IMAP for both, but this isn't always supported by ISPs or email providers, and more, forces you to rely on the server to store your mail. However, you could (again) semi-resolve that issue by using IMAP on one OS and POP on the other.

Other documents/shares - you can set up a shared partition in FAT32, or enable the drivers listed above to give you access to linux or windows partitions. 

Your poker game may or may not work in wine - you'd have to try and see. But if not, that IS what dual booting is there for - so you can boot into Windows for the things you can't do in Linux!

---

