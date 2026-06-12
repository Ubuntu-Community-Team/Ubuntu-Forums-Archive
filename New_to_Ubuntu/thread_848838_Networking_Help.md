---
title: "Networking Help?"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by Richard833 on 2008-07-03
Hello, I recently installed ubuntu on my laptop that previously had crappy vista, I backed all my music and stuff up onto my vista desktop into it's public network folder.

My question is, what would be the easiest way to go about retrieving this data and putting it on my laptop?

Thanks, sorry for being a complete noob.:lolflag:

---

### Post by lisati on 2008-07-03
Have a look [here]("http://ubuntuforums.org/showthread.php?t=202605") for setting up a network - it may be of some help getting your machines talking to each other with the ability to share (and copy) files.

---

### Post by skylinedna on 2008-07-03
I think samba (sudo apt-get install samba)  would be your best bet. its what i use. im sorry im too noob to tell you how to use it in a way you will understand but google configuring samba if you get stuck.  sorry i cant be of more help

---

### Post by AnarkistNZ on 2008-07-03
Share the folder on your Vista machine, then copy it over to your laptop just as you would between two Windows machines.

e.g. Once shared on the Vista machine, jump on your laptop, open a window and in the address type '\\192.168.x.x' (replace with the IP address for your Vista machine) and it will display what you've set up to be shared, then copy/paste.

---

### Post by AnarkistNZ on 2008-07-03
> **skylinedna said:**
> I think samba (sudo apt-get install samba)  would be your best bet. its what i use. im sorry im too noob to tell you how to use it in a way you will understand but google configuring samba if you get stuck.  sorry i cant be of more help

No. Only do this if you're wanting to set up Windows compatible file-sharing **from** the laptop.

Skylinedna: He's sharing from Vista to Ubuntu, not the other way around.

---

### Post by lisati on 2008-07-03
> **AnarkistNZ said:**
> Share the folder on your Vista machine, then copy it over to your laptop just as you would between two Windows machines.

e.g. Once shared on the Vista machine, jump on your laptop, open a window and in the address type '\\192.168.x.x' (replace with the IP address for your Vista machine) and it will display what you've set up to be shared, then copy/paste.

Makes sense. 

