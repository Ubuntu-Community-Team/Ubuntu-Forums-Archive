---
title: "Problem installing"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by humby on 2008-11-28
I just got Wubi and ran it. Everything went smooth. It said I have to reboot. So I did.

But here's what happens:

I boot Ubuntu.

I press ESC for the menu.

I choose normal install.

The Ubuntu logo shows up and then I end up on a command line screen. If I choose Live CD the same thing happens.

Any ideas?

EDIT: I have absolutely not the slightest idea what's going on - that's my very first attempt at installing any kind of Linux.

---

### Post by OldGrey on 2008-11-28
Looking at the screenshots it says to press Enter not Esc. Could that be the problem?

---

### Post by overdrank on 2008-11-28
Ok I see you have also posted in the Wubi section so lets just concentrate on the live cd. Have you checked the cd for errors
You may also want to check the hashes of the iso 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Then make sure you burn the cd as slow as possible.

---

### Post by humby on 2008-11-28
> **OldGrey said:**
> Looking at the screenshots it says to press Enter not Esc. Could that be the problem?

It says to press ESC right after I select to boot Ubuntu (in the very first picture). Then I select to start the installer and press ENTER.

And that's as far as I can go...

BTW: Can you tell me how to restart my PC from the command prompt?

---

### Post by humby on 2008-11-28
> **overdrank said:**
> Ok I see you have also posted in the Wubi section so lets just concentrate on the live cd. Have you checked the cd for errors
You may also want to check the hashes of the iso 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Then make sure you burn the cd as slow as possible.

I thought Wubi downloaded these itself? It did perform an MD5 checksum but beyond that I don't know...

---

### Post by overdrank on 2008-11-28
> **humby said:**
> I thought Wubi downloaded these itself? It did perform an MD5 checksum but beyond that I don't know...

I am sorry, I misunderstood as I thought you are using the live cd also and receive the inframs error also

---

### Post by humby on 2008-11-28
Hey no problem man and thanks for your help - I can certainly appreciate all the help right now!

---

### Post by overdrank on 2008-11-28
> **humby said:**
> Hey no problem man and thanks for your help - I can certainly appreciate all the help right now!

I am not familiar with wubi but on the second screen shot you are offered several choices, have you tried them?

---

### Post by humby on 2008-11-28
> **overdrank said:**
> I am not familiar with wubi but on the second screen shot you are offered several choices, have you tried them?

I haven't tried the ACPI and verbose options but will try them right now and will post result.

EDIT: Tried every option - still getting the BusyBox thing. Can it be because I have my whole disk encrypted?

Maybe I should get it on my USB stick for now...

---

### Post by cwsnyder on 2008-11-28
> **humby said:**
> I just got Wubi and ran it. Everything went smooth. It said I have to reboot. So I did.


The next thing you should have done was remove the Live CD as part of the boot process.

Reboot should first take you to a two item menu to choose between Window$ and Ubuntu (defaults to Window$ if you do not select Ubuntu within about 10 seconds).  Selecting Ubuntu should take you to a short pause where you can press the Esc key to show the menu, but the menu defaults to your install of Ubuntu, so you do not even have to view the menu.  You will come (eventually) to a Login Screen where you can log in as the user you created as part of the WUBI install process.

Log in, and you should be in Ubuntu, only installed on Windows.

---

### Post by humby on 2008-11-28
OK. So I did a persistent instal of Ubuntu on my 2GB USB drive following this article here:

[http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/)

It all seems to be working. It is pretty slow and gave me an error with the clock, then it froze and I had to cold reboot. But that's fixable, I'm sure someone else had it so I should find the answer.

Important thing is it works.

So I'm going to uninstall what Wubi has created and just go on to use Ubuntu from my USB.

Thanks everyone for your input!

---

### Post by overdrank on 2008-11-28
> **humby said:**
> OK. So I did a persistent instal of Ubuntu on my 2GB USB drive following this article here:

[http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/)

It all seems to be working. It is pretty slow and gave me an error with the clock, then it froze and I had to cold reboot. But that's fixable, I'm sure someone else had it so I should find the answer.

Important thing is it works.

So I'm going to uninstall what Wubi has created and just go on to use Ubuntu from my USB.

Thanks everyone for your input!
Ok great and if you choose you can aways run the live cd with out making any changes to your system. Good luck!

---

