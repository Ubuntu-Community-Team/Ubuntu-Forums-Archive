---
title: "Run windows apps on ubuntu"
date: 2024-04-03
forum: New to Ubuntu
---

### Post by noixyy on 2024-04-03
I am trying to install wine to run windows apps in ubuntu. I am getting the error "Unable to correct problems, you have held broken packages." after I run the command "sudo apt install --install-recommends winehq-stable". It is also important to note that I am using the "try ubuntu option" when booting from a usb so I do not have ubuntu installed on my computer. I am planning to make the switch from windows to ubuntu I just want to learn the desktop version of ubuntu and make sure all of my apps work before I do.

---

### Post by Rubi1200 on 2024-04-03
Try running this first before attempting to install WINE:

```
sudo apt update
```

---

### Post by noixyy on 2024-04-04
I’ve tried this many times.

---

### Post by ajgreeny on 2024-04-04
Tell us all you can about your hardware and OS software by running terminal command
**inxi Fzx**
Then copy back here the output from that using code tags please.

There is a How-To for code tags in my signature below.

---

### Post by gezzer2 on 2024-04-04
if you're running from a live USB aka 'Try Ubuntu' you wont be able to install WINE as it will not be able to install as Ubuntu is not installed.
you could try it if you had persistence enabled when creating the install USB but im unsure if that would work.

the try Ubuntu option is to ensure your hardware works and is compatible ..

---

