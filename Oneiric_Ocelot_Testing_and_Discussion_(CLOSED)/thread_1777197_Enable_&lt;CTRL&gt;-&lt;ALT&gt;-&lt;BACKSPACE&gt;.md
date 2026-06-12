---
title: "Enable &lt;CTRL&gt;-&lt;ALT&gt;-&lt;BACKSPACE&gt;"
date: 2011-06-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by JRV on 2011-06-07
How do you enable <CTRL>-<ALT>-<BACKSPACE> in Oneiric? 
Dontzap is not in the repositories, and it is not in the keyboard applet.
It is a necessity when working with pre-release code.

---

### Post by ronacc on 2011-06-07
<alt>-<sysreq>-<k>  kills x now .

---

### Post by collisionystm on 2011-06-07
> **JRV said:**
> How do you enable <CTRL>-<ALT>-<BACKSPACE> in Oneiric? 
Dontzap is not in the repositories, and it is not in the keyboard applet.
It is a necessity when working with pre-release code.

Go to keyboard settings

go to layout tab

OPTIONS ( at bottom ) 

* key sequence to kill the x server * 
check box

done.

---

### Post by JRV on 2011-06-07
> **collisionystm said:**
> Go to keyboard settings

go to layout tab

OPTIONS ( at bottom ) 

* key sequence to kill the x server * 
check box

done.

That works in older versions, but not in Oneiric.

<alt>-<sysreq>-<k> does it, thanks ronacc.

Thread marked solved.

---

### Post by wojox on 2011-06-07
SysReq is also your Print Screen key.

---

### Post by seeker5528 on 2011-06-08
> **wojox said:**
> SysReq is also your Print Screen key.

Except when it isn't, in which case telling people to use the 'Alt' key just confuses the issue.

Better to say something like....

Use 'SysReq'+'K'.

'SysReq' is most commonly a combination of 'Alt'+'Print Screen/SysRq' unless other wise indicated on your keyboard. 

If you don't have 'SysRq' or can't figure out the correct modifier to make 'SysRq' work, the key combination 'Ctrl'+'Alt'+'Print Screen' simulates 'SysRq', which would make the entire key combination 'Ctrl'+'Alt'+'Print Screen'+'K'.

Later, Seeker

---

### Post by novatillasku on 2011-06-09
I need to activate on keyboard settings?, and where exactly?.Thank's.

---

### Post by cornflake000 on 2011-06-10
> **seeker5528 said:**
> the entire key combination 'Ctrl'+'Alt'+'Print Screen'+'K'.

You got to be kidding?... no, you're not, it works... but I think I pulled a ligament trying to reach that far.;)

---

### Post by seeker5528 on 2011-06-10
> **cornflake000 said:**
> You got to be kidding?... no, you're not, it works... but I think I pulled a ligament trying to reach that far.;)

Depending on the layout of your keyboard and how many fingers you have it could be a problem. :p

Later, Seeker

---

### Post by seeker5528 on 2011-06-10
Based on information I found [elsewhere](https://wiki.archlinux.org/index.php/Xorg#Ctrl-Alt-Backspace_doesn.27t_work), there are a couple ways to make 'Ctrl'+'Alt'+'Backspace' work, I tried both of these and they work for me.

First the user specific way.

If you don't already have a .xprofile file in your home directory, create it, then add the line 'setxkbmap -option terminate:ctrl_alt_bksp' to it
```
# This file '~/.xprofile' should be used to customize the environment of your X login session similar
# to the way you would use '~/.profile' to customize the environment of your command line login session.

# export PATH="~/some_directory:$PATH"
# export WINDOW_MANAGER="/usr/bin/fluxbox"

# Eexport LIBOVERLAY_SCROLLBAR=1
export VTEST=FUBAR
setxkbmap -option terminate:ctrl_alt_bksp


```

 That method doesn't work when using LightDM or LXDM for your display manager since '~/.xprofile' fails to get handled correctly while using them.

To make it work as a system wide setting, add the line ```
Option              "XkbOptions" "terminate:ctrl_alt_bksp"
```

to the "InputClass" section of you xorg.conf file. Commonly in Ubuntu xorg.conf doesn't exist and if it does probably doesn't have an "InputClass" section. So you would have to create xorg.conf in the '/etc/X11/' directory, then add the text
```
Section "InputClass"
    Identifier          "Keyboard Defaults"
    MatchIsKeyboard	"yes"
    Option              "XkbOptions" "terminate:ctrl_alt_bksp"
EndSection

```

Later, Seeker

---

### Post by ronacc on 2011-06-10
thanks for the info seeker . You should duplicate that over in tutorials&tips so others than we chosen few in the dev forum can benefit  .

---

### Post by seeker5528 on 2011-06-10
> **ronacc said:**
> You should duplicate that over in tutorials&tips

Tutorialization done, waiting on moderator approval to be visible.

Oops, I guess I should have read the guidelines first about telling how to undo what was done :blush: hopefully if it's rejected there will be some way to get back and edit it. I'm not seeing a way at the moment. 

Ok I was able to find the tab I had it opened in, in the history, and use the back button to get back to it, hopefully it's good enough to pass moderator approval now. But I see it's visible now, so maybe it was good enough already. :p

Later, Seeker

---

### Post by cariboo on 2011-06-10
Tutorial approved.

---

### Post by seeker5528 on 2011-06-10
> **cariboo907 said:**
> Tutorial approved.

D'oh, hopefully using the back button and editing again doesn't make things tooo wierd. ;)

Later, Seeker

---

### Post by cariboo on 2011-06-10
@seeker5528 It seems you created two threads, do you want one removed?

---

### Post by seeker5528 on 2011-06-10
> **cariboo907 said:**
> @seeker5528 It seems you created two threads, do you want one removed?

Yep, remove the one that doesn't have the undo info.

Later, Seeker

---

