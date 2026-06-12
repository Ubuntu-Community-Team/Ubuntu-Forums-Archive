---
title: "Mouse cursor spins for a long time"
date: 2012-02-23
forum: New to Ubuntu
---

### Post by mayur.shetye on 2012-02-23
I have ubuntu 11.10 and I use the classic gnome desktop(no effects)  .When I try to open a folder,for example home folder by going to 'places' on the gnome panel the folder opens but the cursor keeps on spinning.Also,if I double click on a folder while the cursor is spinning the folder opens without delay.But the cursor keeps on spinning and then stops after about 10 secs or so.Does anyone have a fix for this?

---

### Post by matt_symes on 2012-02-23
Hi

The amount of time the cursor spins is dependent on the number of items in the folder you are trying to open. Are there a large  number of items in the folders ?

Do you have many thumbnails in your thumbnail cache ?

Have you looked at the ~/.xsession-errors log file ? That may give some information.

Kind regards

---

### Post by mayur.shetye on 2012-02-24
Thank you for your reply.
The cursor spin problem persists in all folders,even in those having 1-2 items.
I deleted all the thumbnails from my .thumbnails folder in the home directory.Still,the issue is not fixed.
I can't seem to understand much from the .xsession-errors log file.
I've uploaded it.Maybe you can help. :)

---

### Post by mayur.shetye on 2012-02-24
Hi! I would like to add something interesting that I noticed.I use Cairo dock and I had only kept minimum applets in it.Now,I added the applet 'Shortcuts' back to it.When I try to navigate using 'Shortcuts' the mouse cursor does not spin! So,is it possible that the problem lies in the gnome panel?

---

### Post by matt_symes on 2012-02-24
Hi

> (nautilus:1306): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory

The above is nothing to worry about. 

I am unsure about this though. I have never come across it and it does not appear in my .xsession-erros log file when i start Nautilus.

> (nautilus:1306): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

I think some Googling and looking on Launchpad to see if this is problematic and may be the cause of your Nautilus issues, is in order.

> Hi! I would like to add something interesting that I noticed.I use Cairo dock and I had only kept minimum applets in it.Now,I added the applet 'Shortcuts' back to it.When I try to navigate using 'Shortcuts' the mouse cursor does not spin! So,is it possible that the problem lies in the gnome panel?

Try to see if you get the above errors in .xsession-error when using the shortcut option in Cario dock. That may implicate/eliminate that error message.

Kind regards

---

### Post by mayur.shetye on 2012-02-25
...

---

### Post by mayur.shetye on 2012-02-25
Sorry,reposted comments.

---

### Post by mayur.shetye on 2012-02-25
Firstly,sorry for the late reply.
I googled the error and found this
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/738203](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/738203)
But I don't think it is a fix for my problem.
I also checked the .xsession-errors file while using cairo dock shortcuts.There were no errors.(I moved the original file to desktop and created a new .xsession-errors file.The file was blank when I checked it later.)

---

### Post by mayur.shetye on 2012-02-25
More information:
I switched OFF automatic login and with this the mouse cursor problem seems to be fixed.So any idea how this is related to auto login?

---

### Post by matt_symes on 2012-02-28
Hi

> **mayur.shetye said:**
> More information:
I switched OFF automatic login and with this the mouse cursor problem seems to be fixed.So any idea how this is related to auto login?

Absolutley no idea !

I'm really not sure what would cause the problem and why it should work when auto login is disabled.

I do not have the problem here so i am not sure what to suggest.

Kind regards

---

### Post by mayur.shetye on 2012-03-18
Its Ok :)

---

### Post by matt_symes on 2012-03-18
Hi

One thing that may work.

Try disabling file preview in Nautilus. 

From the Nautilus menu ->Edit->Preferences->Preview and set all the options to never.

Nautilus stats each file (as possibly each more than once) to generate the preview, according to what i have read.

