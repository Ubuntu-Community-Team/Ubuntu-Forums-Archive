---
title: "Total new to Linux!! No sound"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by Brutally on 2008-11-26
This my first install of any linux.
I've not heard a sound from this at all what could be the basic error? How would i rectify that too please?
Spec AMD 64 linux 8.04.
Creative X-Fi Fatal1ty sound card there is a linux driver for this but all it does is download to my desktop. How do you install?
Sorry but totally new to this - the instructions in there readme file

SAYS
In terminal,


1) Goto source directory

2) Execute make command as root

   make

   make install


ok i go to source then type make ----- etc but it dont work.
how do i make something root?
Cheers in advance

---

### Post by Peter09 on 2008-11-26
Can you post the output of the command below, which you will need to run in a terminal

```
lshw -C sound
```


Terminal Basics
To make life easier when using the terminal:
1. The up and down arrow keys allow you to move through the command history of the terminal. So if you make a mistake in a command the up arrow will return to it, you can the edit the command using the left/right arrows and the del/backspace keys. Hit enter when you are ready to re-issue.

2. Hitting the TAB key when you are in the middle of typing a command makes the terminal attempt to autocomplete the command/filename that you are typing.  Hitting the TAB key twice displays all the options available for autocompletion.

---

### Post by Brutally on 2008-11-26
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0
  *-multimedia UNCLAIMED
       description: Multimedia audio controller
       product: SB X-Fi
       vendor: Creative Labs
       physical id: 7
       bus info: pci@0000:01:07.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=5 mingnt=4

---

### Post by Peter09 on 2008-11-26
It looks like you have two audio devices, is you onboard device enabled as well as a PCI card?

---

### Post by Brutally on 2008-11-26
Doh ive never seen tried the onboard lol forgot i even had it.
I know the proper soundcard never made a sound since the install.

---

### Post by Sealbhach on 2008-11-26
It wants you to compile the driver. Not really difficult to do, don't worry. First of all, install the compiling tools:

```
sudo apt-get install build-essential
```

Ok, this file that downloads, copy it to your /home directory. This is the directory you see in Nautilus which is named after your username.

Then extract it, you can right click and select "extract here".

Go into the new folder that this creates. You will have to do this by opening a terminal and typing

```
ls
```

This will list all the folders and you should see the name of the new folder.

then

```
cd newfolder
```

Where you substitute "newfolder" with the actual name of the folder.

Now you are in the source directory.

Change to root user:

```
sudo su
```

and enter your password.

Type:

```
./configure
```

This might throw up some error messages, if so report them here. If it all goes smoothly, type:

Type:
```

make
```

After that's done type:

```
make install
```

Which should install the driver for you.


.

---

### Post by Brutally on 2008-11-26
no not getting nothing from that either.
Not just something on mute or something?

---

### Post by Brutally on 2008-11-26
Very helpful this forum :)

did this command compiling tool. It said do you wish to download said yes then it d/l but to where no idea so cant copy to /home :(

---

### Post by Brutally on 2008-11-26
is there not just a mute somewhere that is active?

---

### Post by Peter09 on 2008-11-26
your audio controls are available by right clicking on the speaker icon on the task bar.

---

### Post by ibizatunes on 2008-11-26
If you are using 2 sounds cards, the onboard one, you could turn off in the BIOS and then run with your PCI sound card

---

### Post by Sealbhach on 2008-11-26
> **Brutally said:**
> Very helpful this forum :)

did this command compiling tool. It said do you wish to download said yes then it d/l but to where no idea so cant copy to /home :(

I thought the driver downloaded to your desktop? When you install build essential you don't have to worry where it downloads to. It's the driver you want to compile, I'm assuming it downloaded to your desktop.


.

---

