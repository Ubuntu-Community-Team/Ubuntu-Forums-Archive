---
title: "comic book reader questions"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by willfriedwald on 2008-05-28
am trying to read some downloaded (vintage) comic books in two different formats, "cbr" and "cbz."

On the slightly older Ubuntu format 7,0X) I had no problem with either, it seemed like any program I used could read either format.

Now, in 8.0, I have a problem: I have tried three different reader programs: the basic "document viewer," "Comix," and "qComicbook" - they all can safely open the CBZ format documents, but none of them can open the CBR format comics.

the error message common to all three is that they are lacking an unrar executable.  what is that?  is there some sort of "sudo" command whereby I can install that?

thanks!

willfriedwald

---

### Post by sayakb on 2008-05-28
```
sudo apt-get install rar unrar
```
But I'm not very sure whether it would solve the CBR format anomaly..

---

### Post by willfriedwald on 2008-05-28
I think it did - like instantly!

thanks - will let you know if there's anything more to report - this seems to have worked (so far)!

w

---

### Post by alexandremrj on 2008-05-28
Those kind of files are arquive files so these comic programs need to extract first the files and only them can show them.

You mustn't have any unrar programs in your pc. You can install unrar-free (the unrar version is shareware).

You can search for "unrar-free" in synaptic or run in the command line
sudo apt-get install unrar-free

---

### Post by sayakb on 2008-05-28
> **alexandremrj said:**
> the unrar version is shareware

Really? I've been using it since over a year now.. Did notice.. :confused:

---

### Post by alexandremrj on 2008-05-28
I know it's strange but unrar depends of rar, and in the descripton of rar in synaptic says you can only try it for 40 days.

---

### Post by t0p on 2008-05-28
> **alexandremrj said:**
> I know it's strange but unrar depends of rar, and in the descripton of rar in synaptic says you can only try it for 40 days.

Yes that is strange - because I've installed **unrar**, but I haven't got **rar**... yet unrar works fine.

---

