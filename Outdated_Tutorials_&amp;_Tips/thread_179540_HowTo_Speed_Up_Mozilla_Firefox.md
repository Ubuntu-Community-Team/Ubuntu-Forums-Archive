---
title: "HowTo: Speed Up Mozilla Firefox"
date: 2006-05-20
forum: Outdated Tutorials &amp; Tips
---

### Post by PingunZ on 2006-05-20
This Howto works on Breezy/Dapper ( Gnome and Kde and Xfce )
If you got mozilla firefox and a broadband connection, this howto is really useful 
Ok let's start :)

EDIT :: THIS ALSO WORKS WITH FF BON ECHO

1) In your location bar, type :
```
about:config
```

2) In the filter bar type :
```
network.http.pipelining
```
Normally it says " false " , Double click it so it becomes " true " 

Go to the filter bar again and type :
```
network.http.pipelining.maxrequests
```
Change it to 8

Go to the filter bar again and type :
```
network.http.proxy.pipelining
```
Normally it says " false " , Double click it so it becomes " true " 


Go to the filter bar again and type :
```
network.dns.disableIPv6
```
Normally it says " false " , Double click it so it becomes " true " 

Go to the filter bar again and type :
```
plugin.expose_full_path
```
Normally it says " false " , Double click it so it becomes " true " 

3) Now we are gonna make a new integer 
```

Right click -> New -> Integer
Name : nglayout.initialpaint.delay
Value : 0

```

```

Right click -> New -> Integer
Name : content.notify.backoffcount
Value : 5

```

```

Right click -> New -> Integer
Name : ui.submenuDelay
Value : 0

```

EDIT : Added a few more lines ;) TY Pjotor

Thats it !
Firefox will now be 3 - 30 times faster in loading pages ;)
Hope you guys like it ;)

Grtz PingunZ

---

### Post by kleeman on 2006-05-20
You might want to look into the Fasterfox extension as well...

---

### Post by Pjotor on 2006-05-20
A couple more:

```
content.notify.backoffcount
``` 5

```
plugin.expose_full_path
``` true

```
ui.submenuDelay
``` 0

---

### Post by Harold P on 2006-05-20
I use the FasterFox extension, and tried some of those out. Some of those variables weren't already set by FasterFox. I actually noticed some load time differences. 

Thanks,
Harold

P.S. This also works on XFCE, seeing how this machine is on that DE.

---

### Post by Pjotor on 2006-05-20
You might also want to try this:

```
network.dns.disableIPv6
``` true

---

### Post by i0h on 2006-05-21
thanks mister PingunZ and Pjotor :) it really makes firefox alot better :)

---

### Post by PingunZ on 2006-05-21
No problem iOh, I hope that soon you'll be posting howto's too ;)

Grtz PingunZ

---

### Post by vseehua on 2006-06-02
hmm...just wondering...

doesn't the fasterfox extention automatically do it all for us already?

---

### Post by Alth on 2006-06-04
Woo, speedy.

Yeah, Fasterfox does this stuff, but this is just as easy ^_^

---

### Post by PingunZ on 2006-06-20
vseehua, some of these things are not icluded in the fasterfox extension 

Grtz PingunZ

---

### Post by nealklomp on 2006-06-20
wow! that is rediculious. I mean freakish.
I recently bumped up to another Kernel as well, my machine is sick right now.
Thank you very much.

---

### Post by nealklomp on 2006-06-20
wow! that is rediculious. I mean freakish.
I recently bumped up to another Kernel as well, my machine is sick right now.
Thank you very much.

---

### Post by ????? on 2006-06-20
Just want to add, this works on any version of Firefox (including windoze)

---

### Post by stanz on 2006-06-20
Pretty Ding Dang KEWL.... Thanks!!

---

### Post by mumushi on 2006-06-22
wowowowowoooo... tried it on firefox both in windows and ubuntu and its really speedy now. thanks alot for the howto. keep it up! :D

---

### Post by Moldy Jello on 2006-06-22
well thanks for this, i realy love it now, the speed of firefox was annoying me

---

