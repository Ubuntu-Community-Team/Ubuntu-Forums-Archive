---
title: "I need to login twice to log in - odd"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by verymadpip on 2011-10-23
Hello all.

As the title says, sometimes, when I log in to Oneiric, the jingle starts, then I get a very brief black screen with some white text & I get dumped back to the log in screen.  I log in again & all goes as it should.

It doesn't appear to occur specifically with a restart or a cold boot or anything, just random.

Has anyone else experienced this or does anyone have an idea what it may be & how to solve it?

Any help is greatly appreciated.

---

### Post by AndrewSharpe on 2012-01-02
I have this issue as well.

I've just had a peek at the lightdm log (/var/log/lightdm/lightdm.log) and it suggests another file of relevance (~/.xsession-errors).

I haven't found anything that indicates the cause of this issue yet though I've to do more fiddling with clean logfiles to see if there's anything that stands out.

---

### Post by KdotJ on 2012-01-02
Just to weigh in, I also experience this occasionally. Its only happened a few times.. but Ill keep eyes on this thread. Its doesn't bother me too much though.

---

### Post by stunrock on 2012-01-09
Same problem for me too.

I'm running the 64bit Ubuntu version on a solid state drive (vertex 3)

if it happens some code is blinking on the screen and shining through the lightdm background. Then I know I have to login twice.

---

### Post by KdotJ on 2012-01-09
> **stunrock said:**
> Same problem for me too.

I'm running the 64bit Ubuntu version on a solid state drive (vertex 3)

if it happens some code is blinking on the screen and shining through the lightdm background. Then I know I have to login twice.

I get this too, I get artefacts on the top left of the screen and more appear as I type. They appear in line with the password text field.

---

### Post by Handssolow on 2012-01-20
No solutions yet but I'm getting this too since yesterday when I transferred my HD with 11.10 to a new PC. It all seems to be working except I'm having to log in twice though possibly not every time. On the login screen I've noticed some odd pixels some flashing in the top left quarter of the screen, seems from here that this is a related issue. I've also noticed the Scroll Lock light is lit when the first log in screen appears.

---

### Post by Handssolow on 2012-01-20
It seems to be back to normal.

Had a brief look for other threads on this topic and found these two below.

So I removed and re-installed gdm then appreciated that the default display manager in 11.10 is lightdm where previously it has been gdm. The dilemma I've got is that I'm using gnome-session-fallback with 11.10 not Unity. Selecting lightdm as default during the gdm re-install and I'm still double logging in. I'd didn't see what happened if I selected gdm, I guess an older log in screen from earlier Ubuntus.

Next these
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update

then the Update Manager kicks in and I've several packages which need updating (it wasn't many hours since I last checked). I notice one is related to the kernel and after rebooting as requested, I'm back to normal with single log in. I didn't find anything in launchpad but it was only a quick look.

In the past I think I could look in Synaptic and identify what has been installed in Update Manager, history in Synaptic shows just that, packages which I've chosen to installed myself. Anyone know where to look for Update Manager's history?


