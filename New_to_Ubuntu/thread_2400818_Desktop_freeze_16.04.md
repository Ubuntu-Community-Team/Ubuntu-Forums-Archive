---
title: "Desktop freeze 16.04"
date: 2018-09-10
forum: New to Ubuntu
---

### Post by chaoticbob on 2018-09-10
I've recently migrated from Win10 to Ububtu 16.04 LTS. All went well  (thanks to you guys) until recently - my desktop intermittently freezes.  What I mean by that is that is that the app I'm working with is OK with  controls within its own window, but all desktop controls are dead - so  for example, if this were to happen now (I'm in Firefox) I'd still be  able to compose/post this message, but moving the pointer to the menu  bar at the top of the desktop wouldn't reveal the Firefox menus. And  right-clicking in the desktop space wouldn't do anything.
I can get round this with <CTRL><Alt><F[n<7]> to  bring up a console login , then <CTRL><Alt><F7> to  restart the GUI, which then works as expected. Obviously something is  broken somewhere - can anyone advise?
Robin.

---

### Post by Autodave on 2018-09-10
How long did your install work properly?  What video card do you have and did you install any driver for it? If so, what one and where did you get it from?

---

### Post by chaoticbob on 2018-09-10
Install worked properly for maybe four months. The machine is a low end Dell desktop - integrated graphics AFAIK. It just worked with a basic install, no drivers.
Robin

---

### Post by Autodave on 2018-09-12
First, I would boot the machine from your install medium and chose to "try" and see what happens.  If it still freezes like that, then you probably have a hardware issue rather than a software issue.

If it runs OK from the install medium, you may just want to reinstall it since you said that you have a basic install.  Just make sure to back up anything you need to keep.

If it freezes from the boot medium, then you need to look at hardware. Pull the cover and make sure that all of the cooling fans are functioning and clean.  Memory sticks fail often: if more than one stick, remove the one in slot #2 and try. If still freezing, insert that one into slot #1 and leave the one that was there out and see what happens.

---

### Post by mastablasta on 2018-09-13
i doubt it is a hardware issue if only the desktop (in the background) freezes. this is a DE (desktop environment) issue. sometimes a bug can make it crash. this is a somewhat familiar sight with testing or beta versions (DE crash). it shouldn't happen on stock version. especially not on 16.04 version which is more than 2 years old.

things to do: 
- check the system logs for any error messages (there should a log viewer of sorts pre-installed). since you can recover from the crash you should be able to spot where and when things went wrong. you can also access logs from console using a CLI text editor (for example nano). the logs are in /var/log
- check the desktop version. if you used or installed anything via PPA or directly from internet, it could happen that a system update pulled in newer versions of certain desktop files. this could make the DE unstable (e.g. partially upgraded)
- if you suspect that pc is running hot (is hot to the touch or blows out quite warm air), you can install psensor to monitor the temperature. if you know the CPU model you can check the optimal and max. work temp for the cpu. again i doubt this is the issue, but if all else is good... high temp would usually make it turn off or on GPU it would freeze the picture completely or crash it (something else would be on screen).

if you are unable to solve the crashes, you can switch to another desktop (i suggest XFCE). more on that later, but basically you just install it and select it at sign in.


if you do find a bug be sure to report it, by doing that you start a process to save others from getting the same problem.

edit: also please post the terminal output from the following two commands (you can copy and paste them into terminal and then just mark the result, copy&paste it to forums using code tags - the # icon in advanced answer).

```
lspci | grep VGA

sudo lshw -sanitize
```

more on this here: [https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

---

