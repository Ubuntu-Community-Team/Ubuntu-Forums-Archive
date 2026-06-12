---
title: "Synergy- Two computers one keyboard and mouse"
date: 2006-05-26
forum: Outdated Tutorials &amp; Tips
---

### Post by WolfJay_83 on 2006-05-26
Synergy -two computers, one mouse.

It’s quite common knowlege that using two monitors increases productivity. Anyone who has used two monitors, be it for writing a paper, programming or playing video games knows that it drastically increases speed and keeps you from having to constantly switch between windows.

Unfortunatly, having two monitors is not always an option. Desk space, finances and computer hardware often limit this possiblitly. Many people, however, have a laptop and a computer, or an extra pc lying around. Synergy alows you to pull your laptop up next to your monitor and use it just like an extra monitor. Your keyboard controls whichever computer the mouse is on, and the mouse switches between computers simply by moving it off one screen and onto the other -just like the common dule-monitor setup.

Synergy is cross platform, and even will connect two different operating systems. Allowing you to use one mouse and keyboard for a windows and linux computer! Best of all, it alows cutting and pasting. You can actualy cut and paste text between these computers.

Here are the instructions for setting it up in Ubuntu Linux:

You may need Extra Repositories enabled.
Open a terminal and type: sudo apt-get install synergy
Do this on both computers.
One computer is a server, the other is a client. It doesnt realy matter which.
On the server, you need a file called .synergy.conf
It isn’t supplied with the install, so you need to create it. Mine is attached below, with Bubbles being my server pc, and ubuntu being my laptop.
These names need to be the hostnames of your computer. In Ubuntu, when you open a terminal, your prompt is usualy user@hostname:~$
You simply run the server by entering the command: synergys
and you run the client by running: synergyc ipaddress
Where ipaddress is the ipaddress of the server

Here is the config file:
# stomfi synergy configuration file
#
section: screens
bubbles:
ubuntu:
end
section: links
bubbles:
left = ubuntu
ubuntu:
right = bubbles
end

---

### Post by CalcMaster86 on 2006-08-10
apt-get install synergy doesn't work on my system... i'm able to get other packages, not that one. is there another way around it?

---

### Post by CalcMaster86 on 2006-08-11
never mind, just learned that you have to uncomment some lines in sources.list

---

### Post by Chris Tucker on 2006-08-12
You might want to have synergy start when you log in... 
In Gnome, this can be done by System -> preferences -> sessions   click startup programs in the tabs at the top, click add, and enter the synergys or synergyc line you would if you were doing it by hand in a terminal.

In KDE, this can be done by (in a terminal) ```
kate ~/.kde/Autostart/synergy
```
enter into the file: 
(replace synergys with your synergyc line if this is for a client.)
```
#!/bin/bash
synergys
exit
```
save, and exit, ```
chmod +x ~/.kde/Autostart/synergy
```

log out, and back in, it should work.

---

### Post by Ago12 on 2006-08-13
Looks great, but it doesn't work on my wireless network :(

> fabien@thebigone:~$ cat .synergy.conf
# stomfi synergy configuration file
#
section: screens
thebigone:
laptop:
end
section: links
thebigone:
right = laptop
laptop:
left = thebigone

end


> wlan0     Lien encap:Ethernet  HWaddr 00:09:5B:E3:FE:29  
          inet adr:192.168.0.2  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::209:5bff:fee3:fe29/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:15882 erreurs:34 :0 overruns:0 frame:0
          TX packets:9646 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:20108471 (19.1 MiB) Octets transmis:1335274 (1.2 MiB)
          Interruption:209 


I run synergys on "thebigone" and  "synergyc 192.168.0.2" on "laptop".

