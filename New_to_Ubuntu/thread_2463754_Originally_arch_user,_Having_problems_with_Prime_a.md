---
title: "Originally arch user, Having problems with Prime and wayland on my new ubuntu install"
date: 2021-06-17
forum: New to Ubuntu
---

### Post by kz-n on 2021-06-17
I have installed Ubuntu 21.04 and have been enjoying my time, Only problem for me is that I cannot use prime functionalities anymore, I heard this was X specific and that it was only for Arch, I am very confused about this and really need this for my heavy applications.
During my first boot up I noticed that I had X Server Settings, Even though I think I ran Ubuntu through Wayland, I don't know how to replicate this, However I do know that when I clicked it, A weird GUI appeared that I can't really explain, However it was a resizable panel that had nothing in it, That's the most I can explain.

I am not sure about what XWayland is, or if I should use Wayland or Xorg for gaming and other intensive applications, please instruct me :D.

I am running an asus laptop with an Intel i7-7700HQ and a Intel HD 630 + GTX 1050M

---

### Post by grahammechanical on 2021-06-17
I believe that Ubuntu 21.04 defaults to the Wayland compositor. To get the X-Server - at the login screen press enter. Before putting in the password click the Ubuntu icon in the bottom right corner of the screen and select from the little menu Ubuntu on X-Server. Now, when you login the system will be using X.

Certain applications are coded to run on X. Other applications are coded to use a Wayland compositor. I believe that XWayland makes it possible for Wayland apps to run on X. Or, it may be the other way around. I agree, not the most accurate explanation. This is not a subject I lose sleep over. Let the people who know explain it.

