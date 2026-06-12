---
title: "Moving files..."
date: 2012-09-03
forum: New to Ubuntu
---

### Post by Controll on 2012-09-03
I'm just trying to move one folder from my desktop, to my themes folders via terminal in xubuntu 12.04, but forget how to do so...And google hasn't helped.

Any help?

---

### Post by 73ckn797 on 2012-09-03
Can't you just "cut"" then "paste" into the new folder using the file manager?

---

### Post by Controll on 2012-09-03
> **73ckn797 said:**
> Can't you just "cut"" then "paste" into the new folder using the file manager?

It's not allowing me to paste into my themes folder, besides, I would prefer to know how to move things around in terminal, rather than cut and paste.

---

### Post by 73ckn797 on 2012-09-03
> **Controll said:**
> It's not allowing me to paste into my themes folder, besides, I would prefer to know how to move things around in terminal, rather than cut and paste.

Does the folder have permissions to allow you to make the move? 

Check out this helpful link: [http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by TheMTtakeover on 2012-09-03
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

scroll down to the File & Directory Commands Section.

---

### Post by Controll on 2012-09-04
Okay, I am moving files now, and I can move the folder around just fine from say, desktop to Documents, but when I try to move the folder to my Themes folder, it tells me it cannot move the folder (named: axis) because no such directory exists.

---

### Post by oldos2er on 2012-09-04
> **Controll said:**
> Okay, I am moving files now, and I can move the folder around just fine from say, desktop to Documents, but when I try to move the folder to my Themes folder, it tells me it cannot move the folder (named: axis) because no such directory exists.

Can you copy and paste the exact command and output here so we can see it?

---

### Post by Linux_junkie on 2012-09-05
Using the terminal...
sudo mkdir path/to/dir
sudo cp files from source dir to target dir (as set out above)

Understand this?

---

### Post by Controll on 2012-09-07
controll@Controll:~/Downloads$ mv axis ~/usr/share/Themes
mv: cannot move `axis' to `/home/controll/usr/share/Themes': No such file or directory

Sudo doesn't make it work, either.

controll@Controll:~/Downloads$ sudo mv axis ~/usr/share/Themes
[sudo] password for controll: 
mv: cannot move `axis' to `/home/controll/usr/share/Themes': No such file or directory

---

### Post by deadflowr on 2012-09-07
Hi, try again, but this time remove the grave symbol "~" from the target destination. The grave symbol is shorthand for your home directory so ~/usr/share/themes means
/home/username/usr/share/themes.

---

### Post by steeldriver on 2012-09-07
I think you're confused about a number of things here:

1. Linux filenames are case sensitive - if the directory is /usr/share/themes then /usr/share/Themes is not going to work

2. the ~ (twiddle or tilde) character is a synonym for your home directory, so ~/usr is not the same as /usr

AFAIK the 2 places you are likely to want to put themes are 

```
/usr/share/themes
```(this will need 'sudo' to write or mv files to, and will make them available to all users)

or

```
~/.local/share/themes
```(which will be for personal themes) although the latter may not exist out of the box - in which case you'd need to create it first with

```
mkdir  ~/.local/share/themes
```Hope this helps

---

### Post by Controll on 2012-09-07
> **steeldriver said:**
> I think you're confused about a number of things here:

1. Linux filenames are case sensitive - if the directory is /usr/share/themes then /usr/share/Themes is not going to work

2. the ~ (twiddle or tilde) character is a synonym for your home directory, so ~/usr is not the same as /usr

AFAIK the 2 places you are likely to want to put themes are 

```
/usr/share/themes
```(this will need 'sudo' to write or mv files to, and will make them available to all users)

or

```
~/.local/share/themes
```(which will be for personal themes) although the latter may not exist out of the box - in which case you'd need to create it first with

```
mkdir  ~/.local/share/themes
```Hope this helps

This worked, thanks! But now I am having trouble setting the theme. Through settings manager I go to Appearance, and click on the Style tab, but the theme: axis, is not listed. I also noticed that quite a few other themes that come stock with xubuntu aren't listed as well, but are in the folder.

---

### Post by steeldriver on 2012-09-07
Is there an xfwm4 subdirectory inside your new theme dir? or just gtk2? I think there are extra steps required to make gtk themes work with Xubuntu - not sure though

I think if you look in the /usr/share/themes dir you will see that is the difference between the ones that show up in Settings Manager and those that don't

Also it seems like the default themes dir for Xubuntu is ~/.themes not ~/.local/share/themes as I said above - although fwiw I just dropped a theme set in ~/.local/share/themes and the Settings Manager saw them right away (they are native xfwm4 themes though)

---

### Post by Controll on 2012-09-09
> **steeldriver said:**
> Is there an xfwm4 subdirectory inside your new theme dir? or just gtk2? I think there are extra steps required to make gtk themes work with Xubuntu - not sure though

I think if you look in the /usr/share/themes dir you will see that is the difference between the ones that show up in Settings Manager and those that don't

Also it seems like the default themes dir for Xubuntu is ~/.themes not ~/.local/share/themes as I said above - although fwiw I just dropped a theme set in ~/.local/share/themes and the Settings Manager saw them right away (they are native xfwm4 themes though)

There is only an xfwm4 subdirectory.

---

### Post by Controll on 2012-09-12
> **Controll said:**
> There is only an xfwm4 subdirectory.

Any other help here?

---

### Post by steeldriver on 2012-09-12
where did you get the theme from? if you can post a link I will try to install it on my 12.04 Xubuntu laptop and see if I can troubleshoot it for you

---

### Post by Controll on 2012-09-12
> **steeldriver said:**
> where did you get the theme from? if you can post a link I will try to install it on my 12.04 Xubuntu laptop and see if I can troubleshoot it for you

[http://xfce-look.org/content/show.php/axis?content=95158](http://xfce-look.org/content/show.php/axis?content=95158)

---

### Post by december0123 on 2012-09-12
Put that theme into /usr/share/themes. You will probably need to run your command with sudo.

---

### Post by hypnot0ad on 2012-09-12
> **december0123 said:**
> Put that theme into /usr/share/themes. You will probably need to run your command with sudo.

This did it for me

---

### Post by Controll on 2012-09-12
> **december0123 said:**
> Put that theme into /usr/share/themes. You will probably need to run your command with sudo.

I've done this, even moved the subfolder xfwm4 out into /usr/share/themes, and still it doesn't show up under Appearance in Settings Manager.

---

### Post by steeldriver on 2012-09-12
well it works for me

```
tar xvf 95158-axis-xfwm.tar.gz -C ~/.themes
```and then Settings -> Settings Manager -> Window Manager -> Styles

FWIW it also works if I untar it into ~/.local/share/themes

---

### Post by Controll on 2012-09-12
> **steeldriver said:**
> well it works for me

```
tar xvf 95158-axis-xfwm.tar.gz -C ~/.themes
```and then Settings -> Settings Manager -> Window Manager -> Styles

FWIW it also works if I untar it into ~/.local/share/themes

Yeah I just figured out it isn't an Appearance theme, if that makes any sense.

I moved the xfwm4 folder back to axis and checked Windows Manager and there it was.

Thanks for the help.

---

