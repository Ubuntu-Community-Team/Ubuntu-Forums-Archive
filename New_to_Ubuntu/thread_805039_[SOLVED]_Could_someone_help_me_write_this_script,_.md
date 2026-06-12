---
title: "[SOLVED] Could someone help me write this script, please?"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by geo909 on 2008-05-23
Hello everybody,

I have an old MP3Player which I still use. It's a simple player, no 
playlists, no shuffle, no nothing.

Since it plays tracks in an alphabetic order I would like to write a script
that gives random names (ending in ".mp3") in all of the files of a folder.
This way, I will run the script before I go jogging and I will have my tracks shuffled.

The only problem is that I don't know to write scripts.
I don't know if it is difficult or not. If it easy, could someone do
it for me, please? :mrgreen:

   Thanks in advance!

---

### Post by geo909 on 2008-05-23
**[COLOR="Red"]IGNORE MY PREVIOUS POST!!![/COLOR]**

It actually plays the tracks in the order I put them in.
First put, first played.

So actually I need a script that uses something like "touch"
or "finger" to modify all of the contents of the folder in random order..
Is that difficult?..

---

### Post by nick_h on 2008-05-23
Try this:
```
#!/bin/bash
RANDOM=$$
DAY=`date +%m%d`
for FILE in *; do
	HH=$[ $RANDOM % 24 + 100 ]
	HH=${HH:1}
	MM=$[ $RANDOM % 60 + 100 ]
	MM=${MM:1}
	SS=$[ $RANDOM % 60 + 100 ]
	SS=${SS:1}
	touch -mt $DAY$HH$MM.$SS "$FILE"
done
```

It changes the last modified time of all files in the current directory to a random time.  The last modified date will be set to today's date.

---

### Post by geo909 on 2008-05-23
Thanks! It doesn't work very good, though, it creates many empty files.
See below.

