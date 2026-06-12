---
title: "Accessing my iMac via Ubuntu."
date: 2012-02-09
forum: New to Ubuntu
---

### Post by solaristics on 2012-02-09
Okay, here's my situation so far:

I've got an iMac running Lion, and I've set every possible option to the point where I'm worried I'm wide open for an attack or something. The options on the folders I want to share are set to read/write.

I'm running a netbook with Ubuntu 10.10 on it, and in my 'Network' folder, I can see my mac perfectly clear. I open up the mac and it prompts for my username and password (They're the same for both my machines, so I don't think I've made any mistake there.)

Now, at this point I was excited because I could see all the files and subfolders in my desired shared folder. So I attempt to open a file and get this error:

"An error occured

Could not open location; you might not have permission to open the file."

Now, as I said before, I'm more than certain that I've set all the folders and users on my network to read/write/dowhatyouwant

Any help would be really appreciated.

---

### Post by mebomechanicno1 on 2012-02-09
OK, just to get clear precisely what the problem is, you've "got an iMac running Lion" and you are "running a netbook with Ubuntu 10.10 on it"; presumably from which you are trying to access the iMac?  How have you accessed the iMac?  (How have you actually connected?  Wireless router, LAN?  Is this a tried and trusted connection you have used before successfully?)
 
Second silly question, what happens when you log directly on to the iMac?  Do you get to access the files, or is there still an error message?  (See where we are going?)

---

### Post by solaristics on 2012-02-09
> **mebomechanicno1 said:**
> OK, just to get clear precisely what the problem is, you've "got an iMac running Lion" and you are "running a netbook with Ubuntu 10.10 on it"; presumably from which you are trying to access the iMac?  How have you accessed the iMac?  (How have you actually connected?  Wireless router, LAN?  Is this a tried and trusted connection you have used before successfully?)
 
Second silly question, what happens when you log directly on to the iMac?  Do you get to access the files, or is there still an error message?  (See where we are going?)



Hey, thanks for the quick reply.

Firstly, I'm accessing the iMac from my netbook running Ubuntu. I'm conncting via a Wireless router, and it shows up perfectly well in my network folder. I can SEE the files, I just can't use or copy them because of the permission error.

---

