---
title: "I have only one screen resoltion available"
date: 2019-04-28
forum: New to Ubuntu
---

### Post by Morten_Fjellheim on 2019-04-28
Dear community. Its the first time i post here in a very long time. I tried Ubuntu a few years ago but uninstalled it when si couldnt get some of my favourite games to work. I am sorry if this post doesnt fit the minimum requirements for posts on this forum. Please inform me if this is the case.
I have tried to search this forum and other places, but i cant find something that directs me to a solution.

After i installed the newest ubuntu version earlier today, the only available screen resolution is 1024x768 (4:3). No other resolution is visible in the settings. It also says that Ubuntu doesnt recognise my screen (unknown screen). I dont know what is causing this, it worked fine when i was testing ubuntu from the flash drive.

---

### Post by NM5TF on 2019-04-28
we could use more information to even begin to help you...

to clarify:

this was a clean install of some form of Ubuntu, and not just an upgrade from some previous version ??

the display worked correctly with the live .iso on a flash drive, but not after installation ??

I suspect that you have a nvidia graphics card.....

can you  post the output of 

```
inxi -F
```

that will tell us a lot about your system hardware & software drivers....

can you also post the output of 

```
xrandr
```

that will tell us how the OS interacts with the display...it might look something like mine...

```
[tommy@tommy ~]$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 4096 x 4096
VGA-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1920x1080     60.00*+
   1366x768      59.79  
   1280x800      59.81  
   1280x720      60.00  
   1024x768      75.03    70.07    60.00  
   800x600       72.19    75.00    60.32  
   640x480       75.00    72.81    59.94  
   720x400       70.08  

```
 please use [COLOR="#FF0000"]code tags[/COLOR] to paste your responses into...this makes them more readable...use the [COLOR="#FF0000"]Adv Reply button[/COLOR], select the [COLOR="#FF0000"]#[/COLOR] from the drop down menu,
and paste your responses between the # characters...

we can go from there...

tommy

---

