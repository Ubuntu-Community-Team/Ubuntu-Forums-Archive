---
title: "Very slow shutdown"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by gredawarha on 2012-07-08
Hello all

I have just noticed over the last few days that my Ubuntu 12.04 is taking 30+ seconds to shutdown where before it would shutdown very quickly.

I click the icon in the top right hand corner and then select shutdown or retart.  Then nothing happens for 30 seconds or so and then it begins to shutdown.

Okay this is not the worst thing in the world but it's pretty annoying.  Any idea on what is suddenly delaying the shutdown?

Appreciate any help.

---

### Post by gredawarha on 2012-07-08
In addition if i run the shutdown command from a terminal it shuts down nice and quickly. 

Also my partern has her own log in on the same machine yet does not have the same issue.

---

### Post by Mopar1973Man on 2012-07-08
Being a noob myself but I'm willing to take a crack at it. You might want to look and see what is running on your side and your partners side for apps. Maybe that will give you a idea to the rogue program that might be running causing the slow shut down. Might just find the zombie...

But do a search for system monitor it should pop up...

---

### Post by NikTh on 2012-07-09
Like [Mopar1973Man]("http://ubuntuforums.org/member.php?u=1574534") said , maybe its an app that hangs  properly shutdown or maybe its a graphical problem (cause you said that from terminal its ok). So  from your parnters account or just create a new user to see if its an app that fails to terminated.  
If its a graphical bug you can try to add a line in to /etc/default/halt. 
```
sudo nano /etc/default/halt
```and add this line [B]INIT_HALT = POWEROFF 
[/B]then click Ctrl+x and Y(es) and Enter to save .

---

### Post by gredawarha on 2012-07-09
Thank you both for the replies.  I tried to see if their was a particular program causing the issue but I couldn't find anything obvious.

I then added the line INIT_HALT = POWEROFF and so far that seems to have resolved the issue.

Many thanks

---

### Post by NikTh on 2012-07-09
> **gredawarha said:**
> 
I then added the line INIT_HALT = POWEROFF and so far that seems to have resolved the issue.

Do a further examination and if the problem solved , come back and **mark thread as solved** from** thread tools** . 
Thanks

---

### Post by gredawarha on 2012-07-09
I spoke to soon it is still taking 30+ seconds to shutdown.  Is there anything else I can do to try to resolve this?

---

### Post by NikTh on 2012-07-09
Try to add one more parm in another file. 
Give this command
```
gksudo gedit /etc/default/grub
``` and find the line ***GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"* **
and make it exactly like this 
[B][I]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force" 
[/I][/B]save the document and then run in terminal 
```
sudo update-grub
``` 
Hope this helps

---

### Post by matt_symes on 2012-07-09
Hi

What happens if you shutdown using dbus ?

```
dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop
```

Kind regards

---

### Post by gredawarha on 2012-07-10
Hi NikTh

Changing that line in GRUB did not solve the issue.

Hi matt_symes

Using that command shutdown the computer quickly, there was some text displayed in the terminal but it shutdown to quickly to take note of it.

---

### Post by NikTh on 2012-07-11
> **gredawarha said:**
> 

Hi matt_symes

Using that command shutdown the computer quickly, there was some text displayed in the terminal but it shutdown to quickly to take note of it.

So a workaround (not fix) can be a shortcut with this code. 
Make a script 
```
gedit shutdown.sh
``` 
copy-paste inside the code matt_symes gave you. Save . Then give execute rights
```
chmod a+x shutdown.sh
``` 
then go to keyboard - shortcuts and custom click (+)
At the command box give the path for shutdown.sh 
e.g ```
/home/yourusername/shutdown.sh
``` . Then click "disabled" and define a key. :)

---

### Post by matt_symes on 2012-07-11
Hi

Open a terminal and copy and paste

```
/usr/lib/indicator-session/gtk-logout-helper --shutdown
```

Do you see any error messages ? Does it shutdown quickly ?

