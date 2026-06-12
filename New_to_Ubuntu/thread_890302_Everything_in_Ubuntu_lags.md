---
title: "Everything in Ubuntu lags"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by stockholmsyndrome on 2008-08-14
Running a HP Pavilion dv6000 2ghz centrino w/1gb memory with a somewhat fresh install of hardy. I've since installed a few apps (games, elisa media center which BTW doesn't do anything when I open it, bsnes, skype, open office extensions, firefox extensions etc.) but most recently after what I believe was the result of installing Java JRE 6 everything I do is lagging and jumpy i.e. dragging windows is jerky, firefox flashes pages when they're done loading instead of showing each item load individually, and other programs otherwise function fine but they don't like being moved around the screen or in between desktops 1 or 2. Its even worse when I enable enhanced visual effects with the stretchy windows because they become exteremly difficult to undock. Just to note this is all from the moment I log in, I've disabled some of the session stuff (i.e. bluetooth, printers, evolution) and made those tweaks to firefox, but to no avail. I was thinking of just starting with a fresh install and maybe seeing if I can narrow down what I installed that may be causing this, but I'm not sure if you can install ubuntu on top of itself like you can with windows. I'd appreciate any assistance you can provide to the noob :P

Thanks,

Tom

---

### Post by mattismyname on 2008-08-15
I would open a terminal (Applications->Accessories->Terminal) and then run the command 'top'.  Top will list the applications using the most CPU time.

---

### Post by wolfen69 on 2008-08-15
there used to be a sticky concerning HP laptops, but i guess they have removed it, too bad, as there is alot of people that could benefit from it. especially the newer HP's.

---

### Post by stockholmsyndrome on 2008-08-15
> **mattismyname said:**
> I would open a terminal (Applications->Accessories->Terminal) and then run the command 'top'.  Top will list the applications using the most CPU time.

 5504 root      20   0  394m  46m 7244 S   25  4.6   1:50.82 Xorg               
 6288 thomas    20   0 20636  11m 6948 S    3  1.1   0:04.48 gtk-window-deco    
 5977 thomas    20   0 44992  19m  12m S    2  1.9   0:03.64 gnome-panel        
 5264 root      20   0  8908 2404 1628 S    1  0.2   0:00.10 console-kit-dae    
 5370 root      20   0  3420 1140  988 S    1  0.1   0:00.10 hald-addon-stor    
 6059 thomas    20   0 21676  14m 5772 S    1  1.4   0:04.42 compiz.real        
11959 thomas    20   0 95860  21m  11m S    1  2.2   0:01.42 gnome-terminal     
12039 thomas    20   0  2308 1120  852 R    1  0.1   0:00.96 top                
 8013 thomas    20   0  235m  50m  16m S    0  5.0   0:08.97 java_vm            
    1 root      20   0  2844 1692  544 S    0  0.2   0:01.22 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1

---

### Post by JSCIII on 2008-10-09
dude i need help, i don't know how to use ubuntu, but i've installed the 8.10 beta version in my PC and 'till now, I only know how to use word, games, IM, web browser and switch between desktops, can anyone tell me how to install programs and browse my disk space??? thanks!! :D

---

