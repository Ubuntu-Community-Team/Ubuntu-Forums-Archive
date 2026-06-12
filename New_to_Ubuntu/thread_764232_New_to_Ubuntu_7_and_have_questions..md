---
title: "New to Ubuntu 7 and have questions."
date: 2008-04-23
forum: New to Ubuntu
---

### Post by Universal344 on 2008-04-23
I am new to Ubuntu 7.  I am dual booting it with Vista Ultamate on a seperate partition (I got vista first).

I do have a few questions:

1.I am learning PHP.  I put together some code then saved it.  When I tried to open it in firefox it told me I was trying to open a PHP script and it asked me what I wanted to do.  I clicked open with: firefox and clicked OK.  Then it just opened another tab and asked me again, the process continued.  When I finally said cancel all the other tabs were blank documents with nothing in the URL.  Does anyone know what causes this?

2.I tried to enable desktop effects and it said "desktop effects could not be enabled."  Yet, I have an ATI Radeon 2600 XT with DirectX 10 and Shader Model 4.0 support.  So I go and download the drivers.  Loan behold, it frags my graphics.  So, I reinstall it over the old version.  I couldn't find any drivers that had support for Linux.  Is there any way I will still be able to enable desktop effects or is it hopeless:(?

This is my PHP script I tried to make work (probably doesn't though).

[PHP]
for ($I = 0; $I <= 1; $I++){
	echo date('H:i:s');
	if ($I=1) {
	$I=0
}
}
[/PHP]

Any help is greatly appreciated!

THANKS:):grin:

---

### Post by Paqman on 2008-04-23
> **Universal344 said:**
> 
2.I tried to enable desktop effects and it said "desktop effects could not be enabled."  Yet, I have an ATI Radeon 2600 XT with DirectX 10 and Shader Model 4.0 support.  So I go and download the drivers.  Loan behold, it frags my graphics.  So, I reinstall it over the old version.  I couldn't find any drivers that had support for Linux.  Is there any way I will still be able to enable desktop effects or is it hopeless:(?


Did you try using the ATI drive in Restricted Driver Manager? After installing it you need to go into Appearance and enable desktop effects. If the RDM driver doesn't help you can try getting a more up-to-date one using [Envy](http://albertomilone.com/nvidia_scripts1.html).

---

### Post by Universal344 on 2008-04-23
The RDM was where I installed the drivers from but I will look at the envy thing, thanks!

---

### Post by Barrucadu on 2008-04-23
For your PHP problem - you just can't run PHP scripts like that. You need, if you want to view then through a browser, a webserver + php installed.

---

### Post by annda on 2008-04-23
as to PHP: do you have apache and php extensions installed?

just in case
system > administration > synaptic
edit > mark packages by task > LAMP server

or the easy way in the terminal
```

sudo tasksel
```

select LAMP with <space>

also, you need to put your scripts in an appropriate server docs directory ( usually /var/www) and run them in the browser using the following url:

localhost/name_of_your_script

-- sorry if this is too rudimentary for you, but your post was a little vague

---

### Post by maddog39 on 2008-04-23
To run PHP scripts you will need to install at least these two packages from either the command line or from synaptic.
```

apache2 php5

```To install from the terminal/command line.
```

sudo apt-get install apache2 php5

```
[Edit]
Woops we all posted at the same time I guess, oh well.

---

### Post by Universal344 on 2008-04-23
I am so sorry, 

I forgot to add that I've already installed LAMP

---

### Post by tamoneya on 2008-04-23
it seems to me like it is because you are looping infinitely.  while this may not be the reason why it is failing it is definitely not a good thing.

---

### Post by Universal344 on 2008-04-23
Ahhh,

I think you're right!
Firefox must want to open a new window every time my clock updates.
But, I want to create a constantly updating clock.  How do I do so without an infinite loop.  I know the answer might be obvious but my knowledge of PHP is very limited at this point.  Any help is appreciated!:)

---

### Post by tamoneya on 2008-04-23
javascript refresh

---

### Post by Universal344 on 2008-04-23
What do you mean by javascript refresh?

---

