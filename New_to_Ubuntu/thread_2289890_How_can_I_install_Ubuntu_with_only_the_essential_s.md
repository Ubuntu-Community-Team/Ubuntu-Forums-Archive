---
title: "How can I install Ubuntu with only the essential software?"
date: 2015-08-07
forum: New to Ubuntu
---

### Post by Juan_Lucas_Laur on 2015-08-07
Hello!

I want to install Ubuntu, but I want to choose the apps myself. That is text editor, multimedia player, windowmanager, etc...

Is there a way to do that?

Thanks!

---

### Post by howefield on 2015-08-07
In that case I'd use the minimal cd as long as you don't have a UEFI system.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Basically starts you off with a minimal install and you get to choose pretty much every package to be installed. You would need a modicum of knowledge to navigate through this method. If that puts you off, then choose the Ubuntu flavour with the desktop environment that suits you, then add the packages that aren't included in your vision of perfection. :)

---

### Post by papibe on 2015-08-07
Hi Juan_Lucas_Laur. Welcome to the forum ):P

I'd start with the [minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD"), and then either use [tasksel]("https://help.ubuntu.com/community/Tasksel"), or better apt-get directly.

Here are a couple of links you may find interesting: [Installing plain Xfce instead of Xubuntu]("http://askubuntu.com/questions/116602/how-to-install-xfce-desktop-environment"), and [Setting up the Openbox window manager]("https://help.ubuntu.com/community/Openbox").

Hope it helps. Let us know how it goes.

Come here often, and have fun.
Regards.

---

### Post by oldrocker99 on 2015-08-07
Or, you can use Synaptic to search for and delete the programs you don't want, and to install the programs you **do** want.

---

### Post by Juan_Lucas_Laur on 2015-08-08
Mmmm... the minimal installation it's kinda hard for me yet :(, so maybe i'll try installing Ubuntu normally and manually deleting the programs I don't want. I have a few more questions, though;

If I like how Xfce looks like, but I don't like the applications that are bundled with it and preffer the ones of GNOME... Can I mix them up like that?
Is there any substancial difference between Kubuntu, Lubuntu, Ubuntu, Xubuntu, etc.? Or it is just the same thing, but with a different look?

Thanks!

---

### Post by Topsiho on 2015-08-08
They are basically the same thing, but have different desktops, and the choice of applications is different.
For years now I use Ubuntu, and KDE applications like KStars, without any trouble. KStars is an application of the KDE desktop, the desktop used in Kubuntu.

(I used to use Kubuntu, with KDE3, but don't like the KDE4 desktop for different reasons. Though I sometimes give it another try. Just personal I'm afraid)

Topsiho

---

### Post by HermanAB on 2015-08-08
Howdy,

The way I normally install a minimalist system, is to install a server version, then install a simple desktop such as XFCE and finally install the applications I need.

---

### Post by mörgæs on 2015-08-08
> **Juan_Lucas_Laur said:**
> 
If I like how Xfce looks like, but I don't like the applications that are bundled with it and preffer the ones of GNOME... Can I mix them up like that?
Is there any substancial difference between Kubuntu, Lubuntu, Ubuntu, Xubuntu, etc.? Or it is just the same thing, but with a different look?

Thanks!

Yes, you can mix as you please, but some applications might drag in dependencies.

The difference between the desktop environments is mainly the system load. Lubuntu is lightest and Ubuntu/Kubuntu heaviest.

---

### Post by howefield on 2015-08-08
> **Juan_Lucas_Laur said:**
> Mmmm... the minimal installation it's kinda hard for me yet :(, so maybe i'll try installing Ubuntu normally and manually deleting the programs I don't want. I have a few more questions, though;

Keep it in the back of you mind, it's probably the best solution and one you may gravitate to eventually.

> If I like how Xfce looks like, but I don't like the applications that are bundled with it and preffer the ones of GNOME... Can I mix them up like that?

Yes you can. What exactly are the applications that you would prefer to use in an xfce environment ?

> Is there any substancial difference between Kubuntu, Lubuntu, Ubuntu, Xubuntu, etc.? Or it is just the same thing, but with a different look?

Sort of. I wouldn't describe each flavour in that way, there is more to it than the look.

---

### Post by Juan_Lucas_Laur on 2015-08-08
> **howefield said:**
> Yes you can. What exactly are the applications that you would prefer to use in an xfce environment ?

Hmmm I like LibreOffice, VLC, Gedit, Nautilus... 

Also, I don't like some of the Xfce applications like Abiword or LeafPad much...

---

### Post by mörgæs on 2015-08-09
Then Xubuntu Core is worth trying.


[LIST=1]
[*]Install the minimal ISO as mentioned above using wired internet access.
[*]Reboot.
[*]Run ```
sudo apt-get install xubuntu-core^
``` It could take a while.
[*]Reboot.
[*]Install your favourite apps with a series of commands like ```
sudo apt-get install libreoffice
```
[/LIST]

