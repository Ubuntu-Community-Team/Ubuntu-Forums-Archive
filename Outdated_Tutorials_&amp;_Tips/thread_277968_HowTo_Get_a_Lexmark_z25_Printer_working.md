---
title: "HowTo: Get a Lexmark z25 Printer working"
date: 2006-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by motstudios on 2006-10-15
NOTE: This script seems to not like Edgy. Because of this, I added a second script to remove the question it asks. It still may not work. I don't have a linux distro at this time to test it but will within a few weeks.

Greetings,

    This will hopefully be an easy to use howto to get a Lexmark z25 printer to work under Ubuntu, Kubuntu, Xubuntu. It works for me, it "should" work for others, if it doesn't and you know why, let me know. This supposedly will also work with Lexmark printers between z25 and z35 but I've only tested it on a z25.

NOTE: This script comes "as is" and there's no promise it will work. I made this script to automate the process of installing the driver for my printer (Lexmark z25) and it works for me. If there is an error in the script or if it doesn't work for your z25 printer on Ubuntu then let me know and I'll try to fix it.


Getting the Lexmark z25 Printer working:
1. Download this bash script (right click + save as): 
Dapper: See attached file
Edgy: See attached file

2. Open a terminal and issue the following commands:
sudo apt-get install alien
chmod u+x /pathtoscript/lexmark-z25-z35-VERSION.sh
cd /pathtoscript
sudo ./lexmark-z25-z35-VERSION.sh

3. Follow the prompts.

4. Once the script finishes, use your favorite printer setup program to setup the printer. On Ubuntu theres a printer setup program under System > Administration > Printing. On Xubuntu I believe you will have to install a printer configuration program. On Kubuntu I'm not sure what program is available.

NOTE: You may have to choose Lexmark z35 driver in the printer setup dialog even if you have a z25 printer. It will still work.

On Xubuntu you can use the following command to install gnome-cups-manager to setup the printer.
```
sudo apt-get install gnome-cups-manager
```
once it's installed you can use
```
gnome-cups-manager
```
to setup your printer.

That should be all you will have to do. If you want to see the steps the script takes, open the script with a text editor and have a look.

---

### Post by JulianLx on 2006-12-27
Hi,

I tried your script with my Lexmark Z25 already connected in my Ubuntu 6.10 with alien and RPM installed.
I downloaded the file to Desktop and typeed

julian@la-caja:~/Desktop$ sudo chmod u+x lexmark-z25-z35.sh
julian@la-caja:~/Desktop$ sudo ./lexmark-z25-z35.sh

The outcome was

Script Starting.

Greetings root! This is a simple script to
take the Lexmark z25 drivers and convert them
to a useful format and install them so that
your z25 printer will work under Linux.
You agree this script is just to try to make
things easier and comes with no promise.
However it SHOULD work. Email any errors to
[email]motstudios@gmail.com[/email]

Are you ready (yes or no)? yes
./lexmark-z25-z35.sh: 37: [[: not found
Too bad, exiting.

Do you have any idea what to do?
Do you know about any guideline to try manually?

Happy New Year,

Julian

---

### Post by JulianLx on 2006-12-27
I modified the scritp and got it working.
Now the Z35 does not appears st the list of printer´s drivers.

J

---

### Post by vr04 on 2006-12-29
JulianLx,

The driver doesn't seem to like GNOME. If you follow this installation process in Kubuntu (with KDE) the KDE Print Manager picks up the driver as "Z35" and it works fine. And yes, that's Kubuntu 6.10 (Edgy Eft).

This kind of forced me to try out Kubuntu and KDE in general, and I started liking it. So maybe it's not such a bad thing after all?  :KS

---

### Post by motstudios on 2006-12-31
Well it seems this script doesn't like edgy so i added one just for edgy. it should work but it will not ask any questions.

another note, the drivers are done by lexmark so if the DRIVER doesnt work, there is nothing i can do as i dont make the driver, i just take what lexmark provides and turn it into a usable format that can be used, lol.

thank you for the bug report via email, it let me know this doesnt like Edgy and i will be working on getting it updated to work with edgy.

---

### Post by vr04 on 2007-01-01
motstudios,

Unfortunately, it still won't work in Edgy/GNOME.

Kubuntu works fine, though, as previously mentioned. :KS :D

---

### Post by motstudios on 2007-01-01
hmm, well ill have to look into it. so far i noticed i can install the driver with gnome-cups-manager but i havent found a way to get it installed and working via any easy method. so ill post here anything i find when i find it.

---

### Post by Efwis on 2007-01-03
hiya mostudios,

I have a suggestion for your script.

Most people looking for this printer setup are possibly still in the inital installation phase, One thing I have noticed is that alien is not installed by default, you might want to add a line to download and install that from the repos before running the rest of this script.

without adding that line, this script is unusable for a new Ubuntu user with the lexmark printer.

also I noticed that these steps are not being done, you might want to put these in the script also, unless your doing some magic that I don't see.

```
# cd /usr/lib

# ln -s liblexz35core.so.0.0.0 liblexz35core.so.0

# ln -s liblexz35printer.so.0.0.0 liblexz35printer.so.0

# ln -s liblexz35printjob.so.0.0.0 liblexz35printjob.so.0 
```

I have never been able to get my Lexmark Z25 printer working properly without these lines being used

---

### Post by vr04 on 2007-01-04
> **motstudios said:**
> hmm, well ill have to look into it. so far i noticed i can install the driver with gnome-cups-manager but i havent found a way to get it installed and working via any easy method. so ill post here anything i find when i find it.

How do you install it through gnome-cups? What are the steps to take?

---

### Post by djsim on 2007-02-03
I tried downloading [http://mark.22kb.com/dl/lexmark-z25-z35-edgy.sh](http://mark.22kb.com/dl/lexmark-z25-z35-edgy.sh) but it is a HTML web page, not a bash script. I think the site its on has been either removed or replaced. I can't seem to find it anywhere else.

I am struggling to get my Lexmark Z25 to work. Does anyone else have the script?

---

### Post by motstudios on 2007-02-04
yes the website is down because the domain 22kb.com expired and was not renewed. since i do not own it i cant renew it. also my host has yet to reconfigure my account to use another domain.

because of this im gonna supply the scripts source in the first post after i submit this

---

### Post by redsoxfan3515 on 2010-05-19
I am having a lot of trouble installing my lexmark z25...i am a VERY new user of Ubuntu linux...if anyone can help me, PLEASE DO!!!!:) I would greatly appreciate it...if you know anything that will help me, you can reach me at: [email]redsoxfan3515@aol.com[/email] (or same thing just at Yahoo.com). I appreciate any help i can get, and im hoping i dont need to buy a new printer:(
Matt

---

