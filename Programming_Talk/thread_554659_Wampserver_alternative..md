---
title: "Wampserver alternative."
date: 2007-09-19
forum: Programming Talk
---

### Post by MrDiaz on 2007-09-19
Hello there, I used to work with Wamp (wampserver.com) it basically installs the complete package, all you need to develop applications in php and mysql. I was wondering, is there some kind of alternative similar to wamp I could use on Ubuntu? Or should I install everything separately?

Any help would be appreciated, thanks.

---

### Post by LaRoza on 2007-09-19
```
sudo tasksel
```

Select "LAMPP"

---

### Post by dniezby on 2009-02-07
What is LAMP? Is it an equivalent to WAMP?

If I install it, will it screw anything up?  

I'm about a week into Ubuntu so I'm just getting the hang of things.

I really like it but I'm looking to replace everything I had on windows. Like the original poster stated, I too use Joomla and like to develop it locally. If I install LAMP will this be what I'm looking for?

---

### Post by null.byte on 2009-02-07
Well, get your hands on [XAMPP](http://www.apachefriends.org/en/xampp-linux.html).

---

### Post by Peter76 on 2009-02-07
WAMP is an abbreviation for Windows Apache Mysql PHP, where LAMP is as you now may guess: Linux Apache Mysql PHP. So yes, if you install LAMP under Ubuntu you have the same functionality as with WAMP. Good Luck, Peter

---

### Post by dniezby on 2009-02-07
I installed the Xampp (which apparently is the new name for LAMP) and it seems awesome for developing websites locally.

My question is, is there a way to launch it from a shortcut or something?

Right now, I have to open terminal, type /opt/lampp/lampp start to get it running.

Also, stopping it, is a pain.

In windows, it put an Icon in the systray. I would click it, it would launch the application. Is there an equivalent method available?

---

### Post by Primefalcon on 2009-02-08
you could try xxamp

but you could just do the following

```
sudo apt-get install apache2
```

and then...

```
sudo apt-get install php5
```


and so on for any other aps you want installed

---

### Post by null.byte on 2009-02-08
> **dniezby said:**
> I installed the Xampp (which apparently is the new name for LAMP) and it seems awesome for developing websites locally.

My question is, is there a way to launch it from a shortcut or something?

Right now, I have to open terminal, type /opt/lampp/lampp start to get it running.

Also, stopping it, is a pain.

In windows, it put an Icon in the systray. I would click it, it would launch the application. Is there an equivalent method available?
Right click on your desktop, **Create launcher**. Name: XAMPP, Command: sudo /opt/lampp/lampp start.

---

### Post by dniezby on 2009-02-08
Awesome ! Exactly what I was looking for.

Thank You.

---

