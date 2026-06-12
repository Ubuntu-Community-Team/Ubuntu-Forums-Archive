---
title: "[SOLVED] Ubuntu shift to Edubuntu !?"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by Evil79 on 2008-10-26
Excuse me, i Installed "Ubuntu" on my laptop. and started downloading updates left and right trying to get better Desktop graphics.

well after that i tried restarting. and i noticed that my Ubuntu logo is no more.

Instead there was another logo showing "Edubuntu".

when i red about it on the ubuntu site i was shoked that it was used for learning mainly children!

Now iam assuming the shift from Ubuntu to Edubuntu was done because i started downloading updates left and right withought actually checking them. i thought the more the better.

But i wanted to make sure before formatting my laptop :confused:

Many thanks and appreciation in advance.

Kind regards,
Evil.

---

### Post by tompickles on 2008-10-26
you probably downloaded the edubuntu-desktop package.

try ```
sudo apt-get remove edubuntu-desktop
``` in the terminal to remove all the edubuntu stuff.

thank that is the correct package..... could someone please confirm?

---

### Post by prismpirate on 2008-10-26
> **Evil79 said:**
> Excuse me, i Installed "Ubuntu" on my laptop. and started downloading updates left and right trying to get better Desktop graphics.

well after that i tried restarting. and i noticed that my Ubuntu logo is no more.

Instead there was another logo showing "Edubuntu".

when i red about it on the ubuntu site i was shoked that it was used for learning mainly children!

Now iam assuming the shift from Ubuntu to Edubuntu was done because i started downloading updates left and right withought actually checking them. i thought the more the better.

But i wanted to make sure before formatting my laptop :confused:

Many thanks and appreciation in advance.

Kind regards,
Evil.
I seriously wondered how installing the edbuntu package could improve one's graphics? Maybe the logo looks nicer? Anyways, as tompickles mentioned, 

```

sudo apt-get remove edubuntu-desktop

```

and if you have accidentaly removed your ubuntu desktop:

```

sudo apt-get install ubuntu-desktop

```

---

### Post by Evil79 on 2008-10-26
> **tompickles said:**
> you probably downloaded the edubuntu-desktop package.

try ```
sudo apt-get remove edubuntu-desktop
``` in the terminal to remove all the edubuntu stuff.

thank that is the correct package..... could someone please confirm?

Maybe iam not sure, i just downloaded all the available programs and additional upgrades in hope of getting my VGA updates in order to have better desktop graphics.

Any way ill try that link once iam back from work.

Many thanks for the reply.

Kind regards,
Evil.

---

### Post by Evil79 on 2008-10-26
> **prismpirate said:**
> I seriously wondered how installing the edbuntu package could improve one's graphics? Maybe the logo looks nicer? Anyways, as tompickles mentioned, 

```

sudo apt-get remove edubuntu-desktop

```

and if you have accidentaly removed your ubuntu desktop:

```

sudo apt-get install ubuntu-desktop

```

Maybe i didn't explain the issue as clear as i thought. my apologies. what i meant was i tried to activate the desktop graphics. and i faild. thus i tried downloading all the programs and updates available in hope that one of them will be the Graphic update or the VGA update.

but as i mentioned that changed my login screen to Edubuntu instead of Ubuntu.

Any way ill try that Code you mentioned hopfully it will change back my Ubuntu.

Many thanks for the reply.

Kind regards,
Evil.

---

### Post by C.S.Cameron on 2008-10-26
You can also open synaptic and un-check edubuntu-desktop.

---

### Post by Evil79 on 2008-10-26
> **C.S.Cameron said:**
> You can also open synaptic and un-check edubuntu-desktop.

Indeed it was easier than i thought, i just opened that and unchecked edubuntu and the logo screen is gone.

Many thanks "C.S.Cameron",

Kind regards,
Evil.

---

### Post by Evil79 on 2008-10-28
Ok now the main issue is done. however there is one tiny issue, and its not that important it is just bugging me and i would love to understand the reason.

When i Restart my PC. i get a Loading "Ubuntu" screen.

After the PC restarts. i get a loading "Edubuntu" screen.

But when the Login screen is up. it is an "Ubuntu" screen.

>.< so any idea why is that Edubuntu screen still there !?

Many thanks and appreciation in advance.

Kind regards,
Evil.

---

### Post by Evil79 on 2008-10-28
My apologies, but any idea what could case such a thing Gents ?

Kind regards,
Evil.

---

### Post by Evil79 on 2008-10-28
Still no idea Gents ?

---

### Post by scorchgeek on 2008-10-28
There's probably some other Edubuntu package that hasn't been removed. You could try opening Synaptic Package Manager and doing a search for "Edubuntu" to see if there's a package you haven't uninstalled yet.

---

### Post by dracayr on 2008-10-28
execute ```
sudo update-initramfs -u
```

dracayr

---

### Post by Evil79 on 2008-10-28
> **scorchgeek said:**
> There's probably some other Edubuntu package that hasn't been removed. You could try opening Synaptic Package Manager and doing a search for "Edubuntu" to see if there's a package you haven't uninstalled yet.

Ill try that, although i already checked that several times but maybe something new pops.

Thanks for your time "[COLOR="Red"]scorchgeek[/COLOR]".


Kind regards,
Evil

---

### Post by Evil79 on 2008-10-28
> **dracayr said:**
> execute ```
sudo update-initramfs -u
```

dracayr


From now on ill call you GOD lol. it worked ! Thanks alot "[COLOR="Red"]dracayr[/COLOR]".

Kind regards,
Evil.

---

### Post by mac71 on 2008-10-28
Go to synaptic and install StartUp-Manager.
You can then access it through system>administration. Once you're in you can hit the appearance tab and down the bottom there, you'll find uslpash theme. Just change it back to ubuntu and close.
Let it update and restart to see the return of the ubuntu usplash screen.

---

