---
title: "Linux mint console quote thingy"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by waspbr on 2008-06-14
I know this is a lame question and all, but I have switched from linux mint daryna straight into hardy and... and... and... where was I going with this again? ... oh yeah... there was this quote thing whenever you opened console... und... en... y... e... and I was wondering if it would be possible to implement that into ubuntu (hardy)... Those of you who may know it pls post it below.

---

### Post by Gannon8 on 2008-06-14
Um, what did the quote thing do? You could press up on the arrow keys to see previous commands.

---

### Post by waspbr on 2008-06-14
nooooo... don' t be silly(but if you can't help it I wont judge(lie))...It gave a cool snappy quote from some one important everytime you opened console... I rather liked it.

---

### Post by waspbr on 2008-06-14
bump?

---

### Post by cmay on 2008-06-14
hi.
there is a program that made these comments.
if its the same thing i think about that is.
when you installed mint you checked a box saying you want these fortune cookie/sayings  or something like that.
there is a program that can do this in ubuntu i think but i cant renember the exact name. its gotta be installed via synaptic then.
hope that could help.

---

### Post by dje on 2008-06-14
to get a quote like that type:
```
fortune
```
To get it to output a quote every time you open a terminal add the above command to your .bashrc file in your home directory by doing this:
```
echo "fortune" >> ~/.bashrc
```

hope that helps,
dje

---

### Post by waspbr on 2008-06-14
that's exactly what I was looking for.

cheers

---

### Post by dextrome on 2008-06-18
Thanks seconded. I joined this forum with this same question and one other:

Mint Elyssa has an awesome color scheme/highlighting scheme for its GNOME Terminal. Anyway to somehow get this in Ubuntu?

---

### Post by niko7865 on 2008-08-22
I'd also like the bash scheme from linuxmint ported to ubuntu. Not the fortune, just the colors mainly.

---

### Post by Gannon8 on 2008-08-22
> **niko7865 said:**
> I'd also like the bash scheme from linuxmint ported to ubuntu. Not the fortune, just the colors mainly.

Yeah, that would be nice. I hate how the terminal is just black and white except for the ls command.

---

### Post by LowSky on 2008-08-22
with an open terminal

Edit>preferences>change colors

---

### Post by schauerlich on 2008-08-22
> **Gannon8 said:**
> Yeah, that would be nice. I hate how the terminal is just black and white except for the ls command.

Try this:

[http://www.vias.org/linux-knowhow/lnag_05_05_04.html](http://www.vias.org/linux-knowhow/lnag_05_05_04.html)

There are many more guides like this on the web, so if you don't understand it then a quick google search will turn up 10 more.

---

### Post by Gannon8 on 2008-08-22
> with an open terminal

Edit>preferences>change colors
1. That menu does not exist.
2. Assuming you mean Edit > Current Profile > Colors:
We mean like the computer user and name (person@computer) in one color, the current directory in another color, and input/output in other colors.

---

### Post by schauerlich on 2008-08-22
> **Gannon8 said:**
> 1. That menu does not exist.
2. Assuming you mean Edit > Current Profile > Colors:
We mean like the computer user and name (person@computer) in one color, the current directory in another color, and input/output in other colors.

See my link, that will help you edit the PS1, which controls that sort of stuff.

---

### Post by LowSky on 2008-08-22
> **Gannon8 said:**
> 1. That menu does not exist.
2. Assuming you mean Edit > Current Profile > Colors:
We mean like the computer user and name (person@computer) in one color, the current directory in another color, and input/output in other colors.

thats what I meant. Im at work using a windows computer. Trying to do things from memory doesn't always work. Besides you found it!

---

### Post by hrishi.kb on 2010-11-03
[B]Get Mint Like Fortune-Cookie in your Ubuntu Terminal ! 
[/B]

see this blog post : [http://2x3idiots.blogspot.com/2010/11/get-mint-like-fortune-cookie-in-your.html ]("http://2x3idiots.blogspot.com/2010/11/get-mint-like-fortune-cookie-in-your.html")

Thank You !!

---

