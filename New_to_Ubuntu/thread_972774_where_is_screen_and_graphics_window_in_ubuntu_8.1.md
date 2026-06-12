---
title: "where is screen and graphics window in ubuntu 8.1"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by miroooo on 2008-11-06
i have installed ubuntu 8.1 and can not find  screen and graphics preferences window

any one:confused::confused::confused::confused:

where is screen and graphics window in ubuntu 8.1 

***********************
all the best 

************
miroooo

---

### Post by eternalnewbee on 2008-11-06
**Screen Resolution**: Main Menu > System > Preferences > Screen resolution.
**Graphics** (Do you mean Hardware Driver?): Main Menu > System > Administration > Hardware Drivers.

---

### Post by eternalnewbee on 2008-11-06
To make your life even easier:

---

### Post by miroooo on 2008-11-06
screen resolution does not give me the optimum resolution for my screen 

i want the terminal code for the screen and graphics preferences window

---

### Post by alwayshere on 2008-11-06
gksudo displayconfig-gtk

---

### Post by eternalnewbee on 2008-11-06
> screen resolution does not give me the optimum resolution for my screen 
Check if your Hardware Driver is activated.

---

### Post by miroooo on 2008-11-06
i am newbie

what after applying the code?


and how to Check if my Hardware Driver is activated?

---

### Post by eternalnewbee on 2008-11-06
> and how to Check if my Hardware Driver is activated?
Main Menu > System > Administration > Hardware Drivers.
Did you see the screenshots?

---

### Post by miroooo on 2008-11-06
no thing in it


and what after applying the code?

---

### Post by eternalnewbee on 2008-11-06
No idea about the code. It looks like yo've got an onboard graphic card.
Are you trying to enable compiz?
EDIT: I just tried the code myself and nothing happened after that. Did you get any info?

---

### Post by miroooo on 2008-11-06
yeah, I have on board graphic card

---

### Post by eternalnewbee on 2008-11-06
OK. I found these links that might be of further help to you:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
[http://ubuntuforums.org/showthread.php?t=972453&highlight=screen+resolution](http://ubuntuforums.org/showthread.php?t=972453&highlight=screen+resolution)
[http://www.ubuntu1501.com/2008/04/restart-x-server.html](http://www.ubuntu1501.com/2008/04/restart-x-server.html)
Good reading.

---

### Post by ex-wirecutter on 2008-11-06
I would be a bit careful about using gksudo displayconfig-gtk if I was you, it does not seem to work too well with Intrepid and certainly screwed up my computer .

---

### Post by eternalnewbee on 2008-11-06
> 
You have to run the fusion icon in order to get the effects.
And I would like to say to alwayshere that if you do give advice to follow up.
Not just mention a code and that's it. (no offence meant. Just positive criticism)

---

### Post by miroooo on 2008-11-06
yes, i am agree with you 


p.s i still lost here

i can not configure my screen

---

### Post by alwayshere on 2008-11-08
Just ask and i will reply to you

---

### Post by alwayshere on 2008-11-08
Be a good idea to find out what graphics card you got 
here's an application which can give info on your hardware will be handy to have .Heres how to get it and how to see witch graphics card let us know what ya got > Go to applications  
then 
add/remove 

in search box type 
sysinfo

now tick the box for sysinfo
then
click apply now let it do its thing then close add/remove

Go to applications 
then 
system tools (which you will now have)
open sysinfo 
click hardware
then in dropbox pick graphics card 
click the little triangle 
and the name of your card will show




Or in terminal put

sudo su

then

lshw

will give hardware info in non grapical way

---

