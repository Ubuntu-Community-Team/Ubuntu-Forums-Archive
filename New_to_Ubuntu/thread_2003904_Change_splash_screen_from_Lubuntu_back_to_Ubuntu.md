---
title: "Change splash screen from Lubuntu back to Ubuntu"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by cshin9 on 2012-06-14
I installed lubuntu-desktop on top of my Ubuntu installation. While that worked fine, the splash screen branding changed from Ubuntu to Lubuntu. How do I change it back to Ubuntu?

---

### Post by matt_symes on 2012-06-14
Hi

What is your default.plymouth alternative pointing to ?

From the terminal

```
update-alternatives --display default.plymouth
```

Please post back the results.

Kind regards

---

### Post by amjjawad on 2012-06-17
> **matt_symes said:**
> Hi

What is your default.plymouth alternative pointing to ?

From the terminal

```
update-alternatives --display default.plymouth
```

Please post back the results.

Kind regards

Hi Matt,

Not to interrupt anything but just a question if I may?

Will that behavior change if the last session that the user was logged in to was Ubuntu instead of Lubuntu?

@OP
I always do fresh installation as installing "lubuntu-desktop" package is NOT like installing Lubuntu itself.

Thanks :)

---

### Post by matt_symes on 2012-06-17
Hi amjjawad

> Not to interrupt anything but just a question if I may?

Will that behavior change if the last session that the user was logged in to was Ubuntu instead of Lubuntu?

The splash screen displays what the plymouth symlinks are pointing to and they get updated as part of the *.postinst scripts when a new desktop (etc) is installed. 

From

```
cat /var/lib/dpkg/info/plymouth-theme-ubuntu-logo.postinst
```

```

<snip>
configure)
        update-alternatives \
                --install /lib/plymouth/themes/default.plymouth default.plymouth \
                /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth 100 \
                --slave /lib/plymouth/themes/default.grub default.plymouth.grub \
                /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.grub
<snip>
```

They don't get reset after a reboot only when updated manually or un/installing software that will update them.

I first came across this when i installed kubuntu desktop in Ubuntu and my splash screen changed.

As lubuntu uses plymouth, i suspect it's the same with K/Ubuntu.

Kind regards

---

### Post by amjjawad on 2012-06-18
> **matt_symes said:**
> Hi amjjawad

They don't get reset after a reboot only when updated manually or un/installing software that will update them.


Hi and thanks for the information :)
So, it doesn't matter what session you login to, that will not update it unless ... as you mentioned above - thanks :)

> I first came across this when i installed kubuntu desktop in Ubuntu and my splash screen changed.
I don't install any other DE, I always use Fresh New Installation. So, I don't think I have come across that before :)

>  As lubuntu uses plymouth, i suspect it's the same with K/Ubuntu.
Yes, Lubuntu uses plymouth.

---

### Post by d.atanasov on 2012-06-18
Hi, 

As it was pointed after (l/k/x)ubuntu installation (as packages) the splash screen is changed. I had this many time during installing different sessions, but what I did was just a little bit too drastic to remove the plymouth packages that were for lubuntu (in my latest case). If you can set them by hand it will be better to have them (if you want). 

cheers

---

### Post by paul1149 on 2012-07-13
> **matt_symes said:**
> What is your default.plymouth alternative pointing to ?

```
update-alternatives --display default.plymouth
```

Please post back the results.

Hi Matt and everyone,

I have a similar problem. I tried out lxde, then lubuntu, then went back to lxde. Currently I have the lubuntu splash, followed by a maroon log in screen, and then finally the lxde desktop wallpaper.

The above command returns:

[INDENT][COLOR="DarkRed"]update-alternatives --display default.plymouth
default.plymouth - auto mode
  link currently points to /lib/plymouth/themes/lubuntu-logo/lubuntu-logo.plymouth
/lib/plymouth/themes/lubuntu-logo/lubuntu-logo.plymouth - priority 150
/lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth - priority 100
  slave default.plymouth.grub: /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.grub
Current 'best' version is '/lib/plymouth/themes/lubuntu-logo/lubuntu-logo.plymouth'.
[/COLOR][/INDENT]

This is not a big deal. I'm primarily interested in finding out how this thing ticks.

Thanks much.

---

### Post by matt_symes on 2012-07-13
Hi

> **paul1149 said:**
> Hi Matt and everyone,

I have a similar problem. I tried out lxde, then lubuntu, then went back to lxde. Currently I have the lubuntu splash, followed by a maroon log in screen, and then finally the lxde desktop wallpaper.

