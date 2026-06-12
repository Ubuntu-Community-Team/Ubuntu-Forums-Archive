---
title: "fluxbox q"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by neil_1 on 2012-03-02
i am thinking of switching from unity to fluxbox, i installed fluxbox.
but
which file manager do i use to browse through my files? 
also how do i add menus and items to the main fluxbox menu ?

---

### Post by andrew.46 on 2012-03-02
> **neil_1 said:**
> i am thinking of switching from unity to fluxbox, i installed fluxbox.

You will not regret it :).

> which file manager do i use to browse through my files? 

As you have seen Fluxbox does not have a file manager, it is a window manager rather than a desktop environment. I personally use thunar while many are happy with pcmanfm.

> also how do i add menus and items to the main fluxbox menu ?

Have a look *$HOME/.fluxbox/menu* and make your changes there. All the best with the mighty Fluxbox!!

---

### Post by wolfen69 on 2012-03-02
[http://fluxbox-wiki.org/index.php?title=Category:Configuration_howtos](http://fluxbox-wiki.org/index.php?title=Category:Configuration_howtos)

---

### Post by neil_1 on 2012-03-03
> **andrew.46 said:**
> You will not regret it :).



As you have seen Fluxbox does not have a file manager, it is a window manager rather than a desktop environment. I personally use thunar while many are happy with pcmanfm.



Have a look *$HOME/.fluxbox/menu* and make your changes there. All the best with the mighty Fluxbox!!

