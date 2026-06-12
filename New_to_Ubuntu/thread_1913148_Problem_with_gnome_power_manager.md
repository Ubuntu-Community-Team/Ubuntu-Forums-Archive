---
title: "Problem with gnome power manager"
date: 2012-01-22
forum: New to Ubuntu
---

### Post by sharatsn123 on 2012-01-22
on starting ubuntu 11.04, i am getting the error message 
"configuration defaults of gnome power manager have not been installed correctly. please contact your computer administrator"

i am unable to login..
pls help

---

### Post by hansdown on 2012-01-22
Hi, sharatsn123.

Click

```
ctrl> alt> f1 
```

Type

```
sudo dpkg --configure -a
```

Hit "enter".

---

### Post by sharatsn123 on 2012-01-22
> **hansdown said:**
> Hi, sharatsn123.

Click

```
ctrl> alt> f1 
```

Type

```
sudo dpkg --configure -a
```

Hit "enter".

Thanks hansdown... But the problem persists.

---

### Post by shakabra on 2012-01-22
Interesting problem try this. Maybe / is full?

[http://www.geekdevs.com/2010/04/solved-unable-to-boot-due-to-gnome-power-manager-error/]("http://www.geekdevs.com/2010/04/solved-unable-to-boot-due-to-gnome-power-manager-error/")

I hope this helps.

---

### Post by sharatsn123 on 2012-01-22
Thanks shakabra,
That link was really helpful. The problem was due to low disk space, So I deleted some files using terminal.

Thanks for your help.
[]("http://ubuntuforums.org/member.php?u=554422")

---

### Post by WyvernAldyth on 2012-01-24
Ok guys...

Let's say I really AM an absolute beginner, so I am definitely in the right forum area.
Lets say that when people say RAM,I think they own a dodge truck and that megabites are what I take on a 30 minute lunch break so that I have time left for a smoke.

That being said... I DID finally figure out how to get into terminal (by following link above), and that I definitely do have the same problem with having no free space. I even figured out how to do df -h and see it! (I take pride in my little accomplishments). 

I even did cd /var/log and then removed with rm anything possible that was simply a log - hoping this might make just the tiniest bit of room so that my ungeekified self might be able to get in there and delete something the "normal" way.

I still cannot boot.

Keeping in mind that I hold geeks in the highest regard (to point of telling my 16 year old daughter to date someone on the computer club... not that it would help, her school has a designated computer instructor and has to call Geek Squad to fix THEIR system and he admits he knows nothing of Linix and has only heard of Red Hat in passing and NEVER heard of ubuntu!).

[COLOR=SeaGreen]Exactly how, play by play, do I find something to delete through terminal? Then... how do I delete it - rm (filepath)? Is there something safe to delete that you can just give me some code and I can just hit enter (that would be GREAT!) and I could just reinstall later?[/COLOR]

And just as important... once I do delete something (if I ever figure THAT out)... how do I keep this from rehappening?

This is on a Lenovo 20013 Notepad (thinkpad?) computer with 80G HD that has a 7G partition for ubuntu (hope that helps). 

Gods knows the HD is big enough to handle what is on it as it is practically new... just seems to have been set up wrong to begin with. And as the shop I bought it at actually charges people $90 to convert a Windows computer TO ubuntu (which is of course a FREE program)... you can imagine what they charge for repairs!

---

