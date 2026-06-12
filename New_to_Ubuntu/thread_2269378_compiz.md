---
title: "compiz"
date: 2015-03-15
forum: New to Ubuntu
---

### Post by Ron_Callison on 2015-03-15
In trying to solve a freeze problem with a Lenova Thinkpad T61 I removed COMPIZ.  Now when I boot all of my shortcuts along the left side of the screen are gone and the strip at the top is gone.  I can't get to the software center to re-install COMPIZ. How can I get to the software center please?  Help!

---

### Post by v3.xx on 2015-03-15
Compiz is part of the Unity and cannot be removed.  Can you get to terminal (Ctrl+Alt+T) or console (Ctrl+alt+F2).
```
sudo apt-get install compiz
```

---

### Post by Ron_Callison on 2015-03-15
Control Alt T does nothing.  Rats!

---

### Post by Ron_Callison on 2015-03-15
I got to the council.  I can't remember my login!

---

### Post by ajgreeny on 2015-03-15
You can boot to recovery from grub and set a new password if you can not remember yours.

How have you been updating and installing applications if you can't remember your login and password?

See [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) to enable you to get back working, and while in the command line of recovery mode you can run [B]apt-get install compiz.
[/B]Note no sudo needed as you are already running as root in recovery mode.

---

### Post by grahammechanical on 2015-03-15
Do you get a Grub boot menu? If so, and you are using Ubuntu 14.04 the select Advanced options for Ubuntu. Then select Recovery mode. Then Select Network. Then select Root. Then run the command to install compiz. Then type exit and when back at the recovery menu select Resume and see if you can now get to a working desktop.

Regards.

---

### Post by deadflowr on 2015-03-15
> **v3.xx said:**
> Compiz is part of the Unity and cannot be removed.  Can you get to terminal (Ctrl+Alt+T) or console (Ctrl+alt+F2).
```
sudo apt-get install compiz
```

The OP would need to reinstall the whole shebang:
```
sudo apt-get install ubuntu-desktop
```
Removing compiz removes unity, and ubuntu-desktop.
Reinstalling only compiz would do just that, only reinstall compiz.
By reinstalling the ubuntu-desktop meta-package, the OP will/should get all the packages that where lost.

---

