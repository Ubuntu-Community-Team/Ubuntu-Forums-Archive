---
title: "a good &quot;lite&quot; music player ???"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by maneesh77 on 2008-07-02
I have an old laptop and I want to install a good music player on it. 

But I have very low ram and it's a Pentium 3.  I use amarok for my desktop and like it's functionality. Looking for something similar but with less resource demands. Any suggestions??

---

### Post by aheckler on 2008-07-02
Banshee maybe, or Rhythmbox.

---

### Post by RomeReactor on 2008-07-02
Hi. Also try [BMPx]("http://bmpx.backtrace.info/site/BMPx_Homepage"); it's in the repositories, so yo can find it in Synaptic.

---

### Post by bluepowder7 on 2008-07-02
XMMS - it looks a lot like winamp, and i quite like it!

---

### Post by wolfen69 on 2008-07-02
> **maneesh77 said:**
> I have an old laptop and I want to install a good music player on it. 

But I have very low ram and it's a Pentium 3.  I use amarok for my desktop and like it's functionality. Looking for something similar but with less resource demands. Any suggestions??

how much ram do you have? right now watching tv with vlc, and im only using 12mb. if you can spare a few mb's, vlc might be the answer. plus it can play anything.

---

### Post by editrix on 2008-07-03
Believe it or not, you can play music from the command line--you can't get any lighter than that :-) (But don't ask me how to do it.)

I used to use XMMS on a 64MB machine.

---

### Post by alexandremrj on 2008-07-03
Hello,

with lots of functionality and not much RAM i use exaile (has the bells and whistles for lyrics and album art and all). If you want something lighter you can use Ario:

From the project launchpad: Ario is a full featured client for MPD (Music Player Daemon). The interface used to browse the library is inspired by Rhythmbox but Ario aims to be much lighter and faster. It uses GTK2, Gconf to store configurations and curl to download remote files (like cover arts).

---

### Post by diskotek on 2008-07-03
VLC is better since it can play most of the multimedia files. 99 in 1 :)
however it's playlist things is not that good.

---

### Post by ChameleonDave on 2008-07-03
> **maneesh77 said:**
> I have an old laptop and I want to install a good music player on it. 

But I have very low ram and it's a Pentium 3. for something similar but with less resource demands. Any suggestions??

How light is lite?

If you just want to listen to some files, you can't get simpler than:

```
cd ~/Music
*play* Beethoven_01.mp3  Hotel_California.ogg  Sonic_Youth_02.flac
```

The *play* command comes with the *sox* package.

```
sudo apt-get install *sox*
```

---

### Post by kevmitch on 2008-07-03
xmms or it's newer and better maintained fork, audacious might be up your alley.

---

### Post by TenPlus1 on 2008-07-03
Xmms is very light but I sue MPD Daemon and Gimmix since the daemon is only 5mb and gimmis is a small front-end that not only keeps a database of all your songs, but can play while you are logged out of the system :)

---