BEFORE THE SCRIPT:
```
jorge@linux-kupy:/media/disk> ls -lt
total 229216
-rwx------ 1 jorge root     215 2008-05-24 01:23 make_random.sh
-rwxr-xr-x 1 jorge root 4300382 2008-05-16 10:45 Semi Charmed Life.mp3
-rwxr-xr-x 1 jorge root 7189111 2008-05-11 18:39 transkode-Unknown Artist-Unknown Title 3.mp3
-rwxr-xr-x 1 jorge root 5074713 2008-05-08 18:42 Step It Up.mp3
-rwxr-xr-x 1 jorge root 7189111 2008-05-08 18:40 Vamono.wma.mp3
-rwxr-xr-x 1 jorge root 6381547 2008-05-05 20:23 02 - Dying For Your Love.mp3
-rwxr-xr-x 1 jorge root 5930131 2008-05-05 20:22 05 - Firewall.mp3
-rwxr-xr-x 1 jorge root 7530343 2008-05-05 20:22 08 - The Audience Is Listening.mp3
-rwxr-xr-x 1 jorge root 4390865 2008-05-05 20:21 02 - Viv Woman.mp3
-rwxr-xr-x 1 jorge root 4094524 2008-05-05 20:21 04 -Answers.mp3
-rwxr-xr-x 1 jorge root 5920542 2008-04-28 15:15 My Freedom.mp3
-rwxr-xr-x 1 jorge root 7770774 2008-04-23 09:11 Keep It Steady.mp3
-rwxr-xr-x 1 jorge root 6271298 2008-04-15 19:52 Hip Hop  Ft The Procussions.mp3
-rwxr-xr-x 1 jorge root 4961603 2008-04-15 19:51 J'attends.mp3
-rwxr-xr-x 1 jorge root 5213639 2008-04-15 19:51 Onandon Part  2.mp3
-rwxr-xr-x 1 jorge root 2454347 2008-04-12 22:49 Seduceme.mp3
-rwxr-xr-x 1 jorge root 3682857 2008-04-12 22:49 Cansado.mp3
-rwxr-xr-x 1 jorge root 3210768 2008-04-12 22:49 Habaneando.mp3
-rwxr-xr-x 1 jorge root 3852973 2008-03-29 20:45 Porcelain.mp3
-rwxr-xr-x 1 jorge root 4627283 2008-02-20 10:55 CLOUDS ACROSS THE MOON.mp3
-rwxr-xr-x 1 jorge root 3357341 2008-02-20 10:55 LOCO IN ACAPULCO.mp3
-rwxr-xr-x 1 jorge root 2954845 2008-02-20 10:55 THIS OLD HOUSE.mp3
-rwxr-xr-x 1 jorge root 4608302 2008-02-20 10:55 AUTOMATIC.mp3
-rwxr-xr-x 1 jorge root 3303195 2008-02-20 10:55 GOING BACK TO MY ROOTS.mp3
-rwxr-xr-x 1 jorge root 3156895 2008-02-20 10:55 I WON'T LET THE SUN GO DOWN ON ME.mp3
-rwxr-xr-x 1 jorge root 4111628 2008-02-20 10:55 BABY DON'T FORGET MY NUMBER.mp3
-rwxr-xr-x 1 jorge root 5861240 2008-02-20 10:55 EXPRESS YOURSELF.mp3
-rwxr-xr-x 1 jorge root 4073151 2008-02-20 10:55 ALL NIGHT LONG.mp3
-rwxr-xr-x 1 jorge root 4385102 2008-02-20 10:55 DANCING ON THE CEILING.mp3
-rwxr-xr-x 1 jorge root 5919833 2008-02-20 10:55 CENTERFOLD.mp3
-rwxr-xr-x 1 jorge root 5185870 2008-02-20 10:55 REGGAE NIGHTS.mp3
-rwxr-xr-x 1 jorge root 5387331 2008-02-20 10:55 FATHER FIGURE.mp3
-rwxr-xr-x 1 jorge root 3340884 2008-02-20 10:55 STREET TUFF.mp3
-rwxr-xr-x 1 jorge root 3266644 2008-02-20 10:55 DICTATOR.mp3
-rwxr-xr-x 1 jorge root 3855428 2008-02-20 10:55 YOU WIN AGAIN.mp3
-rwxr-xr-x 1 jorge root 3880113 2008-01-07 14:56 Waves.mp3
-rwxr-xr-x 1 jorge root 3881572 2007-12-02 22:39 Siempre Hay un Precio [2000].mp3
-rwxr-xr-x 1 jorge root 5980160 2007-12-02 17:54 Please Don't Go (Club Mix).mp3
-rwxr-xr-x 1 jorge root 7123192 2007-12-02 17:50 5 Alive.mp3
-rwxr-xr-x 1 jorge root 4470784 2007-12-02 17:38 Titan - Corazon.mp3
-rwxr-xr-x 1 jorge root 8988470 2007-12-02 16:19 hot jazz biscuits.mp3
-rwxr-xr-x 1 jorge root 7843072 2007-12-02 15:57 So What The Fuss.mp3
-rwxr-xr-x 1 jorge root 7666944 2007-12-02 15:57 That Girl.mp3
-rwxr-xr-x 1 jorge root 6771213 2007-12-02 15:17 (The Making Of....) Jill.mp3
-rwxr-xr-x 1 jorge root 9198579 2007-12-02 12:53 Altogether Blue.mp3
-rwxr-xr-x 1 jorge root 6004969 2007-04-04 13:28 Volumen Dos - 12 - Metaluna Mutant, The - Blinky Blue Eyed Sunrise.mp3

```

AFTER THE SCRIPT:

```
jorge@linux-kupy:/media/disk> sh make_random.sh
touch: invalid option -- A
Try `touch --help' for more information.
jorge@linux-kupy:/media/disk> ls -lt
total 229216
-rwxr-xr-x 1 jorge root       0 2008-05-24 23:43 Onandon
-rwxr-xr-x 1 jorge root       0 2008-05-24 23:43 Part
-rwxr-xr-x 1 jorge root       0 2008-05-24 23:42 Fuss.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 23:42 So
-rwxr-xr-x 1 jorge root       0 2008-05-24 23:42 What
-rwxr-xr-x 1 jorge root       0 2008-05-24 23:19 Girl.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 23:19 That
-rwxr-xr-x 1 jorge root       0 2008-05-24 23:06 Charmed
-rwxr-xr-x 1 jorge root       0 2008-05-24 23:06 Life.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 23:06 Semi
-rwxr-xr-x 1 jorge root       0 2008-05-24 23:04 ACAPULCO.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 23:04 in
-rwxr-xr-x 1 jorge root       0 2008-05-24 23:04 loco
-rwxr-xr-x 1 jorge root       0 2008-05-24 21:42 Keep
-rwxr-xr-x 1 jorge root       0 2008-05-24 21:42 Steady.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 21:41 all
-rwxr-xr-x 1 jorge root       0 2008-05-24 21:41 LONG.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 21:41 night
-rwxr-xr-x 1 jorge root       0 2008-05-24 21:27 Freedom.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 21:27 my
-rwxr-xr-x 1 jorge root 3210768 2008-05-24 21:21 Habaneando.mp3
-rwxr-xr-x 1 jorge root 3880113 2008-05-24 20:13 Waves.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 20:11 02
-rwxr-xr-x 1 jorge root       0 2008-05-24 20:11 Viv
-rwxr-xr-x 1 jorge root       0 2008-05-24 20:11 Woman.mp3
-rwxr-xr-x 1 jorge root 7189111 2008-05-24 18:25 Vamono.wma.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 18:16 street
-rwxr-xr-x 1 jorge root       0 2008-05-24 18:16 TUFF.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 16:43 Jill.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 16:43 Making
-rwxr-xr-x 1 jorge root       0 2008-05-24 16:43 Of....)
-rwxr-xr-x 1 jorge root       0 2008-05-24 16:43 (The
-rwxr-xr-x 1 jorge root       0 2008-05-24 16:22 father
-rwxr-xr-x 1 jorge root       0 2008-05-24 16:22 FIGURE.mp3
-rwxr-xr-x 1 jorge root 3682857 2008-05-24 15:04 Cansado.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 14:54 It
-rwxr-xr-x 1 jorge root       0 2008-05-24 14:54 Step
-rwxr-xr-x 1 jorge root       0 2008-05-24 14:54 Up.mp3
-rwxr-xr-x 1 jorge root 2454347 2008-05-24 14:38 Seduceme.mp3
-rwxr-xr-x 1 jorge root 3852973 2008-05-24 13:58 Porcelain.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 12:27 2.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 12:27 Hay
-rwxr-xr-x 1 jorge root       0 2008-05-24 12:27 Precio
-rwxr-xr-x 1 jorge root       0 2008-05-24 12:27 Siempre
-rwxr-xr-x 1 jorge root       0 2008-05-24 12:27 un
-rwxr-xr-x 1 jorge root       0 2008-05-24 11:45 3.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 11:45 Artist-Unknown
-rwxr-xr-x 1 jorge root       0 2008-05-24 11:45 Title
-rwxr-xr-x 1 jorge root       0 2008-05-24 11:45 transkode-Unknown
-rwxr-xr-x 1 jorge root       0 2008-05-24 11:36 express
-rwxr-xr-x 1 jorge root       0 2008-05-24 11:36 YOURSELF.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 11:15 baby
-rwxr-xr-x 1 jorge root       0 2008-05-24 11:15 forget
-rwxr-xr-x 1 jorge root       0 2008-05-24 11:15 NUMBER.mp3
-rwxr-xr-x 1 jorge root 3266644 2008-05-24 10:52 DICTATOR.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 10:01 12
-rwxr-xr-x 1 jorge root       0 2008-05-24 10:01 Blinky
-rwxr-xr-x 1 jorge root       0 2008-05-24 10:01 Blue
-rwxr-xr-x 1 jorge root       0 2008-05-24 10:01 Dos
-rwxr-xr-x 1 jorge root       0 2008-05-24 10:01 Eyed
-rwxr-xr-x 1 jorge root       0 2008-05-24 10:01 Metaluna
-rwxr-xr-x 1 jorge root       0 2008-05-24 10:01 Mutant,
-rwxr-xr-x 1 jorge root       0 2008-05-24 10:01 Sunrise.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 10:01 The
-rwxr-xr-x 1 jorge root       0 2008-05-24 10:01 Volumen
-rwxr-xr-x 1 jorge root       0 2008-05-24 09:51 Dying
-rwxr-xr-x 1 jorge root       0 2008-05-24 09:51 For
-rwxr-xr-x 1 jorge root       0 2008-05-24 09:51 Love.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 09:51 Your
-rwxr-xr-x 1 jorge root       0 2008-05-24 08:52 (Club
-rwxr-xr-x 1 jorge root       0 2008-05-24 08:52 don't
-rwxr-xr-x 1 jorge root       0 2008-05-24 08:52 go
-rwxr-xr-x 1 jorge root       0 2008-05-24 08:52 Mix).mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 08:52 Please
-rwxr-xr-x 1 jorge root       0 2008-05-24 08:45 down
-rwxr-xr-x 1 jorge root       0 2008-05-24 08:45 i
-rwxr-xr-x 1 jorge root       0 2008-05-24 08:45 let
-rwxr-xr-x 1 jorge root       0 2008-05-24 08:45 ME.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 08:45 on
-rwxr-xr-x 1 jorge root       0 2008-05-24 08:45 sun
-rwxr-xr-x 1 jorge root       0 2008-05-24 08:45 won't
-rwxr-xr-x 1 jorge root       0 2008-05-24 08:19 5
-rwxr-xr-x 1 jorge root       0 2008-05-24 08:19 Alive.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 06:47 08
-rwxr-xr-x 1 jorge root       0 2008-05-24 06:47 Audience
-rwxr-xr-x 1 jorge root       0 2008-05-24 06:47 Is
-rwxr-xr-x 1 jorge root       0 2008-05-24 06:47 Listening.mp3
-rwxr-xr-x 1 jorge root 4608302 2008-05-24 06:21 AUTOMATIC.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 03:56 biscuits.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 03:56 hot
-rwxr-xr-x 1 jorge root       0 2008-05-24 03:56 jazz
-rwxr-xr-x 1 jorge root       0 2008-05-24 03:43 AGAIN.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 03:43 win
-rwxr-xr-x 1 jorge root       0 2008-05-24 03:43 you
-rwxr-xr-x 1 jorge root       0 2008-05-24 03:39 back
-rwxr-xr-x 1 jorge root       0 2008-05-24 03:39 going
-rwxr-xr-x 1 jorge root       0 2008-05-24 03:39 ROOTS.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 03:39 to
-rwxr-xr-x 1 jorge root       0 2008-05-24 03:04 across
-rwxr-xr-x 1 jorge root       0 2008-05-24 03:04 clouds
-rwxr-xr-x 1 jorge root       0 2008-05-24 03:04 MOON.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 02:49 HOUSE.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 02:49 old
-rwxr-xr-x 1 jorge root       0 2008-05-24 02:49 this
-rwxr-xr-x 1 jorge root       0 2008-05-24 02:48 Ft
-rwxr-xr-x 1 jorge root       0 2008-05-24 02:48 Hip
-rwxr-xr-x 1 jorge root       0 2008-05-24 02:48 Hop
-rwxr-xr-x 1 jorge root       0 2008-05-24 02:48 Procussions.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 02:17 05
-rwxr-xr-x 1 jorge root       0 2008-05-24 02:17 Firewall.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 02:02 NIGHTS.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 02:02 reggae
-rwxr-xr-x 1 jorge root       0 2008-05-24 01:54 CEILING.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 01:54 dancing
-rwxr-xr-x 1 jorge root       0 2008-05-24 01:38 Altogether
-rwxr-xr-x 1 jorge root       0 2008-05-24 01:38 Blue.mp3
-rwxr-xr-x 1 jorge root 5919833 2008-05-24 01:00 CENTERFOLD.mp3
-rwx------ 1 jorge root     215 2008-05-24 00:55 make_random.sh
-rwxr-xr-x 1 jorge root       0 2008-05-24 00:51 Corazon.mp3
-rwxr-xr-x 1 jorge root       0 2008-05-24 00:51 Titan
-rwxr-xr-x 1 jorge root 4961603 2008-05-24 00:40 J'attends.mp3
-rwxr-xr-x 1 jorge root 4300382 2008-05-16 10:45 Semi Charmed Life.mp3
-rwxr-xr-x 1 jorge root 7189111 2008-05-11 18:39 transkode-Unknown Artist-Unknown Title 3.mp3
-rwxr-xr-x 1 jorge root 5074713 2008-05-08 18:42 Step It Up.mp3
-rwxr-xr-x 1 jorge root 6381547 2008-05-05 20:23 02 - Dying For Your Love.mp3
-rwxr-xr-x 1 jorge root 5930131 2008-05-05 20:22 05 - Firewall.mp3
-rwxr-xr-x 1 jorge root 7530343 2008-05-05 20:22 08 - The Audience Is Listening.mp3
-rwxr-xr-x 1 jorge root 4390865 2008-05-05 20:21 02 - Viv Woman.mp3
-rwxr-xr-x 1 jorge root 4094524 2008-05-05 20:21 04 -Answers.mp3
-rwxr-xr-x 1 jorge root 5920542 2008-04-28 15:15 My Freedom.mp3
-rwxr-xr-x 1 jorge root 7770774 2008-04-23 09:11 Keep It Steady.mp3
-rwxr-xr-x 1 jorge root 6271298 2008-04-15 19:52 Hip Hop  Ft The Procussions.mp3
-rwxr-xr-x 1 jorge root 5213639 2008-04-15 19:51 Onandon Part  2.mp3
-rwxr-xr-x 1 jorge root 4627283 2008-02-20 10:55 CLOUDS ACROSS THE MOON.mp3
-rwxr-xr-x 1 jorge root 3357341 2008-02-20 10:55 LOCO IN ACAPULCO.mp3
-rwxr-xr-x 1 jorge root 2954845 2008-02-20 10:55 THIS OLD HOUSE.mp3
-rwxr-xr-x 1 jorge root 3303195 2008-02-20 10:55 GOING BACK TO MY ROOTS.mp3
-rwxr-xr-x 1 jorge root 3156895 2008-02-20 10:55 I WON'T LET THE SUN GO DOWN ON ME.mp3
-rwxr-xr-x 1 jorge root 4111628 2008-02-20 10:55 BABY DON'T FORGET MY NUMBER.mp3
-rwxr-xr-x 1 jorge root 5861240 2008-02-20 10:55 EXPRESS YOURSELF.mp3
-rwxr-xr-x 1 jorge root 4073151 2008-02-20 10:55 ALL NIGHT LONG.mp3
-rwxr-xr-x 1 jorge root 4385102 2008-02-20 10:55 DANCING ON THE CEILING.mp3
-rwxr-xr-x 1 jorge root 5185870 2008-02-20 10:55 REGGAE NIGHTS.mp3
-rwxr-xr-x 1 jorge root 5387331 2008-02-20 10:55 FATHER FIGURE.mp3
-rwxr-xr-x 1 jorge root 3340884 2008-02-20 10:55 STREET TUFF.mp3
-rwxr-xr-x 1 jorge root 3855428 2008-02-20 10:55 YOU WIN AGAIN.mp3
-rwxr-xr-x 1 jorge root 3881572 2007-12-02 22:39 Siempre Hay un Precio [2000].mp3
-rwxr-xr-x 1 jorge root 5980160 2007-12-02 17:54 Please Don't Go (Club Mix).mp3
-rwxr-xr-x 1 jorge root 7123192 2007-12-02 17:50 5 Alive.mp3
-rwxr-xr-x 1 jorge root 4470784 2007-12-02 17:38 Titan - Corazon.mp3
-rwxr-xr-x 1 jorge root 8988470 2007-12-02 16:19 hot jazz biscuits.mp3
-rwxr-xr-x 1 jorge root 7843072 2007-12-02 15:57 So What The Fuss.mp3
-rwxr-xr-x 1 jorge root 7666944 2007-12-02 15:57 That Girl.mp3
-rwxr-xr-x 1 jorge root 6771213 2007-12-02 15:17 (The Making Of....) Jill.mp3
-rwxr-xr-x 1 jorge root 9198579 2007-12-02 12:53 Altogether Blue.mp3
-rwxr-xr-x 1 jorge root 6004969 2007-04-04 13:28 Volumen Dos - 12 - Metaluna Mutant, The - Blinky Blue Eyed Sunrise.mp3

```

---

### Post by nick_h on 2008-05-23
I think the problem is that I forgot to put the filename in quotes.

---

### Post by wootah on 2008-05-23
> **nick_h said:**
> Try this:
```
#!/bin/bash
RANDOM=$$
DAY=`date +%m%d`
for FILE in *; do
	HH=$[ $RANDOM % 24 + 100 ]
	HH=${HH:1}
	MM=$[ $RANDOM % 60 + 100 ]
	MM=${MM:1}
	SS=$[ $RANDOM % 60 + 100 ]
	SS=${SS:1}
	touch -mt $DAY$HH$MM.$SS $FILE
done
```

It changes the last modified time of all files in the current directory to a random time.  The last modified date will be set to today's date.

Ahhhh very subtle bug here. It is describe here: [http://ubuntuforums.org/showthread.php?t=83424]("http://ubuntuforums.org/showthread.php?t=83424")

Modified code:
```

#!/bin/bash
RANDOM=$$
DAY=`date +%m%d`

while read FILE;do
	HH=$[ $RANDOM % 24 + 100 ]
	HH=${HH:1}
	MM=$[ $RANDOM % 60 + 100 ]
	MM=${MM:1}
	SS=$[ $RANDOM % 60 + 100 ]
	SS=${SS:1}
	touch -mt $DAY$HH$MM.$SS $FILE
done

```

Problem was that you have songs that have spaces in it :) I hope that works for you!

---

### Post by nick_h on 2008-05-23
> Problem was that you have songs that have spaces in it
Yes, that's the problem.  I didn't test it very well. :)

The extra quotes fix the problem though.

---

### Post by wootah on 2008-05-23
> **nick_h said:**
> Yes, that's the problem.  I didn't test it very well. :)

The extra quotes fix the problem though.

Extra quotes?

---

### Post by nick_h on 2008-05-23
```
touch -mt $DAY$HH$MM.$SS [COLOR="Red"]"[/COLOR]$FILE[COLOR="Red"]"[/COLOR]
```

---

### Post by wootah on 2008-05-23
> **nick_h said:**
> ```
touch -mt $DAY$HH$MM.$SS [COLOR="Red"]"[/COLOR]$FILE[COLOR="Red"]"[/COLOR]
```

Ahhhh. I like that way much better :)

Geo909, does this all work ok now?

---

### Post by geo909 on 2008-05-23
Thank you very much! 
Yes, it worked.
But..

...

Ok, please don't kill me!

Well, it seems that the player doesn't sort files by the date they were modified. Sorry that make you spent time on this.

I spent some time trying to figure out how it sorts the songs. When I put new songs it puts them either first or last. No sort by name or anything. I really can't understand. Maybe a scipt that uses "mv" in random order to copy a file in a file with the same name would do the job..
But if you don't have time to spent, it's okay.

---

### Post by nick_h on 2008-05-24
You could try making the access time rather than the last modification time random.  To do this just change the -m flag in the *touch* command to -a.

Most mp3 players use a FAT filesystem.  It may be that the player uses the create time.  The problem here is that linux filesystems don't support create time on files so commands like *touch* will not support changing them.

Using the *mv* command may be an option, or maybe there is something in the *mtools* package.  I'll have a look at it again tonight.

---

### Post by nick_h on 2008-05-25
The easiest way to test this would be to add the following to the bottom of the script:
```
ls -t | while read FILE; do
	cp "$FILE" "$1"
done
```

Run the script in a directory on your PC containing the mp3 files.  Specify the directory on your mp3 player as a parameter to the script.

The script will copy the files to the mp3 player in the random order of the file modification time.

---

### Post by geo909 on 2008-05-25
Hi again, thanks a lot for the help!!

> **nick_h said:**
> You could try making the access time rather than the last modification time random.  To do this just change the -m flag in the *touch* command to -a.


That didn't work.. ..it doesn't seem to que files this way

> 
Most mp3 players use a FAT filesystem.  It may be that the player uses the create time.  The problem here is that linux filesystems don't support create time on files so commands like *touch* will not support changing them.


Indeed, it's a FAT disk.


So, do you say something like that:

```
#!/bin/bash
RANDOM=$$
DAY=`date +%m%d`
for FILE in *; do
	HH=$[ $RANDOM % 24 + 100 ]
	HH=${HH:1}
	MM=$[ $RANDOM % 60 + 100 ]
	MM=${MM:1}
	SS=$[ $RANDOM % 60 + 100 ]
	SS=${SS:1}
	touch -mt $DAY$HH$MM.$SS "$FILE"

	ls -t | while read FILE; do
	cp "$FILE" "$1"
	done

done 

```

> Specify the directory on your mp3 player as a parameter to the script.
Well.. how should I do that?
Let's say I have my disk mounted at 
> /media/disk
Where should I put that?
Forgive my lack of knowledge..

I tried to run it like that and I just take never ending lines like this:

```

cp: cannot create regular file `': No such file or directory
cp: cannot create regular file `': No such file or directory
cp: cannot create regular file `': No such file or directory
cp: cannot create regular file `': No such file or directory
cp: cannot create regular file `': No such file or directory
cp: cannot create regular file `': No such file or directory
cp: cannot create regular file `': No such file or directory
cp: cannot create regular file `': No such file or directory
cp: cannot create regular file `': No such file or directory

```

---

### Post by nick_h on 2008-05-25
Add the code to the end of the script.

```
#!/bin/bash
RANDOM=$$
DAY=`date +%m%d`
for FILE in *; do
	HH=$[ $RANDOM % 24 + 100 ]
	HH=${HH:1}
	MM=$[ $RANDOM % 60 + 100 ]
	MM=${MM:1}
	SS=$[ $RANDOM % 60 + 100 ]
	SS=${SS:1}
	touch -mt $DAY$HH$MM.$SS "$FILE"
done

ls -t | while read FILE; do
	cp "$FILE" "$1"
done

```

Create a directory called *bin* in your home directory.  This will be put in your PATH by your *.bashrc* script.  Move your script into this new *bin* directory.

Run it with:
```
make_random.sh /media/disk
```

The script will change the modification times of all files in the current directory.  Then it will loop through each file in order of modification time and copy it into /media/disk.  If you keep the music in a subdirectory you should include that in the path.

---

### Post by geo909 on 2008-05-27
Hello again!
Unfortunately it doesn't work, it goes like this:

```
jorge@linux-kupy:/media/disk> ./make_random.sh /media/disk
cp: `Porcelain.mp3' and `/media/disk/Porcelain.mp3' are the same file
cp: `Vamono.wma.mp3' and `/media/disk/Vamono.wma.mp3' are the same file
cp: `I WON\'T LET THE SUN GO DOWN ON ME.mp3' and `/media/disk/I WON\'T LET THE SUN GO DOWN ON ME.mp3' are the same file
cp: `Siempre Hay un Precio [2000].mp3' and `/media/disk/Siempre Hay un Precio [2000].mp3' are the same file
cp: `AUTOMATIC.mp3' and `/media/disk/AUTOMATIC.mp3' are the same file
cp: `GOING BACK TO MY ROOTS.mp3' and `/media/disk/GOING BACK TO MY ROOTS.mp3' are the same file
cp: `04 -Answers.mp3' and `/media/disk/04 -Answers.mp3' are the same file
cp: `DANCING ON THE CEILING.mp3' and `/media/disk/DANCING ON THE CEILING.mp3' are the same file
cp: `So What The Fuss.mp3' and `/media/disk/So What The Fuss.mp3' are the same file
cp: `05 - Firewall.mp3' and `/media/disk/05 - Firewall.mp3' are the same file
cp: `LOCO IN ACAPULCO.mp3' and `/media/disk/LOCO IN ACAPULCO.mp3' are the same file
cp: `transkode-Unknown Artist-Unknown Title 3.mp3' and `/media/disk/transkode-Unknown Artist-Unknown Title 3.mp3' are the same file
cp: `(The Making Of....) Jill.mp3' and `/media/disk/(The Making Of....) Jill.mp3' are the same file
cp: `ONCE UPON A LONG AGO.mp3' and `/media/disk/ONCE UPON A LONG AGO.mp3' are the same file
cp: `Habaneando.mp3' and `/media/disk/Habaneando.mp3' are the same file
cp: `STREET TUFF.mp3' and `/media/disk/STREET TUFF.mp3' are the same file
cp: `FATHER FIGURE.mp3' and `/media/disk/FATHER FIGURE.mp3' are the same file
cp: `Seduceme.mp3' and `/media/disk/Seduceme.mp3' are the same file
cp: `Please Don\'t Go (Club Mix).mp3' and `/media/disk/Please Don\'t Go (Club Mix).mp3' are the same file
cp: `LEAN ON ME.mp3' and `/media/disk/LEAN ON ME.mp3' are the same file
cp: `Altogether Blue.mp3' and `/media/disk/Altogether Blue.mp3' are the same file
cp: `YOU WIN AGAIN.mp3' and `/media/disk/YOU WIN AGAIN.mp3' are the same file
cp: `J\'attends.mp3' and `/media/disk/J\'attends.mp3' are the same file
cp: `EXPRESS YOURSELF.mp3' and `/media/disk/EXPRESS YOURSELF.mp3' are the same file
cp: `BABY DON\'T FORGET MY NUMBER.mp3' and `/media/disk/BABY DON\'T FORGET MY NUMBER.mp3' are the same file
cp: `Onandon Part  2.mp3' and `/media/disk/Onandon Part  2.mp3' are the same file
cp: `hot jazz biscuits.mp3' and `/media/disk/hot jazz biscuits.mp3' are the same file
cp: `CLOUDS ACROSS THE MOON.mp3' and `/media/disk/CLOUDS ACROSS THE MOON.mp3' are the same file
cp: `02 - Viv Woman.mp3' and `/media/disk/02 - Viv Woman.mp3' are the same file
cp: `Waves.mp3' and `/media/disk/Waves.mp3' are the same file
cp: `08 - The Audience Is Listening.mp3' and `/media/disk/08 - The Audience Is Listening.mp3' are the same file
cp: `That Girl.mp3' and `/media/disk/That Girl.mp3' are the same file
cp: `CENTERFOLD.mp3' and `/media/disk/CENTERFOLD.mp3' are the same file
cp: `My Freedom.mp3' and `/media/disk/My Freedom.mp3' are the same file
cp: `Cansado.mp3' and `/media/disk/Cansado.mp3' are the same file
cp: `REGGAE NIGHTS.mp3' and `/media/disk/REGGAE NIGHTS.mp3' are the same file
cp: `make_random.sh' and `/media/disk/make_random.sh' are the same file
cp: `02 - Dying For Your Love.mp3' and `/media/disk/02 - Dying For Your Love.mp3' are the same file
cp: `DICTATOR.mp3' and `/media/disk/DICTATOR.mp3' are the same file
cp: `Step It Up.mp3' and `/media/disk/Step It Up.mp3' are the same file
cp: `Keep It Steady.mp3' and `/media/disk/Keep It Steady.mp3' are the same file
cp: `THIS OLD HOUSE.mp3' and `/media/disk/THIS OLD HOUSE.mp3' are the same file
cp: `5 Alive.mp3' and `/media/disk/5 Alive.mp3' are the same file
cp: `Semi Charmed Life.mp3' and `/media/disk/Semi Charmed Life.mp3' are the same file
cp: `Titan - Corazon.mp3' and `/media/disk/Titan - Corazon.mp3' are the same file
cp: `Volumen Dos - 12 - Metaluna Mutant, The - Blinky Blue Eyed Sunrise.mp3' and `/media/disk/Volumen Dos - 12 - Metaluna Mutant, The - Blinky Blue Eyed Sunrise.mp3' are the same file
cp: `ALL NIGHT LONG.mp3' and `/media/disk/ALL NIGHT LONG.mp3' are the same file
cp: `Hip Hop  Ft The Procussions.mp3' and `/media/disk/Hip Hop  Ft The Procussions.mp3' are the same file
jorge@linux-kupy:/media/disk>   
```

Is there a way to make the script add an "x" in front of the name?
That is, copy "mysong.mp3" to "\media\disk\xmysong.mp3""..

Also, I think that mv instead of cp would work better because cp will duplicate the files with a different name.

Sorry for the time-consuming thing, I have the intention to learn some bash programming the sooner I can!

---

### Post by wootah on 2008-05-27
I think this would work?

```
#!/bin/bash
RANDOM=$$
DAY=`date +%m%d`
for FILE in *; do
    HH=$[ $RANDOM % 24 + 100 ]
    HH=${HH:1}
    MM=$[ $RANDOM % 60 + 100 ]
    MM=${MM:1}
    SS=$[ $RANDOM % 60 + 100 ]
    SS=${SS:1}
    touch -mt $DAY$HH$MM.$SS "$FILE"
done

ls -t | while read FILE; do
    cp "$FILE" **"x$1"**
done

```

---

### Post by nick_h on 2008-05-27
I was intending that you kept a copy of your music files in a directory on your PC.  Then the script would copy them to your mp3 player in a random order.  I was leaving you to delete the files from the mp3 player before copying the files.

Because you are running the command in the mp3 player directory the script will try to copy the files onto themselves - hence the errors.

You could easily change the script:
```
mv "$FILE" "x$FILE"
```
This will rename the file to a file prefixed with "x".  Now you don't need the parameter and should run the script from the mp3 player directory.

I'm not sure that this will change the create time though.  I haven't tested it.

---

### Post by geo909 on 2008-05-27
Ignore this. Posted by mistake

---

### Post by geo909 on 2008-05-27
YES! It works!

HA-HA!
Beat my dust all you expensive ipod-owners! 
My 3-year-old, $20-worth, semi-broken, 256MB Taiwan-made MP3Player can actually *SHUFFLE!*
:guitar:

..

Now, after a couple of "shuffles", I have to persuade my mom that all those
"xxx" files inside my stick ain't adult stuff.

Thanks a lot for your time!

---

### Post by nick_h on 2008-05-27
I'm glad it works.  I have an old mp3 player it may be useful for.

If you want to leave the filename unchanged you could rename it straight back to the original.
```
mv "$FILE" "x$FILE"
mv "x$FILE" "$FILE"
```

---

### Post by geo909 on 2008-05-28
Thanks!! That works, too!

---