### Post by Ron_Callison on 2015-03-15
When I type <sudo apt-get install [COLOR=#000000]ubuntu-desktop meta-package> I get "E: Unable to locate package meta-package"[/COLOR]

---

### Post by deadflowr on 2015-03-15
> **Ron_Callison said:**
> When I type <sudo apt-get install [COLOR=#000000]ubuntu-desktop meta-package> I get "E: Unable to locate package meta-package"[/COLOR]

Do the command I posted in the CODE box, not what was written after.
There is no such thing as meta-package,
The ubuntu-desktop package is a meta-package, but that is not the name.

---

### Post by Ron_Callison on 2015-03-15
OK, I did that and no change.

---

### Post by deadflowr on 2015-03-15
> **Ron_Callison said:**
> OK, I did that and no change.
What was the output for the command in the terminal?

---

### Post by Ron_Callison on 2015-03-15
When you say "re-install the whole shebang" do you mean re-install Ubuntu from the beginning from a CD?

"Ubuntu desktop is already the newest version."

---

### Post by v3.xx on 2015-03-15
> **deadflowr said:**
> 
Removing compiz removes unity, and ubuntu-desktop.
Reinstalling only compiz would do just that, only reinstall compiz.
By reinstalling the ubuntu-desktop meta-package, the OP will/should get all the packages that where lost.
Yep, should of thought of that :)

Deadflowr is asking to run the command
```
sudo apt-get install ubuntu-desktop
```
And post the output (in code tags).

[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

---

### Post by v3.xx on 2015-03-15
```
sudo dpkg --configure -a && sudo apt-get -f install
```
Will that give any errors?

---

### Post by deadflowr on 2015-03-15
Before we go further, which version of Ubuntu.
12.04, 14.04, or 14.10.

knowing which version will help from giving you the wrong solutions.

---

### Post by Ron_Callison on 2015-03-15
> **v3.xx said:**
> ```
sudo dpkg --configure -a && sudo apt-get -f install
```
Will that give any errors?


no errors

---

### Post by Ron_Callison on 2015-03-15
> **deadflowr said:**
> Before we go further, which version of Ubuntu.
12.04, 14.04, or 14.10.

knowing which version will help from giving you the wrong solutions.


14.10

---

### Post by mc4man on 2015-03-15
> **Ron_Callison said:**
> In trying to solve a freeze problem with a Lenova Thinkpad T61 I removed COMPIZ.  Now when I boot all of my shortcuts along the left side of the screen are gone and the strip at the top is gone.  I can't get to the software center to re-install COMPIZ. How can I get to the software center please?  Help!
If  like everyone one is assuming you removed the compiz package then only 3 packages would have been removed - compiz, unity, ubuntu-desktop. However *everything*  you've posted here is at odds with that. So maybe describe how you actually " removed COMPIZ"

Otherwise please install ccsm & then open it in a terminal from your desktop, ie. logged in.
If when you actually log in you have a blank desktop then - 
r. click > New Folder > then  open that folder, click on  Computer in sidebar  > /usr/share/applications/ & d. click on the Terminal file.
```
sudo apt-get install compizconfig-settings-manager
```
then ```
ccsm
```
Please post what is show in the terminal from opening ccsm, should be 4  lines, most interested in the 3rd line about Profile.
Ex. here - 
> $ ccsm
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
Loading icons...



---

### Post by Ron_Callison on 2015-03-15
I removed compiz by going to the software center and searching compiz.  When it came up I hit "remove".  Before it removed it warned me that something else would be removed also and I didn't know what it was but proceeded anyway.

I typed the code you suggested but the lines I got back are nothing like you show.  It's too much to show you but the word "python" is repeated several times.

---

### Post by deadflowr on 2015-03-16
> **Ron_Callison said:**
> I removed compiz by going to the software center and searching compiz.  When it came up I hit "remove".  Before it removed it warned me that something else would be removed also and I didn't know what it was but proceeded anyway.

I typed the code you suggested but the lines I got back are nothing like you show.  It's too much to show you but the word "python" is repeated several times.

That *feels* like you ran the ccsm command from the ctrl+alt+F1 console.
Does that sound right?

---

### Post by CantankRus on 2015-03-16
Have you considered just reinstalling from scratch because you appear to have 
done more than just removing compiz if you are getting numerous python errors
or
provide better info on the errors you are getting.

---

### Post by Ron_Callison on 2015-03-16
> **deadflowr said:**
> That *feels* like you ran the ccsm command from the ctrl+alt+F1 console.
Does that sound right?

Yes, from the ctrl+alt+F1 console

---

### Post by Ron_Callison on 2015-03-16
> **CantankRus said:**
> Have you considered just reinstalling from scratch because you appear to have 
done more than just removing compiz if you are getting numerous python errors
or
provide better info on the errors you are getting.

Re-installing from scratch is exactly what I'll do if I can't figure this out soon.

---

### Post by CantankRus on 2015-03-16
Are you able to open a terminal as mc4man described in post #18, after logging in normally to your desktop.
ccsm is a graphical application and won't run from a tty console.

---

### Post by Ron_Callison on 2015-03-16
> **CantankRus said:**
> Are you able to open a terminal as mc4man described in post #18.
ccsm is a graphical application and won't run from a tty console.

Ctrl+alt+T does nothing.  Any ideas?

---

### Post by Ron_Callison on 2015-03-16
> **Ron_Callison said:**
> Ctrl+alt+T does nothing.  Any ideas?

Can I get to the terminal from the console?

---

### Post by CantankRus on 2015-03-16
Try this.
Log in normally to your desktop.
Then ctrl+alt+F1 and login to tty1 
In tty1 run these two commands....
```
cp /usr/share/applications/gnome-terminal.desktop ~/Desktop
chmod +x ~/Desktop/gnome-terminal.desktop
```

Then switch back to your desktop with ctrl+alt+F7 (may be F8)
Do you now have a clickable terminal icon on your desktop?

---

### Post by Ron_Callison on 2015-03-16
> **CantankRus said:**
> Try this.
Log in normally to your desktop.
Then ctrl+alt+F1 and login to tty1 
In tty1 run these two commands....
```
cp /usr/share/applications/gnome-terminal.desktop ~/Desktop
chmod +x ~/Desktop/gnome-terminal.desktop
```

Then switch back to you desktop with ctrl+alt+F7 (may be F8)
Do you now have a clickable terminal icon on your desktop?

Please bare with me here.  After ctrl+alt+F1 how do I login in tty1?

---

### Post by CantankRus on 2015-03-16
> **Ron_Callison said:**
> Please bare with me here.  After ctrl+alt+F1 how do I login in tty1?
TTY1 is just the name of the console at ctrl+alt+F1
Type your username and press "Enter".
You will prompted for your password.
Type in your password...the screen will remain blank as you type....press "Enter".

---

### Post by Ron_Callison on 2015-03-16
> **mc4man said:**
> If  like everyone one is assuming you removed the compiz package then only 3 packages would have been removed - compiz, unity, ubuntu-desktop. However *everything*  you've posted here is at odds with that. So maybe describe how you actually " removed COMPIZ"

Otherwise please install ccsm & then open it in a terminal from your desktop, ie. logged in.
If when you actually log in you have a blank desktop then - 
r. click > New Folder > then  open that folder, click on  Computer in sidebar  > /usr/share/applications/ & d. click on the Terminal file.
```
sudo apt-get install compizconfig-settings-manager
```
then ```
ccsm
```
Please post what is show in the terminal from opening ccsm, should be 4  lines, most interested in the 3rd line about Profile.
Ex. here -

OK, I did this and got to the terminal and the results are just like you show in the code box.

---

### Post by Ron_Callison on 2015-03-16
> **CantankRus said:**
> TTY1 is just the name of the console at ctrl+alt+F1
Type your username and press "Enter".
You will prompted for your password.
Type in your password...the screen will remain blank as you type....press "Enter".

I have to go to work.  May I get back to you later please?

---

### Post by CantankRus on 2015-03-16
> **Ron_Callison said:**
> I have to go to work.  May I get back to you later please?
No problem...someone will answer.

---

### Post by CantankRus on 2015-03-16
Okay, it appears you just removed the compiz metapackage which will in turn remove unity as a dependency.

From the terminal icon on your desktop run...
```
sudo apt-get install unity
```

Then set compiz/unity back to default settings and reload (may take 30 secs or more to reload).....
```
dconf reset -f /org/compiz/ && setsid unity
```

If it fails to reload properly run this command to logout to the greeter ...
```
kill -9 -1
```
...then log back in

---

### Post by Ron_Callison on 2015-03-16
Yeah!!!!  Fixed!!!!  Thank you CantankRus, mc4man, deadflowr and others who gave it a shot.  The last post from CantankRus got the desktop back after I got to the terminal with mc4man's help.  Thanks to the Ubuntu community!

---

