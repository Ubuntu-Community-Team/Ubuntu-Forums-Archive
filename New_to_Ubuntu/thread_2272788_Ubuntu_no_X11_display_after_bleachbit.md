---
title: "Ubuntu no X11 display after bleachbit"
date: 2015-04-08
forum: New to Ubuntu
---

### Post by Hellboy256 on 2015-04-08
[TABLE]
[TR]
[TD="class: votecell"][/TD]
[/TR]
[/TABLE]
I used bleachbit on my Ubuntu 14.10 system. After that I restarted the system and I get this message:
```


  SpamAssassin Mail Filter Daemon: diabled, see /etc/default/spamassassin
 * speech-dispatcher disabled: edit /etc/default/speech-dispatcher
 SSL tunnels disabled, see /etc/default/stunnel4
 * Starting tor daemon...
 * Starting virtual private network daemon(s)...
 * Autostart disabled, no VPN will be started.
 saned disabled; edit /etc/default/saned

 (process:3298): dconf-WARNING **: failed to commit changes to dconf: Cannot autolaunc D-Bus without X11 $DISPLAY

```
  I can still log in with ctrl+alt+f2 into a terminal session...

  Does anyone know how to fix this?

---

### Post by Frogs Hair on 2015-04-08
You could start with the following to see what if any desktop dependencies might have been removed.  

 ```
sudo apt-get install ubuntu-desktop 
```

---

### Post by ajgreeny on 2015-04-08
Is there some sort of bleachbit log that will tell you what was removed?

I did investigate bleachbit a long time ago and ran it once just to see what it was going to remove if I let it do as it wanted to, ie default mode, but it was going to remove several things that I knew I wanted to keep.

Further investigation led to to the realisation that it doesn't help users in the same way that some of the Windows cleaners can, simply because Linux does not get bogged down in the same way with stray libraries and files, nor does it end up crawling, as some of my Windows OSs did in the days that I used it.

For me, after that, bleachbit went the same way as the files that it wanted to delete; I removed it.

Now apart from an occasional ```
sudo apt-get autoremove
```which I also monitor carefully to make sure it doesn't do anything that I don't want it to, I do not do anything special at all.

---