### Post by wong3000 on 2006-06-24
Thanks Pingunz! :KS  it works great for my newly installed dapper drake! muah:D

---

### Post by tipi on 2006-06-24
changed these settings on swiftfox, 
does that mather??

---

### Post by WADemosthenes on 2006-06-25
[QUOTE=tipi]changed these settings on swiftfox, 
does that mather??[/QUOTE]

They should work on swiftfox, shouldn't they?

---

### Post by dcstar on 2006-06-25
[QUOTE=WADemosthenes]They should work on swiftfox, shouldn't they?[/QUOTE]
No difference between Swiftfox and Firefox with settings - treat them as identical.

---

### Post by PingunZ on 2006-07-03
Thanks for the reply's :)

I think this works on switchfox as well

Grtz PingunZ

---

### Post by newlinux on 2006-07-05
Great stuff! I'm doing this on all my computers...

---

### Post by PingunZ on 2006-07-06
Ty newlinux, I do the same thing ;)

Grtz PingunZ

---

### Post by gorilla_king on 2006-07-06
whoa that's just wild! thanks, keep up the awesome work.

---

### Post by FredB on 2006-07-07
Those settings are bad for servers, and you won't get a true speed boost.

The only real boost for surfing ? A bigger bandwith, nothing else.

---

### Post by PingunZ on 2006-07-07
> **FredB said:**
> Those settings are bad for servers, and you won't get a true speed boost.

The only real boost for surfing ? A bigger bandwith, nothing else.

Well as you can see in the previous 20 posts ppl like this ...
This howto is written for desktops and is known all over the web
You don't like it ? so don't follow the howto
Its clearly mentioned that this howto  is made for ppl with a broadband conection

Grtz PingunZ

---

### Post by diepruis on 2006-07-08
Thanks, this really speeds up firefox.

---

### Post by Skia_42 on 2006-07-09
PingunZ: Thanks for posting this... Your one of my 4 official heros now.

---

### Post by PingunZ on 2006-07-09
lol skia, who are the 3 others ?

Grtz PingunZ

---

### Post by andlinux21 on 2006-07-11
I just followed the howto on my old Gateway solo this thing is flying now just like Opera 9 THANKS!!!!

---

### Post by PingunZ on 2006-07-12
Tried this on version Bon Echo and it works ;)

Grtz PingunZ

---

### Post by puddpunk on 2006-07-12
Please guys, be careful with the values you set these at.

Pipelining is ok (but problem prone on some HTTP servers). It means instead of setting up and breaking down connections for each element of a page (image, CSS file etc...) it will reuse the same connection(s).

Please don't set the maxrequests any higher than 8. It will cause the server (especially a high volume server) to have a very noticable overall performance drop for all of it's clients. A lot of servers will limit the amount of concurrent connections from one client to it effectively disabling this option. Again, please don't abuse this setting or server admins will hard limit concurrent connections to their server (and you'll be lucky to get 2 :P)

"network.http.proxy.pipelining" will only work if you are using a HTTP proxy server.

"nglayout.initialpaint.delay" doesn't actually speed anything up. It just lets firefox start drawing the page before it has all the information giving the illusion it's downloading faster. On older computers with slow video it may even have a negative effect due to the speed of redraw when layout information is updated.

---

### Post by Edache on 2006-07-16
Outstanding PingunZ. Thanks for the tip.

---

### Post by PingunZ on 2006-07-17
Ty very much Edache

---

### Post by Iyatos on 2006-07-25
Wow, its much faster!! Thx

---

### Post by Lucidio on 2006-07-25
I have installed Faster Fox in my Firefox, this tweak can work simultaneusly with fasterfox?

---

### Post by PingunZ on 2006-07-25
Yes it does lucidio. some of these tweaks arent included in the fasterfox extension.

---

### Post by bmkrein on 2006-10-06
Hi

How to enable this settings in system-wide to all users?

bmkrein

---

### Post by PingunZ on 2006-11-18
I don't know, I taught it automatically was system-wide.

Cheers

---

### Post by raul_ on 2007-01-27
Darn! Instead of creating a new integer i created a new string! Is there any file i can edit to undo that? I'm using epiphany (i suppose the tweaks work too)

