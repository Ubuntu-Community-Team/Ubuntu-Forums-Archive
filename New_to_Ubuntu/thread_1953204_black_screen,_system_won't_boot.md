---
title: "black screen, system won't boot"
date: 2012-04-05
forum: New to Ubuntu
---

### Post by mukkii on 2012-04-05
I've installed ubuntu for the first time and really don't know anithing about it. 

So, I was downloading something from ftp server and monitor just froz and started blinking. I restarted the pc and got this screen [here]("http://i42.tinypic.com/2nsrp6x.jpg")

I really don't know what happened or what to do?

---

### Post by mal1958 on 2012-04-05
Mukkii, For us to help you, you have to give us some more details on your system.  type (AMD or Intell) as well as details on that (athalon, athalon x2, for AMD or Core duo, quad, i3 i5 i7 and speed) memory in your system, video type (integrated or card  plus chipset (Intell, ATI, nVidia) and model of the card. sound type and anything else you can.  We also need to know which flavor and version of Ubuntu you are using.  

  Giving us this info will help us, help you.

---

### Post by mukkii on 2012-04-06
thanks for reply. It is Intel p 43 dual core 2,6 ghz, 2gb ram. Asus motherboard p5ql-e with integrated sound. nVidia 8500 GT 512 mb ddr2. I installed ubuntu 11.10

---

### Post by maniandram on 2012-04-06
> **mukkii said:**
> I've installed ubuntu for the first time and really don't know anithing about it. 

So, I was downloading something from ftp server and monitor just froz and started blinking. I restarted the pc and got this screen [here]("http://i42.tinypic.com/2nsrp6x.jpg")

I really don't know what happened or what to do?

Hold down SHIFT when the computers starts and select Ubuntu Linux XXX (Recovery mode)
Press ENTER and tell us what you see.

---

### Post by mukkii on 2012-04-06
I get this black screen with or without shift. First purple screen with some stripes shows, then ubuntu tries to boot and this screen appears. Sometime instead of firewall fail says automatic crash report generation [fail], I don't know if that's relevant.

---

### Post by Boyntonstu on 2012-04-06
> **mukkii said:**
> I get this black screen with or without shift. First purple screen with some stripes shows, then ubuntu tries to boot and this screen appears. Sometime instead of firewall fail says automatic crash report generation [fail], I don't know if that's relevant.

I had a similar experience:

USB 11.10 booted fine on PC-a.
Failed on PC-b.  Came through Ubuntu boot with a few lines of text and stalled.
Back on PC-a it booted past the Ubuntu screen and the series of dots and then went completely black. No blinking cursor.

Re-installed, using it now.  

Why?

---

### Post by 23dornot23d on 2012-04-06
It depends on the graphics card -

It tries to determine a number of things automatically

1 .... Graphics Card Type ( [[COLOR=Blue]_**nVidia 8500 GT**_[/COLOR]]("https://www.google.com/search?client=ubuntu&channel=fs&q=black+screen+boot+nVidia+8500+GT&ie=utf-8&oe=utf-8#hl=en&sugexp=frgbld&gs_nf=1&tok=tq2-L4xZ46YIKE-HUgtb6A&pq=black%20screen%20boot%20nvidia%208500%20gt%20solved&cp=6&gs_id=134&xhr=t&q=linux%20black%20screen%20boot%20nVidia%208500%20GT%20solved&pf=p&client=ubuntu&hs=QrT&channel=fs&sclient=psy-ab&oq=linux+black+screen+boot+nVidia+8500+GT+solved&aq=f&aqi=&aql=&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=bb2e42b86b813985&biw=1020&bih=459&bs=1") 512 mb ddr2 - running on ubuntu 11.10 )

2 .... Monitor / Tv Type resolution

3 .... VGA / DVI

The thing is when it stops at a black screen - it may be because one or all of these have not been picked up properly.

To rectify it can be simple if

a) the graphics card is compatible with the version of linux you are using 