### Post by Impavidus on 2024-04-04
You can check the [wine application database](https://appdb.winehq.org/) to see if other people had success using your applications on Wine and read about any tuning they needed.

Using native Linux applications is usually better than using Wine and for most applications a good Linux alternative exists. The exception are games. Some Linux games are available, but most games are Windows only. They may work on Wine.

---

### Post by aljames2 on 2024-04-04
There is also the possibility of running your Windows apps in a Windows virtual machine, or a dual boot system.  If Windows games are the main goal you likely will need to be running on your hardware. I have never tried Wine. I looked in to it once for my Fritz & Chessbase programs but they were not going to work on Wine in my case, so I promoted an old laptop to run windows and do that job.  Dual boot would have also worked.  Lots of ways to approach it depending on your needs & what you have access to.

---

### Post by yancek on 2024-04-04
I'd agree with the post above suggesting you check the wine database for windows applications.  You can install software using a 'live' Ubuntu but you do understand that if you reboot, any changes made will be lost.  I've used 'live' systems and installed software and used it but it is gone on reboot unless you have persistence.  I don't know about wine as I"ve never used it.

---

### Post by noixyy on 2024-04-04
I ended up installing ubuntu on a VM for my testing. I got wine to install but it crashes when I try to run any programs.

---

### Post by QIII on 2024-04-04
It might be helpful for others who would like to assist you if you would describe in detail the behavior you nebulously call "crashing".  Also, please describe the virtualization method you are using.

---

### Post by noixyy on 2024-04-05
I am using Oracle Virtualbox with Ubuntu 22.04. I was trying to run the Battle.net program from Blizzard. The setup runs fine and installs on the VM without any problems, but when I try to run the installed program it says "The program battle.net.exe encountered a serious problem and needs to close. We are sorry for the inconvenience".

---

### Post by yancek on 2024-04-05
You forgot to post a link to the site for the software you are asking about.  Is it the software described at the link below?

[https://us.shop.battle.net/en-us](https://us.shop.battle.net/en-us)

If  it is, when clicking on the Download link, the only option is to  download a file named Battle.net-Setup.exe which is a windows file.   Doing an online search for 'battle.net with blizzard on linux' gets the  page below which explicitly states 'Our games are not intended to work  on Linux'.  

[https://us.battle.net/support/en/article/11571](https://us.battle.net/support/en/article/11571)

If you don't see it on the list at winehq, I doubt it will work

---

### Post by noixyy on 2024-04-05
I was trying to install Battle.net with wine, and it says something along the lines of "The program has encountered a serious error and has to exit". Although I was able to get notepad++ working with wine so I am guessing there are other things that I need to configure to be able to run Battle.net. I am using Oracle's Virtualbox on windows 11.

---

### Post by MAFoElffen on 2024-04-05
Sort of a challenge with WINE, but works in top of Lutris: [https://forum.winehq.org/viewtopic.php?t=37565](https://forum.winehq.org/viewtopic.php?t=37565)

---

### Post by Tadaen_Sylvermane on 2024-04-05
I'd also like to add the suggestion of the Bottles flatpak. It's self contained so you don't have to worry about foreign packages on your system running amok. And it has run everything I've tried. With CLI wine / pol / lutris it was always a crapshoot. And more often than not some stuff just flat failed with little to no explanation for me. I gave up on standard wine and my life is much better for it.

---

### Post by MAFoElffen on 2024-04-05
> **Tadaen_Sylvermane said:**
> I'd also like to add the suggestion of the Bottles flatpak. It's self contained so you don't have to worry about foreign packages on your system running amok. And it has run everything I've tried. With CLI wine / pol / lutris it was always a crapshoot. And more often than not some stuff just flat failed with little to no explanation for me. I gave up on standard wine and my life is much better for it.
That would be great, if it worked for what he want's to do.... Unfortunately, people have reported that the BattleNet install script doesn't seem to want to work in Bottles Flatpack: [https://www.reddit.com/r/linux/comments/194172e/why_do_so_few_people_talk_about_bottles/](https://www.reddit.com/r/linux/comments/194172e/why_do_so_few_people_talk_about_bottles/)

---

### Post by Tadaen_Sylvermane on 2024-04-06
Just install it manually. Screw the script. Didn't even know there was a script. 8.06 or w/e version of wine. Solved. Although I just deleted it finally because I'm sick of the mini game crap in there. Broken buggy, not worth the time. Seems like some of the stuff in WoW is there for the sole purpose of ******* people off. miss the old days.

---

### Post by Impavidus on 2024-04-06
There's no need to run Notepad++ on Wine; there are plenty of native Linux text editors.

There are tricks to run some, but not all, Windows applications on Linux, but if you want a lot of them, better to run Windows. Or abandon those Windows applications and find Linux alternatives. If you try to switch to Linux while continuing to use your Windows-only applications, I predict a lot of frustration.

---

### Post by yancek on 2024-04-06
In post 13, you seem to be saying that you have windows 11 installed and virtualbox on windows 11 and are booting Ubuntu installled in virtualbox and are trying to run this software through wine in Ubuntu, is that right?  If so, why?  The site for the software shows only a windows download option and you have windows installed so why not just use it in windows.

---

### Post by MAFoElffen on 2024-04-06
> **yancek said:**
> In post 13, you seem to be saying that you have windows 11 installed and virtualbox on windows 11 and are booting Ubuntu installled in virtualbox and are trying to run this software through wine in Ubuntu, is that right?  If so, why?  The site for the software shows only a windows download option and you have windows installed so why not just use it in windows.

I saw that also and wondered why in Post #1:
> **noixyy said:**
> It is also important to note that I am using the  "try ubuntu option" when booting from a usb so [COLOR=#ff0000]I do not have ubuntu  installed on my computer[/COLOR]. I am planning to make the switch from windows  to ubuntu I just want to learn the desktop version of ubuntu and make  sure all of my apps work before I do.
He didn't have Ubuntu installed at all. He was trying to install WINE directly into the Live Image Environment of the Booted from the "Try" option of the installer LiveUSB, which is non-persistent.

Then in Post #9 he said
> **noixyy said:**
> I ended up installing ubuntu on a VM for my  testing. I got wine to install but it crashes when I try to run any  programs.
And in Post #11
> **noixyy said:**
> I am using Oracle Virtualbox with Ubuntu 22.04. I  was trying to run the Battle.net program from Blizzard. The setup runs  fine and installs on the VM without any problems, but when I try to run  the installed program it says "The program battle.net.exe encountered a  serious problem and needs to close. We are sorry for the  inconvenience".
Then in Post #13:
> **noixyy said:**
> I was trying to install Battle.net with wine, and it says something along the lines of "The program has encountered a serious error and has to exit". Although I was able to get notepad++ working with wine so I am guessing there are other things that I need to configure to be able to run Battle.net. I am using Oracle's Virtualbox on windows 11.

So, here goes... To the OP (noixvy), please correct me, or add to this if I am wrong or it needs expanding upon:

His major goal is a plan to install Ubuntu Desktop on his computer, learn Ubuntu Desktop, and ensure the programs he thinks he can't live without, works on Ubuntu Desktop... to help him decide if he can move away from having Windows installed on his computer(?)

Good plan really. Simple enough.

ajgreeny, aljames, and I suggested he install Ubuntu on a VM instead of trying to do that on an installer LiveUSB. <-- Because he wanted to try it to learn it before diving in...

At the time, we didn't know which Windows applications he was trying to run. Games are a bit more to try to get to work. Why? Because some have direct hardware calls to extended graphics. Some mentioned that the BattleNet launcher is 32bit... While the games are 64bit.

Instead of just "Guessing" about this, based on past experience... I am going to do what I do and try to recreate it myself in a KVM VM and see what it does require and try to see what does work.

Why? Because, honestly, It's been a while since I've tried to run Windows games on Linux. There are so many other good games that run 'directly' on Linux. And I dual-boot Ubuntu & Linux = I do not (directly) need to do that. The only time I boot Windows these days is to game on games that are only native Windows hardware, or do my Windows Insider testing.

BRB.

---

### Post by 14nd on 2024-04-06
couple years ago when i used linux (then went back to windows now back at linux) , i couldn't for the life of me get wine to work...i gave up.
i would love to to just run 1 application in windows/wine whatever, cause I've searched and cant find anything alternative for linux that works great .
it's a simple thing really lol but it bothers me 
i want to use foxit PDF ,the windows version cause the linux version doesn't have the add signature thingy.
the alternatives i found is xournal++ that seems to work the best for adding signatures but it's just not as easy as with foxit(windows), i don't wanna add a photo all the time and then the background don't match ect ect ...its a mission .
so yea i miss foxit ,just for the signature fuction

so basically i'm just throwing in my 2 cents to add that getting wine to work...well it's a mission impossible 
:P

PS: my "machine" is too crappy to do the VM thing ...

---

### Post by MAFoElffen on 2024-04-06
I got the Battle.Net installer to run under Wine, but the executable that it installs crashes, with a QT error. Is a know problem at Battle.Net and they have a long standing bug report on that, which doesn't seem to be a priority with them.

I have 3 stack traces, thinking I might get around the errors. The first was that you have to set the arch to include -386 before installing WINE, so it has both arches, and do an update/upgrade on the system, before installing Wine so that it includes all the libraries for both arches. Next, yo
u have to include installing package winbind, which their installer uses in their executable... Once you do that their launcher installer works... But then you hit the qt error on trying to start it. it has to do with their code, where an attribute in their code inside a DLL was set to 'hidden'... Nothing you can do about that one.

On Bottles flatpak... It actually has a tweaked version of WINE with a GUI wrapper over it. After creating a Bottle, I used their program installer for installing the Batttle.net launcher, which it said by it's rating that it worked 'well'. Well, they sort of stretched the truth on that abstractly. It does install the 'launcher', so the setup program works... But the launcher itself crashes with a kernel crash. Very badly at that, with kernel panic. Good thing it is inside of a sandbox!!! LOL

Next will be trying with Lutris. That will be tonight "after" I run a few errands.

---

### Post by Tadaen_Sylvermane on 2024-04-06
To further respond to an earlier post about the bottles Battle.net script not working. I was in a mood yesterday and I apologize. I restored my backup get a configuration dump. I've never had much success with scripts in Lutris or anything else. I just did this manually. Took a bit of playing about to find the proper wine version.

The config export yaml file.

```
Arch: win64
CompatData: ''
Creation_Date: '2024-01-21 21:23:21.174971'
Custom_Path: false
DLL_Overrides: {}
DXVK: dxvk-2.3
Environment: Gaming
Environment_Variables: {}
External_Programs:
    d9d75821-a86c-451c-bd24-bd455ae893b5:
        executable: Battle.net Launcher.exe
        folder: /home/jason/.var/app/com.usebottles.bottles/data/bottles/bottles/BattleNet/drive_c/Program
            Files (x86)/Battle.net
        id: d9d75821-a86c-451c-bd24-bd455ae893b5
        name: Battle.net Launcher
        path: /home/jason/.var/app/com.usebottles.bottles/data/bottles/bottles/BattleNet/drive_c/Program
            Files (x86)/Battle.net/Battle.net Launcher.exe
Installed_Dependencies:
- d3dx9
- msls31
- arial32
- times32
- courie32
- d3dcompiler_43
- d3dcompiler_47
- mono
- gecko
- faudio
Language: sys
LatencyFleX: latencyflex-v0.1.1
NVAPI: dxvk-nvapi-v0.6.4
Name: BattleNet
Parameters:
    custom_dpi: 96
    decorated: true
    discrete_gpu: true
    dxvk: true
    dxvk_nvapi: false
    fixme_logs: false
    fsr: false
    fsr_quality_mode: none
    fsr_sharpening_strength: 2
    fullscreen_capture: false
    gamemode: false
    gamescope: false
    gamescope_borderless: false
    gamescope_fps: 0
    gamescope_fps_no_focus: 0
    gamescope_fullscreen: true
    gamescope_game_height: 0
    gamescope_game_width: 0
    gamescope_scaling: false
    gamescope_window_height: 0
    gamescope_window_width: 0
    latencyflex: false
    mangohud: false
    mouse_warp: true
    obsvkc: false
    pulseaudio_latency: false
    renderer: gl
    sandbox: false
    sync: fsync
    take_focus: false
    use_be_runtime: true
    use_eac_runtime: true
    use_runtime: false
    use_steam_runtime: false
    versioning_automatic: false
    versioning_compression: false
    versioning_exclusion_patterns: false
    virtual_desktop: false
    virtual_desktop_res: 1280x720
    vkbasalt: false
    vkd3d: true
    vmtouch: false
    vmtouch_cache_cwd: false
Path: BattleNet
Runner: wine-ge-proton8-26
RunnerPath: ''
Sandbox:
    share_net: false
    share_sound: false
State: 0
Uninstallers: {}
Update_Date: '2024-04-06 16:02:15.859101'
VKD3D: vkd3d-proton-2.11.1
Versioning: false
Versioning_Exclusion_Patterns: []
Windows: win10
WorkingDir: ''
data: {}
run_in_terminal: false
session_arguments: ''
```

Have Hearthstone, WoW, And Starcraft 2 running in this bottle easily. Just run them from the launcher. On rare occasions the bottle fails to load despite clicking it, yet it starts the Wine / Windows processes. So I kill all the processes and relaunch. Rare, but easily fixable. Otherwise I'd suggest I have better performance from Bottles than Windows ever did give me.

```
for i in $(ps aux | grep C: | grep -v grep | awk '{print $2}') ; do
   kill -9 "$i"
done
```

---

### Post by MAFoElffen on 2024-04-06
Yep. Success. <--- This is why I try to do things myself, when others say it doesn't work.

[LIST]
[*]Add arch i396 
[*]apt udate/upgrade 
[*]Install wine-stable, wine-tricks, & winbind 
[*]Add the Ubuntu Lutris PPA 
[*]Update 
[*]Create Battle.Net account & Lutris account 
[*]Install Lutris > Will start Lutris 
[*]Log in to Lutris by hovering on right side of "lutris" bar (the person icon) 
[*]In browser at Lutris, log in, then search for Battle.net > Install to account > will install the launcher and start it at the end of that. 
[/LIST]

See attached.

---

### Post by 14nd on 2024-04-07
found this today
[https://www.howtogeek.com/running-windows-apps-on-linux-with-bottles/](https://www.howtogeek.com/running-windows-apps-on-linux-with-bottles/)
ima try that and see if works with foxit pdf

---

### Post by noixyy on 2024-04-07
Yes my goal is to learn ubuntu desktop so I can move over from windows 11 to Ubuntu but I couldn’t get anything to install on the live usb so I just used my iso to create a VM instead. Doing this I was able to get everything such as wine to install but using battle.net with wine is not just plug and play. Although I did end up trying lutris and got battle.net + world of Warcraft to install which was really my end goal. Although I got these programs to install with lutris I did want to use wine to install programs like nzxt cam and lian li’s rgb control software for my pc which does not seem possible. In addition I also tried bottles which did not work for battle net but lutris works fine.

---

### Post by yancek on 2024-04-07
>  I couldn’t get anything to install on the live usb

That seems unusual to me as I have never had a problem installing software on a 'live' Linux.  Of course, by design it (the software) will not be retained on reboot.

---

### Post by 14nd on 2024-04-08
oh ppfft i correct myself ...one CAN add signature on Foxit for linux 
all this time wasted trying to find an alternative lol
:roll:

---

### Post by 1screw-ball on 2024-04-30
I would be very interested to know how you got on with running foxit pdf in Bottles.

Like so many, I am new to Ubuntu and desperately trying to get away from Windows for a number of reasons.
Mostly because my PC is just below the requirement for W11, but I also don't like the ever creeping intrusion by Microsoft.

I have Ubuntu installed on a separate SSD and have installed Bottles via FlatPak. So far I have tried to get Affinity Publisher to run, without success.

When I look at the Bottles website their demo graphics show dialogue boxes that look nothing like the ones being displayed on my machine.

How did you get on with Bottles  ?

---

### Post by Paulgirardin on 2024-05-05
> **14nd said:**
> couple years ago when i used linux (then went back to windows now back at linux) , i couldn't for the life of me get wine to work...i gave up.
i would love to to just run 1 application in windows/wine whatever, cause I've searched and cant find anything alternative for linux that works great .
it's a simple thing really lol but it bothers me 
i want to use foxit PDF ,the windows version cause the linux version doesn't have the add signature thingy.
the alternatives i found is xournal++ that seems to work the best for adding signatures but it's just not as easy as with foxit(windows), i don't wanna add a photo all the time and then the background don't match ect ect ...its a mission .
so yea i miss foxit ,just for the signature fuction

so basically i'm just throwing in my 2 cents to add that getting wine to work...well it's a mission impossible 
:P

PS: my "machine" is too crappy to do the VM thing ...

I use Xournal++ too.
you can create a signature image that has a transparent background using GIMP or Inkscape or any other image manipulation app.
This gets around the "background don't match" problem.
Search for: "How To Make A Transparent PDF Signature Stamp"  to find a tutorial.

---

