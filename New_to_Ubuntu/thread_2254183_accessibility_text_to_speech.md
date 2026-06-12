---
title: "accessibility: text to speech"
date: 2014-11-25
forum: New to Ubuntu
---

### Post by insub22 on 2014-11-25
i'm a long time user but every time i try and get into accessibility software, i get stumped. hard.

i was wondering what's the top tier screen readers for linux?

i'm looking for something primarily for web articles. there's some firefox addons* that probably will work for me.
but if there is something that runs at the os level, i could use it for pdfs, etc.

(i'm also interested in accessibility from a design perspective and figured this would be a good place to start.)

*ff addons: some of those make mp3's or ogg's. is that feature available?

---

### Post by CantankRus on 2014-11-25
Have a look at [**_[COLOR="#B22222"]cainteoir[/COLOR]_**]("http://www.hecticgeek.com/2012/07/text-to-speech-software-ubuntu-linux-cainteoir-tts/")

You can also use a command to either play highlighted text ...
```
echo $(xsel) | /usr/bin/espeak
```

or save highlighted text to a wav file...
```
echo $(xsel) | /usr/bin/espeak -w output.wav
```
Need to install **xsel** and **espeak**

---

### Post by sudodus on 2014-11-26
I use espeak. There are several languages. You can learn how to tweak it via the man page

```
man espeak
```

and by browsing the internet. You find the voices for a particular language with for example

```
espeak --voices=en
```
```
espeak --voices=sv
```

For example, compare the pronunciation of of these commands

```
espeak -v sv 'Hej värld'
```
```
espeak -v swedish-mbrola-1 'Hej värld'
```
```
espeak -v swedish-mbrola-2 'Hej värld'
```

---

