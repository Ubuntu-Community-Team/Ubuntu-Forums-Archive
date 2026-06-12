---
title: "webcam and printer drivers not found"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by sandeep314 on 2008-10-01
hey all,

i have a brother mfc 6800 printer and i also have a creative live cam notebook pro (vf0250) 

can anyone help me find the drivers ...please....or else i would have to switch back to windows and dont wanna do that....am very happy with linux...

also another silly question.....
i have an acer aspire 3690....and this originally came with windows xp and i recently installed ubuntu 8.04 and i wanted to know if i can install mac os x...and maybe i wont have compatabiltiy issues...any suggestions...

thanks

---

### Post by wolfen69 on 2008-10-01
[Here]("http://www.linuxprinting.org/ppd-o-matic.cgi?driver=hl7x0&printer=Brother-MFC-9050&show=0") is the PPD file to get the printer working. post back if you do not know how to install it. i can't help you with the webcam.

the ppd file is for the mfc-9050, but also works for the 6800. per [here]("http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-MFC-9050").

if you can not get the webcam to work, perhaps you could buy a compatible one? well worth the investment to finally get rid of windows. i dual booted for a while until i got a compatible printer, then bye bye windows.

---

### Post by cariboo on 2008-10-01
For us to help you to get your webcam working we are going to need a little more information. Could you post the output of:

```
lsusb
```

You will have to do this in a Applictions-->Accessories-->Terminal.

If you want to know about installing pirated software you will have to go somewhere else.

Please read this post before asking questions:

[http://ubuntuforums.org/showthread.php?t=885589](http://ubuntuforums.org/showthread.php?t=885589)

Jim

---

### Post by sandeep314 on 2008-10-02
thankyou for the ppd file for the printer. can you please give me step by step the next thing to do. I have opened the ppd file and dont know what to do..sorry for sounding stupid, but i am a new user on ubuntu 8.04 
any help is appreciated.

Thanks,

---

### Post by sandeep314 on 2008-10-02
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 04f9:0111 Brother Industries, Ltd MFC 6800
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 041e:4051 Creative Technology, Ltd 
Bus 001 Device 001: ID 0000:0000

This is what i get when i type lsusb on the terminal.
what exactly does this mean
any help with the camera and printer would be greatly appreciated.

Thanks

---

### Post by duffrecords on 2008-12-19
Try the [hacked ov51x-jpeg module]("http://www.rastageeks.org/ov51x-jpeg/index.php/Main_Page"), specifically the svn version, as there's an error in version 1.5.9.

---

### Post by hyper_ch on 2008-12-19
you have to read the install instructions at the brother site. You'll very likely need to create a print queue yourself. Besides that "difficult" install instructions the brother printers/mfcs I've used this far just work perfectly. Have a read here:  [http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)

---