The above command returns:[INDENT][COLOR=DarkRed]update-alternatives --display default.plymouth
default.plymouth - auto mode
  link currently points to /lib/plymouth/themes/lubuntu-logo/lubuntu-logo.plymouth
/lib/plymouth/themes/lubuntu-logo/lubuntu-logo.plymouth - priority 150
/lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth - priority 100
  slave default.plymouth.grub: /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.grub
Current 'best' version is '/lib/plymouth/themes/lubuntu-logo/lubuntu-logo.plymouth'.
[/COLOR][/INDENT]This is not a big deal. I'm primarily interested in finding out how this thing ticks.

Thanks much.

The alternatives system allows one to have multiple versions of a type of program  installed and to select a particular program to run by default.

I think an example may explain it better.

One of the alternatives is an editor. This is a text editor that will run by default when you use certain programs that require a text editor.

To list the alternative text editors on my system, i can run this command
```

matthew@matthew-Aspire-7540 ~ % update-alternatives --display editor
editor - manual mode
  **link currently points to /usr/bin/vim.basic**
/bin/ed - priority -100
  slave editor.1.gz: /usr/share/man/man1/ed.1.gz
/bin/nano - priority 40
  slave editor.1.gz: /usr/share/man/man1/nano.1.gz
/usr/bin/gedit - priority 10
/usr/bin/mcedit - priority 25
  slave editor.1.gz: /usr/share/man/man1/mcedit.1.gz
/usr/bin/vim.basic - priority 30
  slave editor.1.gz: /usr/share/man/man1/vim.1.gz
  slave editor.fr.1.gz: /usr/share/man/fr/man1/vim.1.gz
  slave editor.it.1.gz: /usr/share/man/it/man1/vim.1.gz
  slave editor.pl.1.gz: /usr/share/man/pl/man1/vim.1.gz
  slave editor.ru.1.gz: /usr/share/man/ru/man1/vim.1.gz
/usr/bin/vim.tiny - priority 10
  slave editor.1.gz: /usr/share/man/man1/vim.1.gz
  slave editor.fr.1.gz: /usr/share/man/fr/man1/vim.1.gz
  slave editor.it.1.gz: /usr/share/man/it/man1/vim.1.gz
  slave editor.pl.1.gz: /usr/share/man/pl/man1/vim.1.gz
  slave editor.ru.1.gz: /usr/share/man/ru/man1/vim.1.gz
Current 'best' version is '/bin/nano'.
matthew@matthew-Aspire-7540 ~ % 
```The default editor program that is run is vim.basic. This is my preferred text editor. I have a number of other choices that i can choose from (such as nano) but these are not the default editor.

The system knows to run vim because of symlinks. 

When a text editor needs to be run it will look at /usr/bin/editor for an editor. 

This is a symlink that points to the alternatives in the /etc/alternatives/

```
matthew@matthew-Aspire-7540 ~ % ls /usr/bin/editor -l
lrwxrwxrwx 1 root root 24 Jan  5  2012 /usr/bin/editor -> /etc/alternatives/editor
matthew@matthew-Aspire-7540 ~ % 
```The alternatives directory is also populated with symlinks that point to the actual editor to run.

```
matthew@matthew-Aspire-7540 ~ % ls -l /etc/alternatives/editor      
lrwxrwxrwx 1 root root 18 Jun 18 22:00 /etc/alternatives/editor -> /usr/bin/vim.basic
matthew@matthew-Aspire-7540 ~ % 
```The system, after following the symlinks will find the editor to run. So when it checks /usr/bin/editor, it follows the links until it reaches /usr/bin/vim.basic.

```

matthew@matthew-Aspire-7540 ~ % readlink -f /usr/bin/editor 
/usr/bin/vim.basic
matthew@matthew-Aspire-7540 ~ %
```One can change the defaul editor used by changing where the symlink in /etc/alternatives points to and this is where the update-alternaives command comes in as it helps automate the process (You don't have to manually change the symlinks or the alternative files).

The same happens with the splash screen. The default alternative points to the splash screen to show. Change the default and a different splash screen will be displayed.

There is a bit more to it than that buut that is the basic idea of the alternatives system. It allows one to set a default from a number of alternatives.

Kind regards

---

### Post by paul1149 on 2012-07-13
Thanks, Matt. I appreciate that and will keep it in mind for further use. I looked at the lubuntu-logo.plymouth file, and it seems to be calling a script, which in turn looked complicated. I think I need to leave this be for now.

Thanks again,
p.

---

