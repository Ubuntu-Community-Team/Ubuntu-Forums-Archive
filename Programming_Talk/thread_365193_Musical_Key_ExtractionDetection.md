---
title: "Musical Key Extraction/Detection"
date: 2007-02-19
forum: Programming Talk
---

### Post by skinny on 2007-02-19
Hi folks,

Does anyone know of a utility which extracts the musical key of an audio file?  The sort of tool I'm looking for is ideally command line based.  I've spent several hours attempting to hunt one down but with no real luck.  I'm not entirely comfortable attempting to implement one from scratch as I've no DSP experience, and my C programming skills leave something to be desired, although if anyone has a solid algorithm for it and a bit of time to explain it or answer any questions from me I would be willing to consider it.  I'm currently midway through a project in Java and would dearly like to add this functionality in some form.

All suggestions or pointers welcome.

cheers,

$

---

### Post by Wybiral on 2007-02-19
Hmm... Can you read the frequency of a given channel in the audio? If so, I think I know enough about music and note theory to help (I know how to find the frequency of any given note... And I could probably write an algorithm to do the opposite)

OR... You could check out guitar tuners. I use gtkguitune to tune my electric (via the microphone plugin) and maybe you can check out their source and see how they determine the notes. There are a handful of other decent guitar tuners out there for linux.

EDIT:

Oh... WOW... You mean detect the key note of a song, not the individual notes? If so... Wow! That sounds complex. Well, there is no KEY, because there are a ton of factors involved there... For instance, one mode of the major scale in key X would be the same notes as another mode of the major scale in key Y because the modes are simply a shifted version of the same scale. So that means, even if two songs use the same scale... They can be different modes of that scale and entirely different "keys" but still have the same notes used in the song.

The only thing the key does is determine the root note... Which mostly only affects the chord progression. But, unfortunately music is art... And a very free form of art. Songs from different genre's, countries, and even artist's will use this music theory different and may altogether disregard scales and chord progressions all together... The "key" may even change from chorus to verse...

The key is really only useful when you're playing music... If someone says play the harmonic minor scale in the key of "D", I know what notes to play. But another mode of the harmonic minor will have the same notes in a completely different key... Needless to say, this would be a nearly impossible chore for a program to do.

You might be able to detect the prominent notes in a progression and list the possible scales that the song uses... Then the user could maybe narrow it down to which key it's in. But like I said... It HEAVILY depends on a lot of factors...

---

### Post by kidders on 2007-02-19
Hi there,

I was fascinated by this post, and I've done some digging around. It's certainly a far more advanced question than the kind of thing that typically turns up on the Ubuntu forum! Depending on how much you already know about this problem, my post could be totally useless to you ... I'm sorry if that's the case.

If, for simplicity's sake, you started with a WAV file (which contains no information about pitch), extrapolating its key effectively amounts to converting it to a MIDI file ... albeit a very rough one. Doing that would be non-trivial (I'm busy trying to resurrect my memory of the maths of it from college!), and you would have to place some pretty draconian limitations on what could be in the WAV to begin with.

