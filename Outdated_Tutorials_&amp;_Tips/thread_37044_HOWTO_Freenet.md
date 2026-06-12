---
title: "HOWTO: Freenet"
date: 2005-05-25
forum: Outdated Tutorials &amp; Tips
---

### Post by battletux on 2005-05-25
Ok so i've been wanting to try this for a while and now i have finally cracked it, i think (well it's working for me at least).

REQUIREMENTS:

Java installed, see [here](http://www.ubuntuguide.org/#jre) if you do not have it installed yet.
A fixed external IP address, or if you have your internet IP's assign dynamically a dynamic DNS service account, such as from dynDNS.org. Please note if you use a dynDNS service make sure your firewall/router has the ability to auto update the dynDNS records to reflect your IP address each time it changes. If not you will manually have to update this each time your IP changes yourself.

Heres how i did it:

Once you have done all the above requirements download freenet:

```
wget http://freenetproject.org/snapshots/freenet-latest.tgz
```

Now you need to extract the files and run freenet for the first time to configure the program

```

tar xfz freenet-latest.tgz
cd freenet
sh start-freenet.sh

```
At this point you will be asked a load of config questions, i suggest you answer them how you want. I just pressed return and used all the default settings.

Once all the questions have been answered and stuff stops going past on your terminal, freenet will be up and running. To test this goto [http://localhost:8888](http://localhost:8888) in your web browser to check, you should see the web interface there, if not you've proberbly not configured java correctly or have not answered the config questions.
Now in your terminal **ctrl+c** to stop freenet, there is a bit more confiuring needed to get it working just yet.

First of all it is best you open up the freenet port on your firewall, reffer to the manufacturers guide on this. As i used the default port i opened up port 24120 and forwarded it to my Ubuntu box.

The next bit we need to edit the freenet.conf file, remember to replace **<user>** with your username:

sudo gedit /home/**<user>**/freenet/freenet.conf

You need to look for the line:

```
%ipAddress=
``` 

And replace it with ```
ipAddress=<YOUR EXTERNAL IP ADDRESS OR DYNDNS NAME>
```

NOw as Ubuntu ships with a 2.6 kernel i had to do the follow tweak to get freenet to work. the reason for this as stated by [freenethelp.org](http://www.freenethelp.org) ```
2.6 kernels:


There is a bug in the Sun JVM (at least the 1.4 versions and possibly 1.5 as well) that causes problems with Linux kernel 2.6 and the kernel that shipped with Red Hat Linux 9. It will cause Freenet to freeze in about an hour (in my machine; the time will vary).
``` 
So to get round this you have to edit the start-freenet.sh script:

```
sudo gedit /home/**<user>**/freenet/start-freenet.sh
```
and on the second line enter the following: ```
export LD_ASSUME_KERNEL=2.4.1
```.

Now in your terminal make sure you are still in your freenet directory (/home<user>/freenet) and run ```
sh start-freenet.sh
``` and this will get freenet running, so back to your web browser and lookup [http://localhost:8888](http://localhost:8888) and the page will load.

When you first run freenet it is really slow and i mean *really* so i understand that if you bear with it and have it running for a while, and use it more, it gets better. But we'll see it been running for 30mins so far and i have one site working on it.

If you want more freenet info then i suggest you give [freenethelp.org](http://www.freenethelp.org) a try.

---

### Post by Franko30 on 2005-07-30
Hi,

Thanks for the quick overview, it worked. I tweaked the memory settings in the start.freenet.sh script according to my actual RAM and it works flawlessly.  :grin:  

Apart from that I'm running everything as delivered in the freenet-latest archive, Didn't even have to use the "export LD_ASSUME_KERNEL=2.4.1" argument.

I have Java 1.5 installed and I must say that I should've done the transition of my Freenet node to Linux much earlier!

I've been running my node for over a year (on a Windows machine with a 3 GHz Athlon XP and 1 GB RAM, 50 GB assigned to my node) and Freenet (Java) never lasted longer than a day or two and it made the machine really **crawl** after 5 minutes.

Now I run my node on a 1.1 GHz Pentium M Laptop with 512 MB RAM with Ubuntu Hoary and everything is usable (50 GB of Freenet residing on an external twofish encrypted harddisc). It uses the bandwidth **more efficiently**, the downloads are **faster**, I have **more nodes** connected (more than 100), Frost runs **more smoothly**, great! It doesn't start to grab more and more memory...

 Why didn't I change earlier? Well, I never thought that changing my node to Linux would be **that easy!** Just copied everything to it's new home (even the datastore, Frost and FUQID). and it runs. Installed WINE via Synaptic, ran 'wine Fuqid.exe' (WINE window mode genrral-'Desktop' or mode explorer.exe-'Managed') and it worked. Amazing.

I recommend to everyone changing your nodes to (Ubuntu) Linux, it brings the fun into using Freenet.

Cheers

Franko30

P.S.: Sorry for all the edits on a simple message, but English is not my native language...

---

