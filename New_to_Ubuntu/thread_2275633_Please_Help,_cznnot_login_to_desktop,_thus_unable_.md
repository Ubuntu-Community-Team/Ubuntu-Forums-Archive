---
title: "Please Help, cznnot login to desktop, thus unable to work. (home/last 3-hours wasted)"
date: 2015-04-27
forum: New to Ubuntu
---

### Post by whereismymindat2 on 2015-04-27
Thanks for reading. 
Re:I work from home/remote. I've spent last 3-4 hours messing around trying to login to my "box"
 
(apology for (arguably borderline hyperbolic title)---just have TONS of work, so best be working! Prefer to not stay up until 3am finishing the day, ya know? ;-) 

The Problem
________________

```


When I boot up, it boots into a tty session. It behaves of course like Terminal--I can get sudo su rights, etc. 

________________
}Thus I've tried everything I can think of
1-"Upgraded" (not "dist" though)

2-"Xubuntu-Desktop (has probably 200-installs--some lib-most packages looks like)

3-Have booted to recovery, "clean", fsck, dpkg repair, etc. 

4-"reinstalled" (?)---but checked grub2 from restore session, it behaves o.k.

5-Booting into restore (holding shift down)--I have 3-kernels install. (why????-no clue) ----- I *THINK* 3-13-0-27, 3-13-0-x (larger number-can't remember 30's) , 3-16-0-47



This has happened once before, I simply just "reinstalled" the OS.

I really really really want to avoid (pragmatic) reinstall. 

Reinstall takes takes 1-ish to 2 hours to reinstall all the stuff I had on before (even using APTIK). 

AKA-"customized" to my most desirable)


```
________________




Solutions?
____________________

  Thank You In ADVANCE!!

---

### Post by Bashing-om on 2015-04-27
whereismymindat2; Hello;

Where there are solutions, there are no problems.

The nature of this condition we often see as a result of either of 2 circumstances.
1) Authorization to access the /home directory has been lost:
```

ls -al .Xauthority
ls -al .ICEauthority

```

2) Running a proprietary graphics driver and a upgrade to the system broke the proprietary driver.
To get an idea of what might be going on here:
```

lspci -vnn | grep VGA -A 12
sudo lshw -C display

```

now we can ask
[INDENT][INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT][/INDENT]

---

### Post by TheFu on 2015-04-27
Just to chime in - be VERY careful running GUI programs as root. VERY CAREFUL.

---