As far as I can make out, successfully identifying the musical key of a waveform...[LIST]
[*]Would depend on having a single, possibly polyphonic (if you're feeling ambitious) instrument line ... preferably not vocal.
[*]Background noise would seriously impact the accuracy of your algorithm, without even more nasty maths to try to compensate for it.
[/LIST]

I've stumbled across a few attempts at writing WAV->MIDI converters over the past hour or so. Naturally, there'd be a lot of work going on in such programs that would be of no use to you (eg working out instruments & note durations), but if it's the end result (rather than the actual coding) that's most important to you, I would suggest borrowing a pre-existing converter. That way, establishing what key a tune fragment is in would be (comparatively) trivial.

Sorry if this post is a waste of your time.

**Edit:**
While I've been writing this, Wybiral has posted too.

The thing that makes guitar tuners easy to write is that, not only is the sound being played a single instrument line, but it's monophonic ... one continuous note, in fact. A program can easily plot the waveform, and identify its frequency. As far as I can make out, doing that over the course of an entire musical phrase is quite tricky ... and processor intensive! I'd love to learn how though!

---

### Post by Lux Perpetua on 2007-02-19
> **skinny said:**
> Hi folks,

Does anyone know of a utility which extracts the musical key of an audio file?  The sort of tool I'm looking for is ideally command line based.  I've spent several hours attempting to hunt one down but with no real luck.  I'm not entirely comfortable attempting to implement one from scratch as I've no DSP experience, and my C programming skills leave something to be desired, although if anyone has a solid algorithm for it and a bit of time to explain it or answer any questions from me I would be willing to consider it.  I'm currently midway through a project in Java and would dearly like to add this functionality in some form.

All suggestions or pointers welcome.

cheers,

$Music likes to modulate in pitch, and some music has no home key at all (atonal music). However, assuming the music is tonal, doesn't modulate, and mostly follows classical tradition, you would probably want to identify the periods and look at the harmonies ending the periods. More generally, this style of music has a hierarchical structure: phrases can be grouped into periods, which can be grouped into larger units, and so on. The really big units usually end on the really important harmonies. The biggest unit, of course, is the entire piece, so as a first naive approximation, you could just look at the last harmony of the piece. The problem with that is if the piece is part of a larger work, it might lead into the next movement by modulating to the dominant in the key of the next movement right before the end. Also, many minor mode classical pieces end on the parallel major tonic chord (Picardy third, anyone?). Moreover, if you're dealing with modern popular music, then you surely know that some songs modulate and never return to their original key. This is actually a violation of the assumption that the piece has a well defined key, but if you care about modern songs at all, then you need to think about this. 

I don't see a way to accomodate varying styles of music other than your code being a conglomeration of special cases along with some AI to pick the one that fits the best, but I'm not the expert on this, so do your own research, and you might find or think of something. Also, as I mentioned, there are some popular styles of music for which the assumptions of your question don't hold. You wouldn't be able to account for atonal or probably even slightly tonal music, like modal jazz.

---

### Post by kidders on 2007-02-19
I agree entirely with Lux Perpetua ... the whole exercise, from the extraction of notes to determining what it's reasonable to infer from them, would be very, very approximate. 

For instance, harminonics & background noise would interfere with your ability to accurately determine what note you're listening to at any one moment in time, and (as Lux has noted) even if you *did* establish that you had a C#, you wouldn't be able to pair that with previous occurrances of F# to conclude you were in D major.

There *must* be little tricks you could use to boost accuracy by experimentation though.

I've been tinkering around with extracting information from the result of performing a rough WAV->MIDI conversion since my last post, just to see what I would end up with. It would be interesting to know just *how* bad a quick, hacky solution to the o/p would be!

---

### Post by KoRnholio on 2007-02-19
As has been echoed before, any solution is only going to work for certain, simpler songs, almost totally void of any modulation.  

Most of my thoughts on the subject have already been stated by others - find the notes that are centered around periods of higher intensity.

The only thing I have to add is that you can also try and find dominants resolving to tonic.  Any tonal composition/song is going to have a lot of fifths and sevenths going to the root.  So if there's two tones which occur frequently, and one of them is a fourth apart, the higher one is likely your home key.  The same for any minor second intervals.

The hardest part though is making sense of all the overtones, though. like kidders said.

---

### Post by Doovoo on 2007-02-19
I don't see how this could be possible (or dependable) with anything but midi, but if somebody does decide to code this, my hat's off to you. You're going to have to account for alot of different variables, but these could be reduced by implementing a user interface. For instance, were you able to input things you already knew about the song or parts of the song (like the time signature, style, a sort of rough modulation threshold etc.) you could have it assume certain things about it.

I'm interested in hearing what applications this kind of code could have. Clearly the OP has something in mind.

---

### Post by yaaarrrgg on 2007-02-20
There's a lot of research in this area, although reading through it probably won't be that enjoyable unless you like math (probably will need Fourier analysis). :) 

Although my opinion is that this problem is solvable without much math at all.  Humans can already do this, and they don't need to solve hundreds of differential equations to do so.

If you want to skip this and try something off the cuff, start looking at natural solutions to the problem, and then try to model it:

First off, look at the cochlea: [http://en.wikipedia.org/wiki/Image:Gray921.png](http://en.wikipedia.org/wiki/Image:Gray921.png)

My first guess on what's happening:  the hammer sets up vibrations (running lengthwise and decaying with time) in the water which form standing waves.  Then the tiny hairlike nerves detect these standing waves and convert the information into frequency data.  Maybe try to model this as an  array, each peak impluse would enter the array, and travel back and forth until decaying.  Its simple to add and subtract the waves, but this will be computationally expensive... not sure it will run in real time.

---

### Post by skinny on 2007-02-21
Hi all & thanks for the responses.

Firstly I haven't looked much into the midi conversion idea, but will be looking further into this. Cheers for the heads up :)

Secondly, I'm aware of the tedious amounts of maths that may be involved, as well as the presence of a Fourier Transform or two. Indeed, upon discussing this problem some time ago with a friend, I was told

"A simply FFT would do the trick I believe, certainly if you only want to check
major vs minor. If you want to verify the key then you need to count the
distribution as well and filter out the baseline very likely"

which meant absolutely nothing to me at the time but now I'm looking into understanding it by first understanding the maths behind Fourier Transforms etc.

> I'm interested in hearing what applications this kind of code could have. Clearly the OP has something in mind.
The application I'm attempting to (very slowly) piece together is rather like a glorified jukebox which mimics what some DJs do for a set.  Tracks must be mixed unless stated otherwise, so bpms and keys must be compatible.

The user points the application at their music directory, which is analysed and various details for each track are recorded into a database.  The user then specifies a set length (playlist length), and plots some points on a set graph, which dictates what the tempo (bpm) of the track should approximately be at that time in the set.  Then the user clicks "go", and a set is produced.

For example, say I want the set to run for three hours, starting with some hip-hop style 90bpm or so tracks, and then climb to 140bpm after a while before dipping back down to 115bpm just near the end.

Early prototypes are working ok, but don't include the automatic detection of musical key, therefore some mixes that are proposed by the application will never sound good because the key clash sours it, even if the bpms are fine.

For further information about this form of harmonic mixing I'd suggest perhaps looking at [DJ Prince's site]("http://www.djprince.no/").
Best example I've seen so far of a musical key detection tool is [tONaRT] (zplane used to have a free demo of it available for windows although I'm not sure if it's still available) but I'm not looking to just buy a solution. I want one that's free, or not at all.

yaaarrrgg: you've got an interesting approach but think I'm going to try the (boring) orthodox avenue first with further Fourier investigations....

$

---

### Post by yaaarrrgg on 2007-02-21
> **skinny said:**
> Hi all & thanks for the responses.
yaaarrrgg: you've got an interesting approach but think I'm going to try the (boring) orthodox avenue first with further Fourier investigations....
$

Ah... that's fine, they are not too hard but I'm a bit rusty in that area of math.  Probably will work well  though.  :)

Also, it occured to me, given your description of the application, that you might only need to try looking at the mixed regions then (rather than the key of the entire song) and try to measure (or quantify) the dissonance in them.    

If you have n songs, it might not be hard to build a list of all possible mixed regions... crossing the begining and ends of songs at the proposed cut points, then pick a chain that minimized the dissonance of the mixed regions.

Dissonant waveforms will be much more wavey, or turbulent looking IIRC, and may be easier to quantify.  This might be simpler and more robust than going for the key, since some songs may end on a different chord than the root of the key (like a deceptive cadence) or jump around a few keys.

---

### Post by kidders on 2007-02-21
Hi guys,

I've been tinkering with a _very_ hacky solution to this question, to try to get a general feel for how much work would be involved. I figured I should post a quick summary, on the off-chance any of it might be useful.

Basically, I was interested in how easy it would be to programatically identify key features of music, assuming I had access to all the information I could want. Actually *getting* the information in the first place is (as has been noted) so complex, that I wanted to give myself some insight into where the major stumbling blocks would be, assuming the transition between physics & music could be made.

I used other peoples' work to convert some simple little MP3s to MIDIs, extracted a list of MIDI events, and used them to recreate a linear description of the tunes ... except I could now *name* the notes being played at any given time. I decided that trying to calculate a list of chord progressions would be a good start. Naive little old me imagined that if I could somehow distill a tune to a simple array that went, for example, { D, A, b, f#, G, A, D }, that there would be only so many possible choices of key. I defined a huge list of cadences and common chord progressions, paired them with the key they are suggestive of, and iterated over the tune, with a view to outputting the number of "suggestive" note/chord sequences per key, at the end.