<off topic>(insert friendly teasing about Jaffas here</off topic>

---

### Post by skylinedna on 2008-07-03
> **AnarkistNZ said:**
> No. Only do this if you're wanting to set up Windows compatible file-sharing **from** the laptop.

Skylinedna: He's sharing from Vista to Ubuntu, not the other way around.


Sorry mate. as i said im a noob too. maybe thats why i was having so much problem.Can you share from xp to ubuntu the same way? i couldnt get it to work. how do you share using a crossover cable?

---

### Post by iaculallad on 2008-07-03
> **Richard833 said:**
> Hello, I recently installed ubuntu on my laptop that previously had crappy vista, I backed all my music and stuff up onto my vista desktop into it's public network folder.

My question is, what would be the easiest way to go about retrieving this data and putting it on my laptop?

Thanks, sorry for being a complete noob.:lolflag:

Install SMBFS in your laptop and use it to mount the Public network folder on your vista desktop in your Ubuntu laptop.

```
sudo apt-get install smbfs
```

Then try reading the procedure I posted on this [thread]("http://ubuntuforums.org/showthread.php?t=847837").

---

### Post by AnarkistNZ on 2008-07-03
> **skylinedna said:**
> Sorry mate. as i said im a noob too. maybe thats why i was having so much problem.

That's cool, I just wanted to make sure you didn't have him running around installing and configuring samba for nothing.

> **skylinedna said:**
> 
Can you share from xp to ubuntu the same way? i couldnt get it to work.


Yes, Ubuntu can browse SMB (Windows File Sharing) shares without any additional configuration. Browse to the share using explorer, and copy/paste as you would if you were copying from Windows to Windows.

> **skylinedna said:**
> 
how do you share using a crossover cable?


The function of a cross-over cable is to connect two computer without the need for a switch in the middle. A straight-through cable can also be used in some situations, as network cards these days are auto-sensing, and know to cross the transmit/receive pairs automatically.

Because the two computers are connected to each other directly in this scenario, and there is no DHCP server to assign an address you would need to configure a private IP address on both computers, as well as a subnet mask. Default gateway and DNS servers aren't needed for this.

Once the computers are physically and logically (e.g. with a cable, and assigned correct address) file sharing can be used as it normally (explained above) without issue.

---

### Post by Richard833 on 2008-07-03
> **AnarkistNZ said:**
> Share the folder on your Vista machine, then copy it over to your laptop just as you would between two Windows machines.

e.g. Once shared on the Vista machine, jump on your laptop, open a window and in the address type '\\192.168.x.x' (replace with the IP address for your Vista machine) and it will display what you've set up to be shared, then copy/paste.

like in firefox?
it doesn't work :(

and i like your solution better, i was half way thru setting up samba and was getting a headache lol

---

### Post by Richard833 on 2008-07-03
PS

I can see my Desktop PC with vista under Network Servers in Ubuntu, but when I click on it, there is nothing inside.

---

### Post by AnarkistNZ on 2008-07-03
> **Richard833 said:**
> like in firefox?
it doesn't work :(

Open up your 'home' folder from your desktop, there will be an address bar at the top (saying something like /home/yourname/ .etc)

Replace that with '\\192.x.x.x' (the IP address of your Vista computer) and it should display the shared files you've allowed on Vista.

---

### Post by AnarkistNZ on 2008-07-03
> **Richard833 said:**
> PS

I can see my Desktop PC with vista under Network Servers in Ubuntu, but when I click on it, there is nothing inside.

That would suggest there is a problem with the way you've setup sharing on your Vista PC in that case.

Make a new folder, right click on it and select 'Sharing & Security' then put your data in there.

The only issue may be in configuring it. They've done horrible things with File Sharing in Vista and made it extremely complicated. I have zero experience with it, and avoid it like the plague so unfortunately I'm not much help with that side of things. Try Google 'configuring file sharing in Vista' or similar if all else fails.

---

### Post by Richard833 on 2008-07-03
> **AnarkistNZ said:**
> Open up your 'home' folder from your desktop, there will be an address bar at the top (saying something like /home/yourname/ .etc)

Replace that with '\\192.x.x.x' (the IP address of your Vista computer) and it should display the shared files you've allowed on Vista.

When I do that it says,

Couldn't display "\\192.168.0.103" 
Nautilus cannot handle this kind of locations.



sorry for being so dumb at linux lol :(

---

### Post by AnarkistNZ on 2008-07-03
> **Richard833 said:**
> When I do that it says,

Couldn't display "\\192.168.0.103" 
Nautilus cannot handle this kind of locations.



sorry for being so dumb at linux lol :(

Sorry, try this 'smb://server/share'

Considering you can see it under 'Network' there's really no need to do it like that anyway. If you can't see it under network (e.g. Auto-discovery fails for some reason) then that method just complicates things.

---

### Post by Richard833 on 2008-07-03
> **AnarkistNZ said:**
> Sorry, try this 'smb://server/share'

Considering you can see it under 'Network' there's really no need to do it like that anyway. If you can't see it under network (e.g. Auto-discovery fails for some reason) then that method just complicates things.

Thanks for your help, but I got it working.
I just had to share the whole damn C:/ drive, individual files wouldn't work.

Thanks :)

---

### Post by bill0102 on 2008-07-04
What's Up all,  want to beat any game you play? check out this  [Top Cheat Codes Site]('http://vncheatcodes.com')
You can play and cheat any game you want from [PSP Cheat Codes]('http://vncheatcodes.com') to [Xbox Cheat Codes]('http://vncheatcodes.com') and many other [Game Cheat Codes]('http://vncheatcodes.com')

---