If you are technical, you can check this out by *stracing* Nautilus and see what it does. I have not had the time to do this but i have read that this is what it does.

Therefore disabling preview may speed it up.

Kind regards

---

### Post by mayur.shetye on 2012-03-21
I tried doing that but the mouse cursor still spins if I enable auto login.

---

### Post by matt_symes on 2012-03-21
Hi

Create a new user and login as that user. Do you still get the same problem ?

At least that will highlight system or user settings.

Kind regards

---

### Post by Bobhuber on 2012-03-21
> **mayur.shetye said:**
> I tried doing that but the mouse cursor still spins if I enable auto login.
You are not alone my friend. I have had the same problem with the same results (disable auto login) for a long time. Posted on this forum with no resolution . To add a bit when I enable autologin the mouse cursor theme changes to what I think is the system default and not what I have selected. I also notice that when opening things from Cairo-Dock with open GL things improve drastically. I thinks its because CD does things thru DBUS but have no idea. The problem is not restricted to Nautilus. I get the spinning cursor with Firefox etc.

---

### Post by mayur.shetye on 2012-03-22
> Create a new user and login as that user. Do you still get the same problem ?Created a new user.The problem still persists if autologin is enabled.

> You are not alone my friendGlad to know! ;) 
But I don't have that problem with firefox,only nautilus.
> I also notice that when opening things from Cairo-Dock with open GL things improve drastically.
Exactly! I don't know how but I forgot to mention that!

---

### Post by matt_symes on 2012-03-22
Hi

You both have an odd problem here. Have you ran a nautilus self check ?

```
nautilus --check
```

Does any step take a long time ?

Or this

```
nautilus -q && nautilus
```

Do you have any networked drives mapped ?

Going back to Bobhuber's point about dbus, try

```
dbus-launch nautilus
```

Does the cursor still spin ?

Kind regards

---

### Post by Bobhuber on 2012-03-22
> **matt_symes said:**
> Hi

Do you have any networked drives mapped ?

Going back to Bobhuber's point about dbus, try

```
dbus-launch nautilus
```Does the cursor still spin ?

Kind regards
No spin at all when running thru dbus . No network drives . I am however running a desktop server on a standalone machine for webpage development. I see the spinning cursor on anything that's processor dependent as if the systems waiting for that process to finish before giving you back the mouse pointer even though the spinning cursor will still open up additional apps as stated by the OP in the original post. Not a big problem to login but more of a frustration that I haven't been able to figure out whats causing it.

---

### Post by mayur.shetye on 2012-03-23
> nautilus --checkNo problem here

> nautilus -q && nautilusThis is what I get for this
> Initializing nautilus-gdu extension
** (nautilus:9136): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
> dbus-launch nautilus
gives the same message as above

Also,I would like to emphasize that the **mouse cursor spins ONLY if I browse using the 'Places' menu in gnome panel**.Running nautilus through terminal does not give me this problem.

---

### Post by mayur.shetye on 2012-03-23
I think the error is because of this bug and is unrelated to the mouse cursor spin issue which I am having
[https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/211966](https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/211966)

---

### Post by matt_symes on 2012-03-23
Hi

@mayur.shetye.

I don't think that bug is a show stopped. I've had it myself without the problems you are having.

Do you get the spinning cursor with

```
dbus-launch nautilus
```

Kind regards

---

### Post by mayur.shetye on 2012-03-23
Yes.If I enable autologin then I still get the spinning cursor with "dbus-launch nautilus" IF I use the 'Places' menu.

---

### Post by matt_symes on 2012-03-24
Hi

> Yes.If I enable autologin then I still get the spinning cursor with "dbus-launch nautilus" IF I use the 'Places' menu.

I'm a bit confused by this. Do you still get the spinning cursor if you type dbus-launch nautilus from the terminal ?

Also, do you still get it with (from the terminal)

```
nautilus --no-desktop
```

I'm quite stumped by this one as it's not an error i can reproduce, and consequently, i cannot investigate it here.

