---
title: "An idea for advanced programmers who play an instrument..."
date: 2008-02-17
forum: Programming Talk
---

### Post by JimKurth on 2008-02-17
I program in C# but I'm not a very skilled one (I'd say more along the lines of beginner going into intermediate).  I have an idea which would be great and I'd love to see it on shelves some day and I could possibly help but the concept is similar to those Guitar Hero and Rock Band games, except it's more advanced...

* You plug your guitar or any electronic instrument output jack into your computer's microphone (audio in) jack.

* You run the game and select what instrument u have plugged in.

* Before playing the game, you will calibrate each note you can play with the computer (it'll record and make a mental note of the frequencies to play that note).  For a guitar, you will pluck every fret on every string so the computer will recognize the difference between 1 note on 1 string and the same note on another string.

* You play the game and it will be like Guitar Hero where you start off playing simple notes and work your way up to advanced songs.  The processor will determine if you're hitting the right notes on the right strings and will judge your performance based on the timing and accuracy of what's presented before the gamer.

* Gradually, you'll get better at the game and ALSO obtain more skills at that instrument.  You won't need to buy a new guitar or a special piano, you can use the same one you have and essentially learn to play the instrument through this game.  You won't be playing with red/green/blue/yellow buttons, but you'll be playing with real guitar strings or real piano keys.

* Gamers = will buy it, Aspiring musicians = will buy it, Music teachers = will buy it as a training tool.  Overall = $$$$ for you or whoever makes this.  Also, it can be expanded with the same program (selling updates for electronic clarinets or violins, or bass players, with sheet music/songs designed for those instruments that go together).

* Why buy books on learning guitars for dummies when you can use your newly acquired guitar, plug it into this game, and learn to play all different styles of music from bluegrass and jazz to disco and metal?

I know there are limitations and audio recording and processing at real-time is very processor-hungry however I do have a means of speeding this up, email me and I'll tell you a way to get around this without losing the processor time if you're interested in something like this.

-JimKurth
[email]james.kurth@hotmail.com[/email]

---

### Post by Engnome on 2008-02-17
Not finished yet but still: [http://gizmodo.com/352800/guitar-rising-for-real-guitar-heroes](http://gizmodo.com/352800/guitar-rising-for-real-guitar-heroes)

> **JimKurth said:**
> The processor will determine if you're hitting the right notes on the right strings and will judge your performance based on the timing and accuracy of what's presented before the gamer.


I wonder if this is possible, or even if you want to have it detected. If you hit the right note it doesn't matter what string you played, maybe you want to play in a different way for some reason. 

Nice idea with having it work on more instruments, ideally it would work with a mic. I play classic guitar and I don't have a mic in my guitar.

---

### Post by JimKurth on 2008-02-17
There is a lot of misconception but even though it's the same note, it will have a slightly different timbre when played on different strings.  If you practice learning different sounds of the same note, you'll notice slight variations based on the thickness of the strings.  Some things that change are the Attack/Sustain/Delay/Release of fretting the string as well as the fundamental frequencies.  Well, I could go into more detail, being an audio engineer college grad, but it's more complicated than it sounds.  

I didn't even notice there was a game like this in the making.  I know I posted articles about this idea a little over a year ago (around Fall 2006).   I wonder if this software is the result from looking at my concept I posted long long ago.

A way to improve processor performance and do things almost real-time is to convert the audio signals into MIDI messages and then process those rather than take samples of audio at real-time.  When you calibrate the guitar frets on each string, it will assign it a MIDI note with a specific velocity and a specific modulation value.  That modulation value will change for the same note on different strings.  Say, an A3 on the 6th string will have a MIDI note of A3, a modulation value of say -16384, and an A3 on the 5th string (open) will have a MIDI note of A3 and a modulation value of 0.  The MIDI modulation parameter ranges from -32767 to 32767.  The range should be separated so that accuracy can be checked and assigned for the performance.  

MIDI is very fast to process and small rather than real-time processing.  Of course we could outfit the guitar with a MIDI connector but that costs more $$ for the person.  If we calibrate each string/fret and assign a MIDI message to each sound produced than we don't need a MIDI connector.

It's a lot more complicated to program and devise how to do this (incorporating chords) but there are methods to do this.  

This program link you sent me sounds very neat and I'm going to check it out more (possibly buy it later if it's worth it).

---

### Post by rbprogrammer on 2008-02-17
> **JimKurth said:**
> 
...
* Before playing the game, you will calibrate each note you can play with the computer (it'll record and make a mental note of the frequencies to play that note).  For a guitar, you will pluck every fret on every string so the computer will recognize the difference between 1 note on 1 string and the same note on another string.
...

i'm not good enough to help you, but this sounds like a great idea.  But someone with a bit of a mathematical background ( not sure if you are or not ) but instead of the computer having to remember each note, you could just code that directly into the program.  Certain notes correspond to certain frequencies.  Exactly how your guitar tuner works.  It just knows the frequency of the note and determines how off the input frequency is.

---

### Post by rbprogrammer on 2008-02-17
in addition to that, you might be able to find a computer engineer ( i'm just not up to that point in college yet to help you ) that can jerry rig one of those bose guitar tuners ( or maybe any type of tuner ) that will determine the note played, and then send a signal to the computer that a program can handle.

---

### Post by ruy_lopez on 2008-02-17
There's some linux guitar tuners at the top of this page, you could adapt them:

[http://sound.condorow.net/guitar.html]("http://sound.condorow.net/guitar.html")

---

### Post by Bruce H. McCosar on 2008-02-17
An interesting idea.  However . . . .

I think the hidden assumption here is that learning to play riffs note-for-note in exact, robotic time will enable one to learn any musical style.  It's a nice idea, but if it were true, MIDI programs wouldn't have "humanize" functions -- intentionally adding a bit of chaos to the velocity and timing.  I know for certain this wouldn't work for jazz or latin.  Even standard notation fails for the subtle levels of swing and rhythm it takes to sound authentic.

A better idea . . . I've never played the game 'guitar hero', but I think a better one would be sort of a play on those Music Minus One CDs . . . a virtual band that attempts to accompany you on a tune, but also responds to the variations in your playing style.  Even a drum program that could flexibly pace the amount of swing, or could play a bit ahead or behind the beat for effect.  Or a virtual bass player that could really groove, not just play canned patterns.

Or, better yet, a band that could quit and walk out when you start playing like crap ;-)

I say this advisedly, because there's nothing worse than going to see a jazz band, and hearing the guitarist whack away note-for-note at every Pat Metheny riff they've ever learned.  How much better if we could all practice with a band . . . even when a band isn't available.  And get intelligent feedback.

Hmm.  22nd century technology?  Probably.  Deckard will be in my house asking me if I've ever flipped over a tortoise before this becomes possible.

I can dream, though.

---

### Post by JimKurth on 2008-02-17
> **Bruce H. McCosar said:**
> An interesting idea.  However . . . .

I think the hidden assumption here is that learning to play riffs note-for-note in exact, robotic time will enable one to learn any musical style.  It's a nice idea, but if it were true, MIDI programs wouldn't have "humanize" functions -- intentionally adding a bit of chaos to the velocity and timing.  I know for certain this wouldn't work for jazz or latin.  Even standard notation fails for the subtle levels of swing and rhythm it takes to sound authentic.

A better idea . . . I've never played the game 'guitar hero', but I think a better one would be sort of a play on those Music Minus One CDs . . . a virtual band that attempts to accompany you on a tune, but also responds to the variations in your playing style.  Even a drum program that could flexibly pace the amount of swing, or could play a bit ahead or behind the beat for effect.  Or a virtual bass player that could really groove, not just play canned patterns.

Or, better yet, a band that could quit and walk out when you start playing like crap ;-)

I say this advisedly, because there's nothing worse than going to see a jazz band, and hearing the guitarist whack away note-for-note at every Pat Metheny riff they've ever learned.  How much better if we could all practice with a band . . . even when a band isn't available.  And get intelligent feedback.

Hmm.  22nd century technology?  Probably.  Deckard will be in my house asking me if I've ever flipped over a tortoise before this becomes possible.

I can dream, though.

Of course nobody will learn a style based on playing a composed piece note-by-note because of the accented notes and velocities/hardness of the playing not to mention the rhythm.  

In my game concept, each song will play out and the hidden part that the players won't see will be the chord changes in the song.  And each song will be in a certain Key (as always).  This would allow more freedom to freestyle solos and play something in minor or major scales and it won't be resolved as bad unless your notes are off-key and sometimes off-tempo.  It doesn't take much for humans to hear something off-key and it's a simple algorithm.  If the song is dictated as a sad song, then minor scales will be accepted but major won't (Try to imagine listening to Everybody Hurts by REM and play a major chromatic scale to the song.  Even if it's in key, it won't sound right at all).

Now, how to deal with if the computerized band members or audience will like it or not?  Well, usually it takes about a second or two to notice and detect a note out of key during the song.  To handle this, we could have the player play the guitar and whatever is played goes Straight into it's audio processor (distortion, chorus, etc) and back out into the speakers, and whatever was played before will get placed into a temporary buffer which will decide if it's accurate in time and in key.

To handle chord strumming, we can have them play each chord used in the piece and calibrate it to a MIDI note as well before the player plays (you're just not going to start playing in front of an audience without any practice), then we'll check for that note when the time comes during the performance.  Since MIDI is a single message, you can't say A3 + C#4 + E4 + A4 into one note, so you'd have to use something not used before (higher octave notes that the guitar cannot play, like C8-B8).

I like the idea of the band getting off stage to walk out on you, and that would be great to set up in the beginning of the game.  Maybe have an audition for singer and other band members and recruit them into the band of your choice (hire a heavy metal drummer for a country band would produce crazy results)...

---

### Post by Bruce H. McCosar on 2008-02-17
> **JimKurth said:**
> It doesn't take much for humans to hear something off-key and it's a simple algorithm . . . .

I like the idea of the band getting off stage to walk out on you, and that would be great to set up in the beginning of the game.  Maybe have an audition for singer and other band members and recruit them into the band of your choice (hire a heavy metal drummer for a country band would produce crazy results)...

Well -- I find the first point is a matter of tolerance.  Chromatic approach notes generally fly right past the radar, provided they're not on strong beats.  Blues and rock in particular make use of some unconventional notes -- the #11 and #9 in the blues scale; phrygian scales (minor with b9 and b13) in heavy metal tunes; chromatic approaches (for example, the funk line E7, E7, E7, D7-D#7- | E7 ... ).  That passing D#7 is almost exactly every 'wrong' note . . . sure is funky, though.

The second point -- now you're talking.  I'd almost pay for a game like that (if I didn't spend so much time playing music in real life, lol).  Then you could work wacky (but realistic) *venues* into the equation:

1. The stage behind the chicken wire from Blues Brothers.

2. That nightmare gig venue . . . a crack house, or the place where all these students live that hasn't been cleaned in like forever.  Musicians all, eventually, get that "worst place we ever played" story.

3. Or the club run by a moron that books two additional out of town acts on a bill already featuring three local bands (considering the shows don't start until 11 pm, and the bars have to close at 2 pm). [True story -- place is closed, now.]

I saw a pretty good folk rock act around town -- they had a heavy metal drummer.  He had more cymbals, in more shapes, than I'd ever seen.  But he was great.

---

### Post by JimKurth on 2008-02-18
> **Bruce H. McCosar said:**
> Well -- I find the first point is a matter of tolerance.  Chromatic approach notes generally fly right past the radar, provided they're not on strong beats.  Blues and rock in particular make use of some unconventional notes -- the #11 and #9 in the blues scale; phrygian scales (minor with b9 and b13) in heavy metal tunes; chromatic approaches (for example, the funk line E7, E7, E7, D7-D#7- | E7 ... ).  That passing D#7 is almost exactly every 'wrong' note . . . sure is funky, though.

The second point -- now you're talking.  I'd almost pay for a game like that (if I didn't spend so much time playing music in real life, lol).  Then you could work wacky (but realistic) *venues* into the equation:

1. The stage behind the chicken wire from Blues Brothers.

2. That nightmare gig venue . . . a crack house, or the place where all these students live that hasn't been cleaned in like forever.  Musicians all, eventually, get that "worst place we ever played" story.

3. Or the club run by a moron that books two additional out of town acts on a bill already featuring three local bands (considering the shows don't start until 11 pm, and the bars have to close at 2 pm). [True story -- place is closed, now.]

I saw a pretty good folk rock act around town -- they had a heavy metal drummer.  He had more cymbals, in more shapes, than I'd ever seen.  But he was great.

First point, yes, there are ways around the system but there always is with anything.  I guess it's a matter of how the melody ties with the notes played over it.  Jam bands are notorious for their constant playing in one scale and no direction as well as no repetition.  Better yet, here's an idea... if you lose the game, instead of having to restart where you left off at and using a continue or a previous save, how about you must perform an 8 minute jam session in a certain key, and you must only use those notes in that key in order to replay where you left off at?     Okay, okay, I don't want the body of the guitar to go swinging into the monitor screen so maybe that will have to be left out. ;)

Second point...good idea about the venues.  That is very true about bands.  There's always one place that makes the band think, "why did i even want to do this?".  Maybe start the band off as bands usually do... playing around in open mic nights at the local bars, and then move up to local club scenes after the clubowners like your demo (how about u make your own demo from a selection of different covers to play) and they allow u to perform there after paying the hefty fees.  Then you splurge all the dough on a van to take you out of the city and then finally you get to be the person that books where you'll play next (you create your own tour, whether it's throughout the country, world, regions, state, etc) but you'll end up losing your hard earned cash for fuel and food while out on the road not to mention oil changes and mechanical problems; so you must plan your tour accordingly to what you think you can make with your skills.  In other words, don't plan a national tour if you can't afford the gas to go the distance.  Also, bands must buy their own effects and amplifiers..   why not include this in your budget in the game?  That also ties in with your weight allowance in your van.... it's all connected like a spiderweb.

This is really starting to sound like an awesome interactive game that hasn't been made yet.  I really want in on this...  heh.

---

### Post by Bruce H. McCosar on 2008-02-18
> **JimKurth said:**
> ...Also, bands must buy their own effects and amplifiers..   why not include this in your budget in the game?  That also ties in with your weight allowance in your van.... it's all connected like a spiderweb.

This is really starting to sound like an awesome interactive game that hasn't been made yet.  I really want in on this...  heh.

Hmm.  Buying equipment, weight allowances . . . experience points?  Hey, this has sort of got that "D&D" vibe going :D

All we need now is 1.) Magic, and 2.) Monsters.

Magic
-------

Ability to purchase special talents or powers.  For example, Ace might decide on ability to vomit blood on stage; Eddie might want super speed macros for playing riffs (eg playing A-G while pushing the 'ALT' key on the guitar plays the entire solo from 'eruption' at 3x speed).

Also could include Magic Artifacts, such as +4 Stratocaster of Stevie Ray Vaughn, or the Cloak of Rehab.

Monsters
-----------

Enemy bands, like Scum of the Earth, or The Good Ole Boys (cf Bob's Country Bunker, the chicken wire venue mentioned above).

Predatory music industry personnel.  The RIAA.  Tabloid journalists.

Crazed fans.  Groupies.  That drunk lady at the bar who keeps asking you to play something she *knows*.

Critics ;-)

Actual monsters, if that Cloak of Rehab doesn't do the trick.  Maybe even a chorus line of purple wombats singing show tunes . . . .

---

