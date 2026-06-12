---
title: "HOWTO: Spice up your login shells with something more interesting"
date: 2005-06-05
forum: Outdated Tutorials &amp; Tips
---

### Post by techmonkey on 2005-06-05
First of all let me start off by saying that I'm not entirely sure that this deserves to be in here at all, but it is a customisation tip that you can use. Also this is my first Howto, so let's hope I didn't screw up. :)

What this howto will tell you how to replace is the rather ugly legal disclaimer that Ubuntu (and only Ubuntu, AFAIK) shows you on its terminals (CTRL+ALT+F1:F6) when you login to them; the dull, drab '"Hoary Hedgehog" on {hostname}' text at the login prompt, and a way to spice up your actual shell sessions.

You'll want to backup these files in case you don't like the effects of this howto:

[list]
[*] /etc/issue
[*] /etc/motd
[*] ~/.bashrc
[/list]

_**Optional Step 0: Remove startup entries**_

In Ubuntu you will be using GDM to automatically startup a graphical desktop, so let's get rid of that, to give us a terminal prompt when we boot into Ubuntu instead of GDM: (this is only optional of course. You may actually prefer to keep your Ubuntu jumping straight to the graphical Ubuntu GDM screen, in which case do NOT run this command. Really.**[1]**)

```
sudo update-rc.d -f gdm remove
*(Enter password)*
```

Now when you reboot your Ubuntu machine, you will get a rather dull, it has to be said, text console as opposed to a GDM login screen. To start Gnome now, all you need to do is type 'startx' to start the X graphical server which GDM starts and uses.

Alternatively, you may type the following to go to GDM and see a graphical login screen. This has the added benefit of not loading Gnome up *at the same time* as the X graphical server, so you may notice a slight difference in how long it takes for Gnome to 'splash' up and settle down, on slower machines. The other benefit of course is that 'startx' just goes straight into your default X session, most likely Gnome. Starting GDM gives you the chance to login to an alternative X session that you may have the option to use, such as fluxbox, or Enlightenment.

```
sudo gdm
*(Enter password if prompted)*
```

**Note:** You can only run gdm as root, hence the sudo.

_**Step 1: Change your issue file**_

The /etc/issue file is what your terminal system (getty, in the case of Ubuntu Hoary) will display just before the login prompt. It's setup by default to say 'Ubuntu 5.04 "Hoary Hedgehog" on {your hostname}', or something to that effect. I've setup my Ubuntu to boot into framebuffered 1024x768 mode, so I've replaced my /etc/issue with a rather big**[2]** ascii art Ubuntu logo, attached to this post.

Download the issue.txt attachment, and place it in your home directory.
Execute this command:

```
cd
sudo mv issue.txt /etc/issue
*(Enter password if prompted)*
```

_**Step 2: Remove the disclaimer**_

Even with a framebuffered 1024x768 console, the Ubuntu disclaimer looks ugly and takes up too much room on-screen. It's kept in the /etc/motd ("Message of the Day") file. A MotD is traditionally displayed to all users who login to a server. You'll find them in IRC, FTP and SSH servers, to name but three.

It's just a text file that is displayed to all logged in users as the first thing they see. You can make the file completely empty, so as to disable the MotD feature, or you can type in a message:

```
**Empty the MotD file:**
     sudo cat /dev/null > /etc/motd

**Place something in the MotD file:**
*Save a text file in your homedirectory, and then:*
     cd
     sudo mv nameofmyfile.txt /etc/motd

```

Now you've either disabled the MotD feature, or added your own personal touch to your login message; Either way, you've eradicated the disclaimer that we all should already know and agree to anyway. :)

**_Step 3: Spice up your bash shell sessions_**

Finally, add something to your actual shell sessions. It's been noted in [this thread](http://ubuntuforums.org/showthread.php?t=32076) how to do this, so I won't go into this here in too much detail, but here's what I have in my .bashrc:

```
*(snip)*
/usr/games/fortune linux linuxcookie | cowsay -n
```