Kind regards

---

### Post by mayur.shetye on 2012-03-25
No, running both the commands doesnt give me the spinning mouse cursor.

---

### Post by matt_symes on 2012-03-25
Hi

Try disabling Naulitus show desktop from dconf.

```
sudo apt-get install dconf-tools
```

Fire it up and look for 

```
org -> gnome -> desktop -> background
```

Disable drawing the back ground and the desktop from there.

Reboot. Any joy ?

Kind regards

---

### Post by mayur.shetye on 2012-03-25
No.That does not help. :(

Just to clear any confusion
The mouse cursor spins IF AND ONLY IF
AUTOLOGIN is enabled and I try to navigate using the Places menu in the gnome panel.
In all other cases I DO NOT get this spinning cursor.

---

### Post by mayur.shetye on 2012-03-25
Just in case, is this related to my issue somehow?
[http://askubuntu.com/questions/89835/mouse-cursor-spinning-forever-after-startup](http://askubuntu.com/questions/89835/mouse-cursor-spinning-forever-after-startup)
I tried the solution given but I cannot find any switching process.

---

### Post by matt_symes on 2012-03-25
Hi

> **mayur.shetye said:**
> Just in case, is this related to my issue somehow?
[http://askubuntu.com/questions/89835/mouse-cursor-spinning-forever-after-startup](http://askubuntu.com/questions/89835/mouse-cursor-spinning-forever-after-startup)
I tried the solution given but I cannot find any switching process.

I really don't know what to suggest. 

The posters idea in that link is a good one if the symptoms are the same as yours. I'm not sure of they are though, if you only see that spinning cursor when starting Nautilus.

I suppose you could stop services running at start up and check for running start up applications when the gnome session is started.

Kind regards

---

### Post by damfino on 2012-04-20
Hi there,

after a dist-upgrade from maverick to natty I got the 'places' spinning cursor syndrome.
The issue, at least in my case, is caused by a weird interaction between gnome classic and xfce. I can easily reproduce the bug simply reinstalling thunar.

So, if you have anything xfce related installed on your system, I suggest to purge all those packages and see if it fixes your problem.

On my system I've used the following command line:

```
sudo apt-get purge exo-utils libexo-1-0 libthunarx-2-0 libxfce4ui-1-0 libxfce4util-bin libxfce4util-common libxfce4util4 libxfconf-0-2 thunar thunar-data thunar-volman xfce-keyboard-shortcuts xfce4-panel xfconf
```

You can use synaptic instead of apt-get, just make sure to "mark for complete removal" all the xfce packages.

---

### Post by tmaranets on 2012-04-20
Have you checked your Systems Settings with Mouse and Touchpad? If you are using Ubuntu on a laptop, have you tried using wire or wireless mouses? Maybe that would help your problem.

---

### Post by aartje on 2012-10-20
I have the same problem on my Ubuntu 12.04 system (updated upto now, october 20th)
I use Gnome classic (no effects) with automated login. When I give the "nautilus"
in a terminal window there is no problem at all. When I use the "normal" Gnome classic
there is no problem either. My feeling is that there is still some "compiz" component
in Nautilus that can't have any effect in "Gnome classic (no effects)" and times out
in (in my case) 15 seconds.

---

### Post by aartje on 2012-10-25
Made an ugly solution.
a)Removed "Places" from the top bar.
b)added a "Nautilus" startup icon in the topbar, that has not the spinning cursor

---

### Post by Singtoh on 2012-12-29
Hello All,

I have been having this same issue since 12.04. I am using 12.10 64 bit with only gnome shell installed and the issue remains. What I did to solve this is go to dconf-editor as matt_symes suggested and unticked only the show-desktop-icons and that cured my problem. Thanks matt_symes for pointing me in the rite direction:o This has been driving me bat@#$% crazy for a long time now:mad: now it's all good.

Cheers,

Singtoh

---