> **wolfen69 said:**
> [http://fluxbox-wiki.org/index.php?title=Category:Configuration_howtos](http://fluxbox-wiki.org/index.php?title=Category:Configuration_howtos)
well thanks guys!
i got to editing my menu now
but i do not know what the command for vmware player is :(
does anyone know ?
i need it in my menu :(
Also,
how do i control my volume ?
like increase/decrease/mute ?
edit:
Also, i got my wallpaper set by
```

fbsetbg -f wallpaper

```
but it doesn't stay after reboot
how do i make it stay ?

---

### Post by neil_1 on 2012-03-03
also is there some sort of battery indicator ?
because my laptop just hibernated and i had no idea the battery was dead :(
edit:
how do i get a temperature indicator too ?

edit:
solved battery indicator by using conky

how do i get the temperature indicator ?

---

### Post by snowpine on 2012-03-03
Fluxbox is a windows manager, not a desktop environment, so it doesn't come with a file manager, power management, volume icon, etc.

Personally I use **gnome-power-manager** and **alsa-mixer** for these tasks. Startup apps go in your ~/.fluxbox/startup (and be sure to use a & symbol).

I really recommend you read the link from **wolfen69** in post #3, it will answer all of your questions. :)

Also:
[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)
[https://help.ubuntu.com/community/Fluxbox/customize](https://help.ubuntu.com/community/Fluxbox/customize)

---

### Post by neil_1 on 2012-03-03
i've done all except
i can't find the command to start vmware player
does anyone know how i can find it ?

---

### Post by andrew.46 on 2012-03-03
> **neil_1 said:**
> i've done all except
i can't find the command to start vmware player
does anyone know how i can find it ?

I do not use vmware player but perhaps *find* can locate a suitable name:

```
sudo find /usr -iname 'vmware*'
```

or some variation of this command...

---

### Post by neil_1 on 2012-03-03
> **andrew.46 said:**
> I do not use vmware player but perhaps *find* can locate a suitable name:

```
sudo find /usr -iname 'vmware*'
```or some variation of this command...
well that didn't get it for me but i got close enough with it!
launcher is "vmplayer"
thanks though!

edit:
all the weather apps that i googled through, their ppa is down 
like conkyforecast etc
does anyone have something like it ?

---

### Post by Rodney9 on 2012-03-03
Conky Weather Thanks To Teo

[http://ubuntuforums.org/showthread.php?t=1156383](http://ubuntuforums.org/showthread.php?t=1156383)


Rodney

---

### Post by neil_1 on 2012-03-03
for some reason my print screen doesn;t work though
i've done what this thread told me to do in the screen shots section
[http://ubuntuforums.org/showthread.php?t=617812](http://ubuntuforums.org/showthread.php?t=617812)
but no image is saved in ~/screenshots :(

edit:
also i have added in 
```

Mod1 F3: Exec gnome-alsamixer

```
in my keys file
but it does not execute
what have i done wrong ?

---

### Post by neil_1 on 2012-03-04
also
i have this
```

[submenu] (Education) 
        [exec] (Maple15) {deskopen /home/neil/Maple/bin/maple15.desktop} 
        [exec] (Ktouch) {ktouch} 
        [exec] (Klavaro) {klavaro} 
    [end]
```

Why doesn't maple get executed ?

---

### Post by neil_1 on 2012-03-05
figured out the maple problem

still didn't figure out how to bind the keys to getting screenshots and
```

Mod1 F3: Exec gnome-alsamixer

```anyone ?

edit:
never mind, fixed it

---

### Post by andrew.46 on 2012-03-07
I have bound the *Print Screen* key to scrot:

```

107 :ExecCommand scrot -q 100

```

This of course goes in $HOME/.fluxbox/keys. Or a bit fancier:

```

107 :ExecCommand scrot -q 100 -e 'gimp $f'

```

which opens the screenshot immediately in gimp. Lots of other possibilities :).

---

### Post by neil_1 on 2012-03-08
> **andrew.46 said:**
> I have bound the *Print Screen* key to scrot:

```

107 :ExecCommand scrot -q 100

```This of course goes in $HOME/.fluxbox/keys. Or a bit fancier:

```

07 :ExecCommand scrot -q 100 -e 'gimp $f'

```which opens the screenshot immediately in gimp. Lots of other possibilities :).

okay, is 107 the sysreq key ?

---

### Post by andrew.46 on 2012-03-08
> **neil_1 said:**
> okay, is 107 the sysreq key ?

Best way to check is by using *xev* but on most systems 107 is the Print Screen | SysRq key.

---

### Post by neil_1 on 2012-03-09
> **andrew.46 said:**
> Best way to check is by using *xev* but on most systems 107 is the Print Screen | SysRq key.
got it!
my keycode is 110
thanks andrew!

one more question though,
how would i lock my screen on fluxbox w/o using xlockmore ?
xlockmore freaks out on my laptop

---

### Post by andrew.46 on 2012-03-10
> **neil_1 said:**
> one more question though,
how would i lock my screen on fluxbox w/o using xlockmore ?
xlockmore freaks out on my laptop

I have never really looked at this but I see that it can be done with good old-fashioned xscreensaver:

```
xscreensaver-command -lock
```

Perhaps bind this to a key or key combination?

---

### Post by neil_1 on 2012-03-10
> **andrew.46 said:**
> I have never really looked at this but I see that it can be done with good old-fashioned xscreensaver:

```
xscreensaver-command -lock
```Perhaps bind this to a key or key combination?
that didn't work either but i started to use gnome-screensaver :D

another question >.>
i attached an image,
in that it shows that the size of my notification area keeps increasing over time for reasons i know not of.
it starts out normal restricted size though

any idea ?
the icons in use are wicd,skype and xfce4-power-manager

---

### Post by andrew.46 on 2012-03-11
> **neil_1 said:**
> [...] the size of my notification area keeps increasing over time for reasons i know not of.
it starts out normal restricted size though

This is a problem posted several times on these forums. A good start to addressing the problem would be to upgrade your copy of Fluxbox to the most recent release version:

```

andrew@skamandros~$ **[COLOR="Red"]fluxbox --version[/COLOR]**
Fluxbox 1.3.2 : (c) 2001-2011 Fluxbox Team

```

and see if this fixes the problem. Otherwise I would suggest posting to the fluxbox-users mailing list, unfortunately I have not personally experienced this problem with Fluxbox.

---

### Post by neil_1 on 2012-03-11
> **andrew.46 said:**
> This is a problem posted several times on these forums. A good start to addressing the problem would be to upgrade your copy of Fluxbox to the most recent release version:

```

andrew@skamandros~$ **[COLOR=Red]fluxbox --version[/COLOR]**
Fluxbox 1.3.2 : (c) 2001-2011 Fluxbox Team

```and see if this fixes the problem. Otherwise I would suggest posting to the fluxbox-users mailing list, unfortunately I have not personally experienced this problem with Fluxbox.
i have 1.3.2 :/
> neil@lappy:~$ fluxbox -v
Fluxbox 1.3.2 : (c) 2001-2011 Fluxbox Team 

---

### Post by bodhi.zazen on 2012-03-11
Keep going. Also look at some of these suggestions

[http://blog.bodhizazen.net/linux/a-5-minute-guide-to-fluxbox/](http://blog.bodhizazen.net/linux/a-5-minute-guide-to-fluxbox/)

For file managers, nautilus, Thunar, or pcmanfm ( I prefer pcmanfm).

---

### Post by neil_1 on 2012-03-16
another question,

if i am formatting my laptop, after i install ubuntu do i just install fluxbox and paste in the .fluxbox folder in /home ?
does this work on mint and debian as well ?

---

### Post by bodhi.zazen on 2012-03-16
> **neil_1 said:**
> another question,

if i am formatting my laptop, after i install ubuntu do i just install fluxbox and paste in the .fluxbox folder in /home ?
does this work on mint and debian as well ?

Should be able to do that.

---

### Post by Rick.B9 on 2012-03-16
> **neil_1 said:**
> another question,

if i am formatting my laptop, after i install ubuntu do i just install fluxbox and paste in the .fluxbox folder in /home ?
does this work on mint and debian as well ?

The paste-in technique works well; it's what I use.  Just reload config or restart Fluxbox after pasting and away you go.  Don't forget to backup your .fluxbox folder somewhere to make it easy on yourself.  Once you get it working to your liking, you wouldn't want to lose it.

---

