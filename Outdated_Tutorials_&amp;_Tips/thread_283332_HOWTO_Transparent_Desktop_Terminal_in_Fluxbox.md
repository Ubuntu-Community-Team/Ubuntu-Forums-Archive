---
title: "HOWTO: Transparent Desktop Terminal in Fluxbox"
date: 2006-10-24
forum: Outdated Tutorials &amp; Tips
---

### Post by jr.gotti on 2006-10-24
Please note...this only applies to Fluxbox (And maybe openbox...I'm not entirely sure.) If you don't know what Fluxbox is, then head over to [http://www.fluxbox.org](http://www.fluxbox.org). Basically, it's a very lightweight, highly customizable window manager. If you're big on eye-candy though, I'd suggest you stick with you're higher end WM's. (Personally, I'd take speed over aesthetics any day...)

But enough about me! 

After searching for a long time on how to have one of those attractive yet surprisingly convienient transparent desktop terminals...I've finally compiled a very quick and easy method on achieving this much sought-after affect.

Surprisingly, many of the guides I found suggested using Eterm...I found it to be bulky and cumbersome, so I decided to go with aterm. Get this from the repositories first...

```
sudo apt-get install aterm
```

Next, you're going to want to edit your "apps" file...

```
vim ~/.fluxbox/apps
```

Now paste the following at the end of the file (Or if it's a new file, just paste it in.)

```

[app]  (aterm)  
  [sticky]      {yes}  
  [Layer]       {12}  
  [Hidden] 
  [Dimensions] {550 500} 
  [Position]  {0 0}   
  [Deco]      {0x1c0}   
[end]

``` 

Most of these options are self-explanitory, but I'll explain them anyway...

The (app) portion dictates which application should follow these rules.
The sticky option places the terminal on all desktops. This should be left as yes.
The Layer option dictates what layer it should be on. This should be left alone.
The hidden option hides the terminal from the 'taskbar.'
The dimensions should be changed to your needs. [height][width]
The position tells FB where to put the terminal. 0 0 is the top left corner.
Finally the deco line strips the terminal of the window decorations.

Now save the file, right click the desktop, and click "Reconfigure."

Now in any existing terminal, you are going to want to type;

```
aterm -tr +sb -fg black -bg white &
```

"-tr" Turns on transparency
"+sb" Turns off the scrollbar
"-fg black" Makes the text black. Change it to what you need.
"-bg white" Makes the selected text white. Again, change it.
"&" Makes the process run in the background. You need this.

That's it! You're done!

I'd suggest placing this command in the startup file, (~/.fluxbox/startup) or as a menu option in ~/.fluxbox/menu.

Thanks,
-Jason

[IMG]http://i26.photobucket.com/albums/c122/jrgotti/fluxitus.jpg[/IMG]

---

### Post by freduardo on 2006-10-24
Great howto, worked like a charm here !
I just need to fiddle around with size and positioning.

Thanks a lot.

---

### Post by paul6 on 2006-10-29
Nice, now if only there was a way to do this in Openbox...

---

### Post by Abstract on 2006-10-29
[img]http://ubuntuforums.org/attachment.php?attachmentid=18462&stc=1&d=1162145396[/img]

---

### Post by zoidburg016 on 2006-10-29
Is there any way to get it to do this automaticaly when I start fluxbox? I tried adding [exec] (aterm) {aterm -tr +sb -fg white -bg black &} to the start up file and it doesn't work.

---

### Post by jr.gotti on 2006-10-30
> Is there any way to get it to do this automaticaly when I start fluxbox? I tried adding [exec] (aterm) {aterm -tr +sb -fg white -bg black &} to the start up file and it doesn't work.   	

Yes, actually...here is a copy of my startup file...

```

exec conky &
exec aterm -tr +sb -fg black -bg white &
exec fbsetbg -l &
exec /usr/bin/fluxbox -log ~/.fluxbox/log

```

As you can see, exec /usr/bin/fluxbox -log ~/.fluxbox/log needs to be the last line. Every other line before that must be formatted as "exec [program] &" The Ampersand (&) is required.

Hope this helped!

-Jason

---

### Post by kerry_s on 2006-10-30
You don't need the exec in the startup for apps.->

conky &
aterm -tr +sb -fg black -bg white &
fbsetbg -l & <-put this in init and you don't need it here
(session.screen0.rootCommand:	fbsetbg -l)

Another alternative is Eterm, which can also be used to set the background.
 [exec] (Eterm) {Eterm --borderless --buttonbar 0 --trans --shade 0 --scrollbar false}

in startup->

Eterm --borderless --buttonbar 0 --trans --shade 0 --scrollbar false &

---

### Post by jr.gotti on 2006-10-30
Well thanks! Didn't know that!

While I'm here...does anyone know how to hide this thing from fbpager? That's the only thing I can't get working...

---

### Post by kerry_s on 2006-10-30
> **paul6 said:**
> Nice, now if only there was a way to do this in Openbox...

You can use all these tips in openbox, the "startup" would be the ".xsession" in openbox.

---

### Post by kerry_s on 2006-10-30
> **pixelPOET said:**
> Well thanks! Didn't know that!

While I'm here...does anyone know how to hide this thing from fbpager? That's the only thing I can't get working...

Try adding-> --skip-taskbar  <to your command

You can also learn to use kdocker and dock it to the system tray.Pic of xfce4-terminal,which is the easyist to set up->

---

### Post by NavmaN on 2006-10-30
Hi, I followed these steps, but when I run 'aterm' from terminal, the terminal freezes, and aterm doesn't load.
Please help,
Thanks,
NavmaN

---

### Post by jr.gotti on 2006-10-31
Hmm....what exactly are you entering in the terminal? And what terminal are you entering it in? Gnome-terminal? And could you post your .fluxbox/apps file? Thanks.

---

### Post by evandrofisico on 2006-11-16
To hide your terminal from the taskbar use wmctrl.

In my machine i use:
 wmctrl -r monitor -b add,skip_taskbar,below

to skip the taskbar, and put it in the lowest level.

---

### Post by shellhrs on 2006-12-28
I tried the method mentioned in Post #1 on an IBM TP 600e running Xubuntu Dapper. It worked like a charm. :-D
I had to install eterm to set the background using fbsetbg though.

However, when I tried the same method on a Compaq Presario 2500 running Ubuntu Dapper, it didn't work. The terminal window borders were disappear as expected, but the scrollbar still appear on the left side of the window. The worst part is that transparency doesn't work.

I tried using eterm instead, but while transparency worked, the terminal window borders just won't disappear.

Can anyone help me?

Thanks.

---

### Post by Maelgwyn on 2007-01-24
Awesome - this worked perfectly!

Just a quick question... How did you get the stats bar on the right of your desktop?

---

### Post by kortelainen on 2008-09-11
Allright.. maybe im like a year to late, but i just switch from gnome to fluxbox.


Allthough, ive been trying to get this to work but all i can perform is a regular transparent window wich has borders, shows on panel (and when alt+tab), i can also move this window.

Im somehow missing some "gdevilspie" liking commands with commands like undercorate, below, skip_pager and alikes.

Any help to get? I have done exactly as the walkthrough says..

Thx for help.

---

### Post by k0rfain on 2008-09-14
is there anyway to take away the window boarder, where close, maximize and lower is?

---

### Post by Hooya on 2009-01-19
Bumping to re-address the two posts above me.  I also have borders and can move the terminal.  How do I get rid of them?

Found it.  Try these settings in the app file

[Deco] {NONE}
[sticky] {yes}
[Position] {715 0}
[Layer] {12}
[FocusHidden] {yes}
[Tab] {No}

---

### Post by monroetransfer on 2009-09-01
> **evandrofisico said:**
> To hide your terminal from the taskbar use wmctrl.

In my machine i use:
 wmctrl -r monitor -b add,skip_taskbar,below

to skip the taskbar, and put it in the lowest level.

Where does this line go? If I run it once I log in and fluxbox is running and my terminal *is* showing up in the taskbar then it works and hides the taskbar item for the terminal, but if I try to put it in my ~/.fluxbox/startup file, even at the very end, it doesn't seem to work. I feel as though I'm so close to getting this to work, but I hate alt-tabbing to it.

---

