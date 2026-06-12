---
title: "Eject toggle key"
date: 2005-11-21
forum: Outdated Tutorials &amp; Tips
---

### Post by shadow on 2005-11-21
(Taken from: [http://gav.brokentrain.net/blog/](http://gav.brokentrain.net/blog/))

While I've always found the eject keyboard shortcut useful in gnome, one thing that has annoyed me is the inability to toggle between two states. (i.e. close it if its open, and vice versa.)

Fortunately, since eject 2.1.0 this ability as been added as a new -T option. (See changelog [here]("http://ca.geocities.com/jefftranter@rogers.com/eject.html").)

The following basic steps are needed to replace your old 'eject' with the new one:-
[LIST]
[*] Uninstall the old version of eject
> sudo apt-get remove eject
[*] Install the package provided [here]("http://gav.brokentrain.net/upload/eject-2.1.3_i386.deb") (Note: this is *required*, because despite 2.1.3's release on the above site the package seems to be unfortunately broken - which I've fixed by replacing a few missing files.)
> sudo dpkg -i [eject-2.1.3_i386.deb]("http://gav.brokentrain.net/upload/eject-2.1.3_i386.deb")
[*] Success!
Can be launched as usual using the *eject -T* flag which will now toggle your cdrom between states.
[/LIST]

**Further steps (adding to keyboard shortcut.)**

This was a bit more tricky, since I found no way to edit gnomes **&#8220;System -> Preferences -> Keyboard Shortcuts&#8221;** list and had to be done via Configuration Edtior (gconf) in **"Applications -> System Tools."**

It's divided into two main steps as follows:-

**Step 1**

[LIST]
[*] Decide on the key you want to bind.
This might sound obvious, but on my Apple keyboard I wanted the specific to far right key labeled 'eject' to do this. This key is a multimedia one and had to be mapped specifically in order for this to work. (If you're just using an ordinary key, skip to step 2.)

[*] Determine the multimedia keycode for this using **'xev'**.
Launch the command **'xev'** in a terminal and hit the key a few times noting the **'keycode'** parameter when the string is output to console. e.g:
> 
KeyRelease event, serial 29, synthetic NO, window 0x3200001,
root 0x76, subw 0x0, time 5996809, (190,33), root:(200,130),
state 0x0, **keycode 204** (keysym 0xffc6, F9), same_screen YES,
XLookupString gives 0 bytes:

[*] Create an **~/.xmodmap** or **/etc/xmodmap** mapping this key.
Open a text editor and insert the line:
> keycode **204** = XF86VendorHome (where **204** is your key as above.)
[*] Restart X. (Ctrl-alt-backspace.)
[/LIST]

**Step 2**

[LIST]
[*] Open **&#8220;Applications -> System Tools -> Configuration Edtior&#8221;**.
[*] Expand the **&#8220;/apps/metacity/keybinding_commands/&#8221;** section.
[*] For the key name *&#8220;command_1&#8221;* insert the value *&#8220;eject -T&#8221;*
[*] Switch to the **&#8220;/apps/metacity/global_keybindings/&#8221;** section.
[*] For the key name *&#8220;run_command_1&#8221;* place the desired keyboard key sequence, (or the xmodmap mapping if you are using some special multimedia key and did the above.) i.e. *'XF86VendorHome'*
[/LIST]

**Success!**

All going well, the key you have set should now be toggling your cdrom.

---

### Post by Saiboogu on 2005-11-22
Hey, no replies? I don't have an eject key on my keyboard, but I'm sure I'd be loving this if I did. 

I still curse myself everytime I reach under my desk and press eject, only to remember I need to eject it on my desktop! ;)

---

### Post by shadow on 2005-11-22
[QUOTE=Saiboogu]Hey, no replies? I don't have an eject key on my keyboard, but I'm sure I'd be loving this if I did. 

I still curse myself everytime I reach under my desk and press eject, only to remember I need to eject it on my desktop! ;)[/QUOTE]

Hahaha, thing is you don't really need an eject keyboard as such - anything will do.

ie Ctrl + e or something. :)

---

### Post by matthewv on 2005-11-23
I set my comp up with Ctrl + Alt + e and it works great.
Thanx

---

### Post by tanari on 2005-11-23
This was of the main features I wanted :)
I put it to F12

---

### Post by autocrosser on 2005-11-23
I just want to do this with my Apple keyboard & Apple G4---Do you know if there is a PPC eject with the same version #????

---

### Post by shadow on 2005-11-23
[QUOTE=autocrosser]I just want to do this with my Apple keyboard & Apple G4---Do you know if there is a PPC eject with the same version #????[/QUOTE]

Hmm, I'm not entirely sure. The source is available over at [http://ca.geocities.com/jefftranter@rogers.com/eject.html](http://ca.geocities.com/jefftranter@rogers.com/eject.html) you could always try compiling it. Note of warning though, there are a few missing files when you try to compile it and configure will fail.

