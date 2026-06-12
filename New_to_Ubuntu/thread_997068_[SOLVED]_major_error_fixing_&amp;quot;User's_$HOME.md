---
title: "[SOLVED] major error fixing &amp;quot;User's $HOME/.dmrc file is being ignored&amp;quot;"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by YQ002lc2 on 2008-11-29
Hello All,

//I started out getting this message: 

User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

//I typed in the following into the terminal

sudo chmod 700 /home/jpinson
sudo chmod 644 /home/jpinson/.dmrc

//as recommended by Oldsoldier2003 on another site which I don't have the //URL for right now. 

//Afterwards, I restarted my computer and got the same message, but this //time when I clicked ok to make it go away, the following error messages //showed up:

Could not update ICEauthority file /home/jpinson/.ICEauthority

//I clicked close on that and the following came up:

There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)


//I clicked close on this, and my normal background image displayed with //the following two messages:

Failed to change to directory '/home/jpinson' (Permission denied)

//then on top of that was the message:

Screensaver functionality will not work in this session.


// I am very new to linux and I've never had any kind of problem like this. Is there a way to fix this, anyone? If not, can I at least backup my /home/jpinson/Documents I had stored on my hard drive...?

---

### Post by Nepherte on 2008-11-29
[http://ubuntuforums.org/showthread.php?p=6138880](http://ubuntuforums.org/showthread.php?p=6138880)

---

### Post by drs305 on 2008-11-29
jpinson,

One of the problems you may be having is that you changed some permissions but didn't change the ownership. I wrote the guide linked by Nepherte. Follow those steps (go to #5 if in a hurry) and if you are still having problems come back and tell us what error messages you are still getting. Hopefully it will not be the same ones you are currently experiencing. ;-)

---

### Post by YQ002lc2 on 2008-11-29
According to Nepherte's instruction:
Since I couldn't otherwise access a terminal
I typed (Ctrl+Alt+F1)
I logged in
Then typed:

sudo chown username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username /home/username
chmod 755 /home/username

where username is whatever your username is.

I then hit (Ctrl + Alt + F7) and (Ctrl + Alt + backspace) to get back to my login screen.

This completely fixed the .dmrc issue!
-------------------------------------------------------------

However, the other issues that arose from my initial attempt to fix it are unresolved.

When I go to log in now I get the following messages:

Could not update ICEauthority file /home/jpinson/.ICEauthority

then I got

There is a problem with the configuration server. (usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256) 

then I got 

A black screen

I initially typed:(DON'T DO THIS!!!)

sudo chmod 700 /home/jpinson
sudo chmod 644 /home/jpinson/.dmrc

If that helps.

---

### Post by drs305 on 2008-11-29
> **jpinson said:**
> 

This completely fixed the .dmrc issue!
-------------------------------------------------------------

However, the other issues that arose from my initial attempt to fix it are unresolved.

When I go to log in now I get the following messages:

Could not update ICEauthority file /home/jpinson/.ICEauthority


Glad we are making progress. When I wrote the guide to .dmrc errors, I tried to provide a solution that would impact the fewest files possible. As you found, they cured your .dmrc problem.

The ICEauthority warning is most likely due to the same issue, and can probably be solved by running the following (assuming "jpinson" is your username):
```

sudo chown jpinson:jpinson $HOME/.ICEauthority
chmod 600 $HOME/.ICEauthority

```

---

### Post by YQ002lc2 on 2008-11-29
Dear drs305,

I tried your code: 

sudo chown jpinson:jpinson $HOME/.ICEauthority

and got the message 
chown: cannot access '//.ICEauthority': No such file or directory

so I first tried :

Sudo chown jpinson /home/jpinson/.ICEauthority
sudo chmod 700 /home/jpinson/.ICEauthority

with no change

Then I tried:

sudo chown jpinson:jpinson /home/jpinson/.ICEauthority
chmod 700 /home/jpinson/.ICEauthority

also with no change.

Any thoughts?

---

### Post by drs305 on 2008-11-29
The file does not exist, which is why the commands are not working!
> 
chown: cannot access '//.ICEauthority': **No such file or directory**



If you haven't rebooted since you fixed the .dmrc error I would try that first. If you have and still get the .ICEauthority warning, here is something you can try:

A few users recommend booting to the recovery mode root prompt and removing the .ICEauthority and .Xauthority files. (I recommend renaming them instead in case you need to restore them.) I know you don't appear to even *have* an .ICEauthority file, but I would run them anyway.
(*Added: I have just done this on my own computer with no ill effects. It creates new files. I also noted it creates 600 permissions so I've modified the earlier post accordingly.*)
```

mv /home/jpinson/.ICEauthority  /home/jpinson/.ICEauthority.backup
mv /home/jpinson/.Xauthority /home/jpinson/.Xauthority.backup
reboot now

```

---

### Post by YQ002lc2 on 2008-11-29
Dear drs305,

I tried your code. 

When I tried:
mv /home/jpinson/.Xauthority /home/jpinson/.Xauthority.backup
I got a message that there was no such file or directory. 

I rebooted anyway, and nothing changed. 

I should clarify that when I ran the other commands earlier such as:

Sudo chown jpinson /home/jpinson/.ICEauthority
sudo chmod 700 /home/jpinson/.ICEauthorit

I did not get any errors such as no such file or directory.
It appeared to work, but when I rebooted, nothing had changed. 


And the mv command worked with /home/jpinson/.ICEauthority...

Any thoughts?

---

### Post by YQ002lc2 on 2008-11-29
Dear drs305,

I tried your code. 

When I tried:
mv /home/jpinson/.Xauthority /home/jpinson/.Xauthority.backup
I got a message that there was no such file or directory. 

I rebooted anyway, and nothing changed. 

I should clarify that when I ran the other commands earlier such as:

Sudo chown jpinson /home/jpinson/.ICEauthority
sudo chmod 700 /home/jpinson/.ICEauthority

I did not get any errors such as no such file or directory.
It appeared to work, but when I rebooted, nothing had changed. 


And the mv command worked with /home/jpinson/.ICEauthority...

Any thoughts?

---

### Post by YQ002lc2 on 2008-11-29
Thank you to everyone who helped me. 


I ended up, with the help of drs305 on IM, using the boot disk to mount my partitions because I couldn't even boot into my system.

I did this by using the ubuntu DVD, going into the "try ubuntu before installing" option, and opening a terminal.

I then did 

sudo fdisk -l

I then determined which was my home directory.
I did:
sudo mount /dev/sda7 /mnt/temp

then I inserted my external HDD into the USB slot. 
All the partitions were automounted 
I did
gksudo nautilus to access my /mnt/temp/jpinson folder which is where my home information is stored. (I have a separate /home partition)

Then I graphically copied and pasted the jpinson file into a folder I created on my external HDD.

I checked to see if everything was the same.

I then unmounted my external HDD partitions, shutdown, and did a clean install of Ubuntu 8.10.

I will later copy back my documents and everything I need from the external HDD.

Thanks again to drs305 and nepherte!

---

### Post by nicolito on 2010-03-30
Even though you consider this problem solved I feel a reinstallation is a tough way to solve a problem.

I experienced a similar problem with the .ICEauthority file. For me the chown and chmod suggested by drs305 solved it.

> **drs305 said:**
> 

The ICEauthority warning is most likely due to the same issue, and can probably be solved by running the following (assuming "jpinson" is your username):
```

sudo chown jpinson:jpinson $HOME/.ICEauthority
chmod 600 $HOME/.ICEauthority

```

I understand that it didn't for jpinson. Just to save some time the next time you experience login problem you can be preventive and install ubuntu on another partition (it can be minimal). Then you can allways login in to that partition and  reach your crashed system from there.

---

