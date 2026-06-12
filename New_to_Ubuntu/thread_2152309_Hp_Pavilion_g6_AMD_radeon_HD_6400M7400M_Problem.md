---
title: "Hp Pavilion g6 AMD radeon HD 6400M/7400M Problem"
date: 2013-06-07
forum: New to Ubuntu
---

### Post by dmavroid on 2013-06-07
Hello,

I am trying to solve the problem with my graphic drivers on ubuntu 13.04 for over 6 days now. i have found several solutions but none of them is working.

Symptomes:
Overheating--My CPU reaches 90degrees (when using xorg server option in additional drivers)
fglrx and fglrx-updates--when i am installing these two options (separetly) and login to my account i cannot see my unity. But when i am installing the drivers manually(form amd site) i am stuck with a poppular message of "system running in low graphic mode" and i cannot procceed to any further than that.

Strange...
i installed xubuntu and my temperature falled to 78degrees maximum and i can use fglrx with no-know problem. But if i switch back to ubuntu i cannot see my unity ( :S )

i have no problem with xubuntu but i like ubuntu more. so if someone can help me to solve this out i would be more than happy.

Thank you for your time and help

P.S. i really like ubuntu :P

---

### Post by ArminasAnarchy on 2013-06-07
If you google something like "ati drivers ubuntu", there's an Ubuntu Wiki page, detailing exactly how to install the drivers, but also how to enable hardware acceleration. Rather than trying to install them from the AMD website, it's probably better to use the fglrx drivers in the repositories, the wiki page will walk you through it quite nicely :).

The CPU is a different issue entirely. Laptops do get MUCH hotter than desktops - but 90c still seems very high. What exactly are you using to detect the temperatures? Generally speaking, anything detecting temperatures in the OS is usually miles off - though in my experience, it's usually under (rather than over) estimating them. Boot into your BIOS after running Prime95 (google it, it's a stress tester and will really put your PC through its paces!) for an hour or so (if you were going to test the stability, you'd want to run it for ~24 hours minimum, but we're doing it just to try to hit the maximum temps), then quickly reboot and see what your *BIOS* temperature reading is (the reading is usually given under something like "PC Health Status" or "HW Monitor" in the BIOS).
I know it sounds stupid, but make sure the laptop is on a hard surface too...even doing just casual things, my Samsung gets pretty warm unless I'm using a lap tray or book under it to make sure the material on my trousers isn't impeding the ventilation slots :P.

---

### Post by dmavroid on 2013-06-08
Thank you for your quick response!
At this point i am only considered about my graphic card, so i will leave the overheating problem for now.
I searched all over the internet and i found really helpfull instructions but unfortunatelly nothing worked :S ! 
May i give you a hint:
1)i haver tryied to install ubuntu 12.04 as well but i cannot go further than the GRUB. i get a message containing the word "killing" which repeats it self eternaly.
2)In my attempt to install ubuntu 13.04, the only way to get into the desktop environment (so i can install ubuntu) is to use nomodeset, otherwise.... black-screen.....

Thank you again for your time and help!

---

### Post by dmavroid on 2013-06-09
I would really appriciate a good advice

thank you

---

### Post by mastablasta on 2013-06-09
> **dmavroid said:**
> 
I searched all over the internet and i found really helpfull instructions but unfortunatelly nothing worked :S ! 

ok so you followed these instrucitons: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

to the letter and where exactly did it not work? any error messages?


probably the instrucitons under 3.2 if you have intel processor in the laptop.

[h=2][SIZE=2]3.2. Manually installing Catalyst 12.6, special case for Intel/AMD hybrid graphics[/SIZE][/h]

---

### Post by dmavroid on 2013-06-09
i followed the exact steps on section 3.2! after rebooting (step 9) i get a message "The system is running on low graphics mode". i Also googled this problem but nothing seems to work once more. To get pass this message i need to reconfigure my grphics in order to login!

---

### Post by abhich on 2013-06-18
have a look at this .
[http://askubuntu.com/questions/103253/how-do-i-turn-off-the-radeon-gpu-ono-my-hp-pavilion-dm4](http://askubuntu.com/questions/103253/how-do-i-turn-off-the-radeon-gpu-ono-my-hp-pavilion-dm4)

i had similar problems and this did the trick. hope it help you too.

---

