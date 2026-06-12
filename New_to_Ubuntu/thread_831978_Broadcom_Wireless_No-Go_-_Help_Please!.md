---
title: "Broadcom Wireless No-Go - Help Please!"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by age99 on 2008-06-17
Hi all,
I've just upgraded to 8.04 and I'm having some issues getting connected using my wireless.  I'm very much a newb at this.  I'm able to "see" the networks when I set the wireless to "roaming mode".  When I select the one I want, it asks me for a passphrase, I enter it, but it doesn't seem to respond I don't have any internet access.  The same network and passphrase work on the same machine (dual-boot) with windows.
I have no problem with my wired net access (same network).  

Should I set up a manual connection?  How would I do this?

Any help would be appreciated.

---

### Post by joshsmith on 2008-06-17
probably a good idea to look for an ndiswrapper guide, google says this:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
which loads the windows driver, into linux, instead of the linux driver

---

### Post by kavmac on 2008-06-17
if your currently able to get to the point of seeing your wireless access points and can enter your passphrase, i suggest downloading and installing wicd.  helped me out greatly the other day.  i'll give you the link to my thread and you can follow the simple instructions there.  you do need to download wicd before you enter anything in terminal though.


hope this helps :)

[http://ubuntuforums.org/showthread.php?t=829571](http://ubuntuforums.org/showthread.php?t=829571)

---

### Post by mivo on 2008-06-17
A good starting point is this page:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

The Hardy-related sub-page recommends the repository at [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) , which allowed me to get Broadcom wireless to work within minutes (on my laptop), without ndiswrapper. But first check to see which Broadcom device you have.

---

### Post by age99 on 2008-06-17
Unfortunately, it seems that Wicd doesn't exist for 8.04.  I tried

[HTML]sudo apt-get install wicd[/HTML]

And it gave me no love:

[HTML]E: Couldn't find package wicd[/HTML]

I'll try some of the other suggestions, and write back.

---

### Post by kavmac on 2008-06-17
you missed the important part - you need to download wicd before you can install it.  i am running hardy too.  follow the download instructions here to get wicd, then the command in the other thread to get it installed in hardy :)