Kind regards

---

### Post by gredawarha on 2012-07-14
Hi Matt

Ran the comand, the machine shuts down quickly but no messages.

---

### Post by gredawarha on 2012-07-15
This is very annoying, I may just have to reinstall which has it's own annoyances. :(

---

### Post by matt_symes on 2012-07-16
Hi

Create another user account  log into it and try to shutdown from that account. Is the shutdown slow ?

Kind regards

---

### Post by hypnot0ad on 2012-07-16
This is what I use and find it to work perfectly,

```
sudo shutdown -h now
```

How long have you had this problem?

---

### Post by techvish81 on 2012-07-18
if I shutdown while the network is connected, it takes double the time than the regular shutdown. so i disconnect network and shutdown.

---

### Post by gredawarha on 2012-07-19
I did a reinstal (keeping my home directory) and the problem still persists so presumably there is something in my home directory that is causing the issue.  I have my videos and photos backed up on an external hard drive and my documetns are on ubuntu one.

I will therefore delete my user account and home/darren directory and then reinstall see if that works.

---

### Post by matt_symes on 2012-07-19
Hi

If you have not reinstalled yet. From the terminal type
```

gnome-session-quit
```

Is that still slow ? Maybe the problem is with saving your sessions.

Kind regards

---

### Post by Wirephire on 2012-07-19
I faced similar behavior in earlier Ubuntu release. The fix I was using:
```
cd /etc/init.d
sudo wget http://www.jejik.com/files/examples/umountcifs
sudo chmod ugo+x umountcifs
sudo update-rc.d umountcifs stop 02 0 6 .
```

---

### Post by gredawarha on 2012-07-30
Gave up in the end and did a fresh install backing up my important stuff first.  Thank you though to those that tried to help me.

---

### Post by Diego Jp on 2012-09-24
> **matt_symes said:**
> Hi

If you have not reinstalled yet. From the terminal type
```

gnome-session-quit
```Is that still slow ? Maybe the problem is with saving your sessions.

Kind regards

I've got that problem :/
running these script it's still slow

---

### Post by daslinkard on 2012-09-24
Are you running NetworkManager?  If so there seems to be a fix [here]("http://www.madanalogy.com/2008/04/fix-slow-ubuntu-shutdown-with-cifs.html").

---

### Post by minja on 2012-12-03
I had a same problem with Ubuntu 12.04 studio. This worked!
Thanks!:KS

> **Wirephire said:**
> I faced similar behavior in earlier Ubuntu release. The fix I was using:
```
cd /etc/init.d
sudo wget http://www.jejik.com/files/examples/umountcifs
sudo chmod ugo+x umountcifs
sudo update-rc.d umountcifs stop 02 0 6 .
```

---

### Post by layolayo on 2013-08-20
I'm running a brand new Lenovo X1 Carbon with 13.04 64bit - and noticed a big difference between the shutdown speeds on this new laptop and my System76 Lemur. The Lemur is ultra fast sub 3 seconds, the Lenovo 5-10 seconds. I have TLP installed - [COLOR=#000000]TLP ([/COLOR][http://askubuntu.com/questions/28543.../285681#285681]("http://askubuntu.com/questions/285434/is-there-a-power-saving-application-similar-to-jupiter/285681#285681")[COLOR=#000000])

Running through several forums, it looks like it is the network settings that cause this delay (for me) and simply by setting the line in /etc/default/tlp

[/COLOR][COLOR=#000000][FONT=monospace][B]DEVICES_TO_DISABLE_ON_SHUTDOWN="bluetooth wifi"
[/B][/FONT][/COLOR][COLOR=#000000]
My laptop now shuts down in the same manner as my Lemur - nice :)

[/COLOR]

---

### Post by layolayo on 2013-08-27
Quick note on this - I'm not sure how or why yet, but this shutdown speed only works on battery... when plugged into a PSU it is back to the 6-10 secs...? maybe that SHUTDOWN is not the answer...

---