More here: [http://xubuntu.org/news/introducing-xubuntu-core/](http://xubuntu.org/news/introducing-xubuntu-core/)

It's not as complicated as it sounds. Post again if you get stuck.

---

### Post by howefield on 2015-08-09
> **Juan_Lucas_Laur said:**
> Hmmm I like LibreOffice, VLC, Gedit, Nautilus... 

None of those would be difficult to add to Xubuntu and work fine. I'd be surprised if many (most) people didn't install LibreOffice and VLC into Xubuntu after installing it, maybe not so much for Gedit and Nautilus as Thunar and Mousepad are pretty competent. :)

> Also, I don't like some of the Xfce applications like Abiword or LeafPad much...

You could leave them alone, the only issue with leaving them is that they would take a tiny amount of disk space, the drawback in removing a package would be the dependencies that might be removed along with it, you need to be watch for that.

Looks like a choice between starting small (as mörgæs describes) and building up or starting big and knocking down :)

---

### Post by Topsiho on 2015-08-09
xfce is a lightweight desktop, and it stands to reason that for that desktop lightweight applications are chosen in stead of the heavyweight ones. Thus Abiword was chosen, and not LibreOffice. But you are completely free to install LibreOffice, and possibly drop Abiword. If your computer can handle LO, then why not. But then also: why chose a lighterweight desktop? A valid reason is of course you like that one better. Not everyone likes Ubuntu, and there are more valid reasons (privacy maybe :( ) to choose something else than Ubuntu.

Topsiho

---

### Post by Juan_Lucas_Laur on 2015-08-09
Does minimalCD installation works with a wireless conection?

---

### Post by howefield on 2015-08-10
> **Juan_Lucas_Laur said:**
> Does minimalCD installation works with a wireless conection?

The minimal installation media is really designed for a wired connection, but should work if your wireless adapter is supported out of the box, (you'll need to configure the connection on the command line though) if you have a wireless card that needs a proprietary driver then it gets much more difficult.

There are a few threads in the forum describing how to access wireless from a minimal install.

---

### Post by Juan_Lucas_Laur on 2015-08-10
I installed the minimal ISO with a wired connection, but, when I type ```
sudo apt-get install xubuntu-core^
``` on the console, the output I get is 
```
E: Unable to locate package xubuntu-core^
E: Couldn't find task 'xubuntu-core'
E: Couldn't find any package by regex 'xubuntu-core^'
```

I'm positive that I'm connected to the internet, because I can Ping google.com without problems. 

The output I get from console after typing sudo dhclient is ```
RTNETLINK answers: file exists
```

Any ideas about what could be the problem?

---

### Post by VMC on 2015-08-10
> **Juan_Lucas_Laur said:**
> I installed the minimal ISO with a wired connection, but, when I type ```
sudo apt-get install xubuntu-core^
``` on the console, the output I get is 
```
E: Unable to locate package xubuntu-core^
E: Couldn't find task 'xubuntu-core'
E: Couldn't find any package by regex 'xubuntu-core^'
```

...

Usually when that happens you need to update apt.

---

### Post by Juan_Lucas_Laur on 2015-08-10
> **VMC said:**
> Usually when that happens you need to update apt.

I gave it a try with sudo apt-get update, sudo apt-get upgrade and sudo apt-get dist-upgrade and the console still says that "it couldn't find any package by regex 'xubuntu-core^'" :(

---

### Post by howefield on 2015-08-11
> **Juan_Lucas_Laur said:**
> I installed the minimal ISO with a wired connection, but, when I type ```
sudo apt-get install xubuntu-core^
```

Why the character at the end ?

When you get that error, it generally means one of 3 things, you have no internet, you need to update or the package doesn't exist.

Looks like it is the latter reason for you. xubuntu-core^ doesn't exist but xubuntu-core probably does.

---

### Post by mörgæs on 2015-08-11
The caret at the end of the command is correct, but you might need the command ```
sudo apt-get install tasksel
``` first.

---

### Post by Juan_Lucas_Laur on 2015-08-11
I have tasksel already at it's newest version (according to the console) but still cant install xubuntu-core :/
I have Ubuntu 14.04.03. Does xubuntu-core work for that version?

---

### Post by howefield on 2015-08-12
According to this post from Elfy xubuntu-core is only available 14.10 onward..

[http://ubuntuforums.org/showthread.php?t=2278048&p=13285278&viewfull=1#post13285278](http://ubuntuforums.org/showthread.php?t=2278048&p=13285278&viewfull=1#post13285278)

which effectively means 15.04 given 14.10 is end of life.

If you use IRC, there are some great people in #xubuntu channel that may be able to confirm (faster than here).

---

### Post by Juan_Lucas_Laur on 2015-08-12
Well, I guess I'll just install Xubuntu and use Synaptic to uninstall the packages that I don't like :P

---