Needless to say, my attempt was a _complete_ flop! The three main reasons seem to be:

[LIST=1]
[*]I had failed to come up with any way of distinguishing the relative significance of notes occurring in sequence. Compare, for instance, the tunes of Arrival of the Queen of Sheba (Handel) and Papa Don't Preach (Madonna). In one case, almost all the notes contribute towards the chord underlying the tune at the time they're heard ... in the other, my code would have no way of knowing which ones to disregard. (I wondered about using percussion channels to help with this.)
[*]Even if I *had* been clever enough to address the first issue, I would still have gotten nowhere, since I had lost any way of positioning individual notes in the context of a bar or a phrase. That meant that my code thought it was being very smart when it "identified" things like plagal cadences, considered such a conventional musical artefact a dead give-away, and picked the wrong key.
[*]Simplistic tunes broke my code, because there was not enough information to identify chords correctly.
[/LIST]

So, my question is how many of you will be able to resist saying "Ha! You idiot!". :lolflag: Do you guys suppose that *anything* about this approach is even vaguely sensible? I'm not so sure I do.

---

### Post by Wybiral on 2007-02-21
Here are the seven modes of the major scale...

Ionian (C), D, E, F, G, A, B
Dorian (D), E, F, G, A, B, C
Phrygian (E), F, G, A, B, C, D
Lydian (F), G, A, B, C, D, E
Mixolydian (G), A, B, C, D, E, F
Aeolian (A), B, C, D, E, F, G
Locrian (B), C, D, E, F, G, A

The note in the parenthesis is the root note. They all have a completely different sound, but they all share the same notes! So say you find the progression "GAB"... It's probably the Mixolydian right, putting it in the key of G... But it doesn't necessarily mean that it is for sure (notice how it's also a progression of the first four modes as well)

Basically, my point is that I think it's possible to create a program that narrows it down and gives a few options for what the key is... But I don't think you can just say for sure.

---

### Post by TrinitronX on 2011-11-01
For what it's worth, here's a description of how the tONaRT algorithm works (reference [here]("http://www.zplane.de/index.php?page=description-tonart")):

> [tONaRT] key detection automatically determines the  key signature of any audio input signal, either monophonic or  polyphonic. Key recognition can be useful in mixing applications to  check if the keys of different tracks are "compatible" or for automatic  generation of high-level meta data information (e.g. ID-Tags). As a  special feature, [tONaRT] also detects the tuning frequency, or standard  (concert) pitch of the input signal.

 The input signal is analyzed about its tonal content  (pitches) via a filterbank. The filterbank's mid-frequencies are  constantly adapted due to the detected standard pitch to increase the  detection accuracy. The resulting pitch distribution is analyzed with a  sophisticated probability model to check for the most likely key acc.  the detected pitch strengths. The detection accuracy is ca. 80 percent,  compared to a random detection accuracy of only 4 percent. When  classifying related keys as correctly detected, the detection accuracy  is well above 90 percent, making [tONaRT] a reliable and robust  technology for automatic key detection. The standard pitch detection has  an accuracy of app. 1-2Hz at 440Hz.
It sounds complicated, but probably isn't too bad.  The "filterbank" is a bunch of bandpass filters (BPF), each centered around the frequency of a note.  They are dynamically re-centered depending on the "standard pitch".  My guess is that the standard pitch is found using an FFT.  The output of these BPF's are statistically analyzed to determine the key.  The statistical model part is probably the hard part to figure out (what model does it use?).  It seems very similar to DTMF decoding, however the input is much more complex.

The statistical model method may be similar to a "language detection" problem for characters.  Each language has a probability distribution of most frequently used characters.  Just count the number of each character in a sample of text, then compare to the model.  There are programs that can detect a language based on this.  Simple ROT13 or substitution cipher cracking programs use a similar method to do their work.

I'd make the analogy here that in this problem, each musical note can be treated like a character, and each key can be treated like a language.

---

