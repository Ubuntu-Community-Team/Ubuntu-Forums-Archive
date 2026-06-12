---
title: "Installing &quot;Hal-Info&quot; for RTE Player-don't know how to do this"
date: 2013-03-17
forum: New to Ubuntu
---

### Post by SeoulGamer on 2013-03-17
Hi,

I want to watch videos on the RTE Player, an Irish website that you can watch Irish tv on. I couldn't watch any videos on this site because of an error message I kept recieving, despite having the Flash Plugin. I am using Ubuntu 12.04 LTS on a 2009 Dell Latitude E6500.

I found a thread detailing a solution to this exact issue, but the instructions given by user "[**[COLOR=#000000]TokyoCrusaders92[/COLOR]**]("http://ubuntuforums.org/member.php?u=1748096&")" didn't make any sense to me. I gather that the instructions are Terminal commands, but they didn't work for me and I assume I'm supposed to know something else about how Terminal works that he didn't describe.

How am I supposed to use the following commands, and why don't they work when I type them in as-is into Terminal?


                  [SIZE=2]"Re: Video error when watching a RTE player TV program         [/SIZE][INDENT]                     Hi,
   Your getting this error because the video is encrypted / DRM'd.  To  play this video the flash player downloads the required library into  ~/adobe/Flash_Player/NativeCache/.... The problem is this downloaded  library requires libhal which is not installed by default in a new  install anymore.  The following steps will fix the issue (they may not  all be necessary but it does work)

Close all browser windows

[B]1)      remove the adobe cache   -  rm ~/.adobe -rf
2)      install hal & hal-info  -  sudo apt-get install hal hal-info

3)       reinstall adobe player   - sudo apt-get install flashplugin-installer --reinstall[/B]

Open your browser and you should be good to go !! 

Ruairi                 "

These commands don't work when I type them into Terminal. I have never used Linux before. What else am I supposed to do to get this commands to work that he doesn't describe here?
[/INDENT]

---

### Post by GrouchyGaijin on 2013-03-17
Right those are terminal commands.
To run them open the terminal (open the dash by pressing the Windows key then type ter and click the terminal icon that appears).
 You can just paste one command in, run it by pressing enter and then paste the next command in and run that one by pressing enter.

To paste into the terminal press Ctrl+Shift+V. (Press the ctrl shift and V keys at the same time).
```
**rm ~/.adobe -rf**
```
```
** sudo apt-get install hal hal-info**
```
before this command executes, you will need to enter the root password
```
**sudo apt-get install flashplugin-installer --reinstall**
```
Since you just entered the root password after the second command, you probably won't have to enter it again after this command.

---

### Post by SeoulGamer on 2013-03-17
That worked perfectly, thanks a million.

---

### Post by ibjsb4 on 2013-03-17
First link

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=RTE+Player&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=RTE+Player&sa=Search&cof=FORID:9)

I did not remove anything, just installed "hal" and it worked.

[ATTACH=CONFIG]240280[/ATTACH]

EDIT: nevermind :)

---