This basically means that just before all the stuff in .bashrc has been done, and control is to be handed to me with a bash prompt, bash will display a 'fortune' from either the linux or linuxcookie files, and it will display it via the cowsay program. You should already have fortune on there in Hoary (possibly Warty too), but cowsay does not come preinstalled AFAIK. Install it, if you like, or remove the '| cowsay -n' part of the command above.

Cowsay basically just takes any input you give it and displays it in an ASCII-art cow with a speech bubble.

```
*Install fortune and cowsay*
sudo apt-get install fortune cowsay
*(Enter password if prompted)*
```

If when you login, you get a message saying it can't find 'linux.dat' or 'linuxcookie.dat' in /usr/share/games/fortunes, then you'll have to install those fortune files. I don't know what packages they'd be in, but possibly '*fortune-linux*' and '*fortune-linuxcookie***[3]**'. You can also see what fortune files you already have, by issuing the following command:

```
ls /usr/share/games/fortunes | less
[i]Press space to see more on screen, or press Q to go back to your shell prompt.
The less program is a handy utility that displays information one-screen-at-a-time.[/i]
```

And there you have it.

For your reference, I made the Ubuntu ascii art logo in the Gimp 2.0, which lets you save images directly to ASCII text.

To see the effects of your new console setup, you can either reboot your machine, or restart the individual processes that need to see the way the new setup looks.

To see the fortune | cowsay program in your .bashrc, just open a new terminal (even in gnome-terminal).

To see the Ubuntu ASCII logo on your terminals, issue this command and press CTRL+ALT+F2 to see, for example, terminal #2:

```
sudo killall getty
*(Enter password if prompted)*
```

This will restart the terminal displays and show you your new Ubuntu ASCII logo.

And to see the effects of the optional step #0 at the beginning, issue this command:

```
sudo killall gdm
*(Enter password if prompted)*
```

And you're done!

I don't have a video-capture card, so I had to write a small shell script to simulate a login shell, and then take a screenshot of that inside of Gnome using gnome-terminal. [Here](http://www.techmonkey.myby.co.uk/junk/simterm.png) it is.



**[1]** You will still be able to access your terminals via the shortcut keys: CTRL+ALT+F1 for terminal #1, CTRL+ALT+F2 for terminal #2, etc. To jump back to your graphical desktop, press CTRL+ALT+F7.

**[2]** I apologise to those who haven't seen the light of the framebuffered console yet, or who have and just haven't got a 1024x768 resolution. The restrains of a lower resolution have put boundaries on how good I can make the logo look for such a low res. If you have a normal console resolution, use smallissue.txt instead.

Alternatively, open your /boot/grub/menu.lst and find your default kernel image. It should be near the bottom of the file, and it will have the entry 'root     hd(0,0)'.
Add **vga=0x317** to the kernel entry, thus:
```

kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet vga=0x317

```

When you reboot into this kernel image, you'll now have a nice 1024x768 console and the Ubuntu ascii logo will actually look good. :)

**[3]** I'm actually pretty sure they come as part of the fortune package itself, so you should automatically get them by default.

---

### Post by mrshark on 2005-06-06
[QUOTE=techmonkey]```
sudo cat /dev/null > /etc/motd
```[/QUOTE]
to empty a file you only need this:
```
> /etc/motd
```
read this: [http://sial.org/howto/shell/useless-cat](http://sial.org/howto/shell/useless-cat)  :wink:

---

### Post by pdk001 on 2005-06-06
it kinda hard to set up

---

### Post by drasko on 2005-06-16
I like it. Tnx.

---

### Post by wawa on 2005-09-21
Nice one..

Thanks

---

### Post by techmonkey on 2005-09-21
No problem. Glad you like it. I should tweak the ASCII logo a bit though. There are 'artifact' characters in the way of the ubuntu text, but anyway.

I just added to the 'Nice BASH prompt' thread with my own prompt, which you can see in the attachment. I rather like it. 

[http://ubuntuforums.org/showthread.php?p=364107#post364107](http://ubuntuforums.org/showthread.php?p=364107#post364107)

---

### Post by duminas on 2005-10-05
"Framebuffered terminal"?
I like the effects sofar, otherwise.

---

### Post by calx on 2006-09-19
Is there any way to add color to the issue or motd?

---