No error messages, but it simply doesn't work... I've tried killing the processus and retry, but no way :(

Plus, I have no error message.

Is there something to set with iptable?

I've tried with and without xgl, it's the same :(

Should I have to simply go out of the screen with the mouse pointer, on left or right?

Thanks a lot, it looks great ;)

---

### Post by Ago12 on 2006-08-14
I stopped the firewall via firestarter, and it now works!

If anyone knew the ports to open...

---

### Post by ckempo on 2006-08-15
> **Ago12 said:**
> IIf anyone knew the ports to open...

Try 24800 - that's the defualt one, unless you've changed it.

---

### Post by aleska on 2006-08-17
first let me say, how friggin' awesome is this app?  I work from home, and on my desk is both my personal pc (Ubuntu) and a work pc (Windows).  I am so psyched that I can now use one keyboard and mouse and use both pc's seamlessly.  Even if you hate Windows, how cool that I can actually copy something in Ubuntu, mouse over to windows and paste in an windows app or vice versa?  I'll answer that, it's super cool!  
Here's a [little blurb]("http://www.skarulis.com/?p=21") on how I got it to work for me.  In case you just want the cliffs notes version, my windows box wasn't picking up on the Ubuntu hostname.  So, on the client (windows) side, I simply changed the Ubuntu hostname from skarulis-desktop to its local IP address.  That was it!  Works like a charm now.  :D

---

### Post by jaybmx on 2006-08-21
damn cool!:D

---

### Post by aanderse on 2006-08-21
I just noticed this thread and am quite happy to hear this :)  I have a question though; will this support special mice with many buttons (like the logitech mice that they have howto's for in this forum) on both machines?

thanks!

---

### Post by krul on 2006-08-23
Thanx for this tip and explanation. It is working perfectly with my Ubuntu server and windows laptop!

---

### Post by Roderik on 2006-08-26
this is ****** great! and a lot easyer and more responsive then the vnc solution.

/me is now running 17" LCD winxp - 20" LCD ubuntu - 17" LCD ubuntu (part2 of twnview), whoot!

---

### Post by temna on 2006-08-31
Now..  Can I use this to control two computers via my notebook?  Say I have two headless PCs, can I control them using Synergy from my notebook?

---

### Post by Roderik on 2006-08-31
no this is like multimonitor on one pc. 

so for example 2 computers, with 2 screens with one keyboard/mouse 

if you like to use multiple computers with one screen, you have to use VNC, NX etc

---

### Post by blackened on 2006-08-31
I've been using synergy for a few months now and it's extremely convenient not to have two keyboards and mouse on the desk. I have side by side monitors connected to two machines. The only problem I've run into was having to write a restart script for both machines as the one running synergy server goes into hibernation while the other machine is my BT box and is always on.

---

### Post by Roderik on 2006-08-31
onothe problem for me is that i'm nable to type a ~ on the keyboardless machine. Using the be-latin1 charmap. But hey, i can live with that :)

---

### Post by Paulo Wageck on 2006-08-31
I have managed to make Synergy working with this howto:
[http://doc.ubuntu-fr.org/applications/synergy](http://doc.ubuntu-fr.org/applications/synergy)

Just ONE problem.... 

From X to X-Server fine.... But when I run a WMWARE machine on the CLIENT, can use inside the virtual machine the mouse, kayboard with small letters... but no CAPITAL letters.... 

What can it be???????

Thanks!

---

### Post by waldschm on 2006-09-01
This software is amazingly handy, just thought I'd point out something I noticed on the website while downloading it though: no encryption. So just be aware that you should use an ssh tunnel on an untrusted network. It's pretty simple to do and they have instructions on the synergy web page.

---

### Post by WIWAWY on 2006-09-11
i have synergy up and running but am having trouble geting it to load on startup 
i have a win 2k server and a kubuntu client

---

### Post by encompass on 2006-09-11
Probably but worth a try either way... report back if it does.  It works with my mightymouse.
But I just wanted to post that this howto is great, quick, and easy.  You may just want to point out how to get your IP add.

---

### Post by qalimas on 2006-09-12
Awesome software, I got it working my first try with my desktop Windows (I must have Ragnarok..) and my Kubuntu laptop.  It's nice, because even though Ragnarok is in full screen, moving it all the way to the left still takes me to my laptop :D  Right now I'm at work, on my Ubuntu workstation with my Kubuntu laptop hooked into the network, and they are using Synergy as I'm typing.


Seriously awesome and useful software, I love it!

---

### Post by radiomog on 2006-09-27
I too can testify that Synergy is da'BoMb :mrgreen: 
It is the first software I was actually excited to hear about and have work in a LONG time (and I've been around since doing basic on a Apple 2e)

I run two computers here at work and it allows me to not have 2 KB&M

my main computer runs XPp and the other machine (toughbook) runs ubuntu DD.

I use Ubuntu to run my internet/data research while my Xp machine does the heavy work with the serious number crunching utilities.

it's a great way to make use of a not so speedy laptop or other computer w/o taking up that much space and you can add as many other computers as you want!

I highly recommend this program 8)

---

### Post by exir on 2006-11-27
I know this amazing program when i was completely running in windows. but since i run now only ubuntu :D i have some problems with it. I start synergys on the server and synergyc on the client. both are starting succesfull, i see on the server that the client has been connected and on the client i see that it has been connected to the server.

But when i move my mouse to the right side of the screen it doesnt jump over to my screen on the laptop :(

does any one know what to do about this one? I cant find it in the manual that was by synergy

my config looks like this:
---
section: screens
10.0.0.161:
john:
10.0.0.151:
fokke:
end
section: links
10.0.0.161:
                right = 10.0.0.151
10.0.0.151:
                left = 10.0.0.161
end
---

Note:
where john is my pc and fokke my laptop. when i dont mention john: and fokke: in the screens section, the server wont even start. if i only use the host names, it wont even start, if i only use ip addresses, it wont even start because it cant find hostnames, adding hostnames also to the screens section fixed my problem

thnx in advance! :)

---

### Post by exir on 2006-11-30
nobody?? :(

---

### Post by encompass on 2006-12-01
Your trying to highjack this post... please create a new post so that people can answer you better.

---

### Post by James.Lazo on 2007-08-07
> **WolfJay_83 said:**
> Synergy -two computers, one mouse.
[B]
These names need to be the hostnames of your computer. In Ubuntu, when you open a terminal, your prompt is usualy user@hostname:~$[/B]



Absolutely brilliant. I just got another computer so I did a fresh install of XP Pro on it and converted my old box into a Kubuntu machine, and installing Synergy was my first Linux task. I was going in circles for hours till I chanced on your beautiful advice.

Much thanks!

James

---

### Post by FrankBlourtango on 2007-08-07
I need to find a video card that ubuntu likes.

---

### Post by fooman on 2007-08-07
never heard of synergy until about 10 minutes ago when i happened upon this thread.

haha....this is soooo cool and really easy to setup!  :)

i hate having to type on the laptops keyboard when i have it sitting on the desk right next to my desktop's monitor.  

now i don't have to anymore!!  i can use my desktops full size keyboard and mx1000 mouse perfectly on both computers!!

thank you 

=D>

edit:  just installed it on the xp partition of my laptop and it runs great with my ubuntu desktop!!  ....yeah!!

---

### Post by parker13 on 2007-08-08
I've been using synergy for years and couldn't live without it. One other important feature is that it synchs the clipboard between the machines (for text, at least), so something copied on one machine can be pasted on another. That really makes it feel like it's all a single desktop.

Here's quick instructions for autostarting the client on Ubuntu (using GDM):

Add the following lines after the comments at the top of **/etc/gdm/PreSession/Default**
```

/usr/bin/killall synergyc
sleep 1
/usr/bin/synergyc HOSTNAME

```

...where HOSTNAME is the name of your server running synergys.

Full instructions for other display managers are available here:
[http://synergy2.sourceforge.net/autostart.html](http://synergy2.sourceforge.net/autostart.html)

---

### Post by eentonig on 2007-08-08
Great peace of work.

In ten minutes, I got it working with  three computers

- Desktop: Feisty Fawn
- Laptop/server: Edgy Eft
- Laptop: XP Pro (From work)

---

### Post by KillerKiwi on 2007-08-08
I use quicksynergy a lot... never did like config files... I've patched it slightly to remember the server host name.

Great stuff

---

