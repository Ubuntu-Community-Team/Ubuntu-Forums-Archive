---
title: "no boot logo upon start up or reboot"
date: 2015-05-15
forum: New to Ubuntu
---

### Post by sypher2 on 2015-05-15
Im dual booting mac osx and xubuntu and i dislike not having some type of logo "greet" me as i boot into xubuntu. all i see is a terminal like interface with the booting sequence. anyway i can change this?

---

### Post by sypher2 on 2015-05-15
sorry for the duplicate, didnt know how to delete other one.
still need an answer please :)

---

### Post by slickymaster on 2015-05-15
> **sypher2 said:**
> sorry for the duplicate, didnt know how to delete other one.
still need an answer please :)
No problem.

Just one thing, remove the [SOLVED] prefix from this thread, using the thread tools at top right, so forum users don't get mislead and assume that your issue is already fixed.

---

### Post by tristan16 on 2015-05-16
Well, the first thing that comes to mind is grub. Open grub's configuration with:

```
sudo gedit /etc/default/grub
```

And make sure the "quiet splash" is enabled in the text file:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

If you have to change that line, make sure you save the file and update grub with:

```
sudo update-grub
```

---

### Post by sypher2 on 2015-05-16
> **tristan16 said:**
> Well, the first thing that comes to mind is grub. Open grub's configuration with:

```
sudo gedit /etc/default/grub
```

And make sure the "quiet splash" is enabled in the text file:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

If you have to change that line, make sure you save the file and update grub with:

```
sudo update-grub
```

let me add a bit more info. When i boot into xubuntu, i see the terminal style loading page fast scrolling down. after pages and pages, then it goes to my splash screen that i set in my regular settings tab. but it just flashes for not more then 1-2 seconds. is their a way i can cover up the entire terminal loading screen with a "loud" splash screen?

Tristan16 my config already has that line uncommented :(

---

### Post by tristan16 on 2015-05-16
> **sypher2 said:**
> let me add a bit more info. When i boot into xubuntu, i see the terminal style loading page fast scrolling down. after pages and pages, then it goes to my splash screen that i set in my regular settings tab. but it just flashes for not more then 1-2 seconds. is their a way i can cover up the entire terminal loading screen with a "loud" splash screen?

Tristan16 my config already has that line uncommented :(

Is the grub graphical terminal disabled? Make sure this line is commented out.

```
# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console
```

---

### Post by sypher2 on 2015-05-18
that worked! thankyou!

---

