---
title: "some help seting up mythtv"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by techno-mole on 2008-11-21
hello all.

i have recently purchased a pci tv card, the sort that lets you watch digital freeview tv etc, it also allows recording and time shifting.

i have it working perfectly in windows, but i want to be able to use it on kubuntu as well, how ever i have run into some problems, the first being that everytime i run mythtv (front end or setup, or anything mythtv for that matter) i get a message about not being a member of the mythtv group, the exact message is 

```
You must be a member of the "mythtv" group before starting any mythtv applications.
Would you like to automatically be added to the group?
(Note: sudo access required)
```

so i select yes and i get this message 

```
For the changes to take effect, your current login session will have to be restarted.  Save all work and then press OK to restart your session.
```

i then restart my session, and when i run the setup again it does exactly the same.

so basically im asking for help with this and any advice in actually setting up mythtv in kubuntu.

or would it be wiser to install mythbuntu ?

cheers in advance for any help.

---

### Post by sockedipocke on 2008-11-21
yo. did you check the mythtv site?
What kubuntu version?

---

### Post by techno-mole on 2008-11-21
i did check the mythtv site, and some other how to's, and they all seem to suggest that once ive restarted the session i should then be a member of the mythtv group.

only it just seems to be stuck in a kind of a loop, so im guessing that even though it says i should be a member it isnt actually adding me.

i am downloading mythbuntu, well why not, and i do remember reading on the myth site that it is possible to install a desktop on it, so i could install kde 4 if i choose to.

---

### Post by m_duck on 2008-11-21
Have you tried manually adding your username to the mythtv group in case the mythtv setup isn't doing it properly?

```
sudo usermod -a -G mythtv username
```

The above will add the user, "username" to the "mythtv" group.

---

### Post by bawilson2 on 2008-11-21
Not 100% sure but I think that once you get to that point that mythtv should be installed. Try checking out under the system menu to see if you have a Mythtv backend setup program installed now.

---

### Post by techno-mole on 2008-11-23
sorry it took so long to get back.

i got stuck at the section i mentioned in my original post, and even after manually adding my user name to the myth tv group it still comes up, when i click on anything myth tv related.

i did try mythbuntu, but had no luck, although it did seem to point to my card not being supported, but im not sure, or it might mean i need to compile a driver for it ?

the card is a kworld plus tv hybrid pci card (vs-dvb-t 210se) im going to check out linuxtv.org and the related sites, but from a quick look my card isnt in the list of ones that are known to work, at least i didnt see it.

---

### Post by mal on 2008-11-23
techno-mole,

I think you are on the right track by making sure that your tv card is recognised by Ubuntu before you try to sort out the mythtv group issues.  You could check the output from the following commands to see if your card is OK:

```
$ lspci
$ dmesg | grep -i tv
$ dmesg | grep -i dvb

```

If this indicates that your card is being recognised by the kernel, there are some tools in the package dvb-utils that can check the operation of your card.  Alternatively you could install Kaffeine.  This is a media player for KDE that can play programs from a tv card.  You might have to set up a channels.conf file for it.  If you get to this point and need some help check back with the forums.

Hope this helps,

Mal

---

### Post by techno-mole on 2008-11-24
cheers for the codes, i have run all 3 of them in terminal and this is the output - 

lspci gives me this (amongst other stuff - ```
01:05.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
```

this is the chip (i think) that is on my tv card.

dmesg | grep -i tv gives no output at all.

and the last code dmesg | grep -i dvb gives me ```
[   13.803921] saa7133[0]: subsystem: 17de:7250, board: KWorld DVB-T 210 [card=114,autodetected]
[   18.244612] DVB: registering new adapter (saa7133[0])
[   18.244617] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
[   22.980528] firmware: requesting dvb-fe-tda10046.fw

```

so im guessing my system does see the card, at least on some level, and its just a case of getting set up correctly to work, does it matter that the second set of code didnt give any output ?

cheers

---

### Post by mal on 2008-11-24
techno-mole,

Yes, it does seem that your card is being detected and, no, it probably doesn't matter that the second command returned nothing.  The dmesg command lists the messages that are created during the boot process and the grep command searches it for "tv" or "dvb" respectively.  As an alternative, you could use the following command:

```
$ dmesg | less

```

to display the full list of boot messages and then type "/dvb" to search for a line that mentions dvb and then have a look around to see if there are any other messages that might give some more clues about whether your card is being properly recognised.  (Type "q" to quit from this.)

If all seems well, I would suggest you try the Kaffeine application to see if you can watch tv.  This might actually meet your needs without even installing mythtv.

Alternatively, I think Totem can also be used to watch tv from a dvb card, but it might also need a channels.conf file to be created for your tv stations.

Regards,

Mal

---

### Post by techno-mole on 2008-11-24
me again.

well i am making progress, ive tried mythtv and its beyond me (if im honest) i also tried klear, which i nearly got working but it keeps giving me an error about a channels.conf file (which i have since added, but it still gives the error)

so i tried kaffeine, which works, well more or less, i did have to find the details of my nearest transmitter, which isnt in any of the lists, so after a fair bit of searching i found some one who has made the required transmitter file, i put this into the dvb-t section of the kaffeine file, and then did a scan and it picked up all the stations first time, so now i can watch tv (free view)

however i do need to do some tweaking as the picture quality is okay, but the picture isnt great, its clear, but evey now and then it just stops and the screen goes kind of pixely, ive attached a screenshot, from the dave channel (i thinks its a re-run of a top gear episode) but you can see what i mean but the picture.

i wonder if its possible to tweak the frequencies a bit ? and get a better reception ? the card is using the roof arial, and its running through a booster, and it doesnt suffer from the same when im on my windows system (dual booting)

cheers for the help by the way.

---