### Post by mebomechanicno1 on 2012-02-09
Try reading here [http://ubuntuforums.org/showthread.php?t=1895084](http://ubuntuforums.org/showthread.php?t=1895084) in case we are busy trying to re-invent the wheel.

---

### Post by solaristics on 2012-02-09
> **mebomechanicno1 said:**
> Try reading here [http://ubuntuforums.org/showthread.php?t=1895084](http://ubuntuforums.org/showthread.php?t=1895084) in case we are busy trying to re-invent the wheel.

Well, unfortunately that guide is a bit useless to me because I'm not trying to set my netbook as an Ubuntu server. I'm doing something far less complicated. I simply want to browse my iMac's files and be able to open them without the permission error. Surely there's something I'm missing here.

---

### Post by mebomechanicno1 on 2012-02-09
Let me see if I can replicate the problem, unless someone else can answer it in the next few hours.

---

### Post by AlanR8 on 2012-02-09
I've got an iMac running on my home network (Lion) and like you can see it perfectly in my "Browse Network" dialogue. In fact, it appears three times and I'd love to know why!

That said, one of the iMac icons when clicked asks for a password like yours, and the next one down asks if I want to log on anonymously which I do and no password or user is required, I can then access the files on the share.

---

### Post by painejake on 2012-02-09
> **AlanR8 said:**
> I've got an iMac running on my home network (Lion) and like you can see it perfectly in my "Browse Network" dialogue. In fact, it appears three times and I'd love to know why!

That said, one of the iMac icons when clicked asks for a password like yours, and the next one down asks if I want to log on anonymously which I do and no password or user is required, I can then access the files on the share.

Regarding it appearing 3 times could be once as SCP/SSH access once as Samba and once as the machine itself I believe.

If you are accessing via SCP/SSH you will be asked for your credentials when you try to connect.

Via Samba you use Connect to Server and you can enter your share credentials there (username and password you use on your iMac)

Try those methods and see if it helps?

---

### Post by AlanR8 on 2012-02-09
Thanks for your reply to MY issue, I'll look in to it. OP, any progress?

---

### Post by painejake on 2012-02-09
That reply was to both of you I imagine it's a similar issue ;)

---

### Post by solaristics on 2012-02-09
> **painejake said:**
> Regarding it appearing 3 times could be once as SCP/SSH access once as Samba and once as the machine itself I believe.

If you are accessing via SCP/SSH you will be asked for your credentials when you try to connect.

Via Samba you use Connect to Server and you can enter your share credentials there (username and password you use on your iMac)

Try those methods and see if it helps?


I think I'm connecting via Samba. How do I go about 'connecting to server'? Is there an option somewhere?

---

### Post by painejake on 2012-02-10
> **solaristics said:**
> I think I'm connecting via Samba. How do I go about 'connecting to server'? Is there an option somewhere?

This should help mate: [http://askubuntu.com/questions/34768/where-is-connect-to-server-for-ssh-connections-in-unity](http://askubuntu.com/questions/34768/where-is-connect-to-server-for-ssh-connections-in-unity)

---

### Post by solaristics on 2012-02-10
> **painejake said:**
> This should help mate: [http://askubuntu.com/questions/34768/where-is-connect-to-server-for-ssh-connections-in-unity](http://askubuntu.com/questions/34768/where-is-connect-to-server-for-ssh-connections-in-unity)


Okay, so I've connected via this method, and I see the folders just as before, but again, I'm being denied access to use them because of the same permission error. I'm completely stumped on it.

Any other ideas?

---

### Post by Learning Linux 2011 on 2012-02-11
I'm pretty sure you need to be accessing the mac as root on your ubuntu machine. 

Try: 
```

gksudo nautilus

```and see if you can access things that way.


If you are trying to access your Mac as a regular user in Ubuntu, you will get those errors.  Since the Mac is using a Unix-like OS (FreeBSD), it puts permissions on folders, just like in Ubuntu.  For example, you won't be able to access the root folder, or many other folders unless you actually are root.  I'm not completely sure that is your problem, but I tried to access a mac using Ubuntu using a Firewire cable and I received the same error message that you did, and I got around it by being root in Ubuntu.

---

### Post by solaristics on 2012-02-12
> **Learning Linux 2011 said:**
> I'm pretty sure you need to be accessing the mac as root on your ubuntu machine. 

Try: 
```

gksudo nautilus

```and see if you can access things that way.


If you are trying to access your Mac as a regular user in Ubuntu, you will get those errors.  Since the Mac is using a Unix-like OS (FreeBSD), it puts permissions on folders, just like in Ubuntu.  For example, you won't be able to access the root folder, or many other folders unless you actually are root.  I'm not completely sure that is your problem, but I tried to access a mac using Ubuntu using a Firewire cable and I received the same error message that you did, and I got around it by being root in Ubuntu.

Hey, thanks for the help. Not being root definitely seems to be the issue, but unfortunately, accessing via nautilus gives me a different error. Accessing my mac via the nautilus window isn't possible apparently, it throws out an error like 'cannot perform that function' or something...so, I'm lost again.

---

### Post by Learning Linux 2011 on 2012-02-12
Ahh, well, not having a Mac, I am limited in what I can tell you.  I used to have a Mac and I started it up using the Firewire mode by pressing the 'T' key on the Mac keyboard and using a Firewire cable to connect the mac to my Ubuntu computer.  I was able to browse quite a bit of the Mac, but of course at the end of the day, the Mac isn't using Ubuntu and any Unix operating system will have safeguards in place, which I imagine the Mac also has.

---

