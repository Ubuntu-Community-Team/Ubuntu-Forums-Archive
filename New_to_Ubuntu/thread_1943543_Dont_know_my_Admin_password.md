---
title: "Dont know my Admin password?"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by crazymac680 on 2012-03-19
Im a total newbee to this. Installed Ubuntu 11.10 on my netbook and cant get my printer working. I've downloaded the file from the lexmark site. Extracted it and then opened the file by double clicking it and then followed the instructions. It then asked me for the administrative password. I entered the password I need at bootup and to install and uninstall but it says it's incorrect. I'm now lost and have no idea how to work the terminal thing? 
Thanks for any help you can give
Dan

---

### Post by wojox on 2012-03-19
That's a bug. I've seen it in Ubuntu and Fedora. Where is the file now, on your Desktop or Downloads?

---

### Post by crazymac680 on 2012-03-19
The file is in downloads. I tried opening with terminal too now but that just opens the installation wizard thing too. Once I click to install it says "this operation requires root(adminitrative) password" My log in password again says its incorrect.
Thanks Daniel

---

### Post by wojox on 2012-03-19
Try this Ctrl + Alt + T will open a terminal. Then copy and paste:

```
cd $HOME/Downloads
la -al
sudo lexmark
```

Finish the "sudo lexmark" with the name of the file you list.

---

### Post by crazymac680 on 2012-03-19
Thanks
I would describe this as having a nightmare!
I copied and pasted what you gave me into my terminal with the intention to add the rest of the name of the file afterward but it just seemed to put a lot more in than I expected.
If I am to just write it in. How do I add the new line?

---

### Post by wojox on 2012-03-19
Sorry they are three seperate commands

```
cd $HOME/Downloads
```
```
la -al
```
```
sudo lexmark
```

---

### Post by crazymac680 on 2012-03-19
Ok what I did was copied your command into a text doc. Then added the full name of the file after sudo. Dont think anything happened. I've tried to copy my results from the terminal but its not working for some reason.
Thanks again

---

### Post by wojox on 2012-03-19
Post back the second command for me please.

---

### Post by crazymac680 on 2012-03-19
I've been pressing enter after each command. Still cant copy out of terminal to show you my results? Its not opening the installer though.

---

### Post by crazymac680 on 2012-03-19
sudo lexmark-inkjet-legacy-wJRE-1.0-1.i386.deb.sh

---

### Post by jerome1232 on 2012-03-19
> **crazymac680 said:**
> I've been pressing enter after each command. Still cant copy out of terminal to show you my results? Its not opening the installer though.

ctrl+alt+c to copy from a terminal (does lexmark really still have this bug? If I recall correctly the lexmark installer requires an unlocked root account, perhaps you'll have to unlock the root account temporarily to solve this, I could be mistaken though)

At anyrate what is the specific model of your printer? Some lexmarks are no better than paper weights under linux.

---

### Post by wojox on 2012-03-19
Okay I just downloaded the package. You should see a [COLOR="Red"]lexmark-*.deb.sh[/COLOR]

Something along those lines. Install with
```
sudo ./lexmark-*.deb.sh
```

---

### Post by crazymac680 on 2012-03-19
Thanks for the help. I'm giving up for the night. Been trying for 2 nights to get this printer working. This Ubuntu will be getting the heave ho if my printer doesn't work.
Thanks again
Dan

---

### Post by crazymac680 on 2012-03-19
All I'm getting is "(sudo) password for daniel" and nothing I type appears
Off to bed. Thanks very much.
Dan

---

### Post by wojox on 2012-03-19
> **crazymac680 said:**
> All I'm getting is "(sudo) password for daniel" and nothing I type appears
Off to bed. Thanks very much.
Dan

echo is off by default. Type your password in, it's fine.

---

### Post by critin on 2012-03-19
> All I'm getting is "(sudo) password for daniel" and nothing I type appears

You will not see the password in the terminal, but it's there.

---

### Post by crazymac680 on 2012-03-20
You guys are amazing! Thanks so much. I just needed to enter my password(Which was invisible so I thought it wasn't going in). 
The commands that worked were
cd $HOME/Downloads
la -al
sudo ./lexmark-*.deb.sh

It then asked my password and it all installed.
Thanks again
Daniel

---

