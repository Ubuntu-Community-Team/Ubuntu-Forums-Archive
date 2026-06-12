---
title: "banshee 1.0 now playing in emesene"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by bullon on 2008-06-13
hi! I just got banshee 1.0, looks great! One problem though, the current song plugin in emesene no longer recognizes banshee, I guess because this new version is a little different, any clues as what I can do to get this to work? thanks. :)

---

### Post by ch3n3t0 on 2008-06-15
Download the attach file into your personal folder and open your terminal

```
$ tar -xjvf emesene.tar.bz2
```
```
$ sudo cp -r emesene /usr/share/emesene
```

sorry for my bad english, bye

---

### Post by iowa on 2008-06-29
That didnt work for me. :(

---

### Post by NovaAesa on 2008-06-29
@bullon,
When you say that it doesn't recognise Banshee, do you mean that there is no option under the CurrentSong plugin's properties for Banshee, *or* that there is an option there (and it is selected), but nothing happens when a song is played?

---

### Post by bubba_169 on 2008-06-29
I think if its the same as me then there is an option for banshee but it doesn't recognise when a song is playing :confused:

Might have something to do with banshee 1.0 being quite separate from the banshee in the ubuntu repos, it even has its own section in gconf.

---

### Post by placunza on 2008-08-18
Great!!!! =D> yuhuuuuuu! thanks!!

---

### Post by aldaan on 2008-08-19
> **ch3n3t0 said:**
> Download the attach file into your personal folder and open your terminal

```
$ tar -xjvf emesene.tar.bz2
```
```
$ sudo cp -r emesene /usr/share/emesene
```

sorry for my bad english, bye

It's working, you just need to type 

```
sudo cp -r emesene /usr/share/
```

instead of the above.

---

### Post by jersoncito on 2008-12-25
Thanks you!
Just on time for Christmas!!!

---

### Post by cuchillas on 2008-12-28
Thanks a lot, it works for me too!!!:)

---

### Post by Berenice on 2011-04-29
=D>
Thanks!

---

