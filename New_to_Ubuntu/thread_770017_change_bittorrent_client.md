---
title: "change bittorrent client"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by gentlemanmasher on 2008-04-27
I want to change my default bittorrent client and for the life of me can not remember the path to get to Azureus from my default.

Can someone give me a hand?

---

### Post by thisiam on 2008-04-27
download the torrent, right click the file and select open with and select your bit torrent client.
now they should all open the same way.

Edit: from terminal type which "name of client" 

> user@user-desktop:~$ which azureus
/usr/bin/azureus
user@user-desktop:~$ 


---

### Post by shtewe on 2008-04-27
i like deluge torrent progrom

its nice

---

### Post by gentlemanmasher on 2008-04-28
Thanks

---

### Post by hyper_ch on 2008-04-28
normally, you can issue just the program name without entering a path... the linux file system takes care, that executable programs are installed in various places which there exists in the PATH variable. So just "azuerus" would start it.

But if you want to run a light-weight, powerful torrent client that is used by the guys who operate TPB and Mininova then have a look at rtorrent ;)

---

### Post by jhorto1 on 2008-05-31
ARGGHHHH!!!
Linux drives me absolutely nuts sometimes. Something as basic as this is such a pain.

I'm trying to change the default bittorrent client and when I open it, it says Transmission or "Use Other" I choose use other.
Then it drops me to a file system browser to find the deluge executable file.
I have NO idea where this is, but if they'd just let me use a custom command I could type 'deluge'. No option for that though.
So I do a search with my binoculars in the top right corner of my desktop and it happily finds deluge with a pretty little deluge icon.

Fantastic! But what's the freaking path!!! I want to give it a path, but can't find where the deluge executables are. How can it give search results without showing where something is? I can't even find an option to display the path.

So mad right now, if you can't tell. I get so frustrated with linux when it takes me so long to do something that should be a no brainer.

Any tips would be greatly appreciated.

---

### Post by Nepherte on 2008-05-31
This will give you the path to the symbolic link executable:
```
whereis deluge
```
You can use that as a path (the path with bin in it).

If you want to know where all the files of deluge are, you can type:
```
locate deluge
```

---

### Post by cariboo on 2008-05-31
Most executable files are located in /usr/bin. here is a link to linux's directory structure.

[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

Jim

---

### Post by jhorto1 on 2008-06-02
Thanks guys. I'll give it a shot.

Once I get some more experience under my belt, situations like this should be more infrequent.

---

### Post by hyper_ch on 2008-06-03
> **jhorto1 said:**
> I have NO idea where this is, but if they'd just let me use a custom command I could type 'deluge'. No option for that though.
So I do a search with my binoculars in the top right corner of my desktop and it happily finds deluge with a pretty little deluge icon.

(1) why didn't "deluge" just work?

(2) you do have a menu with a deluge icon, right? You could have inspected where it links to...

---

### Post by jcslzr on 2010-01-20
> **thisiam said:**
> download the torrent, right click the file and select open with and select your bit torrent client.
now they should all open the same way.

Edit: from terminal type which "name of client"

been looking for an hour

it gives me no answer and also can not find it in tools> options or in the usr/bin folder

maybe just need some sleep

thanks will check tomorrow

---

### Post by lotharmat on 2010-01-20
> **shtewe said:**
> i like deluge torrent progrom

its nice

Deluge refuses point-blank to run for me!

It used to then the Kernel update to .17 borked it! - Just a blank window now!

BTW, how does one use magnet links from The Pirate Bay?

---

### Post by fromthehill on 2010-01-20
> **jcslzr said:**
> been looking for an hour

it gives me no answer and also can not find it in tools> options or in the usr/bin folder

maybe just need some sleep

thanks will check tomorrow

you should install it with the command: "sudo apt-get install deluge"
you can find deluge in the 'applications>internet' menu

---

### Post by jcslzr on 2010-01-20
> **fromthehill said:**
> you should install it with the command: "sudo apt-get install deluge"
you can find deluge in the 'applications>internet' menu

Thanks, I was looking for vuze

Regards,
Carlos

---

