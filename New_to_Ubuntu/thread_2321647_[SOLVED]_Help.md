---
title: "[SOLVED] Help"
date: 2016-04-23
forum: New to Ubuntu
---

### Post by kaika on 2016-04-23
Hi. Ok, my boyfriend has this PC with Ubuntu but it dosent work or it doesnt boot, i really dont know. So he challenge me to fix it, of course i said yes. I really have no idea how to do it but i´m willing to learn.

Everything its ok until this shows up

[ATTACH=CONFIG]268570[/ATTACH]

I tried entering through Advenced Options for Ubuntu and then many options where there, I clicked on the option that said repairing and then it showed up again.
i dont know if it may help but this showed up in the screen

GNU GRUB version 2.02 beta2-9 ubuntu1.7

Update "boot error end kernel panic - Attempt to kill init"

Super duper update: its fixed!! Thank youuu

---

### Post by RobGoss on 2016-04-23
Hello and welcome Kaika to the forum, Well I'm sure the members of this forum can guide you in the right direction

First things first- It will help us help you better if we knew what the specs were for that machine you're trying to get working

How much RAM
What Processor do you have 
What Type of Graphic card are you using and so on

The more info you can share with us the better we can assist you

---

### Post by kaika on 2016-04-23
MOBO: Asus M5A7BL LE 
RAM: CORSAIR cmv8gx3m1a1333c9 8GB
Graphic Card: Nvidia G210 1GB DDR3

He said that he changed the RAM from one slot to the next

---

### Post by grahammechanical on 2016-04-23
Has he also been over-clocking the system?

Do you have a Ubuntu install disc so that you can run a Ubuntu Try/Live session? I am thinking that if you can get to a Ubuntu Live session it might be proof that the kernel panic is not being caused by the hardware. 

If there have been attempts at over-clocking and you have a motherboard user guide you might want to research resetting the BIOS settings back to default settings. According to my Asus motherboard user guide (for a different motherboard to your one) there is an option to Load Default Settings under the BIOS settings utility's Exit menu.

EDIT: Is there another operating system on that machine? Does it load as it should?

Regards.

---

### Post by RobGoss on 2016-04-23
How will you be creating you bootable device Windows or using a Ubuntu desktop. And what would you like to use a DVD or USB drive.

I like using a USB it seems to work the best for me but it's your choice...

This might help you get started Using Ubuntu
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Windows instructions 
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by kaika on 2016-04-23
He said that he didnt overclocked. I tried to do the BIOS thing.. it didnt work.

Also, I dont have a CD or USB so i can run a Ubuntu, BUUUUUUT i have an usb drive that i can use to do that, i will try.

thank you

---

### Post by RobGoss on 2016-04-23
> **kaika said:**
> He said that he didnt overclocked. I tried to do the BIOS thing.. it didn't work.

Also, I dont have a CD or USB so i can run a Ubuntu, BUUUUUUT i have an usb drive that i can use to do that, i will try.

thank you


Once you get your ISO file loaded on to the USB depending how old your machine is you might have to go into your **BIO's **and change it to boot from that USB drive. You can then test Ubuntu out before you even install it by choosing the **Try Ubuntu **option.....

This will help you get things rolling
[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

---

### Post by Geoffrey_Arndt on 2016-04-23
Can you also confirm what version of ubuntu you are trying to install?    14.04 or 15.10 or 16.04 are supported.

---

### Post by kaika on 2016-04-23
Hi guys, I have ubuntu in a bootable usb, i have now entered in the BIOS of the pc, i dont know how to change the default to make it start from a usb.

---

### Post by kaika on 2016-04-23
theres no other operating system, i downloaded ubuntu in a bootable usb i tried it in my laptop and it worked. now im trying to start the PC through usb drive but i dont now where it issss!! im in the BIOS, in Boot section

---

### Post by RobGoss on 2016-04-23
Hello Kaika, How old in this machine?

The reason I'm asking is because if the machine is not that old you might be able to leave things are they are and just choose the right FKEY to get that machine to boot from your USB.

Most times you need to enter the bios using the **F-12** key and change the boot sequence, you then need to choose the **USB **as the first choice, this can be tricky if this is something you've never done before. When I was learning this I would always take a **snap shot** of my BIO's just in case anything when wrong I could put things back the way they were.

Once you get it to boot from the USB everything else will be straight forward...

---

### Post by DuckHook on 2016-04-23
Hi kaika,

We cannot help you with the BIOS setting because we obviously cannot see what you see. However, based on your specs, this should be a relatively new and powerful system, so you should have a USB option.

Rather than changing the BIOS, you can also try hitting <F2>, <F8>, <F10>, <F12> or the <Del> key as your system boots. Sorry there is no one key that works, but there is no consistency across MB manufacturers. If successful, this should bring up a boot device screen that will let you boot from USB.

---

### Post by kaika on 2016-04-23
Hey guys!! I DID ITTTTTTTT. Seriously thank you, you help me a lot.
I use the bootable usb and reinstaled the last version of ubuntu and it worked. Thanks to you I won the bet! 

Hope to speak to you soon, trust me I will have lots of questions 

Kiss:*

---

### Post by Geoffrey_Arndt on 2016-04-23
If you go to the PC makers web site, you should be able to download the "User Manual" in pdf format.   That will tell you exactly how to enable external boot devices.     What DuckHook writes above is often right, I've also seen that some PC's use F11.   This is called the "one time boot" sequence or something similar to that (you will get a menu with the device displayed, so you can choose it.).

By the way, what method & software did you use to create the bootable usb?

EDIT:   I see you solved it . . . good job and good luck!

---

### Post by kaika on 2016-04-23
I downloaded the thing from here 

[www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

**EDIT**

@kaika

I've taken the liberty of correcting your URL for the benefit of others who may view this thread.

---

### Post by DuckHook on 2016-04-23
Congratulations. I hope your boyfriend treats you to a nice dinner for your success.

---

### Post by RobGoss on 2016-04-23
> **kaika said:**
> Hey guys!! I DID ITTTTTTTT. Seriously thank you, you help me a lot.
I use the bootable usb and reinstaled the last version of ubuntu and it worked. Thanks to you I won the bet! 

Hope to speak to you soon, trust me I will have lots of questions 

Kiss:*

That's great it's always good to see someone new accomplish this. I guess you can do just about anything if you really put your mind to it congrats.

---

### Post by RobGoss on 2016-04-23
If you don't mind and you have solved your issue would you mind marking this thread as Solved, you can use the** Thread Tool **tab at the top of this post. Thanks you

---

