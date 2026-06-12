---
title: "Open file with ??? application ??"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by faron45 on 2008-09-07
Downloaded Realplayer for Linux from [http://www.real.com/.Download](http://www.real.com/.Download) is on the desktop.Problem is,I don't know what application to use to open this file with to start the installation process.Can anyone help ? Please.I am really very new to this download & install thing & when I'm asked these questions "what application do you wish to open this file with ?" I always get confused.Thank for any & all help.
                Faron45

---

### Post by Pro-reason on 2008-09-07
Better to ignore that file.  You're supposed to run it from the command line.

Instead, look up how to enable the Medibuntu repositories, and then install RealPlayer in Synaptic.  That way, you get updates, and uninstalling is simpler.

Edit:  Whoops!  Sorry, the Medibuntu repositories have the &#8220;non-free-codecs&#8221; package, but not RealPlayer.  You'll need either the Linux Mint or the Ubuntu Japan repositories for that.

---

### Post by oldos2er on 2008-09-07
> **faron45 said:**
> Downloaded Realplayer for Linux from [http://www.real.com/.Download](http://www.real.com/.Download) is on the desktop.Problem is,I don't know what application to use to open this file with to start the installation process.Can anyone help ? Please.I am really very new to this download & install thing & when I'm asked these questions "what application do you wish to open this file with ?" I always get confused.Thank for any & all help.
                Faron45

 In a terminal, run "cd Desktop","chmod a+x RealPlayer11GOLD.bin," then "sudo ./RealPlayer11GOLD.bin"

---

### Post by faron45 on 2008-09-07
Pro-thanks.I've found those instructions [I think.Heh,heh.] But,still,even if were using like,say,"windows", I would still be lost.How does a person who doesn't know much about computers know which application to open something like that with ? I believe it has something do with what type of file it is.Is there somewhere I could go to learn about such things ??

---

### Post by faron45 on 2008-09-07
Oldos-thank you.But,now,as you might guess,I am fairly new to the comp world.When using the terminal,do I include the quotation marks around "cd Destop" ? I'm very confused about this terminal thing.After typing "cd Desktop",do I hit "enter"? And,then type in chmod a+x RealPlayer11GOLD.bin or,do I type in the whole thing with that comma in between & then hit "enter" ? And,then,the rest ?? See......I feel like such a dumb _hit sometimes.Heh,heh.

---

### Post by jemate18 on 2008-09-07
> **faron45 said:**
> Oldos-thank you.But,now,as you might guess,I am fairly new to the comp world.When using the terminal,do I include the quotation marks around "cd Destop" ? I'm very confused about this terminal thing.After typing "cd Desktop",do I hit "enter"? And,then type in chmod a+x RealPlayer11GOLD.bin or,do I type in the whole thing with that comma in between & then hit "enter" ? And,then,the rest ?? See......I feel like such a dumb _hit sometimes.Heh,heh.

You can do it like this
```
cd Desktop; chmod a+x RealPlayer11GOLD.bin; ./realPlayer11GOLD.bin
```

This can be done in one line and hit enter

---

### Post by oldos2er on 2008-09-07
No, no quote marks. Hit Enter after each separate command.

---

### Post by stevoo on 2008-09-07
Well realplayer is good ... but i wouldnt reccomend it.

Why dont you try someone other media players ? 
If you want to play mp3 i reccomend amarok
For video try Kaffeine.

---

### Post by faron45 on 2008-09-07
Jemate...thanks.No go,though.The terminal tells me "there is no such file or directory".Hmmmmmm.

---

### Post by Pro-reason on 2008-09-07
> **faron45 said:**
> Jemate...thanks.No go,though.The terminal tells me "there is no such file or directory".Hmmmmmm.

This shows that you should really just install it in Synaptic.

Open your */etc/apt/sources.list* file as root.  You can do so with the following command in the terminal:

```
gksu gedit /etc/apt/sources.list
```

Then add the following lines to the bottom of the file:

```

## Medibuntu
deb http://packages.medibuntu.org/ hardy free non-free
#deb-src http://packages.medibuntu.org/ hardy free non-free

## Ubuntu Japan
deb http://archive.ubuntulinux.jp/ubuntu-ja hardy/
#deb-src http://archive.ubuntulinux.jp/ubuntu-ja hardy/
deb http://archive.ubuntulinux.jp/ubuntu-ja hardy-ja/
#deb-src http://archive.ubuntulinux.jp/ubuntu-ja hardy-ja/
deb http://archive.ubuntulinux.jp/ubuntu-ja hardy-experimental/
#deb-src http://archive.ubuntulinux.jp/ubuntu-ja hardy-experimental/

```

Save and close.  You now have the appropriate repositories enabled.

Install the software you need via Synaptic.  Alternatively, enter the following at the command line:

```

sudo apt-get update && sudo apt-get install medibuntu-keyring libdvdcss2 realplayer non-free-codecs

```

You should now be able to play anything.

---

### Post by faron45 on 2008-09-07
Steveo-the only reason I wanted this,was so I could listen to a particular ["station" ?] which uses this player.

---

### Post by Pro-reason on 2008-09-07
> **faron45 said:**
> Steveo-the only reason I wanted this,was so I could listen to a particular ["station" ?] which uses this player.

If all goes well, the installation of RealPlayer will give other players access to the Real codecs.  You'll then be able to listen to that station in MPlayer, VLC, Totem, Amarok, or whatever.

Personally, I use MPlayer on the command line to dump the Real Media stream to a file, which I can then convert to a sensible format (.ogg) for my portable audio player (iRiver).

---

### Post by faron45 on 2008-09-07
Pro-thanks.I will try this.But,all this terminal & comp speak is giving me a headache.I have to run out for awhile.The ol' woman is pestering me.Sorry.And,thanks very,very much everyone.

---

### Post by oldos2er on 2008-09-07
> **faron45 said:**
> Jemate...thanks.No go,though.The terminal tells me "there is no such file or directory".Hmmmmmm.

 You have to run "cd Desktop" first (no quotes).

---

