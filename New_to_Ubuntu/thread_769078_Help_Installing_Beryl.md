---
title: "Help Installing Beryl"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by retskrad on 2008-04-26
Can Somebody plz tell me how to install beryl?

I goggled beryl and went to thier site and wenst to download section. A bunch of programs came up and I dont know which is Beryl. Can somebody explain which one to download, and how to install? Plz, help appreciated.  PS. [COLOR="Red"]LOVE UBUNTU[/COLOR].

---

### Post by adityakavoor on 2008-04-26
beryl is not under development now. Its merged with compiz.

Grab the latest hardy heron and you have compiz pre installed. Enjoy

---

### Post by Joeb454 on 2008-04-26
It's called Compiz Fusion now :) Beryl is discontinued now

And what version of Ubuntu are you running? Compiz-Fusion is installed by default as of 7.10

---

### Post by adityakavoor on 2008-04-26
beryl is not under development now. Its merged with compiz.

Grab the latest hardy heron and you have compiz pre installed. Enjoy

---

### Post by Joeb454 on 2008-04-26
Nice double post ;)

I've noticed that it's become too easy to double post with the forums lately :confused:

---

### Post by retskrad on 2008-04-26
> **Joeb454 said:**
> It's called Compiz Fusion now :) Beryl is discontinued now

And what version of Ubuntu are you running? Compiz-Fusion is installed by default as of 7.10

I have got Ubuntu 8.04 LTS

---

### Post by Joeb454 on 2008-04-26
Then you need to enable all software sources except for Source Code & CD from System>Administration>Software Sources

Then open up synaptic and search for compizconfig-settings-manager :) Install that and you're good to go.

Alternatively open up a terminal, and type (or copy) ```
sudo aptitude install compizconfig-settings-manager
```

To start the manager - go to System>Preferences :)

---

### Post by adityakavoor on 2008-04-26
> **Joeb454 said:**
> Nice double post ;)

I've noticed that it's become too easy to double post with the forums lately :confused:

I am currently using live cd. Probably that lead to a double post.. firefox didnt react that quickly

---

### Post by Alehbye on 2008-04-26
Joeb454 beat me to it! :)

So I assume you want more options than the 3 graphics levels, for that you'll need to install the compizconfig-settings-manager.

Do this from terminal:

```
sudo apt-get install compizconfig-settings-manager
```

It will ask for you password of course and then install the settings gui. Then you can go to System > Preferences > Advanced Desktop Effects Settings. You will have more options than you can shake a stick at. :)

Good luck and I hope this helps.

---

### Post by retskrad on 2008-04-26
I got an error: > E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


EDIT: THANKS I GOT THE CONFIG NOW, THANK YOU VERY MUCH FOR YUOR HELP.

---

### Post by riptreeper on 2008-04-26
The first part went through great then I tried the second one 

and I got 

E: Couldn't find the package compizconfig-settings-manager

Any help ?

Thanks a million.

---

### Post by Joeb454 on 2008-04-26
Do you have the Universe & Multiverse repo's enabled?

System>Administration>Software Sources

---

### Post by riptreeper on 2008-04-26
Yes they are both enabled

---

### Post by adityakavoor on 2008-04-27
> sudo apt-get update
then try

---

