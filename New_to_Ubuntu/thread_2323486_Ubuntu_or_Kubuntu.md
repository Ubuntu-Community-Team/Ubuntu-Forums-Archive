---
title: "Ubuntu or Kubuntu"
date: 2016-05-05
forum: New to Ubuntu
---

### Post by Damon_Campbell on 2016-05-05
Sup guys i recently started using Linux OS's and i saw that Ubuntu has different flavors you can choose
and i started to research on each one i found Ubuntu and Kubuntu very interesting but i need some input 
from you guys and see from your experience and perspective which flavor is i guess you can say better 
and to make it easier i will have some simple requirement questions that you guys can answer so it can 
help us get a better/accurate view on which flavors fits the most. 

I have 4 GB of RAM which flavor runs fast on boot and while in use?

Which flavor has better gaming compatibility because i use steam?

I am also going onto the path of becoming a pentester and doing all that hacking stuff which flavor is better for that environment?
(Do not worry i am not going to use the hacking for bad i live in Las Vegas so i'm looking into stuff like IT, Defcon, and Hackathons)

I will also being doing coding like Python, HTML, PHP, Perl, etc. Which flavor takes that kind of environment?

Which flavor has more security?
(I mean in like firewalls and etc)

Sometimes i like to do usb tethering with my android, which flavor is good for that type of use?

If i'm not gaming or doing hacking stuff sometimes i like to sit back and watch movies, read e-books,
and make images (Like Photoshop), which flavor is good for that environment?

I like to multi-task to get more things done faster, which flavor is good for that?

Which flavor is good when it comes to using VPN's and Proxies?

---

### Post by yancek on 2016-05-05
The difference between Kubuntu and Ubuntu isn't great system wise.  Basically, Kubuntu is Ubuntu with a different Desktop Environment (KDE).  Some other differences but for what you inquire about, it should not make much difference.  Personal preference mostly.  I don't know about Steam on either, never used it.

---

### Post by neu5eeCh on 2016-05-05
The main difference between KDE and Ubuntu, besides Desktop Environment, is that KDE uses QT and Ubuntu is GTK based. Steam _should_ run perfectly well on KDE/Plasma (all my GTK apps run perfectly well), but Steam was initially built to run on Ubuntu. If you Google "Steam QT KDE" you'll notice the occasional hiccup when using Steam on KDE. I run Steam on Plasma 5 and have never had problems with it, with the exception of multiple monitors. I don't know if that's Steam, KDE, or both combined. Personally, I would start out with Ubuntu's Unity. If you don't like it, you can switch.

---

### Post by grahammechanical on 2016-05-05
Linux is the kernel of the operating system. And all the flavours built on Ubuntu use the same Linux kernels as Ubuntu and have available the same Linux hardware modules and also the same open source and proprietary video drivers.

So, in my opinion there is no point asking about comparisons between flavours in regards to performance. Not without telling us the hardware specification of the machine. There comes a point where the hardware specification is such that Ubuntu & all the flavours run equally well. It is when the hardware specification goes to the lower levels that Ubuntu and Kubuntu both excuse themselves from the party.

If the hardware has the power then the choice is a matter of personal preference in regards to user interface. If the hardware lacks power then despite personal preference we have no choice but to consider Xubuntu, Lubuntu or Ubuntu Mate. 

Regards

---

### Post by oldrocker99 on 2016-05-05
It's all what kind of desktop you prefer. KDE has great eye candy and is very configurable, but uses a lot more resources than MATE, LXDE or XCFE; since you have 4GB, look at Ubuntu MATE, Lubuntu, or Xubuntu, the lightest-weight flavors. I personally prefer MATE, which is the desktop I started using back with 8.04, and which I love, but it is a matter of personal preference. 

Under the hood, all Ubuntu flavors are identical, and none is more secure than the others. For a firewall, just open a terminal and type```
sudo ufw enable
```The same repositories are used for all the flavors, and all use the same software (with some programs made for their own desktops, like (in the care of file managers) Konqueror for KDE, Caja for MATE, Thunar for XFCE, PCManFM for LXDE, etc.) For coding, all the languages you mentioned are available, and a bunch you might not yet have heard of; Linux is an ideal environment for any kind of coding. There are companies which develop in Linux first, then port to Windows and Mac. 

You can try burning a USB stick with one of the three lightweight flavors, boot each one, and see what you like the best. One of the great advantages of Linux is the wide choice of GUIs available, and there are more that aren't used in official Ubuntu flavors. The ones I mentioned are recommended for older or low-RAM hardware.

---

### Post by Damon_Campbell on 2016-05-05
Thank you for your feedback i just researched on Ubuntu Mate and i love it already it looks exactly like something that suits me thank you so much for the help i am downloading it now

---

### Post by Damon_Campbell on 2016-05-05
Also thank for the firewall feedback also it is very helpful but i have just one question, what exactly is ufw?

---

### Post by QIII on 2016-05-05
Hello!

To avoid confusion for yourself and others, it would be best to start a new thread for your question about ufw.

---

### Post by oldrocker99 on 2016-05-05
So you know, ufw stands for Uncomplicated FireWall.

---

### Post by courtney2 on 2016-05-05
> I have 4 GB of RAM which flavor runs fast on boot and while in use?
I think they're both good at booting speeds. Kubuntu used to be super slow with KDE 4 desktop for me (so get the newest LTS of Kubuntu). It's especially snappy when you get rid of the login splash in settings. In terms of snappiness, I'm using Kubuntu 16.04 on a solid state drive right now and it is very fast to load applications to the screen and do everything else you need. Again, I don't think the difference in speed will be dramatic between Ubuntu and Kubuntu.

> Which flavor has better gaming compatibility because i use steam?
I personally haven't noticed any differences in gaming compatibility. It's been a clean experience with me while using Kubuntu and it was for me when I used plain Ubuntu.

> I am also going onto the path of becoming a pentester and doing all that  hacking stuff which flavor is better for that environment?
This is all entirely up to you too because all the tools will work on either one just the same. But one thing that (IMO) think makes Kubuntu stand out more is some of the tools that Kubuntu has out of the box. KDE's system monitor (KSysGuard) makes it very easy to see what's mapped where in virtual memory for each process, as well as have more information about a detailed layout.

> I will also being doing coding like Python, HTML, PHP, Perl, etc. Which flavor takes that kind of environment?
I think this comes more down to what your favorite text editor is. I adore KATE and that was one reason why I chose Kubuntu. You could install KATE in Ubuntu too

> Which flavor has more security?
I don't know much about this here too..but in terms of tools it will have all the same, just as others are saying to enable ufw and use gufw for simple firewall management. This is also kind of a weak argument at this point, but Kubuntu I believe will have better support for the upcoming Wayland display server (vs the current and considered insecure X11 display server). Wayland was built with security in mind and KDE is working towards supporting it, however it's still not there yet. Plus in my testing Wayland only seems to work well with the GNOME desktop and Intel drivers..haven't had the chance to try GNOME with Nvidia drivers but last time it went nowhere.

> Sometimes i like to do usb tethering with my android, which flavor is good for that type of use?

If i'm not gaming or doing hacking stuff sometimes i like to sit back and watch movies, read e-books,
and make images (Like Photoshop), which flavor is good for that environment?

For android, they should both be equally capable. For your other question..I've become a fan of Dragon Player for movies, you can get GIMP for Kubuntu (I think it's preinstalled for Ubuntu?), you can also get other programs like Darktable (for RAW image editing), Inkscape and the KDE project develops a digital painting application called Krita which I don't know how to use, but I've seen others use it and it blew my mind to watch. If you want to read e-books then Calibre is good. Krita and Dragon Player are more specifically KDE desktop apps but can work in Ubuntu too.

> I like to multi-task to get more things done faster, which flavor is good for that?

Which flavor is good when it comes to using VPN's and Proxies?

I way way way much more prefer Kubuntu for multitasking. Krunner is amazing for quickly finding applications and files or doing basic math, you can choose from different launchers to see what fits your fancy, workspaces are much easier to manage and navigate and there are also Activities which I haven't gotten used to using but it's like having multiple sessions open within your session...if that makes sense. Plus, if you don't like stock KDE, you can move anything anywhere and created any number of panels you want. It's made to make it easy to make your desktop yours, which turned my eye to the desktop. I feel like I'm much more efficient on KDE. As for VPN and proxy setup, I think they're the same 

I hope this helps! :)

---

### Post by SeijiSensei on 2016-05-06
> **Damon_Campbell said:**
> I am also going onto the path of becoming a pentester and doing all that hacking stuff which flavor is better for that environment?

The desktop environment won't matter in this case because you're going to be running command-line programs like nmap most of the time.

---

