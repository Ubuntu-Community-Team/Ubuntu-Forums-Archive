---
title: "[SOLVED] K3b : I can't make a music CD with mp3's...(?)"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by sdim on 2008-06-11
Hi,everyone.
I tried to make a cd out of some mp3's(for normal purposes,i.e. a music cd,not an mp3 one),but K3b prompted me to convert the songs first to .wav format,and then make the music cd.Is that right?
I was a bit surprised,as every other application I know automatically converts the mp3's to the suitable format for a casual music cd.
Any opinions?
Thank you.

---

### Post by OffAxis on 2008-06-11
> K3b prompted me to convert the songs first to .wav format,and then make the music cd.Is that right

wav (an uncompressed format) is the standard format going into a music cd, so yes, that is correct.

I've never done a music cd in k3b with mp3s, so I'm not sure about the 'On-the-fly' conversion. Sorry.

---

### Post by stchman on 2008-06-11
> **sdim said:**
> Hi,everyone.
I tried to make a cd out of some mp3's(for normal purposes,i.e. a music cd,not an mp3 one),but K3b prompted me to convert the songs first to .wav format,and then make the music cd.Is that right?
I was a bit surprised,as every other application I know automatically converts the mp3's to the suitable format for a casual music cd.
Any opinions?
Thank you.

You need to install the proper k3b codec libraries.

Gutsy or earlier
```
sudo apt-get -y install k3b libk3b2-mp3
```

Hardy
```
sudo apt-get -y install k3b libk3b2-extracodecs
```

You should now be able to burn .mp3 files and create an audio CD.

---

### Post by Vivaldi Gloria on 2008-06-11
Serpentine Audio Cd Creator

I suggest you have a look at it.

```
sudo apt-get install serpentine
```

It's a simple aplication with a nice gui. It was included in the previous ubuntus but omitted in Hardy.

---

### Post by avtolle on 2008-06-11
Brasero, the now-default CD burning application included in Hardy (I think) does the conversion on the fly; just select Audio CD project, pick the files you want to convert, and it does the rest.

---

### Post by sdim on 2008-06-12
Many thanks to all of you who provided useful answers.

---