The way round this was to find another previous source (e.g. [http://www.pobox.com/~tranter/eject-2.1.0.tar.gz](http://www.pobox.com/~tranter/eject-2.1.0.tar.gz)) and copy the missing ones from that.

Good luck if you try it though, but I'm not certain about this os X stuff or whatever. :)

Edit: As the changelog says above, 2.1.0 was where the main option '-T' was added, and from here: [http://www.redhat.com/archives/fedora-announce-list/2005-August/msg00110.html](http://www.redhat.com/archives/fedora-announce-list/2005-August/msg00110.html) I see some mention of a 'eject-2.1.1-0.fc4.1.ppc.rpm' for Fedora, so presumably 2.1.1 can be built successfully anyway.

---

### Post by christooss on 2005-11-23
Hm when cdrom is open eject -T doesn't work. It works with closed cdrom.

BTW eject -t works. Wierd

---

### Post by autocrosser on 2005-11-24
Thanks for the info--BTW--I'm using Ubuntu PPC with a Dual1.25G--Just want to be able to do in Linux what I can do in OSX---The <Eject> opens & closes the Main DVD--<Option><Eject> opens the Slave DVD-ROM:smile:

Just used Alien to install the RPM--will post my results

11/24--Set-up as per the instructions--replaced the i386.rpm with eject-2.1.1-0.fc4.1.ppc.rpm--alien installed just fine--have the same (I guess) keyboard (Clear with Black keys)--keycode 204--<Eject> now opens & closes my main DVD--I just need to find a way to do my DVD-ROM (slave) now---

---

### Post by shadow on 2005-11-25
[QUOTE=autocrosser]
11/24--Set-up as per the instructions--replaced the i386.rpm with eject-2.1.1-0.fc4.1.ppc.rpm--alien installed just fine--have the same (I guess) keyboard (Clear with Black keys)--keycode 204--<Eject> now opens & closes my main DVD--I just need to find a way to do my DVD-ROM (slave) now---[/QUOTE]

Hmm, as far as I know you can give eject a second parameter of the device you're trying to eject. ie I can eject my dvdrom: eject -T /dev/hdc and say, my ipod with eject /dev/sda2.

Find out the device name of your slave and try passing the name to eject.

eg eject -T /dev/hdd (maybe?) I'm not sure cause never had two cdroms :)

---

### Post by autocrosser on 2005-11-25
You are right--eject -T /dev/hdd toggles the DVD-ROM & eject -T /dev/scd0 toggles my external firewire CD burner, so I mapped f15 & f14 to these commands=D> Thanks!!!

---

### Post by teaker1s on 2005-11-25
right click on top desktop bar 'add to panel' and add disk mounter which allows easy mount/unmount and eject-note the eject function not as forceful as gnome shortcut for some reason

---

### Post by autocrosser on 2005-11-25
I've had disc mounter in one panel since Hoary--I just wanted a one-key solution to eject discs:smile:

---

### Post by Brian McConnell on 2005-12-13
well, I did everything described in the initial post, but still no joy :( 
I have Apple keyboard on PPC, so I downloaded the "newer" eject.rpm from Fedora and used alien to convert to .deb, just like a previous poster did, still no joy :(

Any other suggestions for making my eject key (keycode 204) do the toggle?

Help!

---

### Post by penzo on 2005-12-13
I find that command "sudo eject -p" is much better to use;)
It uses /proc/mounts to eject devices instead /etc/mtab

---

### Post by nolodude on 2005-12-31
Thanks, this is handy.

BTW a small typo in "sudo dpkg -i eject-2.1.3_i**836**.deb".

---

### Post by atlas95 on 2006-01-01
I have upgrade my "eject" to this version but now i have a big problem, i can't find how to eject a cd mounted :s, i must cli on the desktop icon and do eject...
before juste press my key binded on my keyboard worked :s..
thanks , sorry for my english

---

### Post by limit223 on 2006-01-01
How about KDE "intrusion"  ? :p 

Control Center- Regional &Accessibility - Input Action - Menu Edito entries - New Action: General-Action Name: Eject, Keyboard Shortcut: press any key standard/non-standard/combination, Command/URL Settings sudo eject -p
Apply.

---

### Post by shadow on 2006-01-09
[QUOTE=Brian McConnell]well, I did everything described in the initial post, but still no joy :( 
I have Apple keyboard on PPC, so I downloaded the "newer" eject.rpm from Fedora and used alien to convert to .deb, just like a previous poster did, still no joy :(

Any other suggestions for making my eject key (keycode 204) do the toggle?

Help![/QUOTE]


Hmm, could you tell me what the output of 'eject -T' gives at your command line?

[QUOTE=nolodude]
Thanks, this is handy.

BTW a small typo in "sudo dpkg -i eject-2.1.3_i836.deb".
[/QUOTE]

Cheers for the tip :)

[QUOTE=atlas95]
I have upgrade my "eject" to this version but now i have a big problem, i can't find how to eject a cd mounted :s, i must cli on the desktop icon and do eject...
before juste press my key binded on my keyboard worked :s..
thanks , sorry for my english
[/QUOTE]

Strange, are you sure you don't have two versions of eject installed? A simple 'whereis eject' will tell you, and if not maybe try passing it the -p option to see if that works out.

---

### Post by Brian McConnell on 2006-01-10
[QUOTE=shadow]Hmm, could you tell me what the output of 'eject -T' gives at your command line?[/QUOTE]
that's the thing, from the command line, eject -T works just fine. It just seems that the shortcut does not work.... I know I followed the instruction fine, but any more help would be cool.....

---

### Post by shadow on 2006-01-13
[QUOTE=Brian McConnell]that's the thing, from the command line, eject -T works just fine. It just seems that the shortcut does not work.... I know I followed the instruction fine, but any more help would be cool.....[/QUOTE]

Hmmm, couple of things to try which I've missed in the initial post:
[LIST]
[*] Try copying /etc/xmodmap to ~/.xmodmap instead if you've got things setup like that.
[*] After you've done that type xmodmap ~/.xmodmap at console.
[*] Verify the following: [http://gav.brokentrain.net/upload/gconf-keybinding_comands.png](http://gav.brokentrain.net/upload/gconf-keybinding_comands.png) and [http://gav.brokentrain.net/upload/gconf-global_keybindings.png](http://gav.brokentrain.net/upload/gconf-global_keybindings.png)
[*] Log off/back in, it should hopefully ask you to "load" the .xmodmap file.
[/LIST]

Let me know if this helps.

---