### Post by whereismymindat2 on 2015-04-28
@[**[COLOR=#DD4814][B]Bashing-om**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1111508") Thanks for the help mate! I let my system reboot to the TTY, and tried both of the ls options first (tty didn't recognize--but I have used before)
These two worked 
lspci -vnn | grep VGA -A 12
sudo lshw -C display
Of course just provided me data on my  video Driver (Intel). Anyway, figured I would consider it a Holiday and just mess with/reinstall everything vs. taking you down a rabbit hole helping me
Thanks again Mate!

---

### Post by whereismymindat2 on 2015-04-28
@[**[COLOR=#000000]TheFu [/COLOR]**]("http://ubuntuforums.org/member.php?u=1037685")    

Thanks for the heads up for running  GUI as root. I very seldom do, but didn't realize was as  serious/potentially harmful as you suggest. Thanks

(I use Palemoon. As per reinstalling my box yesterday, necessary to reinstall PM (it *DID* realize PM was installed, but i did not know the command line to fire the program via terminal start and/or recreate the launcher myself. --Thus had to uninstall-reinstall (no problems)--remembered everything. 

[B]--------------MY APOLOGY IF THIS IS "TOO MUCH" information. I try to offer as much as I belive necessary, respect to you/your time for Gracious assistance.  
 I feel it would be less burden on you to help--with too much vs. not enough (aka-you having to ask can you send this ,send that, etc.) 
THANK YOU!!!
[/B]
___________________________________________________________


```

---if it matters, the Palemoon Launcher uses palemoon %u
---Permissions are 
---Owner=1001
(rest is grayed out, but shows)
Access=read/write
Group=1001
Access=Read and Write
Others=Read and Write

Program--Allow this file to run as program. 
---! Allowing untrusted programs to run poses a security risk to your system. 
```[INDENT=5]

[/INDENT]
___________________________________[INDENT=5]Now I am "confused" not sure if I should be  bit more concerned (FF example below---installed as part of out of box X/Ubuntu Distro)

```

FF Launcher firefox %u
Permissions (my box login user name)
----NOTHING "grayed out"--aka--WILL allow me to change Permissions from the GUI Launcher/Permissions Tab
Access=Read-Write
Group (my box login user name)
Access=read only
Others=read only
Program=(check box checked)--Allow this to run as Program
---! Allowing untrusted programs to run poses a security risk to your system. 

```
[/INDENT]

_________________________________





Back to Subject of Palemoon
________________________________
---when you install it, it asks for the  root password. Not sure why, as  I don't think it runs as root (I can't  imagine they would design that  way). 
Any ideas why that is "necessary"  to install Palemoon? 

I "manually" install Chrome & Opera (course each has "Key"/each packed in *.deb) . each added to sources list  ( /etc/apt/sources.list)-per normal/expected

Of course Chrome/Opera install needs PW, to launch GDebi/Synaptic, 
------99.9% of time, I use GDebi or Synaptic, which of course require root privileges to launch install--thus why I was not "fully alarmed" at Palemoon request. 


Only Programs I've installed with *.sh (root) are Palemoon and Crash Plan Plus 
___________________________________________[INDENT=5]  CPP does not obfuscate the install.sh thus my limited knowledge viewing the install.sh nothing looks out of range for what CPP needs 
.(514-lines code-ZERO obfuscated)
[/INDENT]
[INDENT=9]CPP example
------if it matters--CPP well trusted, well reviwed "Code 42 dot com Cloud backup.  
I cannot imagine they would even be close to the line of questionable as they are a "paid service" Company. 


```

---------Launching installer.sh have standard EULA to y/n read/agree. 
CPP--Asks for permission each directory install (is this ok, press y/n)

CrashPlan will install to: /usr/local/crashplan
And put links to binaries in: /usr/local/bin
And store datas in: /usr/local/var/crashplan
Your init.d dir is: /etc/init.d
Your current runlevel directory is: /etc/rc2.d

```

[/INDENT]
[INDENT=5]CPP- allows to fire from (of course terminal-and I created a Desktop GUI launcher-to fire start). 
Firing from Terminal or Desktop Launcher *DOES* pop up a GUI. (java based). 
[/INDENT]
[INDENT]
[/INDENT]
 

______________________________________


I trust  Palemoon  only because it's a Fork of FF. , I would be very very hesitant to do this with other Programs. 

Is  Palemoon potentially Dangerous? --Under these conditions? 
(per above-I can't imagine it runs as root(?????) --no clue why asks for root PW unless behaving like the CPP *.sh installer


I was going to send a copy of the Palemoon code for you to see if anything potentially dangerous inside the script installer. 

However, the Character encoding--is not "correct"--(or intentionally obfuscated). 

***-Bluefish fails completely (aka-won't even try to open)[INDENT=3]
Palemoon character encoding added to Gedit to try to human readable the *.sh

```

Using--Gedit(opened as root/terminal), 

The .sh installer--the code is obfuscated.  Not sure if   it's (intentional)---or wrong character encoding. 

Per reason, I can't open in  Bluefish, Try Gedit with the following Plugins--none of which   passed the 24-line code length
            
Therefore now confused---First presuming it's Character encoding--(aka showing the  "box" with four smaller boxes inside--"normal" for not recognizing character encoding-sure you have seen)
(no real "reason" for why I picked below, other than it looks very familiar--UTF-8--or vaguely familiar)


UTF-8 (I can see 24-lines of (human readable)  code---the rest is obfuscated. 
Western Windows (1252)---fails completely
Western (ISO-8859-1)--only see 24-lines(human readable) 
Unicode (UTF-32)--fails completely
Central European (ISO-8859-2)--only see 24 lines of code (human readable)
Western (ISO_8859-15)--only see 24 lines of code (human readable)

---(as an fyi-I did click "retry" after choosing each encoding-thus pretty  sure was using that encoding--aka--a few failed completely)
When it fails(showing 24-lines), it defaults back to UTF-8 (which is one encoding on my  box). 24 human readable---does not gray out/error out with "red" header, necessitating close and restart.Defaults back to UTF-8 


```
[/INDENT]
[INDENT]
[/INDENT]
 

This code below is the only (human readable) I can see
         the xx-->  Is a string of 64 Numbers and English alpha characters-of course it's both upper and lower case--
I "x" out (my security)  in case it's a unique id for my box. 


```

#!/bin/bash
unset CDPATH
if [[ ! "$(sed -r s/[a-f0-9]{64}// "$0" | sha256sum)" =~  xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx ]]; then
echo "The installer is damaged!"
exit 2
fi
case $(uname -m) in
i?86)
a1=i686
;;
x86_64)
a1=x86_64
;;
*)
echo "Unsupported architecture."
exit 1
;;
esac
a0=$(mktemp -d /tmp/pminstaller.XXXXXX)
tail -n +25 "$0" | tar -xJf - -C "$a0" || exit 2
PATH="$a0/bin/$a1:$a0/tools:$PATH"
runasroot "$a0/installer.sh"
rm -rf "$a0"
exit

```


Example of won't recognize coding--looks like this.

```
‡yTÿÄŸýè‹©GNÄ+,_PêŸé‚3«à‚óÚ„›RùûW„Ž
```

---fyi--when I paste into this box (using FF browser) ---code is scrambled,   the "box" with four smaller boxes inside--(character encoding error) .DOES NOT show on my FF browser end.
-DOES show on Gedit -- "the box"with four smaller boxes (character encoding error) .

(thus makes me think-----correct???? More likely obfuscated vs. Characxter encoding??????  Aka---FF not showing what is expected for char encoding error ( the "box" with four smaller boxes inside).
  ----Therefore, if an *.sh is obfuscated---any reason WHY? It's a fork, thus not "Proprietary" and is "Free"

in any case, hopefully you can see what I mean by the scrambled. Advise on a char encoding allow you to see all code for anything alarming. 

THANK YOU VERY VERY MUCH FOR THE ASSISTANCE!!!! VERY MUCH APPRECIATED--LAST THING I NEED IS A COMPROMISED BOX.

---

### Post by whereismymindat2 on 2015-04-28
********PS---JUST GREAT**********

When I opened *.sh in Gedit, I I "guess"???? I neglected to uncheck the (always use Gedit app)
Lost ability to "Execute" an *.sh---AKA---is seeing only as a Gedit file. 

How can I change that back to have "Execute" as an option (and top rail) option????? 


*THANK YOU*!!!

---

### Post by whereismymindat2 on 2015-04-28
****PPS*****  See, just "asking" a question, forces me to learn----I used bash in terminal to uninstall palemoon.sh
It  fired the Gui (which is as expected with execute palemoon.sh)---allowing me to uninstall. 

```

[B]BUT,  I'm still missing the "Execute"---*.sh (Gui-Right/Click)--thus still  need help on that
[/B]
```

Palemoon only uses GUI for any  install/uninstall/upgrade---as using below bash (to uninstall)---it  provided nothing verbose about uninstall (and fired the GUI). 
The GUI *DOES* verbose--however, it rips so fast impossible for human readable-watch for suspect. 



----For curious---I know on windows you can point out to  >foo.txt    With Command Line. To see/debug/etc. an Install/Uninstall

If I wanted to try this (to "watch" install/uninstall of Palemoon--is that "TEE" or something else?. 

*THANK YOU*!!!

______________________________

PS----

Again,  if helpful---this is the bash I ran to allow uninstall--I kept term  open even after GUI said completed--about 10-secs later fired an error  in term. 

```


root@Dooley:~# bash --init-file --verbose /home/bender/pminstaller.sh
flags         : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov  pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm  constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl  est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm
flags        : fpu vme de  pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush  dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon  pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr  pdcm lahf_lm dtherm
/usr/bin/palemoon
Killed palemoon(1859) with signal 15
palemoon-bin: no process found
root@Dooley:~# root@Dooley:~# bash --init-file --verbose /home/bender/pminstaller.sh
root@Dooley:~#: command not found
root@Dooley:~#  flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov  pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm  constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl  est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm
flags:: command not found
root@Dooley:~#  flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov  pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm  constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl  est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm
flags:: command not found
root@Dooley:~# /usr/bin/palemoon
bash: /usr/bin/palemoon: No such file or directory
root@Dooley:~# Killed palemoon(1859) with signal 15
bash: syntax error near unexpected token `('


```


_________________________
PS-non-relvant funny joke. (forcing me to look for answer, reminded me of this)
High school English, ask Professor "How do you spell...(long word-forget)--He said, look it up in that dictionary (points across room to 6-9 inch thick dictionary)
I reply--Well, if I KNEW HOW TO *SPELL IT*, I could look it up, but since I don't know *HOW TO SPELL IT*, *HOW* do I look it up????? 

He is pissed!! He walks across room, grabs (least 6-9inch think Dictionary--slams on my desk
Here you go smart @ss--(slamming book on desk)--look it up. 

I wait 10-seconds, say "Never mind, I'll use (synonym--easier to spell)--instead. Don't need dictionary for that, Thanks. 
He said, you are taking the damn dictionary back to where it belongs smart @ss. 
*laughing*

---

