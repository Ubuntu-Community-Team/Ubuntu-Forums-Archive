---
title: "Connection probems to my modem"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by Sowndefex on 2012-10-25
Hi all, First post so hope this is right.

I have had Ubuntu installed on my computer fairly recently by a friend and since he has moved to another town. I had internet yesterday on my normal computer but now I have lost connection. I have connection from my lap top (wireless) but have windows on my lap top. 

So I guess it is my computer settings. I have clicked on the icon wired networks and am "disconnected".

I am sorry but I dont know how to get it back,  Please could you tell me step by step on how to get my connection back.  

Again sorry, this must be a stupid question. I have tried to reset comp and modem but still no luck, 

Please help, many thanks.

---

### Post by roger_1960 on 2012-10-25
Hi and welcome

This may be simple, so here goes.

As it was working, wired I presume, something has changed either in wiring or settings.  Presumably you have checked the cable is plugged in properly..

On the networking drop down, is "enable networking" ticked, if not, click on it.

If no joy, could you press CTR+ALT+T and then type > lspci at the prompt.  Copy and paste the output back to this forum.  (Type > exit to get out of the terminal window.  This output will tell us many of the details of your computer.  Then we can search for problems with your particular hardware.

Roger

---

### Post by Sowndefex on 2012-10-25
Rodger, Many thanks for your reply. I have been tearing my hair out all evening.

I cant copy paste as I have no internet access from my computer so will try a screen shot. yes I checked the cable and even exchanged it aswell.

---

### Post by roger_1960 on 2012-10-25
Hi again

Could you give us the output from

> lshw -C network

I realise its a pain to do but its needed info.  Searching nVidia MCP73 seems to indicate others have had problems as well.

Roger

---

### Post by Sowndefex on 2012-10-26
Hi again Roger

No pain at all, Many thanks for your time.

I am at work at the moment so will get back to you a little later

Many thanks again

Owen

---

### Post by squakie on 2012-10-26
By modem, are you referring to a cable modem/router, a DSL modem/router, or an actual modem?  If it's an actual modem, how are you connecting to it (USB, serial, etc.)?  If it's a router, are you trying via a hard wired connection to the router or via wireless?  Your post refers to things for what I think is a hard-wired connection, but not sure what you are actually trying to do.

---

### Post by squakie on 2012-10-26
BTW - what version of Ubuntu are you running?  It seems some of the older kernels didn't support the forcedeth driver that it appears this device needs.  Could you post back the output of the following:

cat /etc/issue (this will give us the version of Ubuntu)

lsmod | grep forcedeth  (this is the driver for that adapter - we want to see what is loaded)

If you don't know that symbol between the lsmod and grep is the pipe symbol - on my keyboard it's the shifted "\" key.

---

### Post by Sowndefex on 2012-10-26
Hey all,

Many thanks for all your replies. I hope I can answer all your questions. 

The version of ubuntu is 10.04 LTS Lucid Lynx. As for the modem question, hmmm.  I have a CISCO box for WI-Lan and cable connection. The cable from my computer is the usual internet cable. I am pretty sure its a hardwired connection. I am very sorry squakie but your second post was way above my head. The internet for my computer was fine for months and then all of a sudden it was gone!

Please find attached the screen shot.

Many thanks again. I feel so stupid :-(

---

### Post by Sowndefex on 2012-10-26
Hey again, sorry to bump my thread but was wondering if there was any information I have missed? I am really lost here. Should I install windows again?

---

### Post by roger_1960 on 2012-10-26
Hi again

I ( although there are many who know more than me) can't see anything wrong. If it worked before, you must have the right drivers already.  Did it go wrong just after an update?  Have you tried your windows laptop on the wired connection to check that the modem end is working?

---

### Post by Sowndefex on 2012-10-26
Hi again and really many thanks for your time. I will try the laptop now. 

It seemed fine after the update but now cant be sure. I have so much work at the moment that I may have missed something. #

Could it be to do with the Search domains MAC address IPv4 802.1   and all that?   

Totally raging at my computer now! I really love Ubuntu it was working great. But I just havent had time to learn about it yet.

---

### Post by Sowndefex on 2012-10-26
Yes laptop working fine with wired connection.

---

### Post by Hari5g900 on 2012-10-26
why don't you try this:
First of all, go to the networks button on the top (as default) and right-click it.
Then (if I am right) click on the enable networking button
Then click on 'edit connections'
A box will come up
Click on the 'add' button 
If you want a very basic connection (like I have), tick the option 'connect automatically' and do nothing but hit 'apply'.
If I am right, you might have your connection ready.
P.S: I am using Ubuntu 10.04 LTS as well
Cheers:)

---

### Post by Sowndefex on 2012-10-26
OK so I hit network connections

I see wired, wireless, mobilebroad band, VPN and DSL as options.


Wired I have "wired connection" 1 2 3 and 4 However I cannot edit any of these.

I see no enable button to click on.

Really sorry guys, please help me.  :-(

---

### Post by squakie on 2012-10-26
I think the problem is the kernel version.  I had searched the net prior to my previous post, and it seems the older kernels wouldn't work with the forcedeth driver.  The best suggestion I can give you, based on these things, is to upgrade to a more current version of Ubuntu if you can.  I can't remember when the 3.xxxx kernels started being used but that kernel version would probably be a good place to start.  The posts I saw on the net where from the time period of your version of ubuntu.

If you search the internet you'll find the posts I'm talking about.  I believe it's all the kernel version - it won't run the driver.

I believe this may just be for the wireless only side of things, however.  If you are hard-wired and lost your connection, have you tried moving the hard-wire cable at the router to another port?  Perhaps for some reason that particular port went weird on you.

---

### Post by roger_1960 on 2012-10-26
Hi

Following from squakie,

You could try downloading the 12.04 LTS .iso ,burning it to a CD or USB stick, and trying it as a live CD  to test the network connection.  I guess you could do this download with your laptop.

---

### Post by Hari5g900 on 2012-10-27
> **Sowndefex said:**
> OK so I hit network connections

I see wired, wireless, mobilebroad band, VPN and DSL as options.


Wired I have "wired connection" 1 2 3 and 4 However I cannot edit any of these.

I see no enable button to click on.

Really sorry guys, please help me.  :-(
Well there seems to be an edit button and I CAN EDIT IT on my Ubuntu10.04. I even deleted it added a new connection and it worked fine.
Did you try adding a new one?
Or, did you enable network connections?
Also if you left click on it (network connections), there might be a list of wired connections, try clicking on that.

---

### Post by Hari5g900 on 2012-10-27
If it is a kernel problem, you can always upgrade it.
My kernel is always up-to-date

---

### Post by roger_1960 on 2012-10-27
Hi again

Re post #14 you "enable" the edit by selecting the connection in the list - its not obvious - does that help?

Also, have a look at post #5 here 
[http://ubuntuforums.org/showthread.php?t=2071475&highlight=wired+connection](http://ubuntuforums.org/showthread.php?t=2071475&highlight=wired+connection)

Your file should probably be the same as the proposed edit.  If it is not, save it with a new name and then edit the original and save without changing the name.  To edit the file you will need to open a terminal and type (or copy and paste)

> gksu gedit /etc/network/interfaces

enter your password

This opens the text editor with root priviledge so that you can edit the system file as per the link.  Then reboot.

---