---

### Post by raul_ on 2007-01-27
It seems that if you don't put any value in it, when you restart the browser it disappears. :cool: anyway, if anyone has this problem, just close the browser and open ~gnome2/epiphany/mozilla/epiphany/prefs.js with a text editor and delete the line you want

---

### Post by MkfIbK7a on 2007-01-28
great how to!

---

### Post by phormion on 2007-01-28
> **PingunZ said:**
> 
Go to the filter bar again and type :
```
plugin.expose_full_path
```
Normally it says " false " , Double click it so it becomes " true " 



This only prints the full path to browser plugin files in *about : plugins* (no spaces). It won't speed up anything, just help you troubleshoot plugin problems - for example, when you are not sure from where have your plugins been loaded. 

This is explained [here](http://kb.mozillazine.org/Issues_related_to_plugins#Identifying_installed_plugins), among others.

---

### Post by Rab22 on 2007-01-28
Also, if you want to make fonts look a little nicer, you can try...

font.FreeType2.enable -- set to "true"
font.FreeType2.authohinted --> set to "true"

Usually these are 'false'. I find that they make pages look nicer on my system.

Thanks for the information!

-Rick

---

### Post by buuntuu! on 2007-02-08
thanks for the howto, it speeded things up somewhat!

i'm not so happy about the new integers though
> 3) Now we are gonna make a new integer
Code:

Right click -> New -> Integer Name : nglayout.initialpaint.delay Value : 0

Code:

Right click -> New -> Integer Name : content.notify.backoffcount Value : 5

Code:

Right click -> New -> Integer Name : ui.submenuDelay Value : 0

EDIT : Added a few more lines 

i find the initialpaint-integer quite annoying as it makes FF start drawing the page earlier, as puddpunk pointed out,  and it opens with a lot of blank spaces...
what do the other integers do??
i erased the suggested values, but how do i erase the integer??

regards,
buuntuu!

---

### Post by old_geekster on 2007-02-11
Thanks, PingunZ, for the great guide.

I want to use FF 2.0.0.1, because I am having problems with JRE5/6 in Swiftfox 2.0.0.1.  It doesn't work.

SF2 was so much faster, however, that it was hard to use FF2.  This cured the problem.  Now, I have to look at the name to assure I am using FF2.  It is sooo much faster after making the changes.

---

### Post by old_geekster on 2007-02-11
> **PingunZ said:**
> Thanks for the reply's :)

I think this works on switchfox as well

Grtz PingunZ
I checked these settings in SF2 and they are what makes it go faster.

---

### Post by old_geekster on 2007-02-11
Forgive me for hijacking your thread, PengunZ, but I didn't want to start a new Thread for a simple question.

Which of the many "Font" settings do I change to increase the size of the "Font" in the body of the browser.  My old eyes have difficulty reading it.

I know I can go to View and increase it, but I want it to be default.

Thanks for your indulgence.

---

### Post by raul_ on 2007-02-11
> **old_geekster said:**
> Forgive me for hijacking your thread, PengunZ, but I didn't want to start a new Thread for a simple question.

Which of the many "Font" settings do I change to increase the size of the "Font" in the body of the browser.  My old eyes have difficulty reading it.

I know I can go to View and increase it, but I want it to be default.

Thanks for your indulgence.

Edit-> Preferences -> Fonts

I think

---

### Post by old_geekster on 2007-02-11
> **raul_ said:**
> Edit-> Preferences -> Fonts

I think
Thanks, raul.  

I have done that, but it changes the font for the System.  I want to change it in FF2 only.

---

### Post by raul_ on 2007-02-11
> **old_geekster said:**
> Thanks, raul.  

I have done that, but it changes the font for the System.  I want to change it in FF2 only.

I meant in Firefox.

---

### Post by jfeeney on 2011-06-27
> **kleeman said:**
> You might want to look into the Fasterfox extension as well...

Sadly FasterFox doesn't work with the new Firefox 5, so this thread is mighty helpful even 5 years after its creation!

---

