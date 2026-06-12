---
title: "Script to parse log file : Help"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by Leveroc on 2012-11-06
My problem is I need to write a script using zenity to display radiolist of users stats from Urban Terror Game. Displaying how many flag captures, returns, points, headshots, and damage a player did. I have started this by using grep to count the occurances of strings, but it only outputs the number and I need it to give the player name with the number. I problably should use something better but I am a newbie. here is the log file and script I have so far.

#!/bin/bash
label="1jar Captures"
grep -c -F '^1jar^7 has taken the ^4Blue^7 flag!' utlog-ctf.txt

a small sample of the log file is here: and attached to this post
UI menu load time = 145 milli seconds
UI menu load time = 103 milli seconds
16 bots parsed
13 crosshairs parsed
UI menu load time = 7 milli seconds
13 crosshairs parsed
server: EfX: 5 headshots!
server: EfX made 2 headshots
^4FURRIEL^7 has taken the ^1Red^7 flag!
^4FURRIEL^7 dropped the ^1Red^7 flag!
server: }666{SLaYeR made 6 nade kills
server: MEDICO: 11 headshots! (15 percent)
Raf returned the RED flag!
server: CAPITAN: 5 headshots!
server: CAPITAN made 5 headshots
^1-=UrT4 CTF East=- ^3| ^2www.urtctf.com ^3| ^4E-mail [EMAIL="moon.q3@gmail.com"]moon.q3@gmail.com[/EMAIL]
server: Raf: 1 headshot!
^1(DEAD) }666{SLaYeR^3: ^3NO
Raf got a lead enema from pretorian*jramosd.co's retro M4.
server: pretorian*jramosd.co: 2 headshots!
EfX was torn asunder by FURRIEL's crass AK103.
debian_wheezy joined the red team.
debian_wheezy entered the game
^1-=UrT4 CTF East=- ^3| ^2www.urtctf.com ^3| ^4E-mail [EMAIL="moon.q3@gmail.com"]moon.q3@gmail.com[/EMAIL]
server: pretorian*jramosd.co made 2 headshots
jar got shredded to pieces by }666{-pR0_5N!p3r's Negev
CAPITAN was torn asunder by ADMIRAL's crass AK103.
console_tell: ^0(^2b3^0)^7: ^3[pm]^7 Everyone welcome ^7debian_wheezy^7^7 back!

server: CAPITAN: 6 headshots!
ADMIRAL bled to death from CAPITAN's attacks.
^4(DEAD) CAPITAN^3: ^3die
You hit }666{-pR0_5N!p3r in the Legs for 17% damage.
You were hit in the Kevlar by }666{-pR0_5N!p3r for 20% damage.
You protected the Red flag.
You hit }666{-pR0_5N!p3r in the Kevlar for 29% damage.
}666{-pR0_5N!p3r played 'catch the shiny bullet' with debian_wheezy's LR-300 rounds.
You were hit in the Kevlar by FURRIEL for 34% damage.
You were hit in the Kevlar by FURRIEL for 34% damage.
You were hit in the Legs by pretorian*jramosd.co for 17% damage.
debian_wheezy got a lead enema from pretorian*jramosd.co's retro M4.
pretorian*jramosd.co had 7% Health.
^4pretorian*jramosd.co^7 has taken the ^1Red^7 flag!
}666{SLaYeR was torn asunder by FURRIEL's crass AK103.
^4pretorian*jramosd.co^7 dropped the ^1Red^7 flag!
pretorian*jramosd.co has become a nasty stain thanks to }666{SLaYeR's HE gren.
server: }666{SLaYeR made 3 headshots
server: }666{SLaYeR made 7 nade kills
Raf got a lead enema from MEDICO's retro M4.
^1(DEAD) }666{SLaYeR^3: ^3lmao
MEDICO got a lead enema from jar's retro M4.
FURRIEL got a lead enema from EfX's retro M4.
EfX returned the RED flag!
server: CAPITAN: 7 headshots!
EfX got a whole lot of hole from CAPITAN's DE round.
server: CAPITAN made 6 headshots
Santis has become a nasty stain thanks to debian_wheezy's HE gren.
server: debian_wheezy made 1 nade kills
server: }666{-pR0_5N!p3r: 24 headshots! (24 percent)
^1jar^7 has taken the ^4Blue^7 flag!
ADMIRAL got shredded to pieces by }666{-pR0_5N!p3r's Negev

---