[https://wayland.freedesktop.org/xserver.html](https://wayland.freedesktop.org/xserver.html)

As the Arch Wiki says:

> For backwards compatibility to seamlessly run legacy [X11]("https://wiki.archlinux.org/title/X11") applications, [XWayland]("https://wiki.archlinux.org/title/Wayland#XWayland") can be used, which provides an X Server in Wayland.

[https://wiki.archlinux.org/title/Wayland](https://wiki.archlinux.org/title/Wayland)

Regards

---

### Post by CatKiller on 2021-06-17
> **kz-n said:**
> I heard this was X specific and that it was only for Arch 

Neither of these are true. 

> I am not sure about what XWayland is
XWayland is for running X applications in a Wayland session. 

> GTX 1050M

You shouldn't use Wayland. It will work, just about, these days, but XWayland is not hardware-accelerated on Nvidia currently. It's intended to work once the 470 branch is released, which will probably be sometime this month or so.

---

### Post by kz-n on 2021-06-17
Ah damn, Is nvidia completely not supported with Wayland? (And with that I mean would running only with my nvidia gpu work) I really cannot put my word on this as I don't know if Wayland or X11 even have a difference in performance, However even after logging in with Ubuntu Xorg I don't see X Server Settings nor can use prime-run or DRI_PRIME=1.

---

### Post by kz-n on 2021-06-17
> **grahammechanical said:**
> https://wiki.archlinux.org/title/Wayland[/URL]

Regards

You seemed to quote something that only works on arch afaik.

---

### Post by CatKiller on 2021-06-17
> **kz-n said:**
> Ah damn, Is nvidia completely not supported with Wayland?
Wayland works on Nvidia for Gnome and KDE. (Mesa uses generic buffers; Nvidia uses EGL Streams, which has only been plumbed in for KDE and Gnome. Soon everything will be using something different) 

What doesn't work on Nvidia (until 470) is hardware accelerated XWayland. Since the things that will use X in a Wayland session are games, and if you're using the Nvidia device to run them it's because you want them hardware accelerated, that makes it not particularly helpful for you. So, no point in using Wayland, yet. 

There's not really that much point you running 21.04 rather than 20.04 LTS, really, but since you're coming from Arch I'm unlikely to convince you that higher version numbers aren't the be-all and end-all. LTS releases are best for new users, since they'll get all the security updates and newer kernels and whatnot backported without having to be on the upgrade treadmill of a new version every six months.

---

### Post by kz-n on 2021-06-17
Oh hey, I know perfectly well what LTS means, I have used Ubuntu on servers for years.
I just wanted to get myself on the newer version right away cause I think it's the only version with wayland, I wanted to try it out.
I guess I will be going back to X then for now, How can I enable prime features? On my X session I can't use DRI_PRIME, prime-run or X Server Settings

---

### Post by kz-n on 2021-06-17
Oh hey, I know perfectly well what LTS means, I have used Ubuntu on servers for years.
I just wanted to get myself on the newer version right away cause I think it's the only version with wayland, I wanted to try it out.
I guess I will be going back to X then for now, How can I enable prime features? On my X session I can't use DRI_PRIME, prime-run or X Server Settings

---

### Post by CatKiller on 2021-06-17
> **kz-n said:**
> I just wanted to get myself on the newer version right away cause I think it's the only version with wayland, I wanted to try it out.

Wayland's been included for years. 21.04 isn't even the first to be Wayland-by-default (that was 17.10). Wherever it is that you've been getting your information from, I think you'd benefit from using a different source. 

> I guess I will be going back to X then for now, How can I enable prime features? 

You've not even said that you've got as far as installing the proprietary driver. Then, as I understand it, you need to specify which is the normal device and which is the offload device. And then you can use those environment variables to specify applications to be run normally and applications to be offloaded. But it's not something I've ever done; Optimus always seemed like a terrible implementation of a reasonably-sound idea, so I stayed well away from it.

---

### Post by kz-n on 2021-06-17
I just tried to install drivers, It just hangs for a couple of minutes and tells me a system application has failed, I have sent the reports every time it happened.

Lol then I probably misunderstood something, I've only recently got wind of Wayland and since I couldn't find anything about it on the LTS changelog I assumed it wasn't present.
If I can downgrade to the LTS version I'd gladly do that.

Optimus is a bad idea until you take into consideration laptops :/

---

### Post by tea for one on 2021-06-17
> **kz-n said:**
> If I can downgrade to the LTS version I'd gladly do that.

There is no path to downgrade from Ubuntu 21.04 to Ubuntu 20.04 - Fresh installation required

---

### Post by CatKiller on 2021-06-17
> **kz-n said:**
> Optimus is a bad idea until you take into consideration laptops :/
The *idea's* good. Have a performance part that's turned off most of the time to save power. ARM's little-big works OK. Optimus, though, is having two completely different graphics stacks that can't actually communicate with each other, and the high performance part can't actually be turned off. Nvidia's Linux support of Optimus for a decade was "go stick your head in a pig." 

You can't downgrade; it would have to be a fresh install. It doesn't sound like you've done that much that you'd need to redo, and the fresh install is, like, 15 minutes. You'll probably be fine on 21.04, though, since that's what you've got, but in general I'd recommend new users go for the LTS releases: the interim releases are for the testers and guinea pigs. 

Having the proprietary driver installed is a necessary first step. You've not given any detail about how you were trying to do so. You shouldn't try to download anything from Nvidia's site, but you're coming from Arch rather than coming from Windows, so you'd probably have known not to do that anyway.

The repositories have the driver packaged up for Ubuntu, and there's a PPA that gets them before they go into the standard repository. There's an automatic tool that can pull from either of those, but I've never used it.

---

### Post by kz-n on 2021-06-18
Update, It seems my option to start my session with Ubuntu on Xorg disappeared, I only have "Ubuntu" now which I'd guess to be Wayland, How can I fix this?

---

### Post by tea for one on 2021-06-18
In Ubuntu 20.04, the session choices are:-

Ubuntu
Ubuntu on Wayland

Is it different for 21.04?

You can check which session you are using by opening a terminal and entering:-
```
echo $XDG_SESSION_TYPE

```

---