[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by eopi on 2008-06-17
Ok duuuhhhh 

I was trying root and non-root and the install wicd 

Couldn't find Package... 

now let me move my wire back to my laptop...  

"It just works, sometimes"

When you don't know much, like me.

---

### Post by kavmac on 2008-06-17
it's okay.  i did the same thing.  :)

---

### Post by eopi on 2008-06-17
Ok, I' followed the instruction of:

 [I][COLOR="Blue"]   deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras 

where gutsy is your version of Ubuntu in lowercase (dapper, edgy, feisty, gutsy, hardy). Then, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you. 

SNIP 

 Give it a name ("Wicd" works fine). For the command, enter "/opt/wicd/tray.py".[/COLOR][/I]

Anyone have a clue as to what I do now?

---

### Post by kavmac on 2008-06-17
i just added the ```
deb http://apt.wicd.net hardy extras
``` (cause we're using hardy) in the repositories package manager, and then used ```
sudo apt-get install wicd
``` in terminal.  try it that way... :)

---

### Post by eopi on 2008-06-17
Ok

slow down, we need to draw some pictures 

1. I typed in "hardy" as you did
2. I type in sudo apt-get install wicd and get the following:

[B][COLOR="Blue"]reading dependency tree  DONE
Building    
Reading  DONE
wicd is already the newest version
0 upgraded, 0 newly installed, 0 to remove and 153 not upgraded.[/COLOR][/B]

So I think I'm all installed and ready but ....

So now when I open up a browser it still off line (I've removed my cable wire). 

So I don't know what to do now. (??)


An aside: 

see the problem is someone can know a little about becoming root and what not; and terminal command line windows but beyond that they are lost, like me.  This is why people love Windows - Plug and Play... so I'd appreciate some picture drawing and all.  As you can tell I know a little but I still can't get a signal. 

My one friend, an IT guy, didn't believe that Hardy didn't fix my broadcom problem.  I've been trying to get wireless for 4 months now; I shouldn't let it bother me but I haven't learned much of Ubuntu because of it.  

Again Thx for any feedback you may have.

---

### Post by kavmac on 2008-06-17
i apologize, i should've explained that once you use that command, it will install automatically.  so yeah, it's installed already.  now, you have to open it and replace network manager in your system tray.

Menu > Internet > Wicd

Once the gui opens up, it should detect any and all wireless access points within range (that are broadcasting anyway).  once you select yours, click on the tiny arrow pointing right at it

eg > riemac for my network

it opens options up right below it.

it also gives

> Advanced Settings

click on that.  if your connection is encrypted, click on

- Use Encryption

Select what type of passphrase, etc you are using.

eg, mine is WEP (passphrase)

Enter your passphrase.  once it connects, it will show

Connected to (your network) at (number - being the signal strength in percentage format), IP - the IP address your network gives your computer.
eg, Connected to riemac at 86 (IP etc)


Also, at the top of the wireless access points it will show your wired connection.

Once you are able to connect, you can go to Preferences at the top, and seclect Automatically Reconnect on Connection Loss (if you want it to do so).

Now, if you want Wicd to appear in your system tray, you need to add it to sessions.

Menu > System > Preferences > Sessions

Select Add

Name it whatever you'd like (for simplicity I kept mine as Wicd)

Enter:

/opt/wicd/tray.py

in the command line.



I apologize in advance if this is too watered down... let me know if it works for you :)

---

### Post by age99 on 2008-06-17
Sweet.  I just successfully installed the program.

I followed the instructions sent by kavmac: 
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

The only things that I changed (under the Installing Wicd in Ubuntu heading) was 

[HTML]deb http://apt.wicd.net gutsy extras[/HTML]
to
[HTML]deb http://apt.wicd.net hardy extras[/HTML]

I had to use the advanced settings once I started Wicd to add the passphrase (WEP Hex) and it worked great.

I haven't set up a network for the wired version yet, but it looks straightforward.

Adrian

---

### Post by eopi on 2008-06-17
Applications - > Internet  - > Wicd

I did this and there is no gui (no dialog box opens up)?

I created a short cut to desktop but it still doesn't open up. 

Is there email tech service available?  Is there a fee?

---

### Post by kavmac on 2008-06-17
hmm have you tried restarting and seeing if that makes a difference?

if not, [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) should give you more assistance.  you can either use their forums or email them.

---

### Post by eopi on 2008-06-17
grrr  :mad:

:(
:)

I restarted it and the Wicd Manager opens up but the is no wireless networks found.  

This is too funny, Ubuntu is proving to be bad for my health, I hate not knowing something and now I have chest pains and heart burn.  :)  earlier there was a pit in my stomach as if I was back in grad school taking a difficult exam.

Well I guess I can arrange for a super long cable to wire my laptop. 

And on my desktop, I can install Ubuntu as it's wired.  

Or I can ditch Ubuntu altogether, and buy Vista and another McAfee subscription. 

Well, let's see two IT guys ("Linux" guys), one that actually came over to my house and couldn't fix it.  A internet forum... couldn't fix it.  

Thanks for all the input, maybe I'll come back after the next release in 5 months, maybe that will fix it.  :)

Until then have fun with the 3D desktop and all the other goodies.

---

### Post by kavmac on 2008-06-17
another silly question... is your wireless card and the wireless router turned on and enabled?  sorry to hear you might return to vista.  don't waste money on mcafee or any other paid anti virus company - go for a free one - you're just giving the anti virus companies more money to make more viruses!  and don't wait the whole five months.... hardy updates can do more than the nothing you'd be doing by waiting for another release...

---

### Post by age99 on 2008-06-17
Eopi, I had to re-install the Wicd a 2nd time because there was a problem the first time around.  
If you go to:
administration > Synaptic Package Manager
then search for Wicd, then select it, and hit apply, it should let you re-install it, if you have already downloaded it.  Then try it again.  If it doesn't work after that, kake sure that you can see the networks in Windows.

I felt the same way, but you just have to keep plugging at it....

---

### Post by eopi on 2008-06-17
Hey Age99 and Kavmac, thanks for the input.  I went to my Windows partition and everything Wireless is working.  I've never had a problem with it.  

Also Age99, I did reinstall and again it's says that wicd is already the newest version here. :)

Btw, I made attempts beyond this one forum to fix the problem, this happened last Feb and March.  I was under Ubuntu 7.10 (i think) back then.  I thought Hardy would fix the Broadcom problem; so did Linux advocates.  

Ok, so I send the Source Forge WICD group mail list an email message explaining the problem.  

We'll see what they say.  

I'll post up if I get this resolved. Thx. :)

> **kavmac said:**
> another silly question... is your wireless card and the wireless router turned on and enabled?  sorry to hear you might return to vista.  don't waste money on mcafee or any other paid anti virus company - go for a free one - you're just giving the anti virus companies more money to make more viruses!  and don't wait the whole five months.... hardy updates can do more than the nothing you'd be doing by waiting for another release...

---

### Post by RequinB4 on 2008-06-17
if you run
```

lspci

```

and you see b43(something) on the same line as Broadcom, go [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560).

The firmware doesn't come loaded by default, so this lets you use the windows drivers via ndiswrapper.

---

### Post by eopi on 2008-06-18
> **RequinB4 said:**
> if you run
```

lspci

```

and you see b43(something) on the same line as Broadcom, go [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560).

The firmware doesn't come loaded by default, so this lets you use the windows drivers via ndiswrapper.

**[COLOR="Blue"]What does it mean that I did away with the original 'Network Manager' and replaced it with Wicd?[/COLOR]**

Can I still use your suggestion of [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560) ???

See the thing is I'm afraid of destroying a path then not being able to make head way.  Maybe I'm at that point.

---

### Post by RequinB4 on 2008-06-19
It shouldn't matter so long as you didn't break anything getting rid of network-manager

---

