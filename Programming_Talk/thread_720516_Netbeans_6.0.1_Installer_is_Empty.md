---
title: "Netbeans 6.0.1 Installer is Empty ?"
date: 2008-03-10
forum: Programming Talk
---

### Post by joshdudeha on 2008-03-10
I just downloaded the whole Netbeans 6.0.1 IDE.
And I ran
 ```
cd ~/Downloads 
./netbeans-6.0.1-ml-linux.sh
 
``` To execute the file.

It then says: ```
Configuring the installer...
Searching for JVM on the system...
Extracting installation data...
Running the installer wizard...
/usr/share/themes/Human/gtk-2.0/gtkrc:71: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:242: Priority specification is unsupported, ignoring

```

And when the Graphical window opens, it is just blank.
With the title,  "Netbeans IDE Installer"
Nothing else.

I attached a picture of my outcome.
I tried using a different GTK Theme, but nothing happened, justthe same error.
Can someone please help?
I don't want to install it from Synaptic, as they only have 5.5 on there.
Thanks for the help =]

---

### Post by jeremytaylor on 2008-03-10
By any chance to you have compiz or such like running? I've had various problems where java apps give me a blank window like your when desktop effects are turned on.

Jeremy

---

### Post by joshdudeha on 2008-03-10
Nope, compiz is turned off.
=/
Hmm, I really want to start using the IDE
Can i install it via CLI ?

---

### Post by joshdudeha on 2008-03-10
Anyone, pleasee??
Lol. 
Thanks for the suggestions though Jeremy

---

### Post by joshdudeha on 2008-03-10
I keep finding fixes for Beryl, but I use Compiz Fusion, and I don't know if  adding 
```
export AWT_TOOLKIT=MToolkit
``` To my login profile thingy will do anything, as it is a workaround for Beryl.

I'm really stuck here?

---

### Post by joshdudeha on 2008-03-10
Could i install it via Synaptic??
The only result i get on there at the moment is Netbeans 5.5

---

### Post by mssever on 2008-03-10
> **joshdudeha said:**
> I keep finding fixes for Beryl, but I use Compiz Fusion, and I don't know if  adding 
```
export AWT_TOOLKIT=MToolkit
``` To my login profile thingy will do anything, as it is a workaround for Beryl.

I'm really stuck here?

Put that environment setting in /etc/profile, log out, then back in. That's what works for me. Setting it from the terminal doesn't seem to propagate it to the proper place.

---

### Post by joshdudeha on 2008-03-10
Can you tell me how to put that in /etc/profile?

---

### Post by mssever on 2008-03-10
> **joshdudeha said:**
> Can you tell me how to put that in /etc/profile?

```
sudo nano /etc/profile
```

---

### Post by joshdudeha on 2008-03-10
Thanks man, got it working now 
You're all real helpful in these forums
(Y)
Thanks

---

### Post by cipri on 2008-03-14
Wow after about one hour of searching I made it to thanks to this forum :). NICE XD

---

### Post by fcbfan on 2008-04-08
worked for me too. thx. also made my lotus 8 installation GUI working inadvertently. so thanks again :)

---

### Post by thagat on 2009-12-23
> **jeremytaylor said:**
> By any chance to you have compiz or such like running? I've had various problems where java apps give me a blank window like your when desktop effects are turned on.

Jeremy

thanks!, that was my problem :)

---