[http://ubuntuforums.org/showthread.php?t=1854873&highlight=log](http://ubuntuforums.org/showthread.php?t=1854873&highlight=log)

[http://ubuntuforums.org/showthread.php?t=820715&highlight=double+log](http://ubuntuforums.org/showthread.php?t=820715&highlight=double+log)
.

---

### Post by verymadpip on 2012-01-20
Okay, I've noticed when this happens on my rig.  So it's no longer random...

I'm using a Saitek Eclipse II illuminated keyboard.  If I change the colour of the keyboard lighting ***before*** my launcher & panel are visible on my desktop I get thrown back to the lightdm log in.  There's a bit of white text on black, terminal style, but it's too quick for me to make any sense of it.

Actually, I only ever go from blue to purple, which is 2 clicks of a keyboard button, so I'll try blue to red (1 click) & see what happens.  To turn the light off is 3 clicks , so I'll try that too.
(I'm using a different box at the moment so testing will happen this evening).

If anyone has any idea which logs I should be looking at (lightdm I guess) a helpful pointer will be more than welcome.

---

### Post by Handssolow on 2012-01-20
> **verymadpip said:**
> Okay, I've noticed when this happens on my rig.  So it's no longer random...

I'm using a Saitek Eclipse II illuminated keyboard.  If I change the colour of the keyboard lighting ***before*** my launcher & panel are visible on my desktop I get thrown back to the lightdm log in.  There's a bit of white text on black, terminal style, but it's too quick for me to make any sense of it.

Actually, I only ever go from blue to purple, which is 2 clicks of a keyboard button, so I'll try blue to red (1 click) & see what happens.  To turn the light off is 3 clicks , so I'll try that too.
(I'm using a different box at the moment so testing will happen this evening).

If anyone has any idea which logs I should be looking at (lightdm I guess) a helpful pointer will be more than welcome.

Might I suggest you're describing a slightly different problem than others are describing here. I'm sorry I am not able to be more specific as to the reason I've no longer got this double login issue, other than today's update process cured mine.

---

### Post by verymadpip on 2012-01-20
Well, given that I started the thread I thought it would be rude not to share my findings & it's clearly relevant to my situation.

Why did this begin with lightdm & not gdm?  There are no issues with logging into W7, even with changing the colour of the pretty lights.  Curiouser & curiouser.
On the whole it's not a deal breaker, I know how to avoid it happening, fixing it would be a bonus if it's possible.

Aha, I see where to fing the logs now...

---

### Post by stellarsky on 2012-01-22
have had that happen to me also in the past before a upgrade i thing it stopped eventually though i dont recall for sure

---

### Post by KdotJ on 2012-01-25
After I updated yesterday, I have had to log in twice every time (roughly 5 times I've tried). However, I don't always get the artefacts appear on the screen now...

---

### Post by masgeeks on 2012-01-25
I've had a few bouts of the same - 11.10 x64 using gnome shell.  I think it has something to do with the display driver, or rather the hand off.  Usually, just before the boot process gets handed off to lightdm, I'll get a freaked out looking color snowy static mess for a flashing moment, then lightdm pops up, all looks just fine.  This happens on most of workstations, though (nasty AMD video cards).  However, on this one there I've had to log in twice on a few occasions, there have also been a few times where the desktop would start, look normal but then BURP and my desktop will look like the same freaked out snowy color static mess I get in that flashing moment before lightdm.  Gnome shell is accessible, so I can gracefully log out.  If I log out and log back in, it would be ok.  Has not done it the past few days, but I have done a couple kernel updates - running 3.2 generic kernel... seems to be a non-issue now, so... dunno... it was kind of weird, thought it was just me...!!!  Interesting to know others have experienced the same.  Never had a workstation do this before - always something *new and exciting*, lol...

---

### Post by ms99 on 2012-02-07
Had same problem here. Login twice with Pixel shadows in the upper left.

On my system under proprietary drivers two entries are shown:

Accelerated graphics driver NVIDIA (current)
and
Accelerated graphics driver NVIDIA (current-updates)

(current-updates) was active. I changed to (current).

Problem is gone now.

---

### Post by Bolli1983 on 2012-02-07
I'd like to state, that i have that problem, too with Ubuntu 11.10 x64. I did a fresh install, not upgrading from earlier versions. I have a P8H67-M board with H67 chipset and an intel i3 (using built in graphics, no proprietary drivers). The error usually occurs when i first start an application after logging in (usually, not always).

The screen that comes before the second login screen is the following:

[img]https://lh6.googleusercontent.com/-DVSMTCxlOQ0/Tyl80FJMlZI/AAAAAAAADZY/woMAloQo05o/s640/2012-02-01%252018.55.55.jpg[/img]

I'll provide any log asked for, i just don't know which one would be relevant =o

The screen above sometimes appears when shutting down also, prohibiting the system from fully shutting down.

---

### Post by d4m1r on 2012-02-12
I am getting this too (after upgrading from 11.04)....

People say:

sudo su

echo "/usr/sbin/lightdm" > /etc/X11/default-display-manager

exit

^Should fix the problem but I can't confirm that yet.

---

### Post by d4m1r on 2012-02-25
> **ms99 said:**
> **Had same problem here. Login twice with Pixel shadows in the upper left.**

On my system under proprietary drivers two entries are shown:

Accelerated graphics driver NVIDIA (current)
and
Accelerated graphics driver NVIDIA (current-updates)

(current-updates) was active. I changed to (current).

Problem is gone now.

I am still seeing this, and its definitely the exact same issue. I know its a graphics issue because whether I type in my password or even leave it blank, the page goes black for a second and I have to type it in 2nd time to login...

Also, my above post did not fix it for me ](*,)

---

### Post by jbarbieri on 2012-04-23
I also get this problem.

I see it more when the computer is woken up from sleep. I log in once, I can see my desktop, then it fades to black, and I get the login box again. After the second time, I am able to use the computer.

I am running on a Lenovo Thinkpad, 11.10 x86

---

### Post by d4m1r on 2012-04-23
I am still getting this too....After I upgraded to 11.10 from 11.04. Soon after 12.04 comes out, I'll be doing a clean install so hopefully it'll be gone after that...

---

### Post by d4m1r on 2012-04-25
> **d4m1r said:**
> I am still getting this too....After I upgraded to 11.10 from 11.04. Soon after 12.04 comes out, I'll be doing a clean install so hopefully it'll be gone after that...


After looking into my auth.log file, I see several lightdm issues that are repeated over and over and again. A sample of then is below:

```
Apr 25 19:53:51 Damir-Ubuntu lightdm: pam_unix(lightdm:session): session opened 
for user lightdm by (uid=0)
Apr 25 19:53:51 Damir-Ubuntu lightdm: pam_ck_connector(lightdm:session): nox11 m
ode, ignoring PAM_TTY :0
Apr 25 19:53:52 Damir-Ubuntu lightdm: pam_succeed_if(lightdm:auth): requirement 
"user ingroup nopasswdlogin" not met by user "damir"
Apr 25 19:53:52 Damir-Ubuntu dbus[924]: [system] Rejected send message, 2 matche
d rules; type="method_call", sender=":1.21" (uid=114 pid=1652 comm="/usr/lib/ind
icator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Propert
ies" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.12
" (uid=0 pid=1429 comm="/usr/sbin/console-kit-daemon --no-daemon ")
```Could that be related as to why I have to type in my password twice sometimes? Anyone have a suggestion to fix that error?

---

### Post by malchowb on 2012-05-30
> **Handssolow said:**
> No solutions yet but I'm getting this too since yesterday when I transferred my HD with 11.10 to a new PC. It all seems to be working except I'm having to log in twice though possibly not every time. On the login screen I've noticed some odd pixels some flashing in the top left quarter of the screen, seems from here that this is a related issue. I've also noticed the Scroll Lock light is lit when the first log in screen appears.

I did the following and it went away...I had this issue with 11.10 as well.

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update

---

### Post by BruFFy on 2013-01-27
Tried malchowb's sollution but it didn't work for me :(
 
ubuntu 12.04

---

### Post by d4m1r on 2013-01-27
I still has this issue with 12.04.1 (x64) as well....Not as much as 11.10 but still.

---

### Post by paolik65 on 2013-03-20
Same problem here.

Solution: use GDM instead of LIGHTDM solved it for me.

Install GDM and select it in terminal mode with the following command line:


sudo dpkg-reconfigure gdm

---

### Post by d4m1r on 2013-03-20
> **paolik65 said:**
> Same problem here.

Solution: use GDM instead of LIGHTDM solved it for me.

Install GDM and select it in terminal mode with the following command line:


sudo dpkg-reconfigure gdm


Can you post a screenshot of what GDM looks like? Last time I remember, LightDM looks much better and that's why I wanna stick with it.

---

