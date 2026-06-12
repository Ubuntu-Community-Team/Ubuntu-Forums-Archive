---
title: "Audio over ssh"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2008-09-10
okay, so currently I use something like this to stream audio over SSH,

ssh: cat "music.mp" | mpg123 -

And it works fine when I connect through putty on my one windows computer at home.  Audio streams and plays fine.  

However, when I'm at work, the audio streams, but I can never get the audio to actually come over my speakers. 

What's up with this?

---

### Post by rsambuca on 2008-09-10
Have you tried sshfs to mount the remote files to a local directory?

---

### Post by CryptiniteDemon on 2008-09-10
No, but why would audio play on one computer and not the other if I'm using the same interface program?

---

### Post by CryptiniteDemon on 2008-09-10
Wow, I just realized that I'm a moron.

The audio I was playing was coming from the source computer. My computers are in the same room, so I didn't realize that the sound was coming out of my other set of speakers.

Stupid me.

Now I just gotta figure out how to get audio to come out of the remote pc.

---

### Post by rsambuca on 2008-09-10
LOL!  So I'm not the only one that has done that!!!  I was trying to set up my laptop to access my desktop via ssh, and when I played the music, I thought everything was working perfectly.  It was only the next day when I wasn't sitting with my laptop on my home computer desk that I realized the music wasn't coming out of the laptop!

Try installing sshfs on your remote computer.
Create a directory on it so you can mount your server directory to it.  Then execute the following to mount it:```
sshfs user@host:directory mountpoint
```.  You can then just open nautilus or whatever file browser you are using, and it is as if the directory is on your remote computer.  I do this for my music files and play them through rhythmbox.

---

### Post by CryptiniteDemon on 2008-09-11
Hmm, I'm trying to make it where it's universal type of access. That way I can access it from either a windows machine or a linux machine if I want.  

Mostly this all comes from me trying to get access to my stuff through a proxy server because it doesn't block ssh connections.

---

### Post by gvartser on 2008-09-11
Or check out [www.kplaylist.net](www.kplaylist.net).

Awesome music php script allowing you to share the whole of your mp3 collection onto the web then accessible to you everywhere.

I have used this since 2003 and i can highly recommend it.

/g

---