b) the screen / monitor / TV supports the resolution its trying to use

c) type of connector to device is selected and works ok

Here is a series of steps one use went through to get a Nvidia card working .....
( If its Nvidia - possibly looking through the steps taken may give you a answer )

[http://ubuntuforums.org/showthread.php?t=1950251](http://ubuntuforums.org/showthread.php?t=1950251)

The first step is to get to a safe mode ... pressing shift at the start may do this
* ( also this is only going to happen if the installation went in ok )

The screen shot shown looks ok - the fact that the teminal text is coming up and the
only fail shown is for the Firewall .....

It seems to have stopped at the intermediate boot screen ......

Plymouth can be the problem here .... a search on it may give some answers.

[https://www.google.com/search?client=ubuntu&channel=fs&q=black+screen+boot&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&hs=D48&channel=fs&sclient=psy-ab&q=black+screen+boot+plymouth&oq=black+screen+boot+ply&aq=0w&aqi=q-w1&aql=&gs_l=serp.1.0.33i21.7669l12391l0l15271l6l5l1l0l0l0l536l1248l0j3j1j5-1l6l0.frgbld.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=bb2e42b86b813985&biw=1020&bih=459](https://www.google.com/search?client=ubuntu&channel=fs&q=black+screen+boot&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&hs=D48&channel=fs&sclient=psy-ab&q=black+screen+boot+plymouth&oq=black+screen+boot+ply&aq=0w&aqi=q-w1&aql=&gs_l=serp.1.0.33i21.7669l12391l0l15271l6l5l1l0l0l0l536l1248l0j3j1j5-1l6l0.frgbld.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=bb2e42b86b813985&biw=1020&bih=459)

Best I can do at this moment ....

---

### Post by mukkii on 2012-04-06
thank you 23dornot23d for replay. So I've changed the video card. I placed asus eah 4670 and now i get just purple screen, and then monitor goes into standby.

---

### Post by 23dornot23d on 2012-04-06
Have you managed to get into safe mode with either of the graphics cards yet ......

Did you try anything from the links that I gave ?

as the last resort I would switch graphics cards ...... but if it was working ok before
then switching graphics cards should not be needed
( also I have more success with Nvidia than ATI  )


Try running the livecd again ..... 
(check that the graphics card works ok with it first ....)

Let us know more information ..... can you run the livecd ok with the current card in

If it worked before and only failed when you were downloading ..... have you run out of space on your hard drive ?


Try Ctrl + Alt + F2 as you are going in at the purple screen ...... see if you can get to a console ... type in

[COLOR=Blue]**df**[/COLOR]

finds the space on the drives .....

---

### Post by mukkii on 2012-04-07
I ran livecd it works ok (with old card), so I guess it's not the card.

I tried to enter safe mot holding shift, couldn't open it (or anything else)

I checked the hard drive it has 69% used space.

[IMG]http://i44.tinypic.com/23lctxd.jpg[/IMG]

---

### Post by 23dornot23d on 2012-04-07
Now you can get to a terminal

Type in 



> 
sudo apt-get update 

sudo apt-get install linux-headers-`uname -r`  

sudo apt-get remove --purge nvidia-* 

sudo apt-get install nvidia-current 

_______________________________________________________

  only needed if  coming from a desktop ( sudo service gdm restart )

then reboot .... see if it will work .....

---

### Post by mukkii on 2012-04-08
When typing 'sudo service gdm restart' I get: 'gdm:unrecognized service'. I proceeded without it and nothing happened.

---

### Post by cryptotheslow on 2012-04-08
Ubuntu 11.10 uses lightdm in place of gdm in earlier versions. So the command would be 'sudo service lightdm restart'

---

### Post by mukkii on 2012-04-08
so should I try again wit this command?

---

### Post by 23dornot23d on 2012-04-08
Try a reboot ..... is the system working ..... 

the last command is only to try it without having to reboot .....

Let us know how it goes - post a screen shot of anything you see now ....

---

### Post by mukkii on 2012-04-08
First time I tried I didn't type correct quotes in linux-headers line so I got error. I skipped that line and finished the process. After rebooting I could log in to ubuntu but shorty after logging in monitor started "blinking" again and it froze again so I had to restart it...black screen again...entered console again and I changed the quotes on linux-headers line so I managed to enter all 4 lines correctly but after rebooting I just got black screen again.

---

### Post by 23dornot23d on 2012-04-08
something does not seem right .... the blinking - I have never seen it reported before .....

> 
So, I was downloading something from ftp server and monitor just froz  and started blinking. I restarted the pc and got this screen [here]("http://i42.tinypic.com/2nsrp6x.jpg")


> 
First time I tried I didn't type correct quotes in linux-headers line so  I got error. I skipped that line and finished the process. After  rebooting I could log in to ubuntu but shorty after logging in monitor  started "blinking" again and it froze again


_____________________________________________________

Can you get to a console again .....

Lets do a safe-upgrade and make sure the computer is uptodate ....



[B]sudo apt-get update

sudo apt-get install aptitude

sudo aptitude update

sudo aptitude safe-upgrade[/B]

There may be a long list here ..... ( let me know what it wants to remove ( if anything )

otherwise .... if there is nothing to remove ..... carry on .... answer y

reboot after it has finished ....

---

### Post by mukkii on 2012-04-09
there was 0 packages to remove. After rebooting I got same black screen.

---

### Post by 23dornot23d on 2012-04-09
Go to a console and type in this command sequence

cat /etc/*release &&  uname     -s -r && unity --version &&     /usr/lib/nux/unity_support_test -p && dpkg -s mesa-utils

Then post a screenshot of what you get back please ......

---

### Post by mukkii on 2012-04-09
Thank you very much for still trying to find solution.

I got this: Error: Unable to open display

I hope I copied the command correctly.

[IMG]http://i43.tinypic.com/25gqoo4.jpg[/IMG]

---

### Post by 23dornot23d on 2012-04-09
Try this then ..... the other was not running .... because we need unity to run it ..... this may give us more
information though ....... 

[COLOR=Blue]**sudo apt-get install perl**[/COLOR]

LSPCI is the first part in lowercase ....

[COLOR=Blue]**lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'**[/COLOR]

Can you let us see a screen shot or type what it returns ( whichever is easier ) ty

Should return something like this

> 
keith@keith-Aspire-7730ZG:~/Downloads$ lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'
01:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 9300M GS] (rev a1) (prog-if 00 [VGA controller])
        Kernel driver in use: nouveau
        Kernel modules: nouveau, nvidiafb
keith@keith-Aspire-7730ZG:~/Downloads$


---

### Post by mukkii on 2012-04-09
So I restarted computer and system booted :confused::confused:

*without this last post of yours with pearl

---

### Post by 23dornot23d on 2012-04-09
Good to hear - is everything running ok now ?

---

### Post by mukkii on 2012-04-09
Yes it does. I restarted it again and it works fine. Thank you very much for your help. 

But what fixed it. What if this happens again?

---

### Post by 23dornot23d on 2012-04-09
If you want to ..... run the commands again when in UNITY

open a terminal and try them from there ...... then post the output ..... just so we have a record of
how it is running now ..... ( cut and paste into a terminal and then show us the results )
always comes in handy if you need to check how you had it set when it was working ok

[COLOR=Blue]**date && lsb_release -sd || cat /etc/*release &&  uname     -s -r && unity --version &&     /usr/lib/nux/unity_support_test -p && dpkg -s mesa-utils**[/COLOR]

[COLOR=Blue]**lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'**[/COLOR]

---

### Post by mukkii on 2012-04-10
[IMG]http://i40.tinypic.com/zkfqtk.png[/IMG]

---

### Post by mukkii on 2012-04-13
same problem appeard again. So i enterd the last command and got this:

goran@Mescudi:¨$ lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'
01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8500 GT] (rev a1) (prog-if 00 [VGA controller])
        Kernel driver in use: nvidia
        Kernel modules: nvidia_current, nouveau, nvidiafb
goran@Mescudi:¨$

---

### Post by 23dornot23d on 2012-04-13
Have you had any updates or altered anything recently that may have caused
it to happen again ...... 

Is it the same graphics driver that you are using as before ..... or has it been updated .....


If the driver has not been altered then ......

Can you get into it in safe mode ?

We may need to look at the log files ..... 
( I have a suspicion it may be a hardware problem ..... but need to check )

to check ..... the log files may show more information .....

**sudo grep -i error /var/log/Xorg.0.log**
**sudo grep -i error /var/log/kern.log**

can you post back a screenshot of any errors you see ...... 

also

**sudo grep -i nvidia /var/log/dpkg.log**

Hope that this gives us a clue ....

---

### Post by mukkii on 2012-04-13
I didn't have any updates in system or graphics driver. By safe mode you mean recovery mode ctrl+alt+f1?


[B]sudo grep -i error /var/log/Xorg.0.log
[/B]
[  10.678] (EE) NVIDIA(0): check your system's kernel log for additional driver[B]

sudo grep -i error /var/log/kern.log[/B]

[IMG]http://i44.tinypic.com/3448j0n.jpg[/IMG]

**sudo grep -i nvidia /var/log/dpkg.log**

[IMG]http://i43.tinypic.com/33nj96r.jpg[/IMG]

---

### Post by 23dornot23d on 2012-04-13
The last screen shot shows the Nvidia driver has changed from the

295.33

to the

295.40

on the 13th yesterday ....... @ 10 : 26 ........ ( 22 : 26 )


That could be the problem ......

You also have some input output errors on the kernel log ..... 

( not sure exactly what they are ..... maybe someone else may know ..... but I will save the screenshot and have a closer look )

Looks like a Dvd or CD Sr0 .... so not a real problem ..... ( possibly just a bad cd or dvd .... ) somebody else
may be able to confirm this ...

---

### Post by mukkii on 2012-04-13
Nvidia driver changed because I was going through steps mentioned in previous posts uninstalling and installing drivers, checking for system updates etc.

---

### Post by 23dornot23d on 2012-04-13
So what do you think works ......  and how do we get it working again ......

Seems like you need to purge the Nvidia Drivers and go back to the 295.33 again 

Nvidia 295.33

[http://askubuntu.com/questions/121658/how-can-i-go-back-to-nvidia-295-33-driver](http://askubuntu.com/questions/121658/how-can-i-go-back-to-nvidia-295-33-driver)

---

### Post by mukkii on 2012-04-14
I don't know what works. I made this change after pc froze again and black screen showed up.

I purge the drivers and this time I got stuck on screen with ubuntu logo and 5 loading dots. But this time I was able, by holding shift, to enter grub menu.

---

### Post by 23dornot23d on 2012-04-14
The PC should not freeze ....... 

I have a feeling this may be a memory problem how much memory does your machine have ........

Is the memory seated properly ....... 

Have you tried a memory check to make sure it is ok ......

I would expect a error in the logs showing any other hardware failing ..... but memory can cause a freeze ..... as I have seen this happen before ......

* ( thats my best assessment - unless you know of something that you think may be causing it to happen )

---

### Post by mukkii on 2012-04-16
PC froze couple times earlier but it booted ok after restart. Last two times it froze I got the screen...

I found different commands for memory check so I ran them all:

[IMG]http://i42.tinypic.com/2eb8w06.jpg[/IMG]

---

### Post by 23dornot23d on 2012-04-16
Keep a track of what you are doing when it freezes up .....

a) Is it when there is a lot of system load ..... 
b) Is it random .... happens even when the computer is doing nothing .....

Also look at your logs .... there is a logviewer in the menus - if you use UNITY or GNOME SHELL

Go to the Dash or mouse up to the Top left .... and in the search type in LOG ..... it should
pop up ..... then look for the boot log ... the kernel log and the system log .....

The problems that are encountered if any are recorded here ..... and by scanning through the time and date .... you can possibly see where it died or stopped working .....

if the output shows something odd happening - post back the results .....

The time to go check this is after a freeze and you first get into your desktop .....

That is the way to see what happened prior to it dropping out ..... the last time it
froze ..... 

The thing is - memory problems are the hardest to track IMHO .... but if
anyone reading this thread has more knowledge on how too look for a memory problem please say .....

The only other thing I can think to do - is keep the monitor running .....

The System Monitor shows how memory and resources are being used .....

Try to see if the memory is filling up to 100% when it freezes .... or if multiple process's are taking place .....

Thats the best I can say at the moment ......

The screen shots you posted did not mean a lot to me ..... but there seemed to be no
apparent errors on them from what I looked at .....

let us know if you find anything in the logs ..... and also check as before on errors ....

> 
We may need to look at the log files ..... 
( I have a suspicion it may be a hardware problem ..... but need to check )

to check ..... the log files may show more information .....

**sudo grep -i error /var/log/Xorg.0.log**
**sudo grep -i error /var/log/kern.log**

can you post back a screenshot of any errors you see ...... 

also

**sudo grep -i nvidia /var/log/dpkg.log**

Hope that this gives us a clue ....     
You can use this command to quickly scan through large log files looking for
specific words ..... xxxx being the word you are looking for .... [COLOR=Red]**error**[/COLOR] in our case

This first command - just lists ... the logs in the directory where they are stored.

[COLOR=Blue][B]ls /var/log/

[COLOR=Black]or use the file browser dolphin if its easier ....... by clicking on the log files
that are just text files you can scan through them and see if anything
stands out as being a problem .....

also have a look in /var/log/dmesg

Networks sometimes can cause a freeze - but would expect to see a error 
somewhere ......


and this command[/COLOR]
[/B][/COLOR]
[COLOR=Blue]**sudo grep -i [COLOR=Black]xxxx[/COLOR] /var/log/syslog.1**[/COLOR]

[COLOR=Blue]**sudo grep -i **[/COLOR][COLOR=Red]**error**[/COLOR][COLOR=Blue]** /var/log/syslog.1**[/COLOR]



hope this helps narrow down what is happening here ..... we will sort it out .....
or at least find out what is causing the lock-up / freeze .........

---

### Post by mukkii on 2012-04-17
First time it froze I was just downloading something, this time it froze I think it was because big system load. I will monitor log for errors but for now I would just be glad to run system properly.

I ran this command and here is what I got:

[IMG]http://i40.tinypic.com/16jjzg7.jpg[/IMG]

---

### Post by mukkii on 2012-04-17
Ok, so I managed to boot the system, and after log in to unity monitor blinked couple of time and I got just black screen whit blinking cursor on the top in the middle. After another restart I got to unity log in screen, blink again, and black screen, and now it's just the same black screen with [ok] and [fail].

i noticed that every time I get plain black screen with purple stripes after that I get black screen with [ok]s and [fail]s, but when there is no black screen with purple stripes I can get to unity.

---

### Post by 23dornot23d on 2012-04-17
There are lots of Buffer input output errors on the [[COLOR=Blue]**sr0**[/COLOR]]("http://ubuntuforums.org/sr0") which is the CD/DVD drive 

Do you use this a lot while working ...... there may be a fault on it ..... seems too regular
all of those errors .... ( I put it down originally to maybe a bad CD or DVD  )

[COLOR=Red]**But it could be that the player itself is failing**[/COLOR]

it seems there are a lot of errors on this on each screenshot you have posted ....
unless it is just bad CDs / Dvds that are running at the time it crashes ..... ?


Its a desktop machine ......

> 
Intel p 43 dual core 2,6 ghz, 2gb ram. [[COLOR=Blue]_**Asus motherboard p5ql-e**_[/COLOR]]("http://www.asus.com/Motherboards/Intel_Socket_775/P5QLE/") with  integrated sound. nVidia 8500 GT 512 mb ddr2. I installed ubuntu 11.10
is the CD/DVD player being used all the time for music or something or a game maybe ?

and can you do this in a terminal ..... ( LSPCI ) lowercase ,,,, as below ,,,,

**lspci**

This just shows the pci devices and the one below the USB devices .....

**lsusb**

Show some screenshots if you would please .....
My thoughts now are that the CD/DVD drive may be the problem ....

The last 2 commands above will just give others some more information to go
on ........ as my next move would possibly to remove the CD/DVD player or
replace it with another one ...... keep a track of how often it fires those
errors up ..... if it is not while a CD / DVD is playing then there may be
a problem with it ...... 

  A desktop machine then disconnecting the CD player would be easy do to check this

I can only see sda1 there (which it keeps mounting as read only ) ... is it dual boot is windows on sda1
usually with Ubuntu installed there would be other partitions


My only other thought - are you running UBUNTU just from a LiveCD ....
or is it installed on the hard drive .... ? :confused: 

I know earlier you said you installed it for the first time .....  do the command below .... should show
what is there 

**df**

---

### Post by mukkii on 2012-04-17
I dont use cd/dvd much, but there was one dvd couple of days in the device last time this happened. I can't remember if there was one first time it happened. But anyway, I disconnected cd/dvd now.

I had 2 partitions on one hdd with windows. I removed windows completely from one parition and installed ubuntu instead.

here are the screens:

[IMG]http://i40.tinypic.com/2q1z75y.jpg[/IMG]

---

### Post by 23dornot23d on 2012-04-17
Can you this now from the screen console you are on ......

**startx **

- see what it outputs 

Or will it go into UNITY with a normal boot up now ..... if it runs ok with the CD/DVD 
disconnected we may have found the problem .... if it does not .... we may need to
keep checking the logs ..... for something else ......

---

### Post by mukkii on 2012-04-17
[IMG]http://i39.tinypic.com/2m4ek5t.jpg[/IMG]

---

### Post by mukkii on 2012-04-17
I was able to run the system after uninstalling and installing nvidia drivers.

What this previous screen says?

---

### Post by 23dornot23d on 2012-04-17
Ok if you are ok now see how it goes ....

The previous screen shows the output of trying to start the x-server manually .....

You solved the problem by re-installing .....

but sometimes you can create a configuration file specific for your system if this had
not worked ,,, this gets stored in a file called [COLOR=Blue]**/etc/X11/xorg.conf**[/COLOR] .....

my next move was going to re-create a new one - but what you did is fine .....

---

### Post by mukkii on 2012-04-17
23dornot23d, once again thank you very much. You really saved me.

When I logged in, the screen started blinking again like 5 sec it is ok, then 2-3 rapid blinks and so on for 4-5 times then it froze again. I could just move the cursor. After another restart it is ok, for now.

So, what next? How do I prevent this from hapening again. And should I reconnect cd/dvd?

Except  monitoring log files like you said in [post #36,]("http://ubuntuforums.org/showpost.php?p=11849624&postcount=36") should I be doing something else?
*I couldn't find kernel,boot or system log. Just log viewer and system monitor.

---

### Post by 23dornot23d on 2012-04-17
With it still doing it with the CD unplugged - then that should not be the problem
but run it for a day without it plugged in and keep checking the logs ....

We know its probably nothing to do with the CD/DVD drive now ..... but lets see if the
logs show something else up now ......

But obviously - You can re-connect it if you need to use it ...... 

Not ever had one to [[COLOR=Blue]_**flash and freeze**_[/COLOR]]("https://www.google.com/search?q=8500+flashes+and+freeze&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a#hl=en&client=firefox-a&hs=Iot&rls=org.mozilla:en-US%3Aofficial&sclient=psy-ab&q=linux+gt8500+flashes+freeze&oq=linux+gt8500+flashes+freeze&aq=f&aqi=&aql=&gs_l=serp.3...6049l19552l0l20361l24l17l7l0l0l3l701l4244l0j10j2j2j1j1j1l31l0.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=9df23f3c2216102e&biw=1127&bih=498") ..... still seems like a hardware problem ....

You had windows on before it - did it ever do the same with that .... ?  freeze that is ....

or did you add the graphics into a older case ..... 

( the power supply and the output rating from the PSU has to be man enough to handle the graphics card and motherboard ..... what rating is the PSU ...... in watts )

There are online calculators for the size of Power Supply Unit ...... * its another thing
that could be a problem .... not saying it is - but might be worth checking 

[http://support.asus.com/powersupply.aspx](http://support.asus.com/powersupply.aspx)

Possibly a 400 watt - minimum .... but let us know what the rating is ..... 
( these tend to shut everything down - if they cannot handle things though )

digging deep now .... 
No errors in the logs other than the CD/DVD drive problem ....
not memory - as far as we know - ( but it does seem to happen when high load )
not the CD/DVD player ................. ( as this was completely disconnected and its still doing it )
PSU .... if 400 watt then probably not that as the system would do a full restart .....

if there are no other errors ..... possibly a fault with the graphics card ..... 

and you do have another graphics card that you mentioned earlier ...... so to eliminate the possibility of
it being the graphics card ...... then you could try setting it up for the ATI card .... 

> So I've changed the video card. I placed [[COLOR=Blue]_**asus eah 4670 **_[/COLOR]]("https://www.google.com/search?q=asus+eah+4670+solved+linux&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a")and now i get just purple screen

but I know nothing really about those ..... QIII might though ..... so it may be another option ,,,

---

### Post by mukkii on 2012-04-18
I suspended the system last night and this morning I got the screen again.

Does this point to problems in graphic card:

[IMG]http://i41.tinypic.com/211toqx.jpg[/IMG]

I was running windows with ATI card and changed it when was installing ubuntu (swiching cards was just coincidence it had nothing to do wit the fact I wanted to install linux).

I had freezes on windows, but I guess thats jush how it is with windows. Never had blinks or something like that. PSU is 450W I think.

So what card would you recommend?

---

### Post by 23dornot23d on 2012-04-18
Well looking at that - shows 3 [[COLOR=Blue]_**segfaults**_[/COLOR]]("http://en.wikipedia.org/wiki/Segmentation_fault")

All related to the graphics card driver ...... at 4 : 24 pm   to  4 : 28 pm on the 17 April

The thing is did it crash at this time or did it continue to work ..... what was you doing
at the time it crashed ?

Whatever - its probably a problem with the driver or the card ?

I am not experienced enough to tell exactly what those codes mean on the screenshot ..... somebody else maybe can comment on this.

[IMG]http://img705.imageshack.us/img705/6526/errorlog.jpg[/IMG]

Here is the search I did on the segfault problem ..... 

I have looked through a lot of these but cannot see an exact match for the problem
but there seems to be quite a few for that particular card ..... 8500GT
whether they are related is another question ....

[https://www.google.com/search?q=segfault+error+4+nvidia+driver+0000049+706000&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a#hl=en&client=firefox-a&hs=j7t&rls=org.mozilla:en-US%3Aofficial&sclient=psy-ab&q=segfault+error+4+nvidia+driver+gt8500&oq=segfault+error+4+nvidia+driver+gt8500&aq=f&aqi=&aql=&gs_l=serp.3...3309l8640l0l9757l13l12l0l0l0l5l1168l4778l0j6j4-1j3j1j1l12l0.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=bb2e42b86b813985&biw=1101&bih=500]("https://www.google.com/search?q=segfault+error+4+nvidia+driver+0000049+706000&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a#hl=en&client=firefox-a&hs=j7t&rls=org.mozilla:en-US%3Aofficial&sclient=psy-ab&q=segfault+error+4+nvidia+driver+gt8500&oq=segfault+error+4+nvidia+driver+gt8500&aq=f&aqi=&aql=&gs_l=serp.3...3309l8640l0l9757l13l12l0l0l0l5l1168l4778l0j6j4-1j3j1j1l12l0.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=bb2e42b86b813985&biw=1101&bih=500")

( unless someone can identify how to check - which is the problem here card or driver )

[COLOR=Red]** no other driver has worked for you  other than the [[COLOR=Blue]_Nvidia 295.33_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11832511&postcount=26")**[/COLOR]

As you have found that the problem appears to be with the Nvidia Driver  or Card ....... and unless someone can pinpoint a better driver for your  card than the .33 then we really have few options  ......

__________________________________________________________


So the alternatives - you have ...... is to try the other card you have in this machine ......
or search for a better driver for the 8500 GT .... or use another kernel ...... see if that would help ...... 12.04 is due soon ..... often fixes come in with newer versions.

or use the

Asus 4670

and use the drivers for it - under additional drivers ..... [COLOR=Red][B]but the nvidia drivers would
need purging before you swap over ... [/B][/COLOR]

This is a card I know nothing about  ..... you could try some searches on it
for drivers and installation first though .......

One last thought .... the fans on the CPU are they clear of dust and build up .... as the one other
thing is overheating ...... and if the card runs for a while before its locking up / freezing .....

Could try the commands below in a terminal to do a check ..... occasionally


> 
keith@keith-Aspire-7730ZG:~/Downloads$ [COLOR=Blue]**sudo apt-get install nvclock**[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvclock
0 upgraded, 1 newly installed, 0 to remove and 542 not upgraded.
Need to get 63.3 kB of archives.
After this operation, 191 kB of additional disk space will be used.
Get:1 [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) precise/universe nvclock i386 0.8b4+cvs20100914-1ubuntu1 [63.3 kB]
Fetched 63.3 kB in 0s (184 kB/s)
Selecting previously unselected package nvclock.
(Reading database ... 217703 files and directories currently installed.)
Unpacking nvclock (from .../nvclock_0.8b4+cvs20100914-1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up nvclock (0.8b4+cvs20100914-1ubuntu1) ...


keith@keith-Aspire-7730ZG:~/Downloads$ [COLOR=Blue]**sudo nvclock -T**[/COLOR]
Xlib:  extension "NV-CONTROL" missing on display ":0".
[COLOR=Blue]**nVidia Geforce 9300M GS**[/COLOR]
=> GPU temperature: **[COLOR=Blue]54C[/COLOR]**
keith@keith-Aspire-7730ZG:~/Downloads$ 

Mine is a Laptop ... usually Desktops run a lot cooler than this .....


---

### Post by mukkii on 2012-04-19
I installed ATI drivers, and so far everything is ok. We'll see how it goes with this card.

---

### Post by 23dornot23d on 2012-04-19
Ok good to hear ..... and I hope you have a clean run with it ...... :KS

---

### Post by mukkii on 2012-04-21
Well, so far everything runs great. I think I can say now that the problem is solved. I guess the problem was with the drivers, faulty card, or the card just didn't suite rest of the configuration.

One more time thank you 23dornot23d for all the help.

---

### Post by 23dornot23d on 2012-04-21
You are very welcome .... cheers .... glad it worked out ok .... ):P

Can you mark the thread as solved too .... 
in Red ( [COLOR=Red]**Thread Tools**[/COLOR] - towards the top of the page )

---

